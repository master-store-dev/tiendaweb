# Master Store — Suplementos Star Nutrition

Tienda de una sola página. HTML, CSS y JavaScript sin frameworks ni dependencias.

## Estructura

```
index.html          la tienda completa
img/                fotos de productos y logos
README.md           este archivo
```

## Publicar en GitHub Pages

1. Creá un repositorio nuevo en GitHub (puede ser público o privado con cuenta Pro).
2. Subí **el contenido** de esta carpeta a la raíz del repo: `index.html`, la carpeta `img/` y este README. No subas la carpeta `master-store` entera, sino lo que está adentro.
3. En el repo andá a **Settings → Pages**.
4. En *Source* elegí **Deploy from a branch**, rama `main`, carpeta `/ (root)`. Guardá.
5. Esperá un minuto. La tienda queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

Para usar un dominio propio, cargalo en **Settings → Pages → Custom domain** y apuntá el DNS del dominio a GitHub.

## Editar productos

Todo el catálogo está en `index.html`, dentro del `<script>`, en el array `PRODUCTS`.

```js
{id:"proteina", name:"Whey Protein", cat:"Proteínas", tag:"Más vendido", best:true,
 desc:"Proteína de suero microfiltrada. 25 g de proteína por servicio.",
 variants:[{label:"Sachet", size:"908 g · 2 Lb · 30 serv.", price:65000, img:"proteina"},
           {label:"Pote",   size:"908 g · 2 Lb · 30 serv.", price:69000, img:"proteina_pote"}],
 flavors:["Vainilla Ice Cream","Chocolate","Frutilla","Cookies & Cream"]},
```

- `cat` genera los filtros de categoría automáticamente.
- `variants` son los formatos. Si hay más de uno aparece el selector Sachet / Pote.
- `img` apunta a una clave del objeto `IMAGES`, que a su vez apunta a un archivo de `img/`.
- `tag` es la etiqueta sobre la foto. Con `best:true` se pinta oscura.

### Agregar un producto

1. Poné la foto en `img/` (cuadrada, 520x520 px, JPG).
2. Sumá la clave en `IMAGES`, por ejemplo `"bcaa":"img/bcaa.jpg"`.
3. Agregá el objeto del producto al array `PRODUCTS`.

## Configuración

Arriba del `<script>`, en `CONFIG`:

```js
const CONFIG = {
  storeName: "Master Store",
  whatsapp: "542317526578",   // número con código de país, sin + ni espacios
  currency: "$",
};
```

Si el link de WhatsApp no abre el chat, probá agregando un `9` después del `54`:
`5492317526578`. Los celulares argentinos suelen necesitarlo.

## Notas

- El carrito se guarda en el navegador del cliente (`localStorage`, clave `ms_cart_v2`).
- No hay pasarela de pago: el checkout arma el pedido y lo manda por WhatsApp.
- Las fotos usan carga diferida, así que solo se descargan las que se ven en pantalla.
