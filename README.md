# Sitio de Vértice Studio

Una sola página. HTML, CSS y un poco de JavaScript, sin dependencias ni
framework. El logo va incrustado como SVG dentro del HTML: no se pide al
servidor y no parpadea al cargar.

## Cómo verlo

```bash
python3 -m http.server 8123 --directory vertice-studio
```
Luego abre http://localhost:8123

Tiene que servirse por HTTP. Abrir el `index.html` directo con doble clic no
carga la imagen del proyecto.

## Qué falta antes de publicar

| Marcador | Qué poner |
|---|---|
| `⟦X⟧` y `⟦Y⟧` | El plazo real de entrega, en semanas (en la sección de preguntas) |

Además:
- Cambiar el correo de Hotmail por `hola@verticestudio.mx` cuando esté el dominio.
- `assets/proyecto-1.jpg` ya es una captura real del sitio de Mirage Saltillo
  Norte (1440×900, 86 KB). Se generó con `qlmanage` y se recortó por debajo de
  la barra de navegación.
- Poner `og:url` y `og:image` absolutos con el dominio en vivo.

## Decisiones de construcción

- **Retícula.** Dos hairlines fijas enmarcan la columna de contenido. Se probó
  con cuatro columnas y cruzaban el texto: en la sección de preguntas hacían que
  se leyera como una tabla.
- **El ángulo del hero.** Vértice de 60° exactos, igual que el logo. Sin
  `preserveAspectRatio="none"`, que lo deformaba.
- **La animación firma.** Las líneas se dibujan con `stroke-dasharray`, en
  cascada de 110 ms. Los pasos del proceso trazan su línea superior al entrar.
- **Apariciones.** Opacidad más 14px, 300 ms ease-out, escalonadas 60 ms entre
  hermanos. `prefers-reduced-motion` apaga todo y deja el sitio completo.
- **Sin menú en celular.** Es una sola página y la acción que importa es
  "Escríbenos", que sí queda visible siempre. Un menú hamburguesa aquí sería
  ruido.
- **Sección oscura solo en el portafolio.** Es donde el trabajo del cliente
  brilla y donde el azul de la marca no compite con sus colores.

## Al publicar

Sirve como sitio estático en cualquier lado (Netlify, Vercel, Cloudflare Pages).
No hay build. Lo único importante: comprimir la imagen del proyecto y servir
todo por HTTPS.

## Publicación

El repositorio está conectado a Vercel. Cada `git push` a `main` publica solo
en https://vertice-studio-two.vercel.app en menos de un minuto. No hay que
subir zips ni arrastrar nada.
