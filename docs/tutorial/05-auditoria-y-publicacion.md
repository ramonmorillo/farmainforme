# 5. Auditoría y publicación

## Auditoría previa

Usa el prompt de auditoría de prompts-reutilizables.md. Exige evidencia de ejecución y un listado de límites; no permitas cambiar afirmaciones para convertir un test fallido en aprobado.

Revisa las tres modalidades, errores, omisiones, edición, borradores, borrado, logotipo, fuentes, DOCX, PDF, teclado y móviles. Comprueba que no hay tráfico de informes, referencias fabricadas, credenciales, renderizado de HTML aportado ni modificaciones de otras herramientas.

El consentimiento del revisor habilita las exportaciones; no certifica la revisión. La edición libre no vuelve a analizar el texto ni sus referencias. Abre el DOCX en el procesador de textos que se utilizará en el hospital y revisa paginación y logotipo. En PDF selecciona A4 y cabeceras/pies del navegador si necesitas números de página. La exportación PDF depende del diálogo de impresión, no de un servicio remoto.

## GitHub Pages en este repositorio

Este repositorio contiene exclusivamente FarmaInforme, su tutorial y pruebas. No tiene CNAME ni depende del generador de la web personal. Las rutas relativas funcionan bajo /farmainforme/ y en la raíz. La ficha de Santiago y su cifrado siguen en ramonmorillo/ramonmorillo.github.io.

```sh
git status --short
npm test
npm run test:browser
git diff --check
```

Abre la PR de feature/farmainforme a main. Antes de publicar, selecciona Settings → Pages → Source → GitHub Actions en este repositorio. El workflow .github/workflows/pages.yml prueba el núcleo, prepara _site con aplicación, assets y docs y publica al fusionar a main. Se puede volver a ejecutar desde Actions → Run workflow. El workflow ci.yml ejecuta las pruebas Node en PR y push. Las pruebas completas del navegador se ejecutan aparte con npm run test:browser; no se afirma que CI las ejecute.

La URL prevista es https://ramonmorillo.github.io/farmainforme/ y el tutorial está en tutorial.html. Usa como referencia definitiva la URL de salida de Pages, que puede redirigir al dominio personalizado del propietario. No fusiones los enlaces de la web del taller hasta comprobar el despliegue. No hagas force-push ni confundas una rama subida con una aplicación publicada.

## Verificación tras publicar

1. Confirma que GitHub Pages ha desplegado el SHA esperado y que su ejecución termina correctamente.
2. Abre /farmainforme/ en la URL publicada por Pages.
3. Carga una demostración, revisa y exporta un DOCX y un PDF.
4. Abre el tutorial y copia el prompt.
5. Desbloquea Santiago y sigue sus enlaces a aplicación y tutorial.
6. Si hay caché, recarga sin caché; no declares un éxito remoto basándote únicamente en un archivo local.

Si el entorno bloquea el dominio o no dispone de permisos de publicación, registra exactamente lo comprobado y deja la verificación remota como pendiente. No simules una URL de despliegue ni solicites credenciales en el frontend.

## Ejercicio

Audita un fallo introducido en una copia de ejercicio: cambia un identificador de campo sin cambiar el test. Lee el error, corrígelo en su origen y vuelve a ejecutar la prueba. Después revisa el diff para demostrar que no se debilitó la aserción.
