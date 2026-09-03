# Asistente de Ventas - Control de Plagas (Skill)

## Qué es esto

Skill para asistente de ventas que cotiza servicios de control de plagas. Desde la consulta inicial hasta el precio final, sin pasos intermedios.

## Archivos

| Archivo | Función | ¿Cuándo se usa? |
|---|---|---|
| SKILL.md | Cerebro principal. Flujo de 7 pasos, formato de salida, reglas de operación | Siempre |
| REGLAS-GLOBALES.md | Reglas que aplican a toda plaga (localidad, m², alertas, restricciones) | Siempre |
| CATALOGO.md | Índice maestro: plaga → categoría → archivo de ficha | Paso 4 (primero) |
| fichas/RASTREROS-ESTANDAR.md | Cucarachas, Hormigas, Arañas, Escorpiones, Tijeretas, Ciempiés | Según plaga detectada |
| fichas/RASTREROS-AEROSOLES.md | Pulgas, Chinches, Polillas ropa, Psocópteros, Prod. Almacenados | Según plaga detectada |
| fichas/VOLADORES.md | Mosquitos, Moscas, Polillas vuelo, Moscardones, Avispas, Abejas | Según plaga detectada |
| fichas/ROEDORES.md | Ratas, Ratones | Según plaga detectada |
| fichas/DESINFECCION.md | Desinfección | Según plaga detectada |
| fichas/ESPECIALES.md | Murciélagos | Según plaga detectada |
| INSUMOS.md | Precios unitarios y fórmulas de cálculo de insumos | Cuando hay insumos |
| PRECIOS-ZONAS.md | Localidades, clasificaciones, precios base y fórmula de aumento | Para calcular precio final |
| ENTRENAMIENTO.md | Explicaciones del "por qué" de cada regla y pregunta | Solo en modo entrenamiento |

## Cómo funciona

```
Vendedor escribe consulta
  → Parsear datos mencionados
  → Validar caso (¿hacemos esto? ¿derivar?)
  → Diagnosticar según ficha de la plaga
  → Calcular insumos
  → Detectar zona y precio base
  → Entregar cotización final con total
```

## Cómo agregar una plaga nueva

1. Consultar CATALOGO.md para identificar en qué categoría entra
2. Abrir el archivo de fichas/ correspondiente (ej: fichas/RASTREROS-ESTANDAR.md)
3. Copiar una ficha existente como plantilla
4. Completar los campos (preguntas, insumos, alertas, equipo, post-servicio)
5. Agregar la plaga en CATALOGO.md
6. Si tiene insumos nuevos, agregar la fórmula en INSUMOS.md
7. Listo. Las reglas globales ya aplican automáticamente.

## Cómo agregar una localidad nueva

1. Abrir PRECIOS-ZONAS.md
2. Determinar la clasificación según distancia en km
3. Agregar el nombre bajo el partido correspondiente en la clasificación correcta
4. Listo. La fórmula de precio ya aplica automáticamente.

## Cómo cambiar precios

- **Precio base de un servicio** → modificar tabla en PRECIOS-ZONAS.md (sección "Tabla de precios base")
- **Porcentaje de aumento por zona** → modificar tabla en PRECIOS-ZONAS.md (sección "Aumento por clasificación")
- **Precio de un insumo** → modificar tabla en INSUMOS.md (sección "Tabla de precios unitarios")

Cada dato vive en un solo lugar. Un cambio, una edición.

## Plagas soportadas

Rastreros Estándar: Cucarachas, Hormigas, Arañas, Escorpiones/Alacranes, Tijeretas, Ciempiés/Milpiés
Rastreros + Aerosoles: Pulgas/Garrapatas, Chinches, Polillas de la Ropa, Psocópteros, Plagas Prod. Almacenados
Voladores: Mosquitos, Moscas, Polillas vuelo, Moscardones, Tábanos, Avispas, Abejas
Roedores: Ratas, Ratones (solo empresas)
Desinfección: Desinfección (no combinable)
Especiales: Murciélagos (solo interiores domicilios/oficinas)

## No hacemos

- Control de aves
- Plagas de la madera (termitas, bicho taladro)
- Roedores en domicilios particulares
- Víboras / serpientes
- Caracoles / babosas
- Servicios los domingos

## Versión

2.0 - Marzo 2026
