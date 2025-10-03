# Calculadora Digital en Protoboard (TTL/CMOS)

Proyecto académico: calculadora de **8 bits** que **suma, resta y multiplica** montada en **protoboard**. Incluye contadores para operandos, complemento a dos para resta, algoritmo shift‑add para multiplicación, comparador para validación y visualización en **displays de 7 segmentos**.

##  Funcionalidad
- **Operaciones**: `A + B`, `A − B` (complemento a 2), `A × B` (shift‑add).
- **Entradas**: botonera para selector de operación y botón de cálculo.
- **Comparación**:`A>B`, `A=B`, `A<B`.
- **Salida**: Displays de 7 segmentos controlados por BCD→7seg.

##  Diagrama de bloques (borrador)
```

```

##  Lista de componentes estimados:


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



##  Estructura de carpetas
```
.
├── docs/               # Reporte, notas, referencias
├── src/
│   ├── BOM.csv         # Lista de materiales con costos
│   └── diagram.txt     # Sketch ASCII de referencia
├── .gitignore
├── LICENSE             # MIT 
└── README.md
```

- Fotos/Vídeos cortos funcionando.

##  Licencia
Este proyecto se publica bajo **MIT** (ver `LICENSE`).

---

> _Autor: Saul (año 2025). Si usas este material, por favor menciona la fuente._
