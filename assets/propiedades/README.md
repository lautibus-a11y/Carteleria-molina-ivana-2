# Guía para Imágenes de Propiedades

En este directorio se almacenan las fotografías de los inmuebles que se mostrarán en la Cartelera Smart TV.

## Estructura Recomendada

Puedes organizar las fotos por carpetas según la operación e inmueble:

```text
assets/
└── propiedades/
    ├── venta/
    │   ├── casa-quinta-20-de-junio/
    │   │   ├── 01.jpg
    │   │   ├── 02.jpg
    │   │   └── 03.jpg
    │   └── residencia-los-alamos/
    │       ├── 01.jpg
    │       └── 02.jpg
    └── alquiler/
        └── depto-puerto-madero/
            ├── 01.jpg
            └── 02.jpg
```

## Formato y Optimización
- **Formatos admitidos**: `.jpg`, `.jpeg`, `.png`, `.webp`.
- **Resolución recomendada**: 1920×1080 (Full HD) o formato horizontal 16:9 de buena calidad.

## Conexión con el JSON
En el archivo `data/propiedades.json`, simplemente referencia las fotos en el array `imagenes` de cada propiedad:

```json
"imagenes": [
  "assets/propiedades/venta/casa-quinta-20-de-junio/01.jpg",
  "assets/propiedades/venta/casa-quinta-20-de-junio/02.jpg"
]
```
