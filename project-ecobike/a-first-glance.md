---
title: A first glance at Ecobici data
---

Let's take a first look at what can be found in the Ecobici dataset[^1].

## Origins

| Origin                                             |  Count |
|:---------------------------------------------------|-------:|
| CE-271-272 Jesús García - Carlos J. Meneses        |  10796 |
| CE-548 Dr. Mariano Azuela - Jose Antonio Alzate    |  10012 |
| CE-064 Sonora - Ámsterdam                          |   9705 |
| CE-027 Reforma- Havre                              |   9398 |
| CE-273-274 Luis Donaldo Colosio - Av. Jesús García |   9135 |
| CE-031 Hamburgo - Insurgentes                      |   8442 |
| CE-208 Hesiodo-Lamartine                           |   8429 |
| CE-237-238 Andrés Bello-George Eliot               |   8359 |
| CE-014 Reforma - Río de Plata                      |   7713 |
| CE-001 Río Sena-Río Balsas                         |   7711 |
| CE-018 Reforma - Río Rhin                          |   7633 |
| CE-192-193 Rubén Darío.Reforma                     |   7604 |
| CE-038 Cozumel - Puebla                            |   7522 |
| CE-029 Reforma - Bucareli                          |   7489 |
| CE-555 Ribera de San Cosme - Insurgentes Centro    |   7311 |
| CE-036 Puebla - Veracruz                           |   7251 |
| CE-134 Álvaro Obregón-Orizaba                      |   7123 |
| CE-158-159 Huatabampo-Eje 1 Pte. Av. Cuauhtémoc    |   7087 |
| CE-041 Reforma - Av. de la República               |   6945 |
| CE-053 Fernando Montes de Oca - Tula               |   6939 |

## Destinations

| Destination                                        |  Count |
|:---------------------------------------------------|-------:|
| CE-271-272 Jesús García - Carlos J. Meneses        |  20472 |
| CE-014 Reforma - Río de Plata                      |  12015 |
| CE-548 Dr. Mariano Azuela - Jose Antonio Alzate    |  11112 |
| CE-027 Reforma- Havre                              |  10456 |
| CE-064 Sonora - Ámsterdam                          |  10061 |
| CE-266-267 Jesús García - Carlos J. Meneses        |   9534 |
| CE-029 Reforma - Bucareli                          |   8537 |
| CE-273-274 Luis Donaldo Colosio - Av. Jesús García |   8533 |
| CE-031 Hamburgo - Insurgentes                      |   8086 |
| CE-001 Río Sena-Río Balsas                         |   7985 |
| CE-134 Álvaro Obregón-Orizaba                      |   7882 |
| CE-043 Revillagigedo - Juárez                      |   7508 |
| CE-028 Toledo- Tokio                               |   7423 |
| CE-242 Pról. Moliere-Miguel de Cervantes Saavedra  |   7353 |
| CE-158-159 Huatabampo-Eje 1 Pte. Av. Cuauhtémoc    |   7348 |
| CE-018 Reforma - Río Rhin                          |   7313 |
| CE-036 Puebla - Veracruz                           |   7225 |
| CE-555 Ribera de San Cosme - Insurgentes Centro    |   7165 |
| CE-052 Hidalgo - Trujano                           |   7151 |
| CE-038 Cozumel - Puebla                            |   7120 |

## Comments

The most used station is Jesús García - Carlos J. Meneses (both as origin and destination).  
This station is in Buenavista, near a Metro and a Metrobus stations.  

![Buenavista station](/assets/images/Buenavista_map.png)

## How does usage look like by hour of the day?

|   Hour |   Trips (count) |   Duration (min) - Mean |   Duration (min) - Min |   Duration (min) - Max |   Duration (min) - Median |   Duration (min) - 90th Percentile |
|----------------|---------------------|-----------------------------|----------------------------|----------------------------|-------------------------------|------------------------------------|
|           0 |            7,782 |                       16.96 |                       0.50 |                     679.75 |                         12.98 |                              32.87 |
|           5 |           15,104 |                       11.21 |                       0.60 |                     226.40 |                          8.85 |                              21.60 |
|           6 |           53,879 |                       12.02 |                       0.55 |                     474.75 |                          9.52 |                              23.87 |
|           7 |          104,074 |                       16.16 |                       0.53 |                 142,760.62 |                         11.25 |                              27.32 |
|           8 |          129,400 |                       14.63 |                       0.45 |                  30,666.03 |                         11.63 |                              27.97 |
|           9 |          104,244 |                       14.23 |                       0.55 |                   2,779.95 |                         10.95 |                              27.87 |
|          10 |           90,469 |                       15.28 |                       0.83 |                  21,778.62 |                         11.30 |                              30.42 |
|          11 |           90,345 |                       29.28 |                       0.72 |                 566,542.98 |                         11.87 |                              32.23 |
|          12 |           96,539 |                       16.82 |                       0.45 |                  93,681.02 |                         12.00 |                              32.42 |
|          13 |          111,205 |                       16.80 |                       0.57 |                 168,874.10 |                         11.82 |                              30.95 |
|          14 |          129,138 |                       17.32 |                       0.58 |                 161,082.87 |                         11.75 |                              29.98 |
|          15 |          125,663 |                       17.73 |                       0.50 |                 140,900.23 |                         11.97 |                              30.45 |
|          16 |          118,227 |                       16.89 |                       0.43 |                 142,507.73 |                         12.40 |                              31.05 |
|          17 |          132,563 |                       16.33 |                       0.60 |                   2,777.15 |                         13.35 |                              31.88 |
|          18 |          136,959 |                       20.35 |                       0.42 |                 533,874.70 |                         13.62 |                              31.73 |
|          19 |          112,822 |                       19.18 |                       0.62 |                 244,198.52 |                         12.97 |                              30.90 |
|          20 |           83,436 |                       15.76 |                       0.50 |                  30,195.67 |                         11.93 |                              29.88 |
|          21 |           63,845 |                       14.35 |                       0.67 |                   2,718.35 |                         11.20 |                              28.37 |
|          22 |           45,905 |                       14.33 |                       0.68 |                   4,027.85 |                         10.95 |                              27.67 |
|          23 |           26,995 |                       14.20 |                       0.58 |                   2,178.72 |                         11.00 |                              27.08 |

Notably, there is a mid-day lull with most trips happening either in the morning or in the afternoon (as to be expected if this is used for commuting).

![Usage by hour](/assets/images/usage_by_hour.png)

We can confirm this by examining usage by hour, but also by day. Let's look at that to confirm our suspicions.

![Usage by hour and day](/assets/images/usage_by_weekday_hour.png)

Seeing this, then we can conclude that, effectively, this is caused by the commuting times of the users. If you notice, Saturday and Sunday also have less movement in general, but it tends to happen around noon.

## Which are the most common routes?  

We've seen the most common origins and destinations, but we've yet to see which are the most common routes. Let's take a look at them: 

| Route (origin, destination)           |   Count |
|------------------------------------------------------------------------------------------------------------------------|--------|
| ('CE-621 Lago Poniente - Calzada de Tlalpan', 'CE-618 Bartolomé R. Salido - Edzna')                                    |   1,070 |
| ('CE-495 Amado Nervo - de los Maestros', 'CE-498 de los Maestros - Plan de Agua Prieta')                               |    761 |
| ('CE-548 Dr. Mariano Azuela - Jose Antonio Alzate', 'CE-498 de los Maestros - Plan de Agua Prieta')                    |    746 |
| ('CE-618 Bartolomé R. Salido - Edzna', 'CE-621 Lago Poniente - Calzada de Tlalpan')                                    |    720 |
| ('CE-494 Tláloc - Calzada México Tacuba', 'CE-486 Izcoatl - Circuito Interior Melchor Ocampo')                         |    592 |
| ('CE-544 Salvador Díaz Mirón - Nogal', 'CE-548 Dr. Mariano Azuela - Jose Antonio Alzate')                              |    564 |
| ('CE-498 de los Maestros - Plan de Agua Prieta', 'CE-548 Dr. Mariano Azuela - Jose Antonio Alzate')                    |    552 |
| ('CE-539 Naranjo - Av. Ricardo Flores Magon', 'CE-548 Dr. Mariano Azuela - Jose Antonio Alzate')                       |    545 |
| ('CE-208 Hesiodo-Lamartine', 'CE-206 Homero-Moliere')                                                                  |    541 |
| ('CE-548 Dr. Mariano Azuela - Jose Antonio Alzate', 'CE-544 Salvador Díaz Mirón - Nogal')                              |    526 |
| ('CE-030 Hamburgo - Amberes', 'CE-030 Hamburgo - Amberes')                                                             |    496 |
| ('CE-208 Hesiodo-Lamartine', 'CE-242 Pról. Moliere-Miguel de Cervantes Saavedra')                                      |    493 |
| ('CE-174 Joaquín Garcia Icazbalceta-Ignacio Manuel Altamirano', 'CE-111 Guillermo Prieto - Joaquín Velázquez de León') |    491 |
| ('CE-495 Amado Nervo - de los Maestros', 'CE-499 de los Maestros - Calzada de los Gallos')                             |    479 |
| ('CE-538 Nogal - Eligio Ancona', 'CE-548 Dr. Mariano Azuela - Jose Antonio Alzate')                                    |    471 |
| ('CE-174 Joaquín Garcia Icazbalceta-Ignacio Manuel Altamirano', 'CE-257 Manuel Maria Contreras-Villalongin')           |    448 |
| ('CE-270 De la República-Ponciano Arriaga', 'CE-266-267 Jesús García - Carlos J. Meneses')                             |    447 |
| ('CE-111 Guillermo Prieto - Joaquín Velázquez de León', 'CE-174 Joaquín Garcia Icazbalceta-Ignacio Manuel Altamirano') |    447 |
| ('CE-498 de los Maestros - Plan de Agua Prieta', 'CE-495 Amado Nervo - de los Maestros')                               |    446 |
| ('CE-465 Lago Ginebra-Lago Wetter', 'CE-463 Lago Andrómaco-Lago Zurich')                                               |    445 |

We can notice that few stations have more than 500 trips (just 10). Knowing that there are 677 stations in the network (as of May 2025), and that there were 1,778,591 trips in the month, then we'd expect to have $\frac{1,778,591}{677^2}=3.88$ trips per origin-destination pair (same-station origin and destination allowed)

Let's now take a look at how the number of trips per origin-destination pair are distributed:

![Distribution of trips per origin-destination pair](/assets/images/travelpairs-distribution.png)

[^1]: [Data from May 2025](https://ecobici.cdmx.gob.mx/datos-abiertos/).
