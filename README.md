# Landing personal · Proyecto 1 de AI Maker

Este repositorio es mi entrega del **Proyecto 1 del programa AI Maker de The Power**: una landing page personal **sin backend y sin base de datos**, hecha solo con HTML, CSS y herramientas.

- **Página publicada:** <https://javierpolai.github.io/AI_Maker_Proy1_LANDING/>
- **Código:** <https://github.com/javierpolAI/AI_Maker_Proy1_LANDING>

La página es una versión reducida y adaptada de mi web personal real, [jpolanco.es](https://jpolanco.es/). Aquí he dejado solo lo necesario para el ejercicio: presentación, sobre mí, experiencia, formación, aptitudes y contacto.

## Qué pedía el ejercicio y cómo lo cumple

| Requisito | Cómo se cumple |
|---|---|
| Página desplegada en una URL pública | Publicada con **GitHub Pages**, que sirve los archivos del repositorio tal cual (rama `main`, carpeta raíz). |
| Estructura HTML semántica | `header`, `nav`, `main`, `section`, `article`, `ol`/`ul`, `time` y `footer`. Detalle abajo. |
| Diseño responsive | Móvil primero, con puntos de corte de Tailwind (`sm`, `md`). Detalle abajo. |
| Estilos con Tailwind | Tailwind CSS v4: todo el diseño está en clases dentro de `index.html`. No hay CSS escrito a mano. |
| Código en GitHub | Este repositorio. |
| Secciones mínimas | Presentación, Sobre mí, Experiencia, Formación, Aptitudes y Contacto. |

## Arquitectura

Es una web **estática**: no hay servidor que ejecute código ni base de datos. El navegador recibe un HTML y un CSS ya hechos.

```
.
├── index.html        Contenido y estructura (con las clases de Tailwind)
├── css/styles.css    CSS final, generado por Tailwind (no se edita a mano)
├── src/input.css     Punto de entrada de Tailwind y paleta de colores propia
├── favicon.svg       Icono de la pestaña
├── package.json      Scripts y versión exacta de Tailwind
└── README.md         Este documento
```

Flujo de trabajo:

```
index.html + src/input.css  ──(Tailwind CLI)──►  css/styles.css  ──►  GitHub Pages
```

Tailwind lee las clases que uso en `index.html` y genera un CSS con **solo** lo necesario (unos 16 KB). Ese CSS generado se sube al repositorio, de modo que GitHub Pages no necesita compilar nada. La página no usa JavaScript.

## Cómo está hecho

### HTML semántico
Cada parte de la página usa la etiqueta que describe lo que es, no solo `div`:

- `header` con `nav` para el menú, `main` para el contenido y `footer` para el pie.
- Cada bloque de contenido es una `section` enlazada a su título con `aria-labelledby`.
- Un único `h1` (mi nombre), `h2` para cada sección y `h3` para sus elementos, sin saltos de nivel.
- La experiencia es una lista ordenada (`ol`) con cada puesto en un `article`; las fechas van en `time`.
- Accesibilidad básica: enlace «Saltar al contenido», foco visible con teclado, `lang="es"`, textos para lectores de pantalla en los enlaces que abren pestaña nueva.

### Diseño responsive
- Etiqueta `viewport` y enfoque **móvil primero**: los estilos base son los del móvil y se amplían en pantallas mayores.
- Puntos de corte de Tailwind: a partir de `sm` (640 px) los botones y el pie pasan de columna a fila; a partir de `md` (768 px) «Sobre mí» y «Aptitudes» se reparten en columnas.
- Comprobado en 390 px (móvil) y 1440 px (escritorio), sin desplazamiento horizontal.
- Además respeta el modo oscuro del sistema (`dark:`) y la preferencia de reducir movimiento.

### Estilos con Tailwind
- Tailwind CSS **v4.3.5** con su CLI. Los estilos se escriben como clases de utilidad directamente en el HTML (`rounded-xl`, `px-4`, `md:grid-cols-3`…).
- En `src/input.css` defino una paleta propia (azul petróleo y un detalle en vino) mediante `@theme`.

## Herramientas

- **HTML y CSS** como base.
- **Tailwind CSS** para los estilos.
- **Node.js y npm**, solo en desarrollo, para ejecutar Tailwind.
- **Git y GitHub** para el control de versiones y el repositorio; **GitHub Pages** para publicar.
- **Claude Code** (IA) como asistente para adaptar la landing a este ejercicio, siguiendo mis indicaciones y revisando el resultado, en línea con el espíritu del programa.

## Ejecutarlo en local

Hace falta [Node.js](https://nodejs.org/).

```bash
npm install
npm run build   # genera css/styles.css
npm run dev     # opcional: regenera el CSS al guardar cambios
```

Después, abre `index.html` en el navegador.

## Privacidad

El repositorio es público, así que solo contiene información que ya es pública en mi web y en mi perfil profesional. No incluye teléfono, correo, dirección, fotografías ni documentos personales. El contacto se hace por LinkedIn.
