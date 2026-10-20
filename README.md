# Multiplica Conmigo — MVP funcional

Aplicación web progresiva (PWA) para práctica breve y amable de matemáticas, diseñada con principios de accesibilidad, autonomía y baja carga cognitiva.

## Incluye
- Suma, resta, multiplicación (tablas 1–12) y división relacionada.
- Nombre opcional del niño.
- 10 ejercicios por sesión; respuesta por opciones grandes o teclado numérico.
- Mensajes de reintento amables; no muestra “incorrecto” ni revela la solución al fallar.
- Pistas, pausa, progreso visual y celebración final con elección de tres tablas siguientes, suma, resta, división o regreso al menú principal.
- Guardado local de sesiones y borrador sin cuenta, reanudación tras salir y exportación JSON.
- Diseño responsive para móvil, tableta y PC; manifest PWA y service worker para uso sin conexión después de la primera carga.
- Respeta `prefers-reduced-motion`, controles grandes, foco visible, etiquetas accesibles y regiones `aria-live`.

## Ejecutar localmente
Por las reglas de seguridad del navegador, la PWA y el service worker deben probarse desde `localhost` o HTTPS. En la carpeta del proyecto:

```bash
python -m http.server 8080
```

Luego abre `http://localhost:8080`. Para instalarla en Android/Chrome, usa el menú del navegador → “Instalar aplicación” o “Añadir a pantalla de inicio”. En iPhone/iPad, abre en Safari y usa Compartir → Añadir a pantalla de inicio. En PC, usa el icono Instalar del navegador compatible.

## Publicación
Es un sitio estático: puede publicarse en cualquier hosting HTTPS que sirva archivos estáticos (por ejemplo, GitHub Pages, Netlify, Vercel o un hosting propio). No requiere compilación ni claves API. Al actualizar `app.js`, `styles.css` o `index.html`, cambia el nombre de caché en `sw.js` para forzar una nueva versión.

## Persistencia y privacidad
La versión inicial guarda datos en `localStorage` del navegador/dispositivo. No se envían nombres ni resultados a un servidor. El progreso no se sincroniza automáticamente entre dispositivos y puede perderse si se borran los datos del navegador; exporta el JSON para conservar una copia. Para sincronización entre dispositivos, se recomienda añadir Supabase con perfiles de tutor, consentimiento y políticas RLS en una fase posterior.

## Decisiones didácticas y límites
- Las tablas tienen 10 ejercicios: en multiplicación se practica el factor seleccionado por 1–10. La división usa divisiones exactas relacionadas con el número seleccionado. La resta trabaja diferencias sencillas relacionadas con la selección.
- No hay cronómetro competitivo, penalización ni rachas obligatorias. El tiempo se registra solo como referencia de sesión.
- Las opciones de respuesta son distractores generados alrededor de la respuesta; no sustituyen una evaluación individual. Para mayor práctica de recuperación, el modo teclado evita pistas por selección.
- La aplicación es una herramienta educativa general; no diagnostica ni sustituye las adaptaciones indicadas por profesionales.

## Próximas mejoras recomendadas antes de uso escolar amplio
1. Pruebas de usabilidad con niños, familias y docentes.
2. Panel de adulto con perfiles múltiples y ajustes de dificultad, tamaño de letra y número de preguntas.
3. Revisión de accesibilidad con teclado, lector de pantalla y WCAG 2.2 AA.
4. Persistencia cifrada y sincronización opcional, si la escuela necesita informes entre dispositivos.
5. Revisión pedagógica por docentes de matemáticas y especialistas en educación inclusiva.
