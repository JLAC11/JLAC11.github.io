# Balance Score Card

Cuando se desarrollan [KPI](KPI.md)s, esta estrategia los divide en cuatro:

````mermaid
classDiagram

class Finanzas

class Cliente

class NegocioInterno

class Innovación

Finanzas<|--|>Cliente
Finanzas<|--|>NegocioInterno
NegocioInterno<|--|>Cliente
Innovación<|--|>Cliente
NegocioInterno<|--|>Innovación

````

En un worksheet tiene los siguientes encabezados:

1. Dimensión: Finanzas, relación con cliente, producción, innovación y crecimiento
   * Subdimensión: subdivisiones.:
1. Objetivos: ¿Qué se quiere lograr?
1. KPIs
1. Meta del año
1. Resultados al momento del KPI
1. Puntuación (Resultados/meta)
1. Promedio de rendimiento (por subdivisión)
