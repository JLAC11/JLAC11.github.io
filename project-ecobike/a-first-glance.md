---
title: A first glance at Ecobici data
---

Let's take a first look at what can be found in the Ecobici dataset[^1], viewing the most common origin and destination stations.

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

This station is not very close to the geographical center of the Ecobici network, but it connects other transportation media that are better suited for longer routes.

One interesting feature is that the number of trips the largest station receives (as a destination) is nearly twice the amount of trips coming out. Not only that, but its sister station also accounts for nearly as many destinations as origins from "CE-271-272 Jesús García - Carlos J. Meneses".  

Looking at the largest stations, we can see that those are also the largest stations:  

| Station Name                                       |   Capacity |
|----------------------------------------------------|------------|
| CE-266-267 Jesús García - Carlos J. Meneses        |         75 |
| CE-271-272 Jesús García - Carlos J. Meneses        |         74 |
| CE-158-159 Huatabampo-Eje 1 Pte. Av. Cuauhtémoc    |         74 |
| CE-264-275 Héroes Ferrocarrileros - Jesús Garcia   |         71 |
| CE-273-274 Luis Donaldo Colosio - Av. Jesús García |         70 |
| CE-268-269 Luis Donaldo Colosio - Av. Jesús García |         69 |
| CE-237-238 Andrés Bello-George Eliot               |         63 |
| CE-107-108 Tolsa-Balderas                          |         59 |
| CE-445-446 Riff-Avenida Río Churubusco             |         59 |
| CE-235-236 Campos Elíseos-Moliere                  |         55 |
| CE-608 Ahorro Postal - Francisco Márquez           |         51 |
| CE-497 Manuel Carpio - Plan de Ayala               |         51 |
| CE-192-193 Rubén Darío.Reforma                     |         49 |
| CE-390-391 Oso-Félix Cuevas                        |         47 |
| CE-070 Parque México - Michoacán                   |         45 |
| CE-027 Reforma- Havre                              |         43 |
| CE-261 Paseo de la Reforma-Río de la Plata         |         43 |
| CE-035 Liverpool - Génova                          |         41 |
| CE-643 Filipinas - Av. Pirineos                    |         39 |
| CE-696 México - Malintzin                          |         39 |

Notably, those are also the largest stations (as it would be expected). However, with a back-of-the-envelope calculation, we can see that over the 31 days May had, the most transited station would've had 360 departures **per day**, or equivalently, having it been emptied 4.8 times on average each day.

On the other hand, given the bike influx, it would've been filled about 8.8 times **each day**. This means that, on average, the station had to be artificially emptied at least 4 times on average (given bikes cannot be accumulated beyond the station's capacity).

This differential could suggest two things (also applicable to other stations):

1. Stations can be emptied artificially faster than they can be filled. This happens because removed bikes can be placed into any other close station, but bringing them to the place they're actually needed might require tou to visit several stations before being able to fill the required stations. This can cause an imbalance in trips: no bikes available at the station implies no possibility to start a trip there.
2. People do not necessarily have a same start and end route for the day, and might supplement their trips with other transport media (e.g., the bus, Metro, or ridehailing services).[^2]

## How does usage vary hour by hour?

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

Notably, there is a mid-day lull with most trips happening either in the morning or in the afternoon (as to be expected if this is used for commuting). It's also remarkable that 90% of the trips last about half an hour or less.

![Travel trip duration](/assets/images/travel_duration_distribution.png)


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

Most pairs have even less than 25 trips, and by the 100-trip-mark, nearly no stations remain.

This shows that there are just some routes that dominate in transport, while lots of routes are sparsely travelled.

## Continuing with the analysis

I'll continue adding information next in [a second mini-post](looking-at-origin-destination-data.md), where I'll discuss more properties we can learn from inspecting origin-destination data.

[^1]: [Data from May 2025](https://ecobici.cdmx.gob.mx/datos-abiertos/).

[^2]: We can support this argument by looking at origin and destination by the time of day. I'll leave an annex [on a separate page](datasource/annex-trips.md) if you want to followup on this, but I won't be discussing it further.
