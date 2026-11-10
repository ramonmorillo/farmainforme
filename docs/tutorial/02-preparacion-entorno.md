# 2. Preparación del entorno

## Reproducir la aplicación existente

Repositorio: https://github.com/ramonmorillo/farmainforme. El código está en la raíz; la documentación, en docs/tutorial/. No depende del checkout de la web personal.

```sh
git clone https://github.com/ramonmorillo/farmainforme.git
cd farmainforme
git switch -c ejercicio/farmainforme
npm run serve
```

Si la PR inicial aún no está fusionada, cambia primero a feature/farmainforme y crea tu rama de ejercicio desde ella. En tu ordenador abre la raíz del servidor local y tutorial.html. No uses file://: los módulos necesitan HTTP. Node.js >=18 sirve para los tests y Python 3 para el servidor; no hace falta npm install.

Si ya existe un checkout en un entorno en la nube, úsalo: cada tarea ya está aislada. No crees worktrees salvo petición explícita. Conserva cambios ajenos y revisa git status. El navegador de pruebas monta el repositorio bajo /farmainforme/ para reproducir las rutas de un sitio de proyecto de GitHub Pages.

## Crear tu propio proyecto

Crea un repositorio de ejercicio y copia los archivos de este proyecto conservando su estructura y las licencias de assets/fonts/. No copies CNAME, claves ni materiales del taller. Las referencias locales son relativas; los enlaces de vuelta al taller son externos y explícitos. Comprueba también una publicación bajo un prefijo, no solo la raíz. Consulta NOTICE.md antes de redistribuir los materiales.

## Con Claude Code

Instala y autentica Claude Code mediante su documentación oficial vigente: https://code.claude.com/docs/. Entra en la carpeta del proyecto y abre una sesión con el comando claude. Proporciona la especificación del paso 3 y pide primero una auditoría de los archivos existentes. La autenticación del agente no se incorpora a la aplicación ni al repositorio. Disponibilidad y coste del agente dependen de tu cuenta.

## Con Codex

Usa Codex en tu editor, terminal o entorno en la nube según tu instalación, siguiendo https://developers.openai.com/codex/. En la nube selecciona el repositorio y su rama; localmente abre la carpeta con la herramienta instalada. Comprueba qué archivos puede editar y qué comandos puede ejecutar. No asumas que la autenticación, las herramientas de navegador o las dependencias de pruebas de otro entorno están disponibles.

## Flujo básico

```sh
git status --short
npm run test:farmainforme
git diff --check
git diff --stat
```

Lee las diferencias antes de hacer un commit. Nunca incluyas contraseñas, borradores ni datos de pacientes. El código se publica, pero los procesos y las sesiones del navegador no viajan con él.
