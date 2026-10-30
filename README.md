# Contador de efectivo COP

Web app instalable (PWA) para contar billetes y monedas colombianas. Escribes cuántas piezas tienes de cada denominación y ves el total al instante.

**App:** https://torser2028.github.io/cash-counter/

## Funcionalidades (MVP)

- Todas las denominaciones vigentes del Banco de la República:
  - Billetes: $100.000, $50.000, $20.000, $10.000, $5.000, $2.000
  - Monedas: $1.000, $500, $200, $100, $50
- Por cada denominación: un campo de cantidad (con botones − / +) y su subtotal.
- Total general siempre visible arriba (barra fija), con el desglose de billetes y monedas debajo.
- Conteo de unidades por sección.
- Botón **Limpiar** (con confirmación) y **Copiar resumen** (texto para WhatsApp o notas).
- El conteo se guarda en el dispositivo (`localStorage`).
- Se puede instalar en Android ("Agregar a pantalla de inicio") y funciona sin conexión.

## Estructura

```
index.html            App completa (HTML + CSS + JS, sin dependencias)
manifest.webmanifest  Manifiesto PWA
sw.js                 Service worker (caché sin conexión)
icons/                Íconos de la app (192, 512, maskable, apple-touch)
```

## Desarrollo local

No necesita build. Sírvela por HTTP; el service worker no funciona abriendo el archivo con `file://`:

```bash
python3 -m http.server 8000
# abre http://localhost:8000
```

## Publicar cambios

GitHub Pages publica la rama `main` desde la raíz. Al cambiar algún archivo de la app, sube `CACHE_VERSION` en `sw.js` para que los usuarios que ya la instalaron reciban la versión nueva.

## Roadmap

- [ ] Billete de $1.000 de la familia anterior, como opción que se pueda activar
- [ ] Historial de conteos con fecha y nota (p. ej. "cierre de caja")
- [ ] Monto esperado vs. contado (sobrante o faltante)
- [ ] Otras monedas o países
- [ ] Empaquetar para Play Store (TWA / Bubblewrap)
