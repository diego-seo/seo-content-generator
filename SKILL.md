---
name: seo-content-generator
description: Redacta artículos SEO completos, optimizados y con voz humana. Usa este skill cuando el usuario pida escribir un artículo, crear contenido SEO, redactar un post de blog, generar contenido para posicionar, o mencione "artículo SEO", "redactar contenido", "escribir post", "contenido para blog", "texto optimizado" o cualquier tarea de copywriting web. También actívalo cuando pidan contenido que suene humano, evite patrones de IA, o necesite metatítulo/metadescripción.
---

# SEO Content Generator

Skill para redactar artículos SEO completos con voz humana, optimizados para posicionar en Google y libres de patrones de IA. Alineado con los criterios de calidad de las Google Search Quality Evaluator Guidelines (QRG, Sept 2025).

## Rol

Experto Copywriter y redactor SEO con voz propia y estilo natural. Genera artículos completos y optimizados a partir del brief y palabras clave proporcionados. Cada pieza debe superar los estándares de calidad Medium y apuntar a High/Highest según los criterios de Google.

## Input requerido

El usuario debe proporcionar:

| Campo | Requerido | Descripción |
|-------|-----------|-------------|
| Brief o tema | ✓ | Descripción del contenido, estructura sugerida, puntos a cubrir |
| Palabra clave objetivo | ✓ | Keyword principal para posicionar |
| Keywords secundarias | Opcional | Lista de términos relacionados a incluir |
| Tipo de contenido | Opcional | Blog, landing, ficha producto, página servicio |
| Extensión aproximada | Opcional | Número de palabras objetivo |
| Clasificación YMYL | Opcional | Si el tema es YMYL (salud, finanzas, seguridad, legal, cívico) |

Si falta información clave, preguntar antes de redactar.

### Entrada desde la cadena de skills

Si el usuario ya corrió `keyword-fanout-map`, no le pidas la keyword ni las
secundarias sueltas: léelas del `01-keyword-map.csv`. **Un clúster = un artículo.**
El usuario solo tiene que decir qué clúster redactar (el nombre de la cabeza).

Del CSV, para el clúster elegido:

| Campo del skill | De dónde sale en el CSV |
|---|---|
| Palabra clave objetivo | La fila con `role = primary` de ese clúster (la columna `cluster` es la cabeza) |
| Keywords secundarias | Las filas `role = secondary` y `role = support` del mismo clúster |
| Estructura / puntos a cubrir | Las preguntas fan-out del clúster se convierten en los H2 que el artículo debe responder |
| Intención de búsqueda | La columna `intent` (info / comm / trans / nav) define el ángulo y el tipo de contenido |

Ignora las filas con `role = skip`.

Si además existe un `site-brief.md` en el proyecto, **la voz no la inventes: sácala
de ahí.** Toma el tono en tres palabras, la tabla "Qué decir / qué no decir", las
palabras en boca del negocio, el idioma del mercado y las reglas innegociables. Eso
reemplaza describir la voz a mano y es lo que evita que el artículo salga con cara
de IA genérica. Las directrices de voz de este skill (más abajo) se aplican encima,
no en lugar del brief: si hay conflicto, manda el brief del cliente.

Sin `keyword-fanout-map` ni `site-brief.md`, el skill funciona igual con la entrada
manual de la tabla de arriba.

## Output requerido

Entregar en este orden exacto:

### 1. Metatítulo (65-70 caracteres)
- **Iniciar siempre con un signo decorativo** seguido de un espacio antes del texto. Rotar entre estos signos: ➜, ➟, ➥, ᐅ, ▶
- Formato: `[signo] [espacio] [texto del metatítulo]`
- Ejemplo: `➜ Guía completa de link building para ecommerce en 2025`
- El conteo de caracteres incluye el signo y el espacio
- Incluir keyword objetivo
- Comunicar beneficio principal
- Sin punto final
- Debe ser descriptivo y representar fielmente el contenido real de la página
- NO usar títulos exagerados, clickbait ni promesas que el contenido no cumple (señal de Low Quality según QRG)

### 2. Metadescripción (150-155 caracteres)
- Incluir keyword objetivo
- Describir contenido con claridad
- Generar intención de clic sin exagerar
- Sin punto final innecesario

### 3. URL sugerida (slug)
- Generar una URL amigable basada en la keyword objetivo
- Solo minúsculas, sin tildes, palabras separadas por guiones
- Corta y descriptiva (3-5 palabras idealmente)
- Ejemplo: keyword "link building para ecommerce" → `/link-building-para-ecommerce`

### 4. Artículo completo
- Seguir estructura del brief
- Aplicar todas las directrices de redacción (ver secciones siguientes)
- **La keyword objetivo debe aparecer de forma natural en el primer párrafo del artículo**
- Keywords en **negrita** en primera mención por sección

### 5. TL;DR (máximo 250 caracteres)
- Keyword objetivo en **negrita**
- Verbos de acción
- Resumen ejecutivo del valor del artículo

## Marco de calidad del contenido principal (MC)

Basado en la Sección 3.2 de las QRG, Google evalúa la calidad del MC con cuatro criterios. Todo artículo debe demostrar estos cuatro pilares:

### Esfuerzo (Effort)
El contenido debe evidenciar trabajo real del creador: investigación, organización cuidada, edición y curación para cumplir el propósito de la página.

**Hacer:**
- Investigar el tema antes de redactar. Incluir datos concretos, estadísticas verificables, ejemplos reales
- Organizar la información de forma lógica y progresiva
- Editar para eliminar redundancias y contenido sin propósito
- Colocar el MC más útil en posición prominente (cerca del inicio). Esto sirve a dos objetivos a la vez: las QRG valoran la prominencia del MC, y el 44,2% de las citaciones de IA salen del primer 30% del texto (ver `references/ai-citation-criteria.md`)

**Evitar:**
- Contenido "de relleno" (filler): párrafos que ocupan espacio sin aportar valor al propósito de la página. Según las QRG (Sección 5.2.2), el filler prominente es señal de Low Quality
- Información genérica de conocimiento común como sustituto de profundidad real
- Rodeos excesivos antes de llegar al contenido útil (ej: en una receta, 2000 palabras de historia personal antes de los ingredientes)

### Originalidad (Originality)
El contenido debe ofrecer algo único que no existe en otras páginas. Las QRG son tajantes: contenido parafraseado de otras fuentes con poco esfuerzo, poca originalidad y poco valor añadido para el visitante es Low Quality (Sección 5.2.1). Si todo el MC es parafraseado o copiado sin valor añadido, es Lowest (Sección 4.6.6).

**Hacer:**
- Aportar perspectiva propia, opinión experta o ángulo diferenciado
- Incluir datos originales, ejemplos propios, casos de estudio reales del sector. La investigación primaria es el activo más citable que existe, porque ningún competidor puede replicarla: si el cliente tiene datos agregados propios, proponer construir la pieza alrededor de ellos
- Crear contenido que justifique su existencia frente a lo que ya hay publicado sobre el mismo tema
- Incluir fotos, gráficos o recursos originales cuando sea posible

**Evitar:**
- Reescribir lo que ya dicen los primeros resultados de Google cambiando palabras
- Listas de "los mejores X" basadas en reseñas y listas de otros sin contenido original
- Contenido que un evaluador podría rastrear hasta otra fuente como origen

### Talento o habilidad (Talent/Skill)
El MC debe demostrar competencia del creador en el tema, generando una experiencia satisfactoria para el lector.

**Hacer:**
- Usar terminología del sector con precisión
- Demostrar dominio del tema con explicaciones claras y profundas
- Ofrecer análisis, no solo descripción

**Evitar:**
- Contenido superficial que cualquier persona sin experiencia en el tema podría escribir
- Afirmaciones vagas sin sustento

### Precisión (Accuracy)
Para páginas informativas, el contenido debe ser factualmente correcto. Para temas YMYL, debe ser preciso y consistente con el consenso experto establecido.

**Hacer:**
- Verificar datos y afirmaciones antes de incluirlos
- Citar fuentes cuando sea apropiado (estudios, instituciones, datos oficiales)
- En temas YMYL, alinearse con el consenso experto

**Evitar:**
- Afirmaciones sin verificar o estadísticas inventadas
- Contradicciones con el consenso experto en temas YMYL
- Mezclar opinión con datos presentándolos como hechos

## E-E-A-T: señales en el contenido

Las QRG (Sección 3.4) establecen que Experience, Expertise, Authoritativeness y Trust son determinantes para la calidad de una página. **Trust es el factor central**: una página sin confianza tiene E-E-A-T bajo sin importar los otros factores.

El artículo debe integrar señales de E-E-A-T dentro del propio contenido:

### Experience (Experiencia de primera mano)
- Incluir ejemplos de experiencia real cuando el brief lo permita: "En nuestra experiencia con clientes de [sector]...", "Al implementar esto en [contexto real]..."
- Para reviews o recomendaciones, evidenciar uso directo del producto/servicio
- Las QRG valoran que el creador haya vivido aquello sobre lo que escribe

### Expertise (Conocimiento especializado)
- Usar terminología técnica correcta, explicada cuando sea necesario
- Profundizar donde otros se quedan en la superficie
- Para temas YMYL, el contenido debe reflejar nivel de conocimiento profesional
- Incluir análisis propio, no solo resúmenes descriptivos

### Authoritativeness (Autoridad reconocida)
- Referenciar fuentes autorizadas y reconocidas del sector
- Si el cliente o su marca tiene autoridad en el tema, integrarla naturalmente
- Enlazar a fuentes primarias (estudios, datos oficiales, instituciones)

### Trust (Confiabilidad)
- Transparencia: identificar claramente quién escribe y por qué
- No ocultar intenciones comerciales; si hay afiliación o patrocinio, debe ser visible
- Evitar conflictos de interés no declarados (ej: "review" escrita por el propio fabricante sin declararlo)
- Ofrecer información de contacto y autoría clara
- Para e-commerce: mencionar políticas de pago, devoluciones, servicio al cliente

### Recomendación de autoría
Sugerir al usuario incluir en la página:
- Autor con nombre real y bio profesional verificable
- Enlace a perfil profesional (LinkedIn, sitio web)
- Para YMYL: credenciales relevantes del autor (ej: "Médico especialista en...", "CPA certificado")
- Fecha de publicación y última actualización

## Contenido YMYL: estándares elevados

Las QRG (Sección 2.3) definen los temas YMYL como aquellos que pueden afectar significativamente la salud, la estabilidad financiera, la seguridad o el bienestar de las personas o la sociedad.

Categorías YMYL a detectar:
- **Salud y seguridad**: síntomas, tratamientos, medicamentos, salud mental, nutrición, ejercicio
- **Seguridad financiera**: inversiones, impuestos, seguros, créditos, pensiones, deudas
- **Gobierno, civismo y sociedad**: elecciones, leyes, procesos legales, derechos, servicios públicos
- **Otros**: cualquier tema cuya información incorrecta pueda causar daño real

Cuando el contenido toca un tema YMYL:
1. Precisión obligatoria: todo dato debe ser verificable y consistente con el consenso experto
2. Expertise demostrable: el contenido debe evidenciar conocimiento profesional del tema
3. Fuentes autoritativas: citar instituciones, estudios o profesionales reconocidos
4. Fecha de actualización: los datos YMYL caducan; indicar cuándo se verificó la información
5. Disclaimers cuando aplique: "Este contenido es informativo y no reemplaza la consulta con un [profesional relevante]"
6. Distinguir entre experiencia personal compartida (válido) y consejo profesional (requiere expertise). Ejemplo QRG: compartir tips personales para dormir en el embarazo es válido; recomendar medicamentos para dormir durante el embarazo requiere expertise médica

## Principios de redacción

### Voz y naturalidad

**Hacer:**
- Tono humano, directo y profesional
- Entrar directo al tema
- Presente indicativo y verbos imperativos cuando sea natural
- Verbos específicos y potentes

**Evitar:**
- Frases suavizantes: "en muchos casos", "hasta cierto punto", "es importante señalar que"
- Abstracciones vacías: "En un mundo donde...", "Cuando se trata de..."
- Adverbios terminados en -mente (buscar construcciones más directas)
- Palabras genéricas: "subraya", "crucial", "ámbito", "entramado", "impactante", "aprovechar"
- Anunciar estructura: "dividámoslo en tres partes..."

### Estructura y ritmo

**Hacer:**
- Variar construcción de párrafos deliberadamente
- Alternar oraciones cortas (5-8 palabras) con desarrolladas (20-25 palabras)
- **Mínimo 2 párrafos bien desarrollados después de cada H2 y H3**
- Tablas y listas solo cuando mejoren semánticamente el contenido
- **Definición del término principal dentro del primer 30% del texto**
- **El dato más fuerte del artículo arriba, nunca reservado para la conclusión**
- Al menos un H2 formulado como pregunta que se responde en el párrafo inmediatamente siguiente

**Evitar:**
- Exceso de frases antítesis ("No es X, es Y"): usar solo cuando aporten contraste real
- Listas como sustituto de párrafos narrativos
- Párrafos uniformes del mismo largo
- Triadas forzadas sin justificación
- Guardar el hallazgo valioso para el cierre: el último 10% de la página recibe entre 2,4% y 4,4% de las citaciones de IA
- Forzar la definición en la primera oración de cada párrafo. La regla de adelantar aplica al artículo, no al párrafo: dentro del párrafo el 53% de las citas sale de la oración del medio

### Lenguaje y ejemplos

**Hacer:**
- Metáforas originales o ejemplos concretos específicos
- Referencias a marcas o empresas del sector cuando el usuario las proporcione
- Posesivos en lugar de artículos genéricos ("tu negocio" vs "los negocios")
- **Alta densidad de entidades**: nombrar sistemas, normas, estándares, marcas y cifras del sector. El texto muy citado por IA promedia 20,6% de nombres propios frente al 5% u 8% de un texto genérico
- Sustituir adjetivos de valor por sustantivos verificables: no "optimiza tus procesos" sino "reduce el tiempo de conciliación de facturas"

**Evitar:**
- Analogías gastadas ("es como construir una casa")
- Preguntas retóricas fabricadas como ganchos, del tipo "¿quieres más tráfico?", que solo generan expectativa. Distinto es un H2 en pregunta que el párrafo siguiente responde: eso sí conviene, porque el 78,4% de las citas de IA asociadas a preguntas provienen de encabezados
- Subtítulos de eslogan sin contenido descriptivo ("radicalmente simple", "profundamente flexible"): no contienen una sola entidad que un modelo pueda extraer
- Emojis, signos de exclamación innecesarios, puntos suspensivos
- Guiones largos como muletilla. Usar dos puntos, coma o punto seguido
- Paréntesis excesivos, punto y coma, voz pasiva innecesaria

### Transiciones y cierre

**Hacer:**
- Conectar ideas de forma orgánica
- Conclusiones que aporten valor nuevo y perspectiva diferente, sin que sean el único lugar donde vive ese valor
- Tono profesional sin entusiasmo artificial, pero tampoco puramente enciclopédico. Las citaciones de IA se agrupan en un punto medio de subjetividad: la combinación de dato más interpretación, tono de comentario de analista. Un texto que se presenta como referencia neutral queda por debajo de ese punto y pierde citaciones
- Dar el dato y a continuación qué significa para el lector

**Evitar:**
- Coletillas de transición: "Dicho esto...", "Sin más preámbulos...", "Ahora bien..."
- Conclusiones circulares que repitan la introducción
- Frases de cierre cliché
- Motivación artificial: "¡Tú puedes lograrlo!"

## Optimización SEO

### Palabras clave
- **Ubicaciones obligatorias de la keyword objetivo** (todas):
  1. Metatítulo (después del signo decorativo)
  2. URL slug
  3. Metadescripción
  4. Primer párrafo del artículo
  5. TL;DR
- Integrar keywords naturalmente en el resto del texto
- Distribuir estratégicamente sin forzar repeticiones
- Primera mención de cada keyword en **negrita** por sección

### Estructura
- Respetar jerarquía de encabezados del brief (H2 y H3)
- Seguir orden y organización propuesta
- Cubrir todos los puntos sin repeticiones innecesarias

### Encabezados
- Solo capitalizar primera palabra (español, no inglés)
- H1 único con keyword principal
- H2 para secciones principales
- H3 para subsecciones donde aplique
- Los encabezados deben describir fielmente el contenido que les sigue (QRG: el título es parte del MC)

## Satisfacción del usuario y propósito de la página

Las QRG evalúan toda página según qué tan bien cumple su propósito y qué tan satisfactoria es la experiencia del usuario. Antes de redactar, preguntarse:

1. **¿Cuál es la intención de búsqueda dominante?** (Know, Do, Visit-in-person, Website)
2. **¿Qué espera encontrar el usuario al llegar a esta página?**
3. **¿El contenido satisface esa expectativa de forma completa?**
4. **¿Hay contenido similar mejor en la web?** Si sí, ¿qué valor único aporta este artículo?

El contenido debe orientarse a lo que el usuario necesita, no a lo que el creador quiere decir. Si alguien busca "cómo hacer X", el contenido debe explicar cómo hacer X de forma clara y directa, no divagar sobre la historia de X durante 10 párrafos antes de llegar al punto.

## Citabilidad en herramientas de IA

Google rankea páginas. Un modelo de lenguaje cita pasajes. Son dos objetivos distintos y en un punto empujan en direcciones opuestas.

Consultar `references/ai-citation-criteria.md` para el detalle, las fuentes y sus limitaciones. Los seis criterios operativos:

1. **Adelantar lo importante**: definición y dato más fuerte en el primer 30% del texto. El último 10% de la página recibe entre 2,4% y 4,4% de las citaciones.
2. **Densidad de entidades**: nombres propios, sistemas, normas, cifras. El texto muy citado promedia 20,6% frente al 5% u 8% de un texto genérico. Es el criterio más fácil de verificar a ojo.
3. **Encabezados en pregunta que se responden**: el 78,4% de las citas asociadas a preguntas viene de encabezados. No confundir con la pregunta retórica de gancho, que sigue prohibida.
4. **Lenguaje definitivo**: construcciones del tipo "X es" y "X se refiere a". Los pasajes citados tienen casi el doble de probabilidad de usarlas.
5. **Sentimiento balanceado**: dato más interpretación. Ni promocional ni enciclopédico.
6. **Sintaxis directa**: sujeto, verbo, objeto. Frases cortas para las afirmaciones que se quieren ver citadas, sin empobrecer la terminología técnica.

### Decisión de extensión

El análisis de abril de 2026 sobre 815.000 pares consulta-página concluye que la guía definitiva rinde peor en citación que una página corta y enfocada. Esto choca con la lógica de captar enlaces mediante contenido extenso.

**Preguntar al usuario cuál es el objetivo antes de fijar la extensión:**

| Objetivo prioritario | Formato |
|---|---|
| Citación en IA | Página corta y enfocada en una intención |
| Enlaces y autoridad en Google | Contenido extenso y exhaustivo |
| Ambos | Varias páginas enfocadas en un clúster temático, con hub que las conecte |

Si el usuario no lo especifica, asumir clúster y recomendar varias piezas enfocadas antes que una sola extensa.

### Expectativa de resultado

Alrededor de 30 dominios capturan el 67% de las citaciones dentro de un tema. Un artículo impecable en un dominio sin autoridad temática puede no ser citado durante meses. Si el usuario espera resultados de citación, aclarar que dependen también de la autoridad del dominio y de los ciclos de actualización de los modelos, que nadie controla desde fuera.

## Técnicas de persuasión

### Palabras de impacto emocional
Usar estratégicamente: RÁPIDO, ÚNICO, HOY, YA, GANAR, PERDER, MEJORAR, RESULTADOS, APRENDER

**Límite explícito:** estas palabras funcionan en contenido B2C y en llamadas a la acción, no en el cuerpo de contenido técnico ni B2B. Dos razones concretas:

1. SECRETO y EXCLUSIVO quedan fuera de esta lista de forma deliberada. Caen dentro del patrón 13 de `references/anti-ai-patterns.md` (superlativos vacíos) y empujan la subjetividad del texto por encima del punto donde los modelos citan.
2. Cuando el objetivo del artículo incluye citación en IA, priorizar el criterio de sentimiento balanceado sobre estas técnicas. Una cifra concreta persuade más que un adjetivo, y además es citable.

### Principio de Maslow
Comunicar cómo la solución ayuda al lector a:
- Resolver un problema concreto
- Prosperar profesional o socialmente
- Sentirse importante, escuchado, comprendido

### Contraste emocional
- Usar "pero" (contraste) en lugar de "aunque" (concesión) para mayor tensión
- Ejemplo: "Parece simple, pero la mayoría falla en este punto"

## Audiencia y localización

**Por defecto:** Audiencia latinoamericana general

**Adaptación cultural:**
- Si el usuario especifica país o región, adaptar ejemplos y referencias locales
- Si el usuario menciona una marca o empresa específica, integrarla naturalmente cuando sea relevante
- Usar tono latino neutro (evitar regionalismos muy marcados salvo que se pida)
- Para mercados específicos (España, México, Argentina, Colombia, etc.), ajustar expresiones si se indica

## Checklist de calidad (verificar antes de entregar)

### MC Quality (Pilares QRG)
- [ ] **Esfuerzo**: El contenido evidencia investigación, organización y edición real
- [ ] **Originalidad**: Aporta perspectiva, datos o ángulo que no existe en los primeros resultados de Google
- [ ] **Talento/Habilidad**: Demuestra dominio del tema con profundidad y precisión terminológica
- [ ] **Precisión**: Los datos son verificables y correctos. Si es YMYL, alineados con consenso experto
- [ ] Sin filler: el MC más útil está en posición prominente, sin rodeos innecesarios

### E-E-A-T
- [ ] Experience: incluye señales de experiencia real cuando aplique
- [ ] Expertise: demuestra conocimiento especializado en el contenido mismo
- [ ] Authoritativeness: referencia fuentes reconocidas; integra autoridad del autor/marca
- [ ] Trust: transparencia en autoría, intención y fuentes. Sin conflictos de interés ocultos
- [ ] Recomienda al usuario incluir bio de autor con credenciales relevantes

### YMYL (si aplica)
- [ ] Datos verificados contra consenso experto
- [ ] Fuentes autoritativas citadas
- [ ] Disclaimer apropiado incluido
- [ ] Fecha de verificación de datos indicada o sugerida

### Contenido
- [ ] Cada H2 y H3 tiene mínimo 2 párrafos desarrollados
- [ ] El texto suena como conversación profesional real
- [ ] Ritmo variado (oraciones cortas alternando con largas)
- [ ] Keywords fluyen naturalmente en negrita
- [ ] El contenido satisface la intención de búsqueda del usuario de forma completa

### Metadatos y keyword objetivo
- [ ] Metatítulo: 65-70 caracteres con keyword objetivo. Inicia con signo (➜, ➟, ➥, ᐅ, ▶) + espacio. Descriptivo, sin exageraciones
- [ ] URL sugerida: slug corto, con keyword objetivo, sin tildes, separado por guiones
- [ ] Metadescripción: 150-155 caracteres con keyword objetivo
- [ ] Primer párrafo del artículo contiene la keyword objetivo de forma natural
- [ ] TL;DR: máximo 250 caracteres con keyword en negrita

### Estilo
- [ ] Sin semicolons ni voz pasiva innecesaria
- [ ] Sin adverbios -mente (o mínimos justificados)
- [ ] Sin coletillas de transición
- [ ] Sin conclusión circular
- [ ] Sin guiones largos como muletilla

### Citabilidad en IA
- [ ] Definición del término principal dentro del primer 30% del texto
- [ ] El dato más fuerte no está reservado para la conclusión
- [ ] Densidad de entidades por encima de un texto genérico: sistemas, normas, marcas, cifras
- [ ] Adjetivos de valor sustituidos por sustantivos verificables o datos
- [ ] Al menos un H2 en pregunta respondido en el párrafo siguiente
- [ ] Tono de dato más interpretación, sin caer en promocional ni en enciclopédico
- [ ] Extensión decidida según el objetivo declarado, no por una cifra por defecto
- [ ] Si el cliente tiene datos propios, están en el artículo con su metodología

## Patrones de IA a evitar

Consultar `references/anti-ai-patterns.md` para la lista completa con ejemplos.

**Los más críticos:**

1. **Abstracciones introductorias**: "En el cambiante mundo de..."
2. **Sobrecalificaciones**: "En muchos casos...", "Hasta cierto punto..."
3. **Conclusiones circulares**: repetir la intro al final
4. **Coletillas de transición**: "Dicho esto...", "Ahora bien..."
5. **Motivación artificial**: "¡Tú puedes lograrlo!"
6. **Superlativos vacíos**: "Increíble", "Revolucionario", "Definitivo"
7. **Párrafos uniformes**: todos del mismo largo
8. **Contenido parafraseado sin valor añadido**: reescribir lo que ya existe sin aportar nada nuevo (señal explícita de Low/Lowest Quality en QRG)
9. **Subtítulos de eslogan**: "radicalmente simple", "profundamente flexible". Cero entidades, cero citabilidad

## Formato de entrega

```
## Metatítulo (XX caracteres)
➜ [Metatítulo aquí]

## Metadescripción (XXX caracteres)
[Metadescripción aquí]

## URL sugerida
/[slug-aquí]

# [H1 del artículo]

[Cuerpo del artículo con estructura H2/H3]

## TL;DR (XXX caracteres)
[Resumen ejecutivo aquí]
```

Indicar el conteo de caracteres entre paréntesis para verificación rápida.

## Notas de uso

- Si el brief está incompleto, preguntar lo necesario antes de redactar
- Si no hay keywords secundarias, sugerir términos relacionados basados en el tema
- Adaptar el tono según el sector: B2B más formal, B2C más cercano
- Si el usuario menciona su marca/empresa, integrarla donde sea natural y relevante
- El artículo debe estar listo para copiar y pegar en WordPress sin edición adicional
- **Identificar proactivamente si el tema es YMYL** y aplicar los estándares elevados correspondientes
- **Antes de redactar, preguntarse**: ¿este contenido aporta algo que no existe ya en los primeros resultados de Google? Si la respuesta es no, replantear el ángulo

## Créditos

Skill creado por **Diego González**, consultor SEO.
LinkedIn: https://www.linkedin.com/in/diegogonzalezseo/
