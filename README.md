# La evolución táctica del fútbol moderno contada con datos — Premier League 2009–2025

**Autor:** Tobias Castro — Business Intelligence & Analytics Consultant  
**LinkedIn:** [Tobias Castro](https://www.linkedin.com/in/tobias-castro-6a79a0140/)  
**Stack:** Python · pandas · matplotlib · numpy  
**Datos:** FBref vía Kaggle · Premier League 2009–2025

---

## La pregunta

El "10" clásico — el enganche que recibe, gira y da el pase de ruptura — ¿sigue siendo el eje creador del fútbol moderno?

---

## El contexto táctico

El Barça de Guardiola (2008–2012) dominó Europa con un mediocampista ofensivo en el centro de todo. Pero ese sistema requería algo que el fútbol moderno ya no da: **tiempo en la pelota**.

Klopp sistematizó y popularizó el Gegenpressing en Europa con el Dortmund — presionar al rival inmediatamente tras perder la pelota. Ese sistema redujo el tiempo de decisión de 3–4 segundos a menos de 1. El espacio entre líneas desapareció. Y el enganche estático quedó expuesto.

Pero la creatividad no desapareció con él.

---

## Los 4 hallazgos

| Arquetipo | Posición FBref | xAG/90 mediana | vs enganche clásico |
|---|---|---|---|
| Enganche / MF clásico | MF | 0.080 | referencia |
| Extremo invertido / Interior | FW,MF | 0.150 | **+88%** |
| Lateral ofensivo | DF | 0.040 (mediana) · 0.38 (techo TAA) | nuevo arquetipo |
| Central constructor | DF,MF | 0.080 | igual al "10" desde atrás |

> **xAG/90:** goles de asistencia esperados por cada 90 minutos jugados. Mide la calidad de los pases que generaron chances reales, independientemente de si el delantero convirtió.

---

## Visualizaciones

### 1 — El insight central: los arquetipos tácticos
![Arquetipos tácticos](visualizaciones/viz1_arquetipos_tacticos.png)

### 2 — Evolución temporal 2017–2025
![Evolución temporal](visualizaciones/viz2_evolucion_temporal.png)

### 3 — Era clásica vs Era moderna
![Comparación de eras](visualizaciones/viz3_comparacion_eras.png)

### 4 — El nuevo arquetipo: laterales en territorio de mediocampista
![Scatter nuevo arquetipo](visualizaciones/viz4_scatter_nuevo_arquetipo.png)

---

## Estructura del repo

```
murio-el-10-football-analytics/
│
├── notebooks/
│   ├── 01_EDA_PL_202425.py           → Exploración del dataset moderno
│   └── 02_analisis_comparativo.py    → Análisis principal con los 4 hallazgos
│
├── visualizaciones/
│   ├── viz1_arquetipos_tacticos.png
│   ├── viz2_evolucion_temporal.png
│   ├── viz3_comparacion_eras.png
│   └── viz4_scatter_nuevo_arquetipo.png
│
└── README.md
```

---

## Datasets

Los datasets no están incluidos en el repo por tamaño y licencia.
Descargalos directamente desde Kaggle antes de ejecutar los notebooks:

| Dataset | Temporadas | Uso en el análisis | Link |
|---|---|---|---|
| Standard Stats histórico | 2000–2023 · múltiples ligas | Era clásica — Ast/90 por posición | [Kaggle](https://www.kaggle.com/datasets/beridzeg45/top-league-footballer-stats-2000-2023-seasons) |
| Top 5 Ligas Europeas 2017–2025 | 2017–2025 · 5 ligas | Era moderna — xAG/90 y arquetipos | [Kaggle](https://www.kaggle.com/datasets/emrey3lmaz/top-5-league-football-player-stats-2017-2025) |
| FBref PL 2024-25 | 2024–25 · Premier League | Dataset moderno de referencia | [Kaggle](https://www.kaggle.com/datasets/siddhrajthakor/fbref-premier-league-202425-player-stats-dataset) |

Una vez descargados, colocalos en la misma carpeta donde ejecutás los notebooks (o en la raíz del proyecto si usás Colab).

---

## Cómo ejecutar

```bash
pip install pandas numpy matplotlib
```

Ejecutar en orden desde la carpeta `notebooks/`:

```
01_EDA_PL_202425.py           → exploración inicial
02_analisis_comparativo.py    → análisis completo + genera las 4 visualizaciones
```

---

## Nota metodológica

El xAG (Expected Assisted Goals) no existía como métrica antes de la temporada 2017–18. Para el período 2009–2016 se utiliza **Ast/90** (asistencias por 90 minutos) como proxy histórico. Esta limitación está documentada en cada visualización del análisis.

El filtro de calidad aplicado en ambos datasets es **900 minutos mínimos por temporada** (~10 partidos completos), para evitar que muestras pequeñas distorsionen los promedios.

---

## Glosario rápido

| Métrica | Definición simple |
|---|---|
| xAG/90 | Goles de asistencia esperados por 90 minutos. Mide calidad de pases que generaron chances, no solo las que terminaron en gol. |
| Ast/90 | Asistencias reales por 90 minutos. Proxy histórico para 2009–2016. |
| PrgP/90 | Pases progresivos por 90 minutos. Pases que avanzan la pelota 10+ metros hacia el arco rival. |
| p50 / p90 | Percentil 50 (jugador típico) y percentil 90 (top 10% de su posición). |

---

## Conclusión

El fútbol moderno no eliminó al creador. Lo distribuyó en todo el campo.

El extremo invertido genera el doble de xAG/90 que el enganche clásico. El lateral ofensivo de élite llega a triplicarlo. Y el central constructor opera desde atrás con los mismos números que el "10" de hace 15 años.

> *"El '10', se fragmentó en tres arquetipos distintos."*

---

Proyecto 2 — La anomalía que los datos no pueden explicar

Messi con datos · La Liga 2009-2019 + Selección Argentina 2006-2026

Conexión con Proyecto 1: el Proyecto 1 mostró que el pressing moderno fragmentó al creador de juego clásico. Este proyecto analiza al único jugador que desafió esa lógica durante 20 años.

Pregunta central: ¿Cómo se explica con datos que Messi haga un hattrick en un Mundial a los 38 años?

Respuesta: No se explica. Los datos solo confirman la magnitud de la anomalía.

Hallazgos

MétricaDatoContextoG+A/90 promedio La Liga1.5573.5x la mediana del resto de AM/FWTemporadas sobre el p9010 de 10Nunca bajó del top 10%xAG/90 pico (2018-19)0.4803x el extremo invertido del Proyecto 1xAG/90 promedio (2017-21)0.4136x el MF clásico típicoCopa América14G + 17A en 7 torneosMáximo asistidor históricoMundiales16 goles en 6 mundiales*Máximo goleador histórico

*incluyendo Mundial 2026 en curso

Visualizaciones

Mostrar imagen
Mostrar imagen
Mostrar imagen
Mostrar imagen

Datasets

DatasetTemporadasUsoLinkLaLiga Summary (x10)2009–2019G+A/90 Messi vs paresKaggleTop 5 Ligas Europeas2017–2021xAG/90 solo BarcelonaKaggleSelección Argentina2006–2026Datos oficiales FIFA/CONMEBOLFIFA.com · CONMEBOL.com

Decisiones metodológicas


PSG excluido: el dataset solo captura goles de liga, no Champions ni Supercopa → datos incompletos
MLS excluida: Inter Miami no está en las 5 grandes ligas europeas
Selección: datos oficiales de torneos cerrados (FIFA, CONMEBOL) → comparables entre sí



Estructura del repo

tactical-evolution-premier-league/
│
├── notebooks/
│   ├── 01_EDA_PL_202425.py              → Exploración dataset moderno
│   ├── 02_analisis_comparativo.py       → Análisis Proyecto 1
│   └── 03_proyecto_messi.py             → Análisis Proyecto 2
│
├── visualizaciones/                     → Proyecto 1
│   ├── viz1_arquetipos_tacticos.png
│   ├── viz2_evolucion_temporal.png
│   ├── viz3_comparacion_eras.png
│   └── viz4_scatter_nuevo_arquetipo.png
│
├── visualizaciones/                      → Proyecto 2
│   ├── messi_viz1_laliga.png
│   ├── messi_viz2_xag_proyecto1.png
│   ├── messi_viz3_seleccion.png
│   └── messi_viz4_el_numero.png
│
└── README.md


Cómo ejecutar

bashpip install pandas numpy matplotlib

Ejecutar en orden desde notebooks/:


01_EDA_PL_202425.py — exploración inicial
02_analisis_comparativo.py — Proyecto 1 completo
03_proyecto_messi.py — Proyecto 2 completo



Glosario

MétricaDefinición simplexAG/90Goles de asistencia esperados por 90 minutos. Mide calidad de pases que generaron chances, independientemente de si el delantero convirtió.Ast/90Asistencias reales por 90 minutos. Proxy histórico para períodos sin xAG.PrgP/90Pases que avanzan la pelota 10+ metros hacia el arco rival por 90 minutos.G+A/90Goles más asistencias por 90 minutos. Métrica de producción ofensiva total.p50 / p90Percentil 50 (jugador típico) y percentil 90 (top 10% de su grupo).

*Proyecto de portfolio — Sports Analytics · Business Intelligence*  
*Tobias Castro · [LinkedIn](https://www.linkedin.com/in/tobias-castro-6a79a0140/) · tobiascastro9813@gmail.com*
