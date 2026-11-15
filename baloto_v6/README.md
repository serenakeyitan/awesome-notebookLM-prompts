# Baloto Master AI v6.0 — Guía de instalación (5 minutos)

## 1. Subir la caché de datos a Google Drive (opcional pero recomendado)
En **Mi unidad** crea la carpeta `BalotoMasterAI` y copia dentro:
- `historico_baloto.csv`
- `historico_revancha.csv`
- `premios_por_categoria.csv`

Con esto la primera ejecución no tiene que descargar 660 sorteos (solo traerá los nuevos). Si no los copias, el notebook los descarga solo (3–6 min la primera vez).

## 2. Abrir el notebook en Colab
`Baloto_Master_AI_v6_0.ipynb` → Archivo → Subir notebook (o súbelo a tu repo de GitHub y ábrelo desde allí).

## 3. Ejecutar en orden
| Celda | Qué hace | Cuándo correrla |
|---|---|---|
| 1 | Instala lo que falte, monta Drive, define reglas y precio | Siempre, al iniciar sesión |
| 2 | Define el scraper oficial | Siempre |
| 3 | Actualiza el histórico desde baloto.com y lo valida | Siempre (pon `ACTUALIZAR_DESDE_WEB=False` si no hay internet) |
| 4–5 | Estadística descriptiva + gráficos | Cuando quieras el resumen analítico |
| 6 | Probabilidades exactas, validación con ganadores reales, valor esperado | Cuando quieras saber cuánto vale el tiquete hoy |
| 7 | **Motor v6** → Tabla 2 de tickets | Antes de cada sorteo |
| 8 | Backtest motor vs azar | Cuando quieras comprobar la honestidad del motor |
| 9 | OCR de imágenes (resultados o tiquetes) | Opcional |
| 10 | Registrar y verificar tus jugadas | Después de jugar / después del sorteo |
| 11 | Panel interactivo con botón | Para uso rápido |
| 12 | Exportar Excel + PDF | Cuando quieras el informe |

## 4. Parámetros que vale la pena tocar
- Celda 1: `PRECIO_BALOTO`, `PRECIO_CON_REVANCHA` (verifícalos en baloto.com), `USAR_DRIVE`.
- Celda 4: `VENTANA_RECIENTE` (sorteos para "calientes/fríos"), `JUEGO_ANALISIS` (`baloto`, `revancha` o `ambos`).
- Celda 7: `PESOS` (frecuencia / rezago / uniforme) y `NUM_TICKETS`.

## 5. Flujo típico de un día de sorteo
1. Celdas 1 → 3 (actualiza resultados del sorteo anterior).
2. Celda 10: `verificar_jugadas()` → ¿ganaste algo con los tiquetes anteriores?
3. Celda 7: genera la Tabla 2 → `registrar_tickets_del_motor(tickets, sorteo=NNNN)`.
4. (Opcional) Celda 12: exporta el informe.

## 6. Lo que la v6 NO promete
Ninguna combinación tiene más probabilidad que otra (1 en 15.401.568 para el mayor). El motor optimiza **no compartir el premio** (combinaciones poco populares) y la app te da **datos oficiales, valor esperado real y control de gastos**. Juega con moderación.
