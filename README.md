# Calculadora Digital en Protoboard (TTL/CMOS)

Proyecto académico: calculadora de **4 bits** que **suma, resta y multiplica** con lógica TTL/CMOS montada en **protoboard**. Incluye contadores para operandos, complemento a dos para resta, algoritmo shift‑add para multiplicación, comparador para validación y visualización en **displays de 7 segmentos**.

## ✨ Funcionalidad
- **Operaciones**: `A + B`, `A − B` (complemento a 2), `A × B` (shift‑add).
- **Entradas**: botonera para `A↑/A↓`, `B↑/B↓`, selector de operación y botón de cálculo.
- **Comparación**: LEDs `A>B`, `A=B`, `A<B` vía 74HC85.
- **Salida**: 2× displays de 7 segmentos controlados por BCD→7seg (CD4511).  
- **Alimentación**: 9V → 5V (LM7805) con desacoplos.

## 🧱 Diagrama de bloques (borrador)
```
[ Botones A↑ A↓ ]-->[ Contador A (74HC161) ]---\
                                                >--[ Sel. op (+/−/×) ]--\
[ Botones B↑ B↓ ]-->[ Contador B (74HC161) ]---/                         \
                                                 [ Complementador (74HC04) ]--(para resta)
                                                                          |
                                [ Registro despl. (74HC595) ]<-- B (×) ---/
                                                                          \
                                                       [ Sumador 4b (74HC283) ]-->[ Acumulador ]
                                                                                         |
                                                                                [ Comparador 74HC85 ]--> LEDs
                                                                                         |
                                                        [ 2× CD4511 ] --> [ 2× Display 7 seg ]
```

> El esquema final puede migrarse a KiCad/Logisim más adelante.


## 📦 Lista de componentes (BOM) — estimada
_Véase también `src/BOM.csv`._

| Ítem | Cant. | Ref. sugerida | Nota |
|---|---:|---|---|
| Protoboard full-size | 1 | Genérico | 830 puntos o similar |
| Sumador 4 bit | 1 | 74HC283 (DIP) | Sumador binario |
| Comparador 4 bit | 1 | 74HC85 (DIP) | Indicadores A>B, A=B, A<B |
| Contador binario 4 bit | 2 | 74HC161 (DIP) | Para A y B |
| Inversor hex | 1 | 74HC04 | Complemento a 2 / debounce |
| Registro de desplazamiento | 1 | 74HC595 | Shift‑add (×) o manejo de segmentos |
| Driver BCD→7 seg | 2 | CD4511 | Para 7 segmentos |
| Display 7 segmentos | 2 | ánodo común | 0.56” clásico |
| Botones táctiles | 6 | 12×12 mm | A↑, A↓, B↑, B↓, Op, Calc |
| Resistencias 220 Ω | 8–12 | — | Limitación de segmentos/LEDs |
| Transistores NPN | 2 | PN2222/2N3904 | Energizar dígitos/LEDs si aplica |
| Regulador 5V | 1 | LM7805 | + capacitores 100 nF y 10 µF |
| Jumpers | 1 set | — | Puentes para protoboard |

> **Costos**: completa `precio_unitario_usd` en `src/BOM.csv` y el total se recalcula automáticamente.

## ⚙️ Cómo replicar
1. Cablear contadores 74HC161 para A y B con botones ↑/↓ (con debounce RC + Schmitt si es posible).
2. Resta: invertir B (74HC04) y sumar 1 usando `Cin=1` del 74HC283.
3. Multiplicación: algoritmo shift‑add con 74HC595 y acumulador.
4. Visualización: BCD→7seg con CD4511 y resistencias de 220 Ω.
5. Comparación: 74HC85 hacia LEDs de estado.
6. Alimentación: 9V → 5V (LM7805) con desacoplos.

## 🗂️ Estructura de carpetas
```
.
├── docs/               # Reporte, notas, referencias
├── hardware/           # Esquemas/PCB (KiCad/Logisim) cuando estén
├── images/             # Fotos del armado, diagramas
├── src/
│   ├── BOM.csv         # Lista de materiales con costos
│   └── diagram.txt     # Sketch ASCII de referencia
├── .gitignore
├── LICENSE             # MIT (puedes cambiarla)
└── README.md
```

## 📸 Recomendaciones para verse profesional
- Subir **fotos nítidas** del armado en `images/`.
- Añadir un **diagrama** (PNG/SVG) en `docs/` y enlazarlo aquí.
- Completar `docs/REPORTE.md` con resultados/pruebas.
- Crear una **Release** en GitHub (versión v1.0.0) con el ZIP del material del curso.

## 🧪 Pruebas sugeridas
- Tabla de verdad parcial de suma/resta (A=5, B=3 …).
- Casos borde: `A < B` en resta; `A×B` con productos > 15.
- Fotos/Vídeos cortos funcionando.

## 📄 Licencia
Este proyecto se publica bajo **MIT** (ver `LICENSE`).

---

> _Autor: Dania (año 2025). Si usas este material, por favor menciona la fuente._
