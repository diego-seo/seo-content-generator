# Criterios de citabilidad en IA

Guía para escribir contenido que los modelos de lenguaje extraigan y citen, no solo que Google indexe.

**Regla de oro:** Google rankea páginas. Un modelo cita pasajes. Son dos objetivos distintos y a veces empujan en direcciones opuestas.

## Fuente de los datos

Los porcentajes de este documento provienen del análisis de Kevin Indig (Growth Advisor) publicado en Growth Memo en febrero de 2026, sobre 18.012 citaciones verificadas de ChatGPT, reseñado por Search Engine Land. Se complementa con dos análisis posteriores del mismo autor: uno de marzo de 2026 sobre concentración de dominios citados, y uno de abril de 2026 sobre 815.000 pares consulta-página.

**Limitaciones que hay que tener presentes:**
- Un solo investigador, metodología propia, sin replicación independiente publicada
- Mide principalmente ChatGPT, no Perplexity, Claude ni Gemini
- Los patrones son correlaciones observadas, no causalidad demostrada
- No sustituyen las Quality Rater Guidelines de Google para el objetivo de ranking

Usar como evidencia que respalda decisiones de redacción, nunca como ley física.

## 1. La rampa de esquí: dónde poner lo importante

Distribución de las citaciones según su posición en el artículo:

| Tramo del artículo | Porcentaje de citas |
|---|---|
| Primer 30% | 44,2% |
| Tramo central | 31,1% |
| Último tercio | 24,7% |
| Último 10% de la página | entre 2,4% y 4,4% |

El estudio califica el patrón de estadísticamente indiscutible. La interpretación del autor es que el modelo clasifica rápido: decide temprano si la página responde la consulta.

**Qué hacer:**
- La definición del término principal, en el primer 30% del texto
- El dato más fuerte del artículo, arriba, no reservado para el final
- Si hay una cifra propia o un hallazgo original, en los primeros párrafos

**Qué no hacer:**
- Guardar la conclusión valiosa para el cierre. Casi nadie la cita y ningún modelo la extrae
- Abrir con contexto histórico, definiciones de diccionario o rodeos antes del punto
- Poner la tabla comparativa o el resumen al final del artículo

### El matiz que casi todos aplican mal

A nivel de párrafo el patrón se invierte:

| Posición dentro del párrafo | Porcentaje de citas |
|---|---|
| Oración del medio | 53% |
| Primera oración | 24,5% |
| Última oración | 22,5% |

Adelantar lo importante aplica al artículo completo, no a cada párrafo. Forzar una definición en cada primera línea produce textos mecánicos. Dentro del párrafo, priorizar claridad y densidad de información sobre la posición.

## 2. Densidad de entidades: el criterio más medible

| Tipo de texto | Nombres propios sobre el total |
|---|---|
| Texto promedio en inglés | 5% a 8% |
| Texto muy citado | 20,6% |

Un modelo cita pasajes que contienen referentes concretos: marcas, productos, estándares, normas, cifras, nombres de sistemas, términos técnicos del sector.

**Ejemplo real de contraste** (mismo sitio, mismo sector, una página se cita y la otra no):

Página citada, describe qué hace el producto:
> valida reclamaciones contra PO, precio, promoción y términos de flete, y soporta SAP, Oracle y Microsoft Dynamics

Página nunca citada, subtítulos de la misma web:
> Results-Driven, Radically Simple, Deeply Flexible, Enterprise Trust

El segundo bloque no contiene una sola entidad. No hay nada que un modelo pueda extraer ni verificar.

**Qué hacer:**
- Nombrar sistemas, normas, estándares y marcas del sector cuando el brief lo permita
- Sustituir adjetivos de valor por sustantivos verificables
- Incluir cifras con su unidad y su fuente

**Qué no hacer:**
- Subtítulos de eslogan que no describen nada
- "Optimiza tus procesos" en lugar de "reduce el tiempo de conciliación de facturas"
- Adjetivos como flexible, potente, innovador, sin el dato que los sostenga

## 3. Encabezados en pregunta

El contenido citado tiene el doble de probabilidad de incluir signos de interrogación. Y el dato clave: el 78,4% de las citaciones asociadas a preguntas provenían de encabezados, no del cuerpo.

La lectura del autor es que el modelo trata cada H2 como un prompt y el párrafo siguiente como su respuesta.

**Importante, para no confundirlo con un patrón de IA:** una pregunta retórica de gancho sigue siendo un patrón a evitar. La diferencia está en si la pregunta se responde.

| Tipo | Ejemplo | Veredicto |
|---|---|---|
| Retórica de gancho | "¿Quieres más tráfico orgánico?" | Evitar. No se responde, solo genera expectativa |
| Encabezado que se responde | "¿Cómo se calcula el rebate acumulado?" | Usar. El párrafo siguiente lo contesta |

**Qué hacer:**
- Convertir en pregunta los H2 que en efecto se responden en el párrafo siguiente
- Responder en la primera o segunda oración después del encabezado, sin preámbulo
- Incluir una pregunta delimitadora por artículo cuando aplique, del tipo "en qué se diferencia X de Y", porque delimita el concepto frente a sus vecinos

**Qué no hacer:**
- Convertir todos los encabezados en preguntas de forma mecánica
- Preguntas cuya respuesta llega cuatro párrafos después

## 4. Sentimiento balanceado

Las citaciones se agrupan alrededor de 0,47 de subjetividad en la escala del estudio: ni dato seco ni opinión emocional. El autor lo describe como tono de comentario de analista, la combinación de hecho más interpretación.

Esto corta en dos direcciones y ambas importan:

- **Demasiado promocional** pierde citas: superlativos, entusiasmo, lenguaje de venta
- **Demasiado neutral** también pierde: la definición de diccionario sin interpretación no aporta nada que un modelo quiera citar

**Qué hacer:**
- Dar el dato y después qué significa para el lector
- Tomar posición cuando hay evidencia que la respalde
- Mantener el registro de análisis profesional

**Qué no hacer:**
- Describirse como referencia neutral. Ese posicionamiento baja la subjetividad por debajo del punto útil
- Enumerar hechos sin decir qué implican
- El extremo opuesto: adjetivos de marketing sin sustento

## 5. Claridad de nivel negocio

| Grupo | Grado Flesch-Kincaid |
|---|---|
| Contenido más citado | 16 |
| Contenido que rinde peor | 19,1 |

Grado 16 corresponde a lectura de nivel profesional, no a texto simplificado. La diferencia se explica por frases más cortas y sintaxis más directa, no por vocabulario más pobre.

**Qué hacer:**
- Sujeto, verbo, objeto. Una idea por oración
- Terminología técnica del sector cuando aporta precisión
- Frases cortas para las afirmaciones que se quieren ver citadas

**Qué no hacer:**
- Subordinadas encadenadas
- Simplificar la terminología técnica: eso baja la densidad de entidades
- Confundir claridad con contenido superficial

## 6. Longitud: el trade-off que hay que declarar

El análisis de abril de 2026, sobre 815.000 pares consulta-página, concluye que la estrategia de guía definitiva produce peores resultados de citación que una página más corta y enfocada.

Esto entra en tensión con la lógica de posicionamiento tradicional, donde el contenido extenso capta más enlaces. **No hay una respuesta única: depende del objetivo del artículo.**

| Objetivo prioritario | Formato recomendado |
|---|---|
| Citación en herramientas de IA | Página corta y enfocada en una intención |
| Enlaces y autoridad en Google | Contenido extenso y exhaustivo |
| Ambos | Muchas páginas enfocadas organizadas en un clúster temático, con un hub que las conecte |

El análisis de marzo de 2026 encontró que las páginas citadas de forma repetida no son páginas de intención única aisladas, sino guías amplias a nivel de categoría que responden docenas de preguntas relacionadas. La reconciliación de ambos hallazgos: amplitud a nivel de sitio o clúster, brevedad a nivel de página individual.

**Preguntar al usuario cuál es el objetivo antes de decidir la extensión.** Si no lo especifica, asumir clúster: varias piezas enfocadas antes que una sola pieza extensa.

## 7. Investigación primaria

El estudio observa que la investigación primaria es rara, y que cuando aparece resulta mucho más densa en citaciones que una página ordinaria.

Esto conecta con el pilar de Originalidad del marco MC del skill: un dato propio no es solo señal de calidad para Google, es el activo más citable que existe, porque ningún competidor puede replicarlo.

**Qué hacer:**
- Si el cliente tiene datos agregados propios, proponer construir la pieza alrededor de ellos
- Encuestas al sector, benchmarks internos, resultados agregados y anonimizados de clientes
- Presentar el dato con metodología visible: muestra, periodo, forma de medición

## 8. Concentración de dominios: expectativa realista

El análisis de marzo de 2026 encontró que alrededor de 30 dominios capturan el 67% de las citaciones dentro de un tema. La conclusión del autor es que sin autoridad suficiente se queda fuera de un número limitado de plazas.

Consecuencia práctica al escribir: un artículo perfecto en un dominio sin autoridad temática puede no ser citado durante meses. El contenido es condición necesaria y no suficiente. Cuando el usuario espere resultados de citación, aclarar que también dependen de la autoridad del dominio y de los ciclos de actualización de los modelos, que ningún proveedor controla.

## Checklist de citabilidad

Verificar antes de entregar:

- [ ] La definición del término principal está en el primer 30% del texto
- [ ] El dato más fuerte del artículo no está reservado para la conclusión
- [ ] Densidad de nombres propios y entidades notablemente por encima de un texto genérico
- [ ] Los adjetivos de valor están sustituidos por sustantivos verificables o cifras
- [ ] Al menos un H2 en pregunta que se responde en el párrafo siguiente
- [ ] Si aplica, una pregunta delimitadora del tipo "en qué se diferencia X de Y"
- [ ] Cada afirmación importante cabe en una oración de sujeto, verbo y objeto
- [ ] El tono combina dato e interpretación, sin caer en promocional ni en enciclopédico
- [ ] La extensión responde al objetivo declarado por el usuario, no a una cifra por defecto
- [ ] Si hay datos propios disponibles, están en el artículo y con su metodología
