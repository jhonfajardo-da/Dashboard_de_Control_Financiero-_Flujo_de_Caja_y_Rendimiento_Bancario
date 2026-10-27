# 📊 Dashboard de Control Financiero, Flujo de Caja y Rendimiento Bancario

![Power BI](https://img.shields.io/badge/Power_BI-F2C94C?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-1D6F42?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)

## 📌 Descripción del Proyecto

Este repositorio contiene la solución analítica integral enfocada en la gestión de **Flujo de Caja, Tesorería y Rendimiento Bancario**. El proyecto consolida y procesa los movimientos de tesorería a partir de más de 2,700 registros transaccionales, evalúa la salud financiera operativa y optimiza la toma de decisiones ejecutivas en capital de trabajo.

La solución permite auditar ingresos, egresos, saldos consolidados y rendimiento por entidad bancaria en tiempo real, garantizando un control estricto sobre la liquidez de la organización.

---

## 🎯 Objetivos Analíticos

* **Monitorear la Liquidez Neta:** Evaluar la evolución del flujo de caja operativo y la disponibilidad de caja en tiempo real.
* **Analizar la Concentración Bancaria:** Medir la distribución de saldos y volumen de transacciones por entidad bancaria y tipo de cuenta.
* **Auditar Flujos de Ingresos y Egresos:** Mapear las entradas y salidas operacionales para detectar patrones de gasto y optimizar el fondo de maniobra.
* **Evaluar Gastos Operativos y Financieros:** Identificar comisiones, costos bancarios e impactos por tipo de cambio.

---

## 📈 Indicadores Clave de Rendimiento (KPIs Globales)

| Métrica KPI | Valor Absoluto | Descripción |
| :--- | :--- | :--- |
| **Ingresos Totales (Inflow)** | **$94.602.867,00 USD** | Total de recursos monetarios percibidos en el periodo. |
| **Egresos Totales (Outflow)** | **$44.863.841,00 USD** | Total de desembolsos y pagos operativos realizados. |
| **Flujo de Caja Neto** | **$49.739.026,02 USD** | Diferencia neta entre ingresos acumulados y egresos. |
| **Margen de Utilidad** | **37,58%** | Porcentaje de rentabilidad neta sobre las operaciones financieras. |
| **Transacciones Procesadas** | **2.725 registros** | Volumen total de movimientos auditados en el sistema. |

---

## 🔍 Análisis de Resultados y Hallazgos Clave

### 🏦 1. Rendimiento y Distribución por Entidad Bancaria

* **Concentración de Liquidez:**  Chase Bank lidera el volumen de ingresos con más de $33.2 millones, seguido por Bank of America con $24.1 millones.
* **Cobertura de Operaciones:** Las operaciones se distribuyen eficientemente en 5 entidades bancarias clave (Chase Bank, Bank of America, BBVA Bancomer, Santander y Citigroup).

| Banco / Entidad | Saldo Actual (USD) | Ingresos (USD) | Egresos (USD) | Participación (%) |
| :--- | :--- | :--- | :--- | :--- |
| **Chase Bank** | $33.261.602,80 | $15.740.513,24 | $17.521.089,56 | 35,16% |
| **Bank Of America** | $24.137.104,56 | $20.370.899,51 | $3.766.205,05 | 25,51% |
| **BBVA Bancomer** | $17.406.979,81 | $6.334.576,05 | $11.072.403,76 | 18,40% |
| **Santander** | $12.392.384,20 | $924.489,81 | $11.467.894,39 | 13,10% |
| **Citigroup** | $7.404.795,57 | $1.493.362,31 | $5.911.433,26 | 7,83% |

---

### 💸 2. Estructura de Ingresos y Egresos Operativos

* **Control de Salidas:** Los egresos representan aproximadamente el 47,4% de los ingresos totales, manteniendo un fondo de maniobra sumamente saludable.
* **Canales de Pago:** Diversificación de flujos a través de métodos como Efectivo, PayPal, MercadoPago y transferencias bancarias.

| Categoría de Flujo | Monto (USD) | % del Total | Tendencia |
| :--- | :--- | :--- | :--- |
| **Cobros / Ingresos Recibidos** | $94.602.867,00 | 100,00% | Creciente |
| **Pagos y Egresos Operativos** | $44.863.841,00 | 47,43% | Controlado |
| **Utilidad Consolidada**| $35.548.590,00 | 37,58% | Estable |

---

## 🖼️ Evidencias / Dashboard

![Dashboard de Control Financiero](Finanzas.pdf)

---

## 📐 Medidas DAX Utilizadas

El modelo analítico en Power BI incorpora lógica de cálculo financiera mediante medidas DAX avanzadas:

```dax
// 1. Total Ingresos (Inflow)
Total_Ingresos = 
SUMX(
    FILTER('Movimientos', 'Movimientos'[Tipo] = "Ingreso"),
    'Movimientos'[Monto]
)

// 2. Total Egresos (Outflow)
Total_Egresos = 
SUMX(
    FILTER('Movimientos', 'Movimientos'[Tipo] = "Egreso"),
    'Movimientos'[Monto]
)

// 3. Flujo de Caja Neto
Flujo_Caja_Neto = [Total_Ingresos] - [Total_Egresos]

// 4. Saldo Disponible Consolidado
Saldo_Disponible = 
CALCULATE(
    SUM('Cuentas_Bancarias'[Saldo_Inicial]) + [Flujo_Caja_Neto]
)

// 5. Ratio de Cobertura de Liquidez
Ratio_Cobertura = 
DIVIDE([Total_Ingresos], [Total_Egresos], 0)
