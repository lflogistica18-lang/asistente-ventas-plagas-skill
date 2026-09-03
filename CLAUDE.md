# Asistente de Ventas - Control de Plagas (Skill)

Skill de Claude Code para cotizar servicios de control de plagas. Los vendedores consultan y el asistente diagnostica, calcula insumos, detecta zona y entrega cotizacion final con mensaje copy-paste para el cliente.

## Stack

- Skill de Claude Code (sin codigo, todo en Markdown)
- Interfaz web en `index.html` (HTML standalone, sin dependencias)
- Precios en pesos argentinos (ARS)

## Archivos y cuando se consultan

| Archivo | Proposito | Paso del flujo |
|---|---|---|
| SKILL.md | Cerebro: flujo de 7 pasos, formato de salida, reglas | Siempre |
| REGLAS-GLOBALES.md | Reglas transversales: localidad, m2, combos, recargos, alertas | Paso 2 (siempre) |
| CATALOGO.md | Indice maestro: plaga → categoria → archivo de ficha | Paso 4 (primero) |
| fichas/RASTREROS-ESTANDAR.md | Cucarachas, Hormigas, Arañas, Escorpiones, Tijeretas, Ciempies | Paso 4 (segun plaga) |
| fichas/RASTREROS-AEROSOLES.md | Pulgas, Chinches, Polillas ropa, Psocopteros, Prod. Almacenados | Paso 4 (segun plaga) |
| fichas/VOLADORES.md | Mosquitos, Moscas, Polillas vuelo, Moscardones, Avispas, Abejas | Paso 4 (segun plaga) |
| fichas/ROEDORES.md | Ratas, Ratones | Paso 4 (segun plaga) |
| fichas/DESINFECCION.md | Desinfeccion | Paso 4 (segun plaga) |
| fichas/ESPECIALES.md | Murcielagos | Paso 4 (segun plaga) |
| INSUMOS.md | Precios unitarios y formulas de calculo | Paso 5 |
| PRECIOS-ZONAS.md | Localidades, clasificaciones, precios base | Paso 6 |
| RESPUESTA-CLIENTE.md | Template copy-paste para WhatsApp + consultas frecuentes | Paso 7 |
| ENTRENAMIENTO.md | Explicaciones del "por que" de cada regla | Solo modo entrenamiento |
| CASOS-PENDIENTES.md | Log de situaciones no cubiertas | Automatico |

## Flujo resumido

```
Mensaje vendedor → Parsear datos → Validar caso → Diagnostico plaga
→ Calcular insumos → Detectar zona/precio → Doble salida:
  1. Mensaje copy-paste para el cliente (WhatsApp)
  2. Cotizacion interna del vendedor
```

## Reglas clave

- Doble salida siempre: mensaje cliente (sin tecnicismos) + cotizacion interna (con alertas tecnicas)
- Domicilios interior siempre cotizan como "hasta 1000m2"
- Combo 2 plagas: servicio mayor completo + 40% del menor
- Combo 3+: mostrar individuales y pares, vendedor decide
- >5000m2 o chinches en hoteles → derivar a Lucas
- Recargos horarios: antes 17hs 0%, 17-20 +20%, 20-22 +35%, 22-01 +50%
- Factura A o transferencia → total + IVA 21%
- No hacemos: aves, madera, roedores domiciliarios, domingos

## Convenciones de edicion

- Cada dato vive en un solo archivo (fuente unica de verdad)
- Plaga nueva → agregar ficha en el archivo de fichas/ correspondiente + actualizar CATALOGO.md + formula en INSUMOS.md
- Localidad nueva → agregar en PRECIOS-ZONAS.md
- Precios → modificar en el archivo correspondiente (PRECIOS-ZONAS o INSUMOS)
- Casos no cubiertos se registran automaticamente en CASOS-PENDIENTES.md
