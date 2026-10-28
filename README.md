# 📊 Análisis de ventas y marketing con Python

Limpieza de datos, análisis exploratorio, estadística descriptiva y dashboard interactivo sobre ventas, campañas de marketing y clientes de un negocio minorista.

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AlejandroCalello/analisis-ventas-marketing-python/blob/main/analisis_ventas_marketing.ipynb)
&nbsp;·&nbsp; [**Ver el dashboard interactivo**](https://htmlpreview.github.io/?https://github.com/AlejandroCalello/analisis-ventas-marketing-python/blob/main/dashboard_ventas.html)

## Preguntas que responde el análisis

- ¿Qué productos y categorías generan los ingresos? ¿Se cumple la regla 80/20?
- ¿Cómo se distribuyen los ingresos y qué productos se salen de lo normal?
- ¿El precio de un producto se relaciona con las unidades que vende?
- ¿La inversión en marketing se relaciona con los ingresos?
- ¿Cómo evolucionan las ventas a lo largo del año?

## Datos

| Archivo | Contenido | Filas |
|---|---|---|
| `data/ventas.csv` | Ventas: producto, categoría, precio, cantidad, fecha | 3.035 (3.000 tras la limpieza) |
| `data/marketing.csv` | Campañas: producto, canal, costo, fechas | 90 |
| `data/clientes.csv` | Clientes: edad, ciudad, ingresos | 567 |

## Proceso

1. **Exploración y calidad:** tipos, nulos y duplicados en las tres tablas.
2. **Limpieza:** eliminación de 35 duplicados, normalización de textos, conversión de fechas y de precios (texto con `$` y comas a número), imputación del precio faltante con el promedio del producto y descarte de las filas sin cantidad.
3. **Integración:** unión de ventas con marketing por producto, verificando que no queden productos sin cruzar.
4. **Análisis:** Pareto, media/mediana/desvío, outliers por IQR, correlaciones de Pearson y Spearman con p-valor, evolución diaria y acumulada.
5. **Visualización:** gráficos con Matplotlib y Seaborn, y un dashboard con selector de métrica en Plotly.

## Hallazgos principales

- **Ingresos totales:** $1.467.093,52 en 2024, repartidos entre 30 productos y 3 categorías.
- **No se cumple el 80/20:** el 20% de los productos (6 de 30) aporta el 27,1% de los ingresos y hacen falta 22 productos para llegar al 80%. Los ingresos están bastante repartidos.
- **Outliers:** 4 productos con ingresos muy altos (Lámpara de Mesa, Auriculares, Microondas, Cafetera) y 3 con ingresos muy bajos (Tablet, Heladera, Candelabro).
- **Categorías muy parejas:** Electrodomésticos 34,4%, Electrónica 32,9% y Decoración 32,7%. La primera supera a la última en solo un 5,4%.
- **Precio vs. unidades:** r = 0,22 (p = 0,25), una correlación débil y no significativa. Los precios promedio van de $71 a $81, así que casi no hay variación para medir su efecto.
- **Marketing vs. ingresos:** r = 0,24 (p = 0,20), tampoco significativa. Los costos están en una escala muy distinta a la de los ingresos y habría que confirmar su unidad antes de calcular un ROI.

## Limitaciones

- Son solo 30 productos, por lo que las correlaciones tienen poca potencia estadística.
- `ventas` no tiene `id_cliente`, así que no se pudo vincular el comportamiento de los clientes con las ventas.
- Se analizan ingresos, no rentabilidad (no hay costos de producto).

## Cómo ejecutarlo

**En Colab:** tocá el botón "Abrir en Colab" de arriba y elegí *Entorno de ejecución → Ejecutar todo*. El notebook descarga los datos desde este repositorio.

**En local:**

```bash
git clone https://github.com/AlejandroCalello/analisis-ventas-marketing-python.git
cd analisis-ventas-marketing-python
pip install -r requirements.txt
jupyter notebook analisis_ventas_marketing.ipynb
```

## Estructura del repositorio

```
├── analisis_ventas_marketing.ipynb   # notebook con todo el análisis
├── dashboard_ventas.html             # dashboard interactivo (Plotly)
├── requirements.txt
├── README.md
└── data/
    ├── ventas.csv
    ├── marketing.csv
    └── clientes.csv
```

## Herramientas

Python · pandas · NumPy · Matplotlib · Seaborn · SciPy · Plotly · Google Colab

---

**Alejandro Calello** · BI / Data Analyst · [LinkedIn](https://www.linkedin.com/in/alejandrocalello) · [GitHub](https://github.com/AlejandroCalello)
