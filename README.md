# Challenge-Telecom-X---parte-2
Tercer Challenge Data Science Alura Latam G8

# Informe de Clasificación de Cancelación de Clientes

## 1. Objetivo del Proyecto

El objetivo principal de este análisis fue identificar los factores más influyentes en la cancelación de clientes dentro de una empresa de telecomunicaciones. Para ello, se entrenaron diferentes modelos de clasificación y se evaluó su rendimiento con métricas como la **F1-score** y la **matriz de confusión**. A partir de estos resultados, se elaboraron propuestas estratégicas para mejorar la retención de clientes.

---

## 2. Preparación de los Datos

Se utilizaron datos previamente procesados en otro proyecto, los cuales ya estaban:

- **Limpios**: sin valores nulos ni inconsistencias.
- **Binarizados**: la variable objetivo (cancelación) fue transformada en binaria (0 = no canceló, 1 = canceló).

---

## 3. Modelos Utilizados

Se entrenaron y compararon los siguientes modelos de clasificación:

- `RandomForestClassifier` (Bosques Aleatorios)
- `XGBoostClassifier` (Gradient Boosting)
- `KNeighborsClassifier` (K-Nearest Neighbors)

---

## 4. Métricas de Evaluación

Se emplearon las siguientes métricas para evaluar el rendimiento de cada modelo:

- **F1-score**: métrica equilibrada entre precisión y recall.
- **Matriz de confusión**: para observar el rendimiento por clase.

La métrica F1 es especialmente útil en contextos con clases desbalanceadas o cuando ambos errores (falsos positivos y falsos negativos) son importantes.

---

## 5. Importancia de las Variables

### 5.1 RandomForestClassifier

Las 10 variables más influyentes en la predicción fueron:

| Posición | Variable                                                        | Importancia (%) |
|----------|------------------------------------------------------------------|-----------------|
| 1        | `remainder__customer_tenure`                                     | 18.34           |
| 2        | `onehotencoder__account_contract_Month-to-month`                | 16.82           |
| 3        | `remainder__account_charges_total`                               | 13.42           |
| 4        | `onehotencoder__internet_internetservice_DSL`                   | 7.43            |
| 5        | `onehotencoder__internet_internetservice_Fiber optic`           | 6.55            |
| 6        | `remainder__internet_onlinesecurity`                             | 5.19            |
| 7        | `remainder__internet_techsupport`                                | 4.57            |
| 8        | `remainder__account_charges_monthly`                             | 4.22            |
| 9        | `onehotencoder__account_paymentmethod_Electronic check`         | 3.90            |
| 10       | `onehotencoder__account_contract_Two year`                       | 3.77            |

### 5.2 XGBoostClassifier

Las variables con mayor importancia relativa fueron:

- `remainder__account_charges_total`
- `remainder__account_charges_montly`
- `remainder__customer_tenure`
- `remainder__cuentas_diarias`

---

## 6. Resultados de los Modelos

Los modelos `RandomForestClassifier` y `XGBoostClassifier` fueron los que obtuvieron mejores resultados en términos de clasificación, especialmente para la clase negativa (clientes que **no se retiraron**). Esto sugiere que el modelo está aprendiendo bien a distinguir a los clientes leales, aunque se podrían realizar ajustes para mejorar la detección de clientes propensos a cancelar.

- **RandomForestClassifier**:
  - Buen equilibrio entre precisión y recall.
  - Importancia variable clara y explicativa.
- **XGBoostClassifier**:
  - Alto rendimiento.
  - Buen manejo de relaciones no lineales.
- **KNeighborsClassifier**:
  - Buen rendimiento, aunque inferior a los anteriores.
  - Tiempo de predicción mayor.

---

## 7. ¿Hubo Underfitting o Overfitting?

Se descartó la presencia de underfitting, ya que los modelos lograron captar patrones importantes de los datos, obteniendo buenos resultados de clasificación.

Tampoco se observó overfitting significativo. El rendimiento en los conjuntos de entrenamiento y prueba fue similar para los mejores modelos (Random Forest y XGBoost), lo que indica que el modelo generaliza adecuadamente a nuevos datos.

---

## 8. Principales Factores de Cancelación

Los factores más influyentes en la decisión de cancelar el servicio fueron:

- **Duración del cliente (`customer_tenure`)**: los clientes con menos tiempo tienden a cancelar más.
- **Tipo de contrato**: los contratos mensuales muestran una mayor tasa de cancelación.
- **Cargos totales y mensuales**: los clientes con cargos más altos tienden a cancelar con mayor frecuencia.
- **Tipo de servicio de Internet**: el uso de tecnología como Fibra Óptica se asocia a mayor cancelación.
- **Servicios de seguridad y soporte técnico**: la ausencia de estos servicios se relaciona con la cancelación.

---

## 9. Estrategias de Retención Sugeridas

A partir de los resultados obtenidos, se proponen las siguientes estrategias para reducir la tasa de cancelación:

- **Fomentar contratos de largo plazo**: ofrecer descuentos o beneficios por adquirir contratos anuales o bianuales.
- **Ofrecer paquetes económicos o descuentos progresivos**: especialmente para clientes con cargos altos.
- **Incluir servicios de seguridad y soporte técnico**: como parte de los paquetes base para mejorar la experiencia del cliente.
- **Campañas de fidelización durante los primeros meses**: dado que los clientes nuevos son más propensos a cancelar, brindarles atención preferencial puede mejorar su permanencia.
- **Monitorear continuamente las variables clave**: para aplicar intervenciones personalizadas a clientes en riesgo.

---

## 10. Conclusión

El análisis y los modelos implementados permitieron identificar con claridad los factores que inciden en la cancelación de clientes. La combinación de técnicas como Random Forest y XGBoost mostró ser eficaz para detectar patrones relevantes y proporcionar interpretaciones accionables. Este enfoque puede ser integrado en sistemas de alertas tempranas para evitar la pérdida de clientes mediante estrategias personalizadas de retención.
