# 🧠 Machine Learning — Supervised Learning II

## Checklist completo de la práctica

---

## 1️⃣ Modelo supervisado (baseline)

### Objetivo
Aprender un modelo de clasificación usando el dataset **MagicTelescope**.

### Tareas
- Cargar dataset
- Analizar datos
    - dimensiones
    - balance de clases
    - tipos de variables
- Preprocesado (si hace falta)
    - normalización / escalado
    - limpieza
    - separación train/test
- Elegir **un algoritmo de los vistos en clase**
- Ajustar hiperparámetros correctamente
    - usar validación cruzada (NO test)
- Evaluar rendimiento final en test

### Explicar en Markdown
- Por qué eliges ese modelo
- Metodología de evaluación
- Métricas utilizadas
- Resultados obtenidos
- Limitaciones del modelo

---

## 2️⃣ Estudio de sobreajuste por hiperparámetro (Complexity analysis)

### Objetivo
Analizar overfitting variando **UN hiperparámetro clave**

### Tareas
- Elegir hiperparámetro relevante
    - Ejemplos:
        - profundidad árbol
        - C en SVM
        - k en KNN
        - número de neuronas
- Mantener todo lo demás fijo
- Entrenar para múltiples valores
- Medir:
    - error entrenamiento
    - error validación/test
- Dibujar gráfica: performance vs hiperparámetro (train y test)

### Explicar
- Por qué ese hiperparámetro
- Dónde aparece overfitting
- Dónde aparece underfitting
- Conclusiones

---

## 3️⃣ Estudio por tamaño de muestra (Learning curves)

### Objetivo
Ver cómo cambia el rendimiento al aumentar datos de entrenamiento

### Tareas
- Usar el mejor modelo encontrado
- Entrenar con subconjuntos crecientes:
    - 5%
    - 10%
    - 20%
    - 40%
    - 60%
    - 80%
    - 100%
- Medir:
    - rendimiento train
    - rendimiento test/validación
- Dibujar gráfica: performance vs tamaño dataset

### Explicar
- Qué ocurre con pocos datos
- Cuándo se estabiliza
- Si el modelo necesita más datos

---

## 4️⃣ Aprendizaje semi-supervisado (SSL)

### Objetivo
Transformar el problema a semi-supervisado

### Tareas
- Convertir parte de etiquetas en "sin etiqueta"
- Implementar técnica SSL
    - self-training
    - pseudo-labeling
    - label propagation
    - etc.
- Entrenar con diferentes cantidades de datos etiquetados:
    - 1%
    - 5%
    - 10%
    - 20%
    - 50%
- Comparar contra modelo totalmente supervisado

### Dibujar gráfica
Performance vs cantidad de datos etiquetados

### Explicar
- Cuántos datos etiquetados hacen falta
- Si SSL mejora
- Cuándo deja de mejorar

---

## 5️⃣ Entregables

### 📄 Notebook en PDF
Debe incluir:
- Código funcionando
- Explicaciones en Markdown
- Justificación de decisiones
- Gráficas comentadas

### ⚠️ Obligatorio
Declarar uso de herramientas externas:
- uso de StackOverflow
- uso de ChatGPT
- librerías externas

---

### 🗣️ Entrevista
Debes poder explicar:
- metodología
- resultados
- conclusiones

---

## 6️⃣ Cómo te evaluarán

| Parte | Puntos |
|-------|--------|
| Metodología correcta | 2 |
| Overfitting vs tamaño | 2 |
| Overfitting vs hiperparámetro | 2 |
| Semi-supervisado | 2 |
| Documentación + defensa | 2 |
| **Total** | **10** |

---

## 💡 Consejo importante

Si haces bien:
- validación cruzada
- separación train/val/test
- análisis razonado

→ tienes prácticamente el aprobado asegurado.

---

Si quieres, también te puedo preparar la **estructura base del notebook (plantilla lista para empezar)**.
