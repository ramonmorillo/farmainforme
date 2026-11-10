# FarmaInforme

Aplicación docente para elaborar solicitudes especiales SOLES adaptables al centro, informes CFT breves o extensos y evaluaciones individualizadas. Incluye un tutorial reproducible de seis pasos, prompts y pruebas.

## Estado y revisión

La implementación está en la rama `feature/farmainforme`. Abre una PR hacia `main` para revisarla antes de publicar. No hay que fusionar la antigua implementación en la web personal: allí se conserva únicamente la ficha del taller con enlaces externos.

## Ejecutar

Requisitos: Node.js >=18 y Python 3. No hacen falta paquetes npm, backend, claves API ni compilación.

```sh
git clone https://github.com/ramonmorillo/farmainforme.git
cd farmainforme
git switch feature/farmainforme
npm run serve
```

La aplicación está en la raíz del servidor local; el tutorial, en `tutorial.html`. No abras `index.html` mediante file://. Las rutas relativas permiten servir el mismo contenido en la raíz, en `/farmainforme/` o bajo otro prefijo.

## Comprobaciones

```sh
npm test
npm run test:browser
```

Las 13 pruebas Node no requieren dependencias. Las pruebas de navegador requieren Playwright para Python, python-docx, pypdf y Chromium, herramientas de desarrollo que no se descargan en la aplicación. El script levanta un servidor temporal bajo `/farmainforme/` para detectar dependencias de rutas absolutas y verifica los tres informes, DOCX/PDF, borradores, edición, teclado, móvil y tutorial. Artefactos fuera del repositorio. Consulta `docs/tutorial/limitaciones.md`.

## Publicar después de fusionar la PR

1. En este repositorio abre **Settings → Pages → Build and deployment → Source → GitHub Actions**.
2. Fusiona la PR a `main`. El workflow `Publicar FarmaInforme en GitHub Pages` prueba y publica solo los archivos públicos. También se puede ejecutar manualmente desde Actions.
3. Comprueba el despliegue y la dirección que devuelve Pages. La URL prevista es `https://ramonmorillo.github.io/farmainforme/`; GitHub puede redirigir al dominio personalizado heredado de la web del propietario.
4. Abre la aplicación y `tutorial.html`, prueba una demostración y las dos exportaciones.
5. Solo tras verificar ese despliegue, fusiona el cambio de enlaces del taller en `ramonmorillo.github.io`.

El workflow no se activa al subir una rama de desarrollo. Una PR abierta tampoco publica nada. No se incluye CNAME ni se configura un dominio personalizado para este proyecto.

## Documentación y alcance

Tutorial: `tutorial.html`; documentos: `docs/tutorial/`; arquitectura: `docs/tutorial/arquitectura.md`; pruebas: `tests/` y `scripts/`. El código de la aplicación está en la raíz. `.github/workflows/` contiene pruebas Node para PR y publicación al fusionar a main.

No hay IA, análisis automático de evidencia ni bibliografía generada. PDF usa el diálogo de impresión del navegador; DOCX es Open XML editable real. Las fuentes se verifican manualmente. Los borradores locales no se cifran. Solo datos ficticios: requiere revisión farmacéutica y no es un producto sanitario certificado. La aplicación es pública y no hereda la clave del taller.

## Procedencia

Migración desde `ramonmorillo/ramonmorillo.github.io`, commit `5c98668`. Se conservan las licencias de las fuentes y el registro de decisiones. Consulta `NOTICE.md`. No se incluyen claves, talleres cifrados ni materiales de otras herramientas.
