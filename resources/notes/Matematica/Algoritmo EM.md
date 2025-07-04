# Algoritmo E-M

Algoritmo Expectation-Maximization. Se hace de manera iterativa.

A veces no se conocen todas las observaciones de un muestreo; por ejemplo, si se determina en modelos de supervivencias suele medirse hasta un tiempo $\tau$, y solo podríamos saber que los datos $X>\tau$.

Asumiendo que los datos completos tienen una densidad conjunta  $f(x;\theta)$ y que los datos observados tienen una densidad conjunta $g(y;\theta)$, y la densidad conjunta de los datos completos una densidad $k(x|y;\theta)$.
Entonces, queremos encontrar los parámetros $\theta$ tales que maximicen $f(x;\theta)$. Si se tiene acceso a las observaciones completas entonces los datos observados no agregan información por lo que, por la ley de probabilidad total:
$$f(x;\theta) = f(x,y;\theta)=k(x|y;\theta)g(y;\theta)$$
Y
$$\log f(x,y;\theta) = \log k(x|y;\theta)+ \log g(y;\theta)$$

Pero sin acceso a los datos $x$, solamente los observados $y$, entones se pueden fijar los parámetros a que sean $\phi'$:

En el paso $E$:
$$\begin{align}
Q(\phi|\phi') &= \mathbb{E}_{x\sim f(\cdot;\phi')}\log g(y;\theta) + \mathbb{E}_{x\sim f(\cdot;\phi')}\log k(x|y;\theta) \\ 
&= \log g(y;\theta) + \mathbb{E}_{x\sim f(\cdot;\phi')}\log k(x|y;\theta)
\end{align}$$
En el paso $M$: se encuentran los parámetros que maximicen $Q(\phi|\phi')$

Entonces, sea $x$ los datos completos y $y$ los datos observados, y que:
$$f(x,y|\theta) = f(x|\theta) = f(x|y,\theta) f(y|\theta)$$

Entonces, la *logverosimilitud* es la siguiente:
$$\log f(x|\theta) = \log f(x|y,\theta) + \log f(y|\theta)$$

Supongamos que $X\sim f(x|\theta^{(0)})$, entonces el valor esperado (paso E):
$$\begin{align}
\mathbb{E}_{X\sim f(x|\theta^{(0)})}\log f(x|\theta) &= \mathbb{E}_{X\sim f(x|\theta^{(0)})}\log f(x|y,\theta)+\log f(y|\theta) \\ &= Q(\theta|\theta^{(0)})\end{align}$$
Y maximizando (el paso M):
$$\theta^{(1)} = \arg\max_{\theta}Q(\theta|\theta^{(0)})$$

### Ejemplo:

Normal con censura por la derecha
---

excalidraw-plugin: parsed
tags: \[excalidraw\]

---

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Text Elements

t ^8lpP9BXe

1 ^ep2j196w

2 ^EqNEWK6y

3 ^avRjWLF4

X ^4LhQnUQB

%%

# Drawing

````json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://excalidraw.com",
	"elements": [
		{
			"type": "line",
			"version": 22,
			"versionNonce": 1826177758,
			"isDeleted": false,
			"id": "x3HhN3MuUNhmIs6QJ0Hzp",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -118.48631286621094,
			"y": -224.25379943847656,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 1.646881103515625,
			"height": 156.3471221923828,
			"seed": 437429442,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331302902,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					1.646881103515625,
					156.3471221923828
				]
			]
		},
		{
			"type": "line",
			"version": 35,
			"versionNonce": 88280514,
			"isDeleted": false,
			"id": "oTrkl_dOAsmzkyT4oaBok",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 108.04074096679688,
			"y": -77.5299072265625,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 225.6731719970703,
			"height": 0.91558837890625,
			"seed": 1517773314,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331305851,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					-225.6731719970703,
					0.91558837890625
				]
			]
		},
		{
			"type": "text",
			"version": 3,
			"versionNonce": 114780126,
			"isDeleted": false,
			"id": "8lpP9BXe",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 126,
			"y": -58,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 12,
			"height": 25,
			"seed": 2133756830,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331308522,
			"link": null,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "t",
			"rawText": "t",
			"baseline": 18,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "t"
		},
		{
			"type": "text",
			"version": 25,
			"versionNonce": 1137532738,
			"isDeleted": false,
			"id": "ep2j196w",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -135.59066772460938,
			"y": -116.69482421875,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 6,
			"height": 25,
			"seed": 1365870686,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331318088,
			"link": null,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "1",
			"rawText": "1",
			"baseline": 18,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "1"
		},
		{
			"type": "text",
			"version": 3,
			"versionNonce": 991765314,
			"isDeleted": false,
			"id": "EqNEWK6y",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -140,
			"y": -155,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 15,
			"height": 25,
			"seed": 138470274,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331313459,
			"link": null,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "2",
			"rawText": "2",
			"baseline": 18,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "2"
		},
		{
			"type": "text",
			"version": 3,
			"versionNonce": 1324905026,
			"isDeleted": false,
			"id": "avRjWLF4",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -140,
			"y": -185,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 15,
			"height": 25,
			"seed": 286921346,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331315803,
			"link": null,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "3",
			"rawText": "3",
			"baseline": 18,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "3"
		},
		{
			"type": "line",
			"version": 45,
			"versionNonce": 2088974722,
			"isDeleted": false,
			"id": "ZJOtfA56thCwA8UeBOVm-",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -109.38043212890625,
			"y": -103.6400146484375,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 130.9335174560547,
			"height": 0.9156494140625,
			"seed": 254027522,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331326108,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					130.9335174560547,
					-0.9156494140625
				]
			]
		},
		{
			"type": "ellipse",
			"version": 23,
			"versionNonce": 594433630,
			"isDeleted": false,
			"id": "HYBX8ONUq1M3FT-nUB4vf",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 18.195816040039062,
			"y": -111.57537841796875,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 10.071807861328125,
			"height": 12.513458251953125,
			"seed": 1804113822,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331328835,
			"link": null
		},
		{
			"type": "text",
			"version": 23,
			"versionNonce": 2047742786,
			"isDeleted": false,
			"id": "4LhQnUQB",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -66.53321838378906,
			"y": -126.7791748046875,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 13,
			"height": 25,
			"seed": 589768258,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331337171,
			"link": null,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "X",
			"rawText": "X",
			"baseline": 18,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "X"
		},
		{
			"type": "line",
			"version": 177,
			"versionNonce": 624229534,
			"isDeleted": false,
			"id": "tiFtjT-LlSX0dj61etdFp",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -117.0089340209961,
			"y": -141.58370680880375,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 219.95466562483853,
			"height": 1.5381956019572527,
			"seed": 409971394,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331357089,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					219.95466562483853,
					-1.5381956019572527
				]
			]
		},
		{
			"type": "line",
			"version": 27,
			"versionNonce": 1294220382,
			"isDeleted": false,
			"id": "3wcsy0PUt9KrNjg54i_1f",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "dashed",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 105.50985717773438,
			"y": -143.15478515625,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 73.55471801757812,
			"height": 0.30523681640625,
			"seed": 1333325086,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331369079,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					73.55471801757812,
					-0.30523681640625
				]
			]
		},
		{
			"type": "line",
			"version": 125,
			"versionNonce": 1966277918,
			"isDeleted": false,
			"id": "07ndRjAg0FoNhP5i0I8UB",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -115.50084686279295,
			"y": -173.2574644991388,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 111.93462630968882,
			"height": 0.7827856226971921,
			"seed": 1491811550,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1650331383784,
			"link": null,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					111.93462630968882,
					-0.7827856226971921
				]
			]
		},
		{
			"type": "ellipse",
			"version": 102,
			"versionNonce": 1866589122,
			"isDeleted": false,
			"id": "HvCCdfTdHI-WXlMGQiEwu",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -6.606746162925255,
			"y": -180.17234802246094,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 8.610354866538541,
			"height": 10.697713622063032,
			"seed": 1813645314,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1650331383784,
			"link": null
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#000000",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "hachure",
		"currentItemStrokeWidth": 1,
		"currentItemStrokeStyle": "dashed",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 1,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStrokeSharpness": "sharp",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"currentItemLinearStrokeSharpness": "round",
		"gridSize": null,
		"colorPalette": {}
	},
	"files": {}
}
````

%%

Supongamos que $x_1,...,x_m$ están observados y $x_{m+1}>a,...,x_n>a$ están censurados.

* Datos observados:
  $$y_1=x_1,y_2=x_2,...,y_m=x_m$$
  $$y_{m+1}=\{x_{m+1>a}\},y_n=\{x_m>a\}$$
  ![Pasted image 20220418202700.png](../Images/Pasted%20image%2020220418202700.png)

Entonces, la logverosimilitud de la función normal es la siguiente:
$$\log f(x|\theta) = K -\frac{1}{2}(x-\theta)^2$$
Donde K es una constante. Tomando los datos:
$$\log f(x|\theta) = K -\frac{1}{2}\sum_{i=1}^n(x_i-\theta)^2$$
Considerando los datos observados y los censurados:
$$\log f(x|\theta) = K -\frac{1}{2}\sum_{i=1}^m(x_i-\theta)^2 - \frac{1}{2}\sum_{i=m+1}^n(x_i-\theta)^2$$
Entonces:
$$\\log f(x|\theta) = K
-\frac{1}{2} \sum\_{i=1}^mx_i^2
-\frac{1}{2} \sum\_{i=m+1}^nx_i^2
-\frac{1}{2} \sum\_{i=1}^n\theta^2

* \\theta\left(\sum\_{i=1}^mx_i+\sum\_{i=m+1}^nx_i\right)$$
  En el paso de valor esperado:

$$Q(\theta|\theta^{(0)}) = K-C - \frac{1}{2}n\theta^2+\theta\mathbb{E}_{X\sim f(x|\theta^{(o)})}\left[ \sum_{i=1}^mx_i+\sum_{i=m+1}^nx_i \right]$$
Para los valores observados:
$$\mathbb{E}(X_i|Y_i)=\mathbb{E}(X_i|X_i) = X_i, \quad i=1,...,m$$
Entonces, los no observados:
$$\mathbb{E}(X_j|Y_j) = \mathbb{E}(Z)$$
Donde $Z$ es una distribución normal truncada en $(a,\infty)$ con parámetros $(\theta,1)$:
$$\theta+\frac{\phi(a-\theta)}{1-\Phi(a-\theta)} = \omega_\theta$$
Donde $\phi$ es la densidad  de la distribución normal con media 0 y varianza 1 y $\Phi$ es la distribución normal con media 0 y varianza 1. Entonces, habiendo hecho las cuentas se obtiene que:
$$Q(\theta|\theta^{(0)}) = C_1- \frac{1}{2}n\theta^2+\theta\left[\sum_{i=1}^m{x_i} + (n-m)\omega_{\theta^{(0)}}\right]$$
Maximizando (obteniendo la derivada de $Q$ con respecto a $\theta$):
$$\frac{d}{d\theta}Q(\theta|\theta^{0}=-n\theta + m\bar{x}_{obs}+(n-m)\omega_{\theta^{(0)}}$$

Entonces, obteniendo el argumento del máximo:

$$\theta^* = \frac{m\bar{x}_{obs}+(n-m)\omega_{\theta^{(0)}}}{n}$$
Sustituyendo $\omega_{\theta^{(0)}}$:
$$\theta^* = \frac{m}{n}\bar{x}_{obs} + \frac{n-m}{n}\left(\theta^{(0)}+\frac{\phi(a-\theta^{(0)})}{1-\Phi(a-\theta^{(0)})}\right)$$

Entonces haciéndolo en un solo paso:
$$\theta^{(j+1)} = \frac{m}{n}\bar{x}_{obs} + \frac{n-m}{n}\left(\theta^{(j)}+\frac{\phi(a-\theta^{(j)})}{1-\Phi(a-\theta^{(j)})}\right)$$

Por el otro lado, puede entenderse tal cual la verosimilitud de la siguiente manera:

$$\mathcal{L}(\theta|y) \propto \prod_{i=1}^m\phi(x_i|\theta,1)\left(1-\Phi(a-\theta)\right)^{n-m}$$
Debido a que la probabilidad de que $x>a$ es $\Phi(a-\theta)$.
