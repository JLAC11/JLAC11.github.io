---
title: "Credit Modelling"
---

Recently, I've thought a lot about the credit conditions here in Mexico.

<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>PSA Mortgage Simulator</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link
      href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@300;400;500;600&family=IBM+Plex+Sans:wght@300;400;500&display=swap"
      rel="stylesheet"
    />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
  </head>
  <body>
    <div class="shell">
      <header>
        <div class="header-left">
          <h1>PSA Mortgage Simulator</h1>
          <p>Prepayment · Amortization · Duration · Rate Sensitivity</p>
        </div>
        <span class="header-badge">OTS / Richard-Roll Model</span>
      </header>

      <!-- Controls -->
      <div class="controls-grid">
        <div class="control-block">
          <label>Mortgage Coupon</label>
          <div class="control-row">
            <input
              type="range"
              min="2"
              max="15"
              step="0.1"
              value="6.5"
              id="sl-rate"
            />
            <span class="control-val" id="v-rate">6.5%</span>
          </div>
        </div>
        <div class="control-block">
          <label>Market Rate</label>
          <div class="control-row">
            <input
              type="range"
              min="1"
              max="15"
              step="0.1"
              value="6.5"
              id="sl-mkt"
            />
            <span class="control-val" id="v-mkt">6.5%</span>
          </div>
        </div>
        <div class="control-block">
          <label>Term (years)</label>
          <div class="control-row">
            <input
              type="range"
              min="5"
              max="30"
              step="5"
              value="30"
              id="sl-years"
            />
            <span class="control-val" id="v-years">30</span>
          </div>
        </div>
        <div class="control-block">
          <label>PSA Override</label>
          <div class="control-row">
            <input
              type="checkbox"
              id="sl-override-toggle"
              title="Toggle manual PSA"
            />
            <span
              class="control-val"
              id="v-override-label"
              style="font-size: 11px; color: var(--text3)"
              >Auto</span
            >
          </div>
        </div>
        <div class="friction-block">
          <label>Refinancing<br />Friction</label>
          <span class="friction-desc"
            >Shifts S-curve rightward — higher = greater barriers (legal costs,
            notary, thin secondary market)</span
          >
          <input
            type="range"
            min="0"
            max="0.6"
            step="0.05"
            value="0"
            id="sl-friction"
            style="width: 180px"
          />
          <span class="friction-val" id="v-friction">0.00 — US baseline</span>
        </div>
      </div>

      <!-- Manual PSA row (hidden by default) -->
      <div id="manual-psa-row" style="display: none; margin-bottom: 16px">
        <div
          class="control-block"
          style="display: flex; align-items: center; gap: 16px"
        >
          <label style="margin: 0; white-space: nowrap">Manual PSA %</label>
          <input
            type="range"
            min="0"
            max="600"
            step="10"
            value="150"
            id="sl-psa"
            style="flex: 1"
          />
          <span class="control-val" id="v-psa">150%</span>
        </div>
      </div>

      <!-- Implied PSA -->
      <div class="psa-pill">
        Implied PSA (S-curve): <b id="implied-psa">—</b>
        <span class="psa-tag" id="psa-mode-tag">RATE-DEPENDENT</span>
      </div>

      <!-- Metrics -->
      <div class="metrics-grid">
        <div class="metric-card">
          <div class="metric-lbl">WAL</div>
          <div class="metric-val" id="m-wal">—</div>
          <div class="metric-sub">years · principal timing</div>
        </div>
        <div class="metric-card">
          <div class="metric-lbl">Modified Duration</div>
          <div class="metric-val" id="m-dur">—</div>
          <div class="metric-sub">years · price sensitivity</div>
        </div>
        <div class="metric-card">
          <div class="metric-lbl">Effective Duration</div>
          <div class="metric-val" id="m-edur">—</div>
          <div class="metric-sub">years · ±100bps OAS adj.</div>
        </div>
        <div class="metric-card">
          <div class="metric-lbl">Peak CPR</div>
          <div class="metric-val" id="m-cprmx">—</div>
          <div class="metric-sub">annualized prepay rate</div>
        </div>
        <div class="metric-card">
          <div class="metric-lbl">Total Prepaid</div>
          <div class="metric-val" id="m-prep">—</div>
          <div class="metric-sub">of $100k notional</div>
        </div>
      </div>

      <!-- Tabs -->
      <div class="tab-bar">
        <button class="tab-btn active" id="tab-amort">Amortization</button>
        <button class="tab-btn" id="tab-prepay">CPR / SMM</button>
        <button class="tab-btn" id="tab-scurve">Refinancing S-curve</button>
        <button class="tab-btn" id="tab-ratesens">Rate Sensitivity</button>
      </div>

      <!-- Amortization -->
      <div class="chart-panel active" id="panel-amort">
        <div class="legend-row">
          <span class="legend-item"
            ><span class="l-line" style="background: #4a9eff"></span>Actual
            balance</span
          >
          <span class="legend-item"
            ><span class="l-dash" style="border-color: #4a6080"></span>Scheduled
            (no prepay)</span
          >
        </div>
        <div class="chart-wrap">
          <canvas
            id="ch-amort"
            role="img"
            aria-label="Amortization: actual vs scheduled balance"
          ></canvas>
        </div>
      </div>

      <!-- CPR/SMM -->
      <div class="chart-panel" id="panel-prepay">
        <div class="legend-row">
          <span class="legend-item"
            ><span class="l-line" style="background: #00d4aa"></span>CPR % (left
            axis)</span
          >
          <span class="legend-item"
            ><span class="l-line" style="background: #ff6b6b"></span>SMM %
            (right axis)</span
          >
        </div>
        <div class="chart-wrap">
          <canvas
            id="ch-prepay"
            role="img"
            aria-label="CPR and SMM over loan age"
          ></canvas>
        </div>
      </div>

      <!-- S-curve -->
      <div class="chart-panel" id="panel-scurve">
        <div class="legend-row">
          <span class="legend-item"
            ><span class="l-line" style="background: #9b7fe8"></span>Implied PSA
            (current friction)</span
          >
          <span class="legend-item"
            ><span class="l-dash" style="border-color: #4a6080"></span>US
            baseline (friction = 0)</span
          >
          <span class="legend-item"
            ><span class="l-dot" style="background: #f0a500"></span>Current
            position</span
          >
        </div>
        <div class="chart-wrap">
          <canvas
            id="ch-scurve"
            role="img"
            aria-label="S-curve: implied PSA vs coupon/market ratio"
          ></canvas>
        </div>
      </div>

      <!-- Rate sensitivity -->
      <div class="chart-panel" id="panel-ratesens">
        <div class="legend-row">
          <span class="legend-item"
            ><span class="l-line" style="background: #4a9eff"></span>WAL</span
          >
          <span class="legend-item"
            ><span class="l-dash" style="border-color: #00d4aa"></span>Mod.
            duration</span
          >
          <span class="legend-item"
            ><span class="l-line" style="background: #f0a500"></span>Eff.
            duration</span
          >
          <span class="legend-item"
            ><span class="l-dash" style="border-color: #4a6080"></span>Implied
            PSA% (right)</span
          >
        </div>
        <div class="chart-wrap">
          <canvas
            id="ch-ratesens"
            role="img"
            aria-label="WAL, modified and effective duration, implied PSA across market rates"
          ></canvas>
        </div>
      </div>

      <footer>
        PSA model per Public Securities Association (1985) · S-curve
        calibration: OTS / Richard &amp; Roll (1989) · Effective duration via
        ±100bps finite difference with PSA re-pricing · $100,000 notional
      </footer>
    </div>

    <script>
      const NOTIONAL = 100000;
      const A = 0.2406,
        B = 0.1389,
        K = 5.952,
        THRESH0 = 1.089,
        CPR_FLOOR = 0.005;

      function scurveCPR(ratio, friction) {
        const thresh = THRESH0 + friction;
        const peakMax = A - B * Math.atan(K * (THRESH0 - 2.0));
        const peakF = peakMax * Math.max(0.2, 1 - friction * 1.2);
        const raw = A - B * Math.atan(K * (thresh - ratio));
        const scaled = CPR_FLOOR + (raw - CPR_FLOOR) * (peakF / peakMax);
        return Math.max(CPR_FLOOR, Math.min(scaled, peakF));
      }
      function scurvePSA(coupon, mkt, friction) {
        return Math.round((scurveCPR(coupon / mkt, friction) / 0.06) * 100);
      }
      function psaCPR(month, psaPct) {
        return Math.min(month * 0.002, 0.06) * (psaPct / 100);
      }
      function cprToSMM(cpr) {
        return 1 - Math.pow(1 - cpr, 1 / 12);
      }

      function buildSchedule(psaPct, couponRate, years, discountRatePct) {
        const n = years * 12,
          rc = couponRate / 100 / 12,
          rd = discountRatePct / 100 / 12;
        const pmt =
          rc > 0 ? (NOTIONAL * rc) / (1 - Math.pow(1 + rc, -n)) : NOTIONAL / n;
        let bal = NOTIONAL,
          balSched = NOTIONAL;
        const months = [],
          bals = [],
          balScheds = [],
          cprs = [],
          smms = [],
          allCFs = [];
        for (let m = 1; m <= n; m++) {
          if (bal < 0.01) break;
          const cpr = psaCPR(m, psaPct),
            smm = cprToSMM(cpr);
          const interest = bal * rc;
          const schedPrin = Math.max(0, Math.min(pmt - interest, bal));
          const prepay = Math.max(0, (bal - schedPrin) * smm);
          bal = Math.max(0, bal - schedPrin - prepay);
          const intS = balSched * rc,
            sp2 = Math.max(0, Math.min(pmt - intS, balSched));
          balSched = Math.max(0, balSched - sp2);
          allCFs.push({
            m,
            cf: interest + schedPrin + prepay,
            prin: schedPrin + prepay,
            prepay,
          });
          months.push(m);
          bals.push(+(bal / 1000).toFixed(3));
          balScheds.push(+(balSched / 1000).toFixed(3));
          cprs.push(+(cpr * 100).toFixed(3));
          smms.push(+(smm * 100).toFixed(4));
        }
        const totalPrepaid = allCFs.reduce((a, x) => a + x.prepay, 0);
        const peakCPR = cprs.length ? Math.max(...cprs) : 0;
        let walN = 0,
          walD = 0;
        for (const x of allCFs) {
          walN += x.m * x.prin;
          walD += x.prin;
        }
        const wal = walD > 0 ? walN / walD / 12 : 0;
        let pv = 0,
          macN = 0;
        for (const x of allCFs) {
          const df = Math.pow(1 + rd, -x.m),
            pvCF = x.cf * df;
          pv += pvCF;
          macN += (x.m / 12) * pvCF;
        }
        const mac = pv > 0 ? macN / pv : 0,
          modDur = mac / (1 + rd);
        return {
          months,
          bals,
          balScheds,
          cprs,
          smms,
          wal,
          peakCPR,
          totalPrepaid,
          modDur,
          pv,
        };
      }

      function effectiveDuration(coupon, mkt, years, friction, bumpBps = 100) {
        const bump = bumpBps / 10000;
        const psaUp = scurvePSA(coupon, mkt + bump * 100, friction);
        const psaDn = scurvePSA(coupon, mkt - bump * 100, friction);
        const psa0 = scurvePSA(coupon, mkt, friction);
        const pUp = buildSchedule(psaUp, coupon, years, mkt + bump * 100).pv;
        const pDn = buildSchedule(psaDn, coupon, years, mkt - bump * 100).pv;
        const p0 = buildSchedule(psa0, coupon, years, mkt).pv;
        return p0 === 0 ? 0 : (pDn - pUp) / (2 * p0 * bump);
      }

      let charts = {},
        activeTab = "amort",
        manualMode = false;

      // Dark chart colors
      const C = {
        blue: "#4a9eff",
        gray: "#4a6080",
        teal: "#00d4aa",
        coral: "#ff6b6b",
        purple: "#9b7fe8",
        amber: "#f0a500",
        grid: "rgba(100,160,255,0.07)",
        text: "#4a6080",
        bg: "#0f1520",
      };

      function chartDefaults() {
        return {
          responsive: true,
          maintainAspectRatio: false,
          animation: false,
          plugins: { legend: { display: false } },
        };
      }
      function xAxis(label) {
        return {
          title: {
            display: true,
            text: label,
            color: C.text,
            font: { size: 11, family: "IBM Plex Mono" },
          },
          ticks: {
            color: C.text,
            font: { size: 10, family: "IBM Plex Mono" },
            maxTicksLimit: 10,
          },
          grid: { color: C.grid },
        };
      }
      function yAxis(label, color) {
        return {
          title: {
            display: true,
            text: label,
            color: color || C.text,
            font: { size: 11, family: "IBM Plex Mono" },
          },
          ticks: {
            color: color || C.text,
            font: { size: 10, family: "IBM Plex Mono" },
          },
          grid: { color: C.grid },
        };
      }

      function destroyChart(id) {
        if (charts[id]) {
          charts[id].destroy();
          delete charts[id];
        }
      }

      function makeAmortChart(data) {
        destroyChart("amort");
        const step = Math.max(1, Math.floor(data.months.length / 80));
        const labels = data.months.filter((_, i) => i % step === 0);
        charts["amort"] = new Chart(document.getElementById("ch-amort"), {
          type: "line",
          data: {
            labels,
            datasets: [
              {
                data: data.bals.filter((_, i) => i % step === 0),
                borderColor: C.blue,
                borderWidth: 2,
                backgroundColor: "rgba(74,158,255,0.06)",
                fill: true,
                pointRadius: 0,
                tension: 0.3,
              },
              {
                data: data.balScheds.filter((_, i) => i % step === 0),
                borderColor: C.gray,
                borderWidth: 1.5,
                borderDash: [5, 4],
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
              },
            ],
          },
          options: {
            ...chartDefaults(),
            scales: { x: xAxis("Month"), y: yAxis("Balance ($k)") },
          },
        });
      }

      function makePrepayChart(data) {
        destroyChart("prepay");
        const step = Math.max(1, Math.floor(data.months.length / 80));
        const labels = data.months.filter((_, i) => i % step === 0);
        charts["prepay"] = new Chart(document.getElementById("ch-prepay"), {
          type: "line",
          data: {
            labels,
            datasets: [
              {
                data: data.cprs.filter((_, i) => i % step === 0),
                borderColor: C.teal,
                borderWidth: 2,
                backgroundColor: "rgba(0,212,170,0.06)",
                fill: true,
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "yCPR",
              },
              {
                data: data.smms.filter((_, i) => i % step === 0),
                borderColor: C.coral,
                borderWidth: 2,
                borderDash: [5, 3],
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "ySMM",
              },
            ],
          },
          options: {
            ...chartDefaults(),
            scales: {
              x: xAxis("Month"),
              yCPR: { position: "left", ...yAxis("CPR (%)", C.teal) },
              ySMM: {
                position: "right",
                title: {
                  display: true,
                  text: "SMM (%)",
                  color: C.coral,
                  font: { size: 11, family: "IBM Plex Mono" },
                },
                ticks: {
                  color: C.coral,
                  font: { size: 10, family: "IBM Plex Mono" },
                },
                grid: { drawOnChartArea: false },
              },
            },
          },
        });
      }

      function makeSCurveChart(coupon, mkt, friction) {
        destroyChart("scurve");
        const ratios = [],
          psas = [],
          psasBase = [];
        for (let r = 0.4; r <= 2.001; r += 0.02) {
          ratios.push(+r.toFixed(2));
          psas.push(Math.round((scurveCPR(r, friction) / 0.06) * 100));
          psasBase.push(Math.round((scurveCPR(r, 0) / 0.06) * 100));
        }
        const currentRatio = coupon / mkt;
        let bestIdx = 0,
          bestDist = Infinity;
        ratios.forEach((r, i) => {
          const d = Math.abs(r - currentRatio);
          if (d < bestDist) {
            bestDist = d;
            bestIdx = i;
          }
        });
        const dotData = ratios.map((_, i) => (i === bestIdx ? psas[i] : null));
        charts["scurve"] = new Chart(document.getElementById("ch-scurve"), {
          type: "line",
          data: {
            labels: ratios,
            datasets: [
              {
                data: psasBase,
                borderColor: C.gray,
                borderWidth: 1.5,
                borderDash: [3, 3],
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
              },
              {
                data: psas,
                borderColor: C.purple,
                borderWidth: 2.5,
                backgroundColor: "rgba(155,127,232,0.06)",
                fill: true,
                pointRadius: 0,
                tension: 0.3,
              },
              {
                data: dotData,
                borderColor: C.amber,
                backgroundColor: C.amber,
                borderWidth: 0,
                pointRadius: dotData.map((v) => (v !== null ? 8 : 0)),
                pointStyle: "circle",
              },
            ],
          },
          options: {
            ...chartDefaults(),
            plugins: {
              legend: { display: false },
              tooltip: {
                callbacks: { label: (ctx) => `PSA: ${ctx.parsed.y}%` },
                bodyFont: { family: "IBM Plex Mono" },
              },
            },
            scales: {
              x: xAxis("Coupon / market rate ratio"),
              y: yAxis("Implied PSA%"),
            },
          },
        });
      }

      function makeRateSensChart(coupon, years, friction) {
        destroyChart("ratesens");
        const mktRates = [],
          wals = [],
          mdurs = [],
          edurs = [],
          psaArr = [];
        for (let mr = 1.0; mr <= 14.01; mr += 0.25) {
          const psa = scurvePSA(coupon, mr, friction);
          const d = buildSchedule(psa, coupon, years, mr);
          const ed = effectiveDuration(coupon, mr, years, friction);
          mktRates.push(mr.toFixed(2) + "%");
          wals.push(+d.wal.toFixed(2));
          mdurs.push(+d.modDur.toFixed(2));
          edurs.push(+Math.max(0, ed).toFixed(2));
          psaArr.push(psa);
        }
        charts["ratesens"] = new Chart(document.getElementById("ch-ratesens"), {
          type: "line",
          data: {
            labels: mktRates,
            datasets: [
              {
                data: wals,
                borderColor: C.blue,
                borderWidth: 2,
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "yDur",
              },
              {
                data: mdurs,
                borderColor: C.teal,
                borderWidth: 2,
                borderDash: [4, 3],
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "yDur",
              },
              {
                data: edurs,
                borderColor: C.amber,
                borderWidth: 2.5,
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "yDur",
              },
              {
                data: psaArr,
                borderColor: C.gray,
                borderWidth: 1.5,
                borderDash: [2, 3],
                backgroundColor: "transparent",
                pointRadius: 0,
                tension: 0.3,
                yAxisID: "yPSA",
              },
            ],
          },
          options: {
            ...chartDefaults(),
            scales: {
              x: xAxis("Market rate"),
              yDur: { position: "left", ...yAxis("Years") },
              yPSA: {
                position: "right",
                title: {
                  display: true,
                  text: "Implied PSA%",
                  color: C.gray,
                  font: { size: 11, family: "IBM Plex Mono" },
                },
                ticks: {
                  color: C.gray,
                  font: { size: 10, family: "IBM Plex Mono" },
                },
                grid: { drawOnChartArea: false },
              },
            },
          },
        });
      }

      function frictionLabel(f) {
        if (f === 0) return "0.00 — US baseline";
        if (f <= 0.1) return f.toFixed(2) + " — minor friction";
        if (f <= 0.25) return f.toFixed(2) + " — moderate (e.g. UK)";
        if (f <= 0.4) return f.toFixed(2) + " — high (e.g. Mexico)";
        return f.toFixed(2) + " — very high friction";
      }

      function render() {
        const coupon = +document.getElementById("sl-rate").value;
        const mkt = +document.getElementById("sl-mkt").value;
        const years = +document.getElementById("sl-years").value;
        const friction = +document.getElementById("sl-friction").value;
        const overrideOn =
          +document.getElementById("sl-override-toggle").value === 1;

        document.getElementById("v-rate").textContent = coupon.toFixed(1) + "%";
        document.getElementById("v-mkt").textContent = mkt.toFixed(1) + "%";
        document.getElementById("v-years").textContent = years;
        document.getElementById("v-friction").textContent =
          frictionLabel(friction);

        manualMode = overrideOn;
        document.getElementById("manual-psa-row").style.display = overrideOn
          ? "block"
          : "none";
        document.getElementById("v-override-label").textContent = overrideOn
          ? "Manual"
          : "Auto";
        document.getElementById("psa-mode-tag").textContent = overrideOn
          ? "MANUAL"
          : "RATE-DEPENDENT";
        document.getElementById("psa-mode-tag").style.color = overrideOn
          ? "var(--amber)"
          : "var(--accent)";

        let psa;
        if (overrideOn) {
          psa = +document.getElementById("sl-psa").value;
          document.getElementById("v-psa").textContent = psa + "%";
          document.getElementById("implied-psa").textContent = psa + "%";
        } else {
          psa = scurvePSA(coupon, mkt, friction);
          document.getElementById("implied-psa").textContent = psa + "%";
        }

        const d = buildSchedule(psa, coupon, years, mkt);
        const ed = effectiveDuration(coupon, mkt, years, friction);

        document.getElementById("m-wal").textContent = d.wal.toFixed(2) + " yr";
        document.getElementById("m-dur").textContent =
          d.modDur.toFixed(2) + " yr";
        document.getElementById("m-edur").textContent =
          Math.max(0, ed).toFixed(2) + " yr";
        document.getElementById("m-cprmx").textContent =
          d.peakCPR.toFixed(2) + "%";
        document.getElementById("m-prep").textContent =
          "$" + (d.totalPrepaid / 1000).toFixed(1) + "k";

        if (activeTab === "amort") makeAmortChart(d);
        else if (activeTab === "prepay") makePrepayChart(d);
        else if (activeTab === "scurve") makeSCurveChart(coupon, mkt, friction);
        else if (activeTab === "ratesens")
          makeRateSensChart(coupon, years, friction);
      }

      function switchTab(t) {
        activeTab = t;
        document
          .querySelectorAll(".tab-btn")
          .forEach((b) => b.classList.toggle("active", b.id === "tab-" + t));
        document
          .querySelectorAll(".chart-panel")
          .forEach((p) => p.classList.toggle("active", p.id === "panel-" + t));
        render();
      }

      document
        .querySelectorAll(".tab-btn")
        .forEach((b) =>
          b.addEventListener("click", () =>
            switchTab(b.id.replace("tab-", "")),
          ),
        );
      [
        "sl-rate",
        "sl-mkt",
        "sl-years",
        "sl-friction",
        "sl-friction",
        "sl-override-toggle",
        "sl-psa",
      ].forEach((id) => {
        const el = document.getElementById(id);
        if (el) el.addEventListener("input", render);
      });

      render();
    </script>
  </body>
</html>
