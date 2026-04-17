# Calculador de Pagos — Material Hernández

Herramienta digital para calcular el pago a operarios según el esquema de tarifas por bulto de cemento acordado en 2026.

## Características

- **Dos formas de ingreso**: pegar datos desde Google Sheets (tabulado) o ingreso manual con formulario
- **Cálculo automático** según tarifario 2026:
  - Grupo 1 (Bloques Vibrados A-1, A-2, A-3, A-12): $13.500 base / $16.500 premium por bulto equipo de 2 operarios
  - Grupo 2 (Paleao BP-1, Vibrado A-4): $20.000 base / $23.000 premium por bulto (1 operario)
  - Grupo 3 (Calados y Celosías): $24.500 base / $27.000 premium por bulto (1 operario)
  - Productos especiales: Granito, Arena, Día de Trabajo
- **Deducciones opcionales** (hasta 2 por operario con motivo)
- **Recibo PDF** descargable por operario, tamaño media carta horizontal
- **Lógica inteligente**: el umbral premium se evalúa por equipo y por día

## Publicación en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser privado o público)
2. Sube el archivo `index.html` (renombra `calculador_tarifas_MH.html` a `index.html`)
3. Ve a **Settings** → **Pages**
4. En "Source" elige **Deploy from a branch** → **main** / **(root)**
5. En 2 minutos tienes la URL pública

Una vez publicada, puedes compartir el link por WhatsApp al equipo y cualquiera puede usarla desde celular o computador.

## Uso rápido

**Opción 1 — Pegar datos:**
1. Copia las filas desde Google Sheets (selecciona las columnas Fecha, Producto, Unidad, Cantidad, Planta, Operarios, #Op, Materia Prima, unidad, Bultos)
2. Pega en la caja de texto
3. Clic en **Procesar registros**
4. Verifica la vista previa y clic en **Calcular pagos**

**Opción 2 — Ingreso manual:**
1. Clic en pestaña **Ingreso manual**
2. Por cada producción: selecciona fecha, producto, cantidad, bultos y operarios
3. Agrega filas con **+ Agregar fila**
4. Clic en **Calcular pagos**

**Revisar y descargar:**
- Cada operario aparece en un bloque con el detalle de su producción
- Agrega deducciones opcionales (valor + motivo)
- Clic en **Descargar recibo PDF** para cada uno, o **Descargar todos**

## Formato de datos esperado

Columnas separadas por tabulaciones (tal como se copian de Sheets):

```
13/04/2026	PP B. VIBRADO A-2	unidad	96	PLANTA 2	OSCAR VILLAFAÑE, GUSTAVO CACIANO	2	CEMENTO	unidad	2
```

- **Fecha**: DD/MM/YYYY
- **Producto**: nombre exacto (p.ej. "PP B. VIBRADO A-2")
- **Cantidad**: unidades producidas
- **Operarios**: separados por coma (se normalizan al primer nombre)
- **#Op**: número de operarios
- **Bultos**: bultos de cemento usados (soporta 0.5, 1, 1.5, 2, ...)

## Notas técnicas

- 100% HTML/JS/CSS — no requiere servidor ni backend
- Funciona offline después de cargar la primera vez
- Funciona en celular, tablet y computador
- Los recibos se generan usando jsPDF (CDN)
- El logo está embebido en el archivo (base64)
