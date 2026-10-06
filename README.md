# Análisis de atención, NPS y CSAT – CCC

Página estática (un solo archivo `index.html`, sin servidor ni dependencias que instalar).

## Qué hace
- **Análisis del reporte de casos:** carga el Excel "Cases con correos" de Salesforce y, por caso y por correo de agente, muestra qué faltó (saludo, empatía, agradecimiento, próximos pasos, plazo, cierre), tiempos de respuesta, casos sin responder, correos repetidos, y alertas de seguridad del producto. Incluye ideas para ganar promotores y un resumen por agente. Permite descargar el detalle en CSV.
- **Matriz de calidad:** incluye la matriz de causas raíz de detractores (Contact Center, Process, Product, etc.) con su causa secundaria, cuándo aplica y qué se espera del agente. Cada caso muestra una causa raíz sugerida con la evidencia encontrada. Es una sugerencia: el analista de calidad confirma.
- **Calculadora NPS y CSAT:** cada agente calcula sus indicadores y recibe feedback y guías de atención por tipo de cliente.

## Publicar en GitHub Pages
1. Crea un repositorio nuevo y sube `index.html` y este `README.md` a la raíz.
2. En el repositorio: **Settings → Pages → Build and deployment → Source: Deploy from a branch**.
3. Elige la rama `main` y la carpeta `/ (root)`, y guarda.
4. En uno o dos minutos la página queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

## Privacidad
- El Excel se lee **solo en el navegador**: no se sube ni se guarda en ningún lado.
- No subas el reporte con datos de clientes al repositorio; solo el `index.html`.
- La página carga la librería SheetJS desde `cdnjs.cloudflare.com` (requiere internet). Si tu red la bloquea, descarga `xlsx.full.min.js` al repositorio y cambia la ruta del `<script>`.

## Formato esperado del reporte
Columnas: `Número del caso`, `Última modificación por: Nombre completo`, `Nombre De`, `Cuerpo del texto`, `Dirección de origen`, `Fecha del mensaje`, `Country Marketed`, `Insert Brand`, `Product Description (SKU)`, `Subjects`.
Los correos de agentes se identifican por el dominio `@kenvue.com`; los automáticos (`noreply`) se ignoran.

## Parámetros
El SLA de respuesta (24 h) y el máximo de correos de agente por caso (4) se ajustan en la página y recalculan el análisis. Son valores iniciales, no vienen de la matriz.

## Actualizar la matriz
La matriz está en el arreglo `QM` dentro de `index.html`. Si el equipo de calidad cambia una causa, edita ese arreglo.

## Límites
- Las reglas son palabras clave: ayudan a priorizar la revisión, no reemplazan la auditoría de calidad.
- Salesforce corta el cuerpo del correo cerca de 1.000 caracteres; en esos casos no se evalúa el cierre.
