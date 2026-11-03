# CompetencIA

Tus competencias transversales, de A1 a C2, con evidencias verificadas. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/competencia/

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

Autoevaluación formativa de **cinco competencias transversales para el empleo** (Comunicación, Trabajo en equipo, Autogestión, Iniciativa y liderazgo, Adaptabilidad) con una **escala criterial de seis niveles, A1–C2**, a la manera del MCER de idiomas. Pensada para el Observatorio Ocupacional de la Universidad Miguel Hernández de Elche.

- **Estudiante:** rellena un perfil breve (titulación, rama, curso, empleo al que aspira, tipo de experiencia) y cuenta **una situación real por competencia** (120–250 palabras, guiada por cuatro preguntas: qué pasó, qué hice, qué resultado tuvo, qué aprendí). Opcionalmente indica en qué nivel se situaría antes de analizar.
- **La IA propone** un nivel por competencia con 1–3 **citas literales** de su texto, qué le falta para el nivel siguiente y una actividad de desarrollo ligada a su titulación y al empleo al que aspira.
- **El código comprueba:** cada cita debe aparecer en la situación de *esa* competencia (las de otra no cuentan); las que no aparecen se marcan ⚠ y se descartan. Después aplica un **tope por número de pruebas verificadas**: 0 → sin evidencia; 1 → como mucho B1; 2 → como mucho C1; 3 o más → sin tope. Si la IA propuso más, se dice. Situaciones de menos de 40 palabras no se analizan.
- **El estudiante confirma** el nivel final de cada competencia (puede cambiarlo; queda registrado). Ve su autoevaluación frente a lo que respaldan sus pruebas.
- **Salidas:** informe personal en Word, trabajo en JSON (para retomarlo) y, de forma voluntaria, una **ficha anónima CSV** para el Observatorio.
- **Panel del Observatorio** (sin IA): carga muchas fichas a la vez, descarta inválidas y repetidas, filtra por rama y curso y muestra la distribución de niveles confirmados, la mediana, la diferencia media entre autoevaluación y nivel confirmado y cuántos cambiaron la propuesta. **No desglosa grupos de menos de 5 fichas.** Exporta Word y CSV agregados.
- Los descriptores de nivel viven como datos en `src/competencias.js`: otra institución adapta el marco cambiando ese fichero.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador. No hace falta servidor.

## Privacidad

- Todo (perfil, situaciones, resultados, fichas del panel) se guarda en el navegador (IndexedDB). No hay servidor.
- Al analizar salen hacia el proveedor de IA elegido: las situaciones con correos, teléfonos, DNI/NIE y el nombre de la persona **enmascarados**, la titulación, el curso, la rama y el empleo al que aspira. El **nombre no se envía nunca**. Antes del primer envío se muestra lo que sale y se pide confirmación.
- El enmascarado no detecta nombres de terceras personas: la app pide no escribirlos.
- La ficha del Observatorio no contiene nombre ni texto de las situaciones; lleva un identificador aleatorio (para detectar duplicados) y el mes, no la fecha.

## Límites

- **No es un test psicométrico ni de personalidad, no diagnostica y no acredita.** Es una orientación formativa; los niveles dependen de lo que la persona sabe contar por escrito y del modelo de IA usado.
- La escala y los descriptores son una **propuesta propia**, inspirada en las capacidades transversales de ESCO, **no validada** psicométricamente. Antes de usarla para decisiones (o para investigación publicable) haría falta un estudio de validez y fiabilidad con jueces expertos, y el visto bueno del comité de ética.
- El código comprueba que las citas existen y limita el nivel por número de pruebas; **no puede comprobar que la IA haya interpretado bien el descriptor**. Por eso el nivel lo confirma la persona.
- Las fichas son autoinformes: se pueden manipular. El panel sirve para orientar acciones de grupo, no para comparar personas.
- Probado con IA simulada (OpenAI, Gemini y Claude) en Chromium; **no se ha probado con una clave real**.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche).


ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *CompetencIA* (v1.0.0) [Software]. (DOI en trámite)

## Pruebas

`node tests/nucleo_test.js` y `node tests/ejemplo_test.js` (lógica pura), `node tests/claves.js` (traducciones) y `python3 tests/smoke_test.py` (navegador con IA simulada).

## Licencia

MIT. Véase [LICENSE](LICENSE).
