# Limitaciones y validación · FarmaInforme v1

## Límites clínicos y de datos

- Versión docente con datos ficticios. No es un producto sanitario certificado ni una autorización de uso clínico.
- Las plantillas son propias y adaptables: no constituyen un formulario SOLES nacional ni una reproducción oficial de GENESIS/MADRE.
- No analiza evidencia, compara ensayos, obtiene financiación o verifica bibliografía automáticamente. Las afirmaciones y marcas de verificación proceden del usuario.
- La edición manual no se analiza semánticamente; el autor debe revisar si sus afirmaciones siguen correspondiendo a las fuentes.
- El cálculo presupuestario es una diferencia aritmética anual de costes con supuestos aportados, no una evaluación económica completa.
- El navegador guarda borradores sin cifrar y sin sincronizar; la cuota, el modo privado o borrar datos del sitio pueden impedir su conservación. No usar para datos de pacientes sin autorización institucional y controles adecuados.

## Límites técnicos

- DOCX es un subconjunto de Open XML con estilos sencillos. Debe comprobarse en el procesador de textos institucional; no se ha afirmado una validación visual en todas las versiones de Microsoft Word o LibreOffice.
- PDF requiere la opción Guardar como PDF del navegador; no es una descarga automática. La numeración depende de sus opciones de cabecera y pie.
- La aplicación no funciona desde file:// ni ofrece un service worker para instalación sin conexión. Una vez cargada, la elaboración no requiere servicios externos; la guía carga los documentos al abrirlos.
- Las búsquedas externas dependen de disponibilidad y condiciones del proveedor. No se integran APIs ni se promete que el contenido externo esté actualizado.
- La aplicación y la documentación son públicas. La clave del taller no proporciona autenticación a estas rutas.

## Registro histórico antes de la migración

Validación realizada el 10 de noviembre de 2026 en el entorno de desarrollo:

- Node 24.22.1: 13 pruebas de node:test aprobadas, sin fallos ni omisiones. Cubren las tres modalidades, fecha, obligatoriedad, omisiones, modo CFT, costes, trazabilidad, borradores, cuota, datos dañados, URLs, edición y DOCX.
- Chromium con Playwright para Python 1.62.0: recorridos completos de las tres modalidades aprobados. Exportaciones DOCX abiertas con python-docx 1.2.0; se verificaron ZIP, CRC, XML, metadatos, texto, logo, tabla económica y pie PAGE.
- Tres PDF de demostración de cuatro páginas, generados por el motor de impresión de Chromium. pypdf 6.10.0 confirmó metadatos visibles, medicamento ficticio, referencias aportadas, avisos y ausencia de controles del formulario en el texto. Se comprobó que el botón invoca impresión. La elección manual de impresora o Guardar como PDF depende del sistema del usuario.
- Edición final con una etiqueta HTML maliciosa tratada como texto, sin ejecución; DOCX editado comprobado. Botones de exportación bloqueados hasta confirmar revisión.
- Guardado y recuperación tras recarga, borrado individual y total, historial dañado y conservación de una clave de otra aplicación: aprobados. El manejo de cuota se comprueba en la prueba del núcleo.
- Anchuras 360, 390, 768 y 1440 px en bienvenida, formulario y vista previa; tabla sin desbordamiento. Etiquetas de formulario, activación por teclado y lectura alternativa del tutorial sin JavaScript: aprobadas. Se revisaron capturas de bienvenida y móvil.
- Seis pasos del tutorial, documentos del mismo origen, copia de especificación original y prompt de auditoría, persistencia y reinicio de marcas y enlaces locales: aprobados. Sin peticiones a servicios externos durante los recorridos de aplicación y tutorial; sin errores JavaScript ni respuestas HTTP fallidas en esas rutas.
- Integración local con Santiago: desbloqueo con la clave actual, enlace a la aplicación, regreso con sesión recuperada y enlace al tutorial, aprobados. Se comparó la fuente con el commit de partida 834cb61: fuera de la ficha FarmaInforme se conserva exactamente el contenido previo, incluidas las otras tres herramientas y los materiales.
- talleres:check y talleres:verify para Santiago aprobados tras regenerar solo Santiago. validate-google-ia y validate-recursos-ia aprobados. validate-content ejecutado en una copia temporal para no modificar su informe versionado: 35 módulos, sin errores.
- npm test conserva un fallo previo: sitemap.xml no coincide con el generador. No se regeneró ni se alteró para ocultar el fallo, que ya existía antes de FarmaInforme.

No se ha realizado validación clínica, auditoría profesional independiente, certificación de accesibilidad ni comprobación visual en Microsoft Word, LibreOffice, Safari o Firefox. Los enlaces y APIs externos no se han dado por verificados frente a bloqueos de red. Las pruebas del despliegue público de esta versión deben registrarse separadamente: las pruebas anteriores se ejecutaron localmente, no demuestran publicación.

## Segunda versión propuesta

Plantillas institucionales validadas, pruebas visuales en los procesadores de textos objetivo, accesibilidad con usuarios, importación/exportación de borradores bajo política del centro y una evaluación separada de cualquier integración con fuentes o IA. No añadir sincronización o datos reales por defecto.

## Validación del repositorio independiente

La migración conserva código y capacidades y modifica únicamente empaquetado, rutas, documentación, despliegue y enlaces. npm test ejecuta las pruebas propias, sin el validador general de la web personal. El script de navegador se ejecutó satisfactoriamente bajo /farmainforme/: tres modalidades, DOCX y PDF de cuatro páginas por modalidad, borradores, edición literal, móviles, teclado, seis pasos y copia de prompts, sin errores de JavaScript o HTTP ni tráfico externo. Se verificaron también las 13 pruebas Node, la sintaxis YAML de los workflows y el empaquetado de Pages. El núcleo, formularios y motor DOCX se compararon byte a byte con la implementación de origen sin cambios. Estas comprobaciones no equivalen a ejecutar GitHub Actions en sus servidores. Las pruebas cifradas de Santiago siguen perteneciendo al repositorio de la web.

La implementación se incorporó a main y el primer despliegue público fue confirmado por GitHub Pages en https://github.com/ramonmorillo/farmainforme/actions/runs/42848611792 (commit 8ea9813), con destino ramonmorillo.es/farmainforme/. La comprobación directa del dominio desde el entorno de desarrollo estuvo bloqueada por su proxy; no se presenta como prueba funcional remota. Cada actualización posterior debe verificar su propio despliegue. Una rama subida no demuestra publicación. No se han transferido los borradores de un navegador u origen anterior; localStorage pertenece al origen desde el que se ejecuta la aplicación.

Se comprobó además el artefacto estático servido desde la raíz y el recorrido taller cifrado → enlace externo de proyecto → aplicación → tutorial. Para esta última prueba el dominio externo se simuló en el navegador con los archivos locales del artefacto; no demuestra disponibilidad del dominio público. La comprobación del taller se ejecutó en su repositorio, sin copiar la clave ni los materiales a FarmaInforme.
