
# Introducción: ¿Cómo codificar lenguaje?
- Codificación ingenua (Bag of Words, one-hot):
  - No considera el orden.
  - No genera espacio semántico.
- Palabras cercanas no son necesariamente similares.
- Necesitamos representaciones continuas + muchos datos.

# Modelos de lenguaje neuronales
- Típicamente las palabras son codificadas en **one-hot**.
- Solución: **matriz de embeddings** entrenada junto al modelo.
- Propiedades de embeddings:
  - Capturan similitud semántica.
  - Espacio vectorial refleja relaciones entre palabras.
- Técnicas populares: **Word2Vec, GloVe**.
- Producto esencial: **matriz de embedding**.

# Propiedades de embeddings
- Generan **vecindades semánticas** (palabras similares → vectores cercanos).
- Capturan relaciones con operaciones vectoriales:
  - `king - man + woman ≈ queen`.
- Usados como base en múltiples tareas de NLP.

# Limitaciones de embeddings simples
- Codifican palabras, no frases.
- Para frases → sumar o promediar embeddings.
- Pierden información secuencial y contextual.
- Necesitamos modelos que consideren **orden** y **contexto**.

# Seq2Seq al rescate
- Introducen arquitectura **encoder-decoder** basada en RNN.
- **Encoder**:
  - Procesa secuencia de entrada.
  - Genera vector contextual (estado oculto).
- **Decoder**:
  - Genera secuencia de salida a partir del contexto.
- Aplicable a cualquier tipo de secuencia (traducción, resumen, etc.).

# Propiedades de Seq2Seq
- Entrada y salida pueden tener distintos largos.
- El vector de contexto **C** codifica la información relevante.
- Captura el orden de las palabras → ventaja sobre BoW.
- Ejemplo: **Traducción automática** (Sutskever et al., 2014).

# Limitaciones de Seq2Seq básico
- Dependen totalmente de un único vector de contexto C.
- C tiene **importancia fija** en todos los pasos.
- Difícil capturar información de secuencias largas.

# Atención: contextos adaptativos
- Introduce una capa adicional para ponderar relevancia.
- Cada paso del decoder “atiende” a distintos estados del encoder.
- Ventajas:
  - Especialización paso a paso.
  - Reduce carga en el vector C.
- Mecanismo diferenciable (aprendido con SGD).
- Modelo de Bahdanau et al. (2015) → **soft-attention**.

# Ejemplos de atención
- Traducción automática (See & Manning, 2017).
- Resumen de documentos.
- Image captioning (Xu et al., 2015):
  - Traducción de “lenguaje visual” a texto.
  - Problema: vocabulario visual no está definido.
  - Solución: usar features de última capa convolucional.
- Atención sobre objetos → mejoras (Anderson et al., 2018).

# Conclusiones
- One-hot → no semántico, sin orden.
- Embeddings → espacio semántico útil, pero sin contexto.
- Seq2Seq → encoder-decoder para modelar secuencias.
- Atención → asigna pesos dinámicos, mejora representaciones.
- Base para Transformers y modelos modernos.

# Lecturas recomendadas
- Visualizing NMT: https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/  
- Show, Attend and Tell (Xu et al., 2015): https://arxiv.org/pdf/1502.03044.pdf/  
