README - Análisis de Cesta de Mercado con Apriori

Objetivo
Este proyecto aplica aprendizaje no supervisado (algoritmo Apriori) para descubrir patrones de compra en tickets de supermercado / retail.
Permite:
- Encontrar conjuntos de productos frecuentes.
- Generar reglas de asociación con métricas de soporte, confianza y lift.
- Proponer recomendaciones de cross-sell (venta cruzada).
- Identificar bundles o combos para promociones.
- Visualizar las asociaciones mediante gráficos y grafos.

Dataset
Columnas requeridas:
- BillNo → ID de ticket/transacción.
- Itemname → nombre del producto.
- Quantity → cantidad vendida (se eliminan cantidades negativas).
- (Opcional): Date, Price, CustomerID, Country.

Metodología
1. Preprocesamiento
   - Filtrar cantidades (Quantity > 0).
   - Construir matriz ticket × producto (0/1).
2. Itemsets frecuentes (Apriori)
   - Uso de min_support ajustable (ej. 0.02 = 2% de tickets).
3. Reglas de asociación
   - Métricas: support, confidence, lift.
   - Filtrado por lift >= 1.0.
4. Acciones derivadas
   - recommend_from_rules: recomendaciones de cross-sell.
   - top_bundles: bundles para promociones.
   - Grafo de reglas con NetworkX.

Resultados
- Reglas top por lift → muestran asociaciones más fuertes.
- Bundles frecuentes → combinaciones populares para promociones.
- Scatter plot → relación support vs confidence, color/tamaño proporcional a lift.
- Grafo de reglas → dependencias producto–producto.

Requisitos
Archivo requirements.txt:
- pandas
- mlxtend
- matplotlib
- networkx

Cómo correrlo
1. Instalar dependencias:
   pip install -r requirements.txt
2. Abrir notebooks en notebooks/:
   - 01_build_basket.ipynb → preparación de la matriz.
   - 02_apriori_rules.ipynb → minería de itemsets y reglas, visualizaciones.

Próximos pasos
- Implementar FP-Growth (más eficiente en datasets dispersos).
- Analizar asociaciones por país, cliente o periodo temporal.
- Integrar como recomendador online.


