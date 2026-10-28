# Estructura de Propiedades

Aquí puedes organizar las propiedades de la cartelería según su operación:

```text
assets/
├── venta/
│   └── propiedad-ejemplo/
│       ├── info.json       (Datos: título, precio, ubicación, m2, etc.)
│       ├── 1.jpg           (Fotos de la propiedad)
│       └── 2.jpg
└── alquiler/
    └── propiedad-ejemplo/
        ├── info.json
        ├── 1.jpg
        └── 2.jpg
```

### Formato recomendado para `info.json`:
```json
{
  "title": "Nombre de la propiedad",
  "location": "Barrio / Ciudad",
  "price": "USD 250.000",
  "m2": "180 m²",
  "ambientes": "4 Amb.",
  "dormitorios": "3 Dorm.",
  "custom": "Cochera doble / Piscina / Vista al río"
}
```
*Las imágenes pueden tener cualquier nombre (`.jpg`, `.jpeg`, `.png`, `.webp`).*
