# AGENTS.md — Cartelera inmobiliaria para Smart TV

## 1. Propósito del proyecto

Desarrollar una cartelera inmobiliaria digital para **Ivana Molina & Asociados Bienes Raíces**, pensada para mostrarse en una Smart TV dentro de una oficina inmobiliaria.

La web debe presentar propiedades automáticamente, con un diseño elegante, profesional y legible desde varios metros de distancia. Las fotografías deben ser las protagonistas y la información debe mantenerse estable mientras cambian las imágenes.

El sitio se publicará como web estática en **Vercel**. El contenido se actualizará manualmente mediante un archivo JSON y fotografías dentro del proyecto.

No se necesita panel de administración, base de datos, autenticación, backend ni API.

Este archivo es la guía principal para cualquier agente de programación que trabaje en el proyecto.

---

## 2. Metodología de trabajo obligatoria

### Antes de modificar archivos

1. Inspeccioná la estructura, los archivos, el código y los recursos existentes.
2. Identificá qué funcionalidades ya existen y qué podría romperse con los cambios.
3. No sobrescribas ni elimines archivos sin entender su propósito.
4. Presentá un plan breve que incluya:
   - Diagnóstico del proyecto.
   - Archivos que proponés crear o modificar.
   - Diseño visual que vas a implementar.
   - Arquitectura y lógica de funcionamiento.
   - Riesgos técnicos y limitaciones.
   - Pruebas que vas a realizar.
5. **Esperá mi aprobación antes de comenzar la implementación**, salvo que te haya autorizado expresamente a implementar en ese turno.

### Durante el desarrollo

- Trabajá por etapas y realizá cambios pequeños y verificables.
- No modifiques funcionalidades ajenas al objetivo sin una razón justificada.
- No inventes propiedades reales, precios, fotografías, datos de clientes ni logotipos.
- Si falta una decisión importante, preguntá antes de asumirla.
- No agregues dependencias ni complejidad innecesaria.
- Conservá la coherencia entre el código existente y los nuevos cambios.

### Al finalizar

- Ejecutá las pruebas que sean posibles.
- Informá qué probaste realmente y cuáles fueron los resultados.
- No afirmes que una prueba fue exitosa si no la ejecutaste.
- Indicá qué archivos se crearon o modificaron.
- Explicá cómo ejecutar y publicar el proyecto.
- Aclar á qué cuestiones requieren una prueba en la Smart TV física.

---

## 3. Diseño visual: clásica moderna

La dirección visual elegida es **clásica moderna**: elegante, minimalista, profesional y sobria.

El resultado debe parecer una cartelera digital de una inmobiliaria profesional, no un dashboard, una plantilla genérica ni una web comercial convencional.

### Principios visuales

- La fotografía del inmueble es el elemento más importante de la pantalla.
- La información debe ser legible desde varios metros de distancia.
- La jerarquía visual debe ser clara y equilibrada.
- Usá márgenes, alineaciones y espacios consistentes.
- La modernidad debe surgir de la composición, la tipografía y las proporciones.
- Evitá los efectos decorativos que distraigan de las propiedades.
- La interfaz debe transmitir confianza y profesionalismo.

### Paleta de colores

Utilizá una paleta neutra:

- Negro o gris carbón para la cabecera.
- Blanco para la información principal.
- Gris muy claro para fondos secundarios.
- Negro o gris oscuro para los títulos.
- Gris medio para la información complementaria.
- Gris claro para separadores discretos.

Podés utilizar estas variables CSS como base:

```css
:root {
  --color-header: #202020;
  --color-background: #ffffff;
  --color-surface: #f5f5f3;
  --color-text: #202020;
  --color-muted: #707070;
  --color-border: #e5e5e5;
}
```

Los valores pueden ajustarse ligeramente para mejorar el contraste, pero se debe mantener la identidad neutra.

No utilices verde neón, dorado decorativo, colores estridentes, auroras ni degradados multicolores.

### Tipografía

- Elegí una tipografía elegante, moderna y legible.
- Preferí fuentes del sistema para mejorar la compatibilidad.
- Si utilizás una fuente externa, la web debe seguir funcionando si no se descarga.
- Diferenciá claramente el nombre de la inmobiliaria, el tipo de operación, el título, la ubicación, las características y el precio.
- El título y el precio deben tener tamaños generosos.
- Evitá textos diminutos, fuentes decorativas, cursivas excesivas y párrafos largos.

---

## 4. Distribución de la pantalla

La referencia principal es una pantalla horizontal de **16:9**, optimizada para 1920 × 1080 y adaptable a 3840 × 2160.

La pantalla debe dividirse en tres zonas.

### A. Cabecera superior oscura

Una franja horizontal compacta y elegante.

Debe contener:

- Nombre de la inmobiliaria: `IVANA MOLINA & ASOCIADOS`.
- Tipo de operación: `EN VENTA` o `EN ALQUILER`.

La marca debe tener buen contraste y estar alineada de forma limpia.

El tipo de operación debe ser visible, pero no competir con la fotografía ni con el título de la propiedad.

Si existe un logotipo real dentro del proyecto, puede utilizarse respetando sus proporciones. Si no existe, utilizá el nombre en texto. No inventes un logotipo.

No agregues menús ni navegación convencional.

### B. Zona central de fotografía

Esta zona debe ocupar la mayor parte de la pantalla y casi todo el ancho disponible.

Reglas obligatorias:

- No superponer títulos sobre la fotografía.
- No colocar el precio sobre la fotografía.
- No agregar botones, etiquetas, íconos ni controles encima de la imagen.
- No utilizar marcos gruesos.
- No oscurecer la imagen con capas negras.
- No aplicar filtros que alteren los colores reales del inmueble.
- No utilizar zoom permanente, parallax ni movimientos artificiales.
- Evitar recortar detalles importantes de la propiedad.

Utilizá `object-fit: contain` o `object-fit: cover` según la composición y las fotografías disponibles. Priorizá mostrar el inmueble correctamente.

Si quedan espacios alrededor de la imagen, utilizá un fondo neutro.

### C. Franja inferior clara de información

Debajo de la fotografía debe existir una franja blanca o gris muy claro.

La distribución recomendada es:

- **Izquierda:** título de la propiedad y ubicación.
- **Centro:** superficie y características principales.
- **Derecha:** precio, destacado visualmente.

Ejemplo ficticio:

`CASA QUINTA CON PARQUE | 20 de Junio · 1.500 m² | USD 250.000`

El título debe ser visible desde lejos. El precio debe destacarse con un tamaño importante y un peso tipográfico firme.

La superficie y las características solo deben mostrarse si tienen información disponible.

No muestres campos vacíos, `null`, `undefined` ni separadores sin contenido.

Si hay demasiadas características, mostr á solamente las más importantes para facilitar la lectura rápida.

La franja inferior debe mantener su posición mientras cambian las fotografías de una misma propiedad. No debe desplazarse ni reconstruirse visualmente en cada transición.

---

## 5. Elementos visuales prohibidos

No agregues:

- Glassmorphism o Liquid Glass.
- Tarjetas flotantes.
- Efectos 3D.
- Parallax.
- Fondos animados.
- Aurora mesh.
- Partículas.
- Brillos decorativos.
- Sombras pesadas.
- Bordes excesivamente redondeados.
- Carruseles con flechas visibles.
- Paginación con puntos.
- Botones de navegación.
- Barras de progreso llamativas.
- Menús o paneles de control.
- Textos superpuestos a las fotografías.
- Animaciones largas o complejas.

El diseño debe ser premium por su composición, sus fotografías, su tipografía y su equilibrio visual, no por acumular efectos.

---

## 6. Funcionamiento de la cartelera

La cartelera debe reproducirse automáticamente, en un ciclo infinito.

El comportamiento esperado es:

1. Cargar y validar la configuración y las propiedades.
2. Seleccionar las propiedades activas y ordenarlas según el campo `orden`.
3. Preparar una fotografía válida.
4. Mostrar la primera propiedad cuando la imagen esté lista.
5. Mantener visible la información de la propiedad.
6. Cambiar automáticamente entre sus fotografías.
7. Al terminar las fotografías, pasar a la siguiente propiedad.
8. Al terminar la última propiedad, volver a la primera.
9. Repetir el ciclo indefinidamente cuando la opción de repetición esté activada.

### Configuración inicial

- Intervalo por fotografía: `7000` milisegundos.
- Duración de transición: `400` milisegundos.
- Reproducción continua: activada.

Estos valores deben poder modificarse desde el JSON y no estar dispersos como números mágicos por el código.

### Reglas de reproducción

- Si una propiedad tiene una sola fotografía, debe permanecer visible durante el intervalo configurado y luego avanzar.
- La información de la propiedad debe permanecer estable mientras cambian sus fotografías.
- Utilizá una transición de opacidad discreta.
- Evitá los flashes blancos o negros entre imágenes.
- Siempre que sea posible, prepará la siguiente fotografía antes de mostrarla.
- Si una imagen falla, omitila o aplicá una recuperación controlada.
- Si una propiedad no tiene imágenes válidas, omitila.
- Si no hay propiedades válidas, mostrá un mensaje de error sencillo y legible.
- Evitá temporizadores duplicados, cambios simultáneos y acumulación de eventos.
- No recargues toda la página en cada transición.
- Durante la reproducción normal no deben necesitarse teclado, mouse ni control remoto.

---

## 7. Tecnologías y arquitectura

Utilizá únicamente:

- HTML5.
- CSS3.
- JavaScript vanilla.

No utilices React, Vue, Angular, Next.js, jQuery, GSAP, frameworks CSS ni librerías de carrusel.

El proyecto debe ser estático y publicable directamente en Vercel.

No necesita:

- Base de datos.
- Backend.
- API.
- Autenticación.
- Panel administrativo.
- Servicios externos para mostrar las propiedades.

Elegí la solución más sencilla que cumpla los requisitos de forma fiable.

### Estructura sugerida

```text
cartelera-inmobiliaria/
├── index.html
├── styles.css
├── app.js
├── data/
│   └── propiedades.json
├── assets/
│   ├── logo/
│   │   └── logo.webp
│   └── propiedades/
│       ├── casa-quinta/
│       │   ├── 01.webp
│       │   ├── 02.webp
│       │   └── 03.webp
│       └── terreno/
│           ├── 01.webp
│           └── 02.webp
└── README.md
```

El logotipo es opcional. Si no existe o no es necesario, no crees recursos ficticios.

Podés adaptar esta estructura si el proyecto existente justifica otra organización, pero mantenela pequeña, clara y fácil de mantener.

---

## 8. Modelo de datos JSON

Toda la información de las propiedades debe almacenarse en `data/propiedades.json`.

Ejemplo orientativo:

```json
{
  "configuracion": {
    "intervaloFotoMs": 7000,
    "transicionMs": 400,
    "repetir": true
  },
  "propiedades": [
    {
      "id": "casa-quinta-20-de-junio",
      "activa": true,
      "orden": 1,
      "operacion": "venta",
      "titulo": "Casa quinta con parque",
      "ubicacion": "20 de Junio",
      "precio": "USD 250.000",
      "superficie": "1.500 m²",
      "caracteristicas": [
        "Parque",
        "Piscina",
        "Quincho"
      ],
      "imagenes": [
        "/assets/propiedades/casa-quinta/01.webp",
        "/assets/propiedades/casa-quinta/02.webp",
        "/assets/propiedades/casa-quinta/03.webp"
      ]
    }
  ]
}
```

Los datos son ficticios y solo sirven para ilustrar la estructura. No deben presentarse como propiedades reales de la clienta.

### Requisitos de los datos

- Mostrar únicamente propiedades con `activa: true`.
- Respetar el orden definido por `orden`.
- Admitir una cantidad variable de propiedades y fotografías.
- Permitir campos opcionales.
- Ocultar los campos que no tengan información.
- Validar el JSON y los campos necesarios.
- Gestionar los errores de una propiedad sin detener las demás.
- No utilizar los datos del JSON como código HTML confiable.
- No mostrar `undefined`, `null` ni información incompleta.

Documentá cómo añadir propiedades, cambiar precios, modificar el orden, activar o desactivar propiedades y agregar, reemplazar o quitar fotografías.

---

## 9. Buenas prácticas de desarrollo

### Legibilidad y mantenibilidad

- Escribí código claro, consistente y fácil de revisar.
- Usá nombres descriptivos en español o inglés de forma consistente.
- Mantené funciones pequeñas y con una responsabilidad clara.
- Evitá funciones gigantes que validen datos, manipulen el DOM, controlen temporizadores y administren toda la reproducción al mismo tiempo.
- Evitá duplicar lógica.
- Centralizá la configuración y las constantes.
- Comentá las decisiones que no sean obvias, no cada línea.
- No construyas abstracciones genéricas sin un uso real.
- No agregues complejidad innecesaria.

### Principios SOLID

Aplicá SOLID de forma proporcional al tamaño del proyecto. No conviertas una pequeña web estática en una arquitectura empresarial innecesaria.

**S — Responsabilidad única**

Cada módulo o función debe tener una responsabilidad clara. Por ejemplo, separar la validación de los datos, el control del ciclo de reproducción y la presentación visual.

**O — Abierto/cerrado**

Permití agregar campos o ajustar comportamientos sin tener que modificar muchas partes independientes del sistema. No construyas sistemas de plugins si no son necesarios.

**L — Sustitución de Liskov**

Si introducís abstracciones o implementaciones intercambiables, todas deben respetar el contrato esperado. No fuerces este principio si el proyecto no necesita jerarquías ni implementaciones intercambiables.

**I — Segregación de interfaces**

Evitá módulos con responsabilidades y contratos demasiado grandes. Cada componente debe depender solamente de las funciones que necesita.

**D — Inversión de dependencias**

Separá las reglas de reproducción de los detalles de presentación cuando resulte útil. Evitá que toda la lógica dependa directamente de elementos específicos del DOM.

### Alta cohesión y bajo acoplamiento

- Agrupá el código por responsabilidades relacionadas.
- Mantené juntas las funciones que cambian por la misma razón.
- Separá la lectura y validación del JSON, la secuencia de propiedades y fotografías, la actualización visual y los estilos.
- Evitá dependencias circulares.
- No dependas de variables globales ocultas si podés pasar los datos explícitamente.
- Centralizá el estado de reproducción.
- Evitá duplicar información en varios estados cuando pueda derivarse de una única fuente de verdad.
- Definí contratos sencillos entre módulos.
- Gestioná los errores de forma explícita.

Si uno o pocos archivos JavaScript bien organizados son suficientes, preferilos antes que crear muchos módulos sin necesidad. La separación debe mejorar la comprensión real del código.

### Estado y asincronía

- Evitá crear múltiples temporizadores para la misma reproducción.
- Guardá y limpiá los identificadores de temporizadores cuando corresponda.
- Evitá que una carga lenta provoque cambios simultáneos.
- Evitá mostrar la fotografía de una propiedad con los datos de otra.
- Controlá los errores de `fetch`, las respuestas HTTP y el parseo del JSON.
- No dejes promesas rechazadas sin manejar.
- Evitá mantener referencias innecesarias a imágenes o nodos del DOM.
- Prevení estados inconsistentes cuando una fotografía falle o tarde en cargar.

### HTML y accesibilidad

- Utilizá HTML semántico.
- Mantené una jerarquía de encabezados razonable.
- Añadí `alt` descriptivo a las fotografías cuando corresponda.
- Conservá contraste suficiente entre texto y fondo.
- No uses el color como única forma de distinguir la operación.
- Incluí metadatos de viewport y un título adecuado para el documento.
- La interfaz debe seguir siendo comprensible si una fuente externa no carga.

### CSS

- Utilizá variables CSS para colores, espacios y valores compartidos.
- Evitá reglas duplicadas y selectores excesivamente complejos.
- No uses `!important` salvo que exista una razón concreta.
- Diseñá primero para 16:9 y adaptá el contenido a otras dimensiones.
- Asegurá una buena visualización tanto en 1080p como en 4K.
- Evitá animar propiedades costosas; preferí `opacity` para los fundidos.
- Respetá las preferencias de movimiento reducido cuando corresponda, sin romper la reproducción automática.

### Seguridad y robustez

- No insertes contenido del JSON como HTML ejecutable.
- Preferí `textContent` y creación segura de elementos DOM frente a `innerHTML` para contenido dinámico.
- No incluyas claves API, contraseñas ni credenciales.
- No uses `eval` ni técnicas similares.
- Validá los datos antes de utilizarlos.
- Mostrá errores de forma controlada.
- No agregues telemetría ni solicitudes a servicios externos sin autorización.

---

## 10. Rendimiento y compatibilidad con Smart TV

La aplicación debe ser liviana y estable, especialmente en televisores con navegadores antiguos o recursos limitados.

- No cargues todas las fotografías simultáneamente.
- Precargá solamente la siguiente imagen necesaria cuando sea razonable.
- Mantené pequeño y estable el número de elementos del DOM.
- No reconstruyas toda la interfaz en cada transición.
- Evitá filtros, blur, parallax y animaciones complejas.
- Utilizá fotografías optimizadas para pantalla grande.
- Preferí WebP cuando el navegador lo soporte.
- Si el televisor no admite WebP, documentá una alternativa JPEG sencilla.
- Como referencia inicial, intentá que las fotografías pesen aproximadamente entre 150 y 350 KB cuando la calidad y las dimensiones lo permitan, sin degradar excesivamente la imagen.
- No dependas de CDN, fuentes, scripts ni APIs externas para mostrar la cartelera.
- Verificá que todas las rutas funcionen en Vercel.
- No asumas que todos los televisores tienen el mismo navegador ni las mismas capacidades.

La interfaz debe adaptarse a 1920 × 1080 y 3840 × 2160.

No prometas compatibilidad universal sin probar el modelo real de la Smart TV.

El modo de pantalla completa solo debe implementarse si el entorno lo permite. No prometas impedir que el televisor entre en suspensión o active su salvapantallas, ya que esto puede depender del sistema operativo y de sus ajustes.

---

## 11. Pruebas mínimas

Cuando las herramientas disponibles lo permitan, comprobá:

1. Carga y validación del JSON.
2. Manejo de JSON inválido o inaccesible.
3. Orden correcto de las propiedades.
4. Exclusión de propiedades inactivas.
5. Propiedades con una fotografía y con varias fotografías.
6. Avance automático entre imágenes.
7. Avance entre propiedades y retorno a la primera.
8. Manejo de imágenes inexistentes o dañadas.
9. Ocultamiento de campos opcionales vacíos.
10. Ausencia de `undefined`, `null` y errores visibles.
11. Ausencia de temporizadores duplicados y cambios simultáneos.
12. Diseño a 1920 × 1080 y 3840 × 2160.
13. Ausencia de desplazamiento y controles visibles durante la reproducción.
14. Funcionamiento de las rutas en un servidor local y en Vercel.

Las pruebas en un navegador de escritorio no reemplazan la prueba en la Smart TV física.

Si el usuario proporciona el modelo y el sistema operativo del televisor, tenelos en cuenta para revisar la compatibilidad. Documentá qué se probó y qué queda pendiente.

---

## 12. Publicación y mantenimiento

El contenido se actualizará manualmente y luego se volverá a publicar en Vercel.

Incluí un archivo `README.md` con instrucciones sencillas para:

1. Ejecutar el proyecto localmente mediante un servidor estático.
2. Entender por qué `fetch()` puede fallar si se abre directamente `index.html` mediante `file://`.
3. Editar el JSON manteniendo una sintaxis válida.
4. Organizar y optimizar las fotografías.
5. Agregar, quitar, ordenar y desactivar propiedades.
6. Cambiar precios, ubicaciones y características.
7. Ajustar el intervalo y la transición.
8. Subir los cambios al repositorio Git y publicarlos en Vercel.
9. Diagnosticar problemas comunes de imágenes y compatibilidad.

No agregues un backend ni un panel de administración para resolver tareas que se pueden hacer editando JSON y archivos de imágenes.

---

## 13. Criterios de aceptación

El proyecto se considera listo cuando:

- Reproduce las propiedades activas automáticamente y en un ciclo infinito.
- Presenta fotografías grandes y sin textos superpuestos.
- Mantiene una cabecera oscura compacta y una franja inferior clara.
- Muestra título, ubicación, superficie, características disponibles y precio con una jerarquía clara.
- Utiliza transiciones discretas.
- Evita pantallas vacías durante los cambios normales.
- Gestiona errores de datos e imágenes sin bloquear toda la reproducción.
- Mantiene un código legible, cohesivo y de bajo acoplamiento.
- Aplica los principios SOLID cuando son útiles, sin sobrearquitectura.
- No incorpora dependencias ni servicios innecesarios.
- Puede desplegarse como sitio estático en Vercel.
- Incluye documentación práctica para mantenerlo.
- Informa honestamente qué pruebas se realizaron y qué debe verificarse en el televisor real.

### Prioridades finales

1. Fidelidad al diseño clásica moderna.
2. Legibilidad desde varios metros.
3. Fotografías protagonistas.
4. Reproducción automática fiable.
5. Rendimiento y compatibilidad con Smart TV.
6. Código simple, mantenible y seguro.
7. Alta cohesión y bajo acoplamiento.
8. Publicación sencilla en Vercel.

**Regla final:** analizá primero el proyecto, presentá el plan y esperá mi aprobación antes de implementar, salvo autorización explícita para avanzar directamente.


