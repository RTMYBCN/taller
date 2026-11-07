# RTMY · Taller de Paella — versión con imagen de marca

Reconstrucción de [`RTMYBCN/taller`](https://github.com/RTMYBCN/taller) con la identidad
oficial de RTMY y una capa de movimiento nueva. Un solo `index.html` autocontenido
(ilustraciones, sello y QR van embebidos en base64); solo necesita internet para las
tipografías de Google Fonts.

## Qué cambia respecto al original

**Marca**
- Fondo burdeos `#741C1C` (único color corporativo) + crema `#FBF7EE`. Fuera el negro
  `#0D0D0D` y el rojo `#C0272D`, que no son colores de marca.
- Tipos oficiales: **Anton** (display) + **Poppins** (UI), con *Noto Sans SC* para chino.
- Sello real del logo en cabecera, pantalla de inicio y pantalla final.
- Sin emojis en la interfaz: iconos SVG propios y banderas en SVG (los emoji de bandera
  no se dibujan en muchos navegadores de TV, Windows y Linux).
- El cronómetro es un disco crema circular: la paella vista desde arriba.
- Las ilustraciones dibujadas a mano se mantienen intactas.

**Movimiento**
- Entrada de texto enmascarada palabra a palabra, escalonada por idioma.
- Barrido crema en el cambio de paso, en lugar del destello rojo.
- Dígitos con rodillo: solo se anima la cifra que cambia.
- Anillo de progreso a 60 fps (antes el contador saltaba de segundo en segundo).
- Ilustración con entrada tipo pegatina y flotación continua.
- Últimos 10 s: latido del disco + halo expansivo, sin parpadeo de opacidad.
- Raíl de progreso superior con un segmento por paso, de ancho proporcional a su duración.
- `prefers-reduced-motion` respetado.

**Funcionamiento**
- Se adapta a cualquier resolución (antes estaba clavado a 1920×1080).
- Reloj con `requestAnimationFrame` y tiempo real: no acumula deriva en los 42 min.
- `↑` / `↓` suman o restan 30 s al paso en curso.
- Pantalla completa automática al empezar y `Wake Lock` para que la TV no se duerma.
- Micro-deriva de 7 px cada 15 min como protección contra el *burn-in*.

## Controles

| Tecla | Acción |
|---|---|
| `Espacio` / `K` / clic | Pausa |
| `→` `PageDown` `N` | Paso siguiente |
| `←` `PageUp` `P` | Paso anterior |
| `↑` / `↓` | +30 s / −30 s en el paso actual |
| `F` | Pantalla completa |
| `R` | Volver al inicio |

Las teclas `PageUp` / `PageDown` son las de los mandos pasadiapositivas.

### Mando de la televisión

La pantalla de idiomas se maneja entera con el mando: `←` `→` mueven el foco entre
las banderas, `↓` baja al botón de empezar y `OK` marca o arranca. El foco se ve con
un borde crema y arranca puesto en la primera bandera.

A 1920×1080 el escenario no lleva ninguna transformación CSS, a propósito: los
navegadores de televisión calculan la navegación por foco con el rectángulo sin
transformar, y un `translate` deja los botones fuera de su alcance.

## Contenido

Los 20 pasos, los 7 idiomas, las duraciones y las ilustraciones son exactamente los del
repo original; no se ha tocado ni una línea de copy.
