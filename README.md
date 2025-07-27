# Producción Energética Argentina

Este repositorio contiene un proyecto BI enfocado en producción energética (gas y petróleo) en Argentina, utilizando datasets públicos y herramientas cloud.

---

## 📂 Contenido del repositorio

- `serie-produccion-gas-natural-sesco.csv`  
  Producción histórica de gas natural, por cuenca y total.

- `serie-produccion-petroleo-sesco.csv`  
  Producción histórica de petróleo, por cuenca y total.

- Scripts de transformación en Power Query Online  
  Incluyen limpieza, tipado de columnas, extracción de año/mes, renombrado y validación.

---

## 🧠 Objetivo del proyecto


Preparación de modelo unificado para visualización y análisis por cuenca/mes/año

---

## ⚙️ Desarrollo técnico

### 🔗 Conexión web
- Origen: CSV raw desde GitHub (HTTPS)
- Datos ingeridos en Dataflow Gen1 de Power BI Service

### 🛠️ Transformaciones aplicadas
- Tipado correcto (números, fechas, enteros)
- Columnas duplicadas para extraer `Año` y `Mes`
- Conversión explícita a `DateTime` para habilitar carga incremental
- Reordenamiento y renombrado de columnas por claridad
- Adición de columnas fijas (`Fuente`, `Dataset`, `Fecha actual`) como metadata interna

### 🔄 Carga incremental
- Intento de activación en Dataflow Gen1 → bloqueo por falta de capacidad Premium
- Desactivación manual luego de múltiples intentos y errores visuales
- Decisión: continuar con actualización completa periódica sin segmentar

---

## ✅ Log de decisiones clave

| Tema | Decisión | Motivo |
|------|----------|--------|
| Unificación de tablas | Mantener gas y petróleo por separado | Mayor control y flexibilidad |
| Fecha como clave | Convertida a `DateTime` | Requisito de Service para carga incremental |
| Tablas extra | No se usa `dim_fecha` por ahora | Las fechas ya vienen alineadas |
| Documentación | Centralizada en este README | Proyecto chico, enfoque concreto |

---

## 🧪 Próximos pasos

- Crear visualizaciones comparativas por cuenca y por mes/año
- Documentar insights en producción energética
- Opcional: agregar tabla calendario si se requiere análisis DAX avanzado

---

## 📜 Licencia y uso

Los datasets provienen de fuentes públicas de SESCO / GitHub y se utilizan con fines exploratorios.
---

_Proyecto en curso — última actualización: 26/07/2025_
