---
name: ahorro-de-tokens
description: "Reglas de trabajo para que Claude gaste menos tokens (y menos límite de uso): respuestas cortas, cero adulación, sin narrar el plan, ediciones parciales en vez de reescribir archivos, validar antes de decir listo y lecturas en paralelo. Aplicar siempre, en todas las tareas."
---

# Ahorro de tokens

## 1. No programar sin contexto
- ANTES de escribir código: lee los archivos relevantes, revisa git log, entiende la arquitectura.
- Si no tienes contexto suficiente, pregunta. No asumas.

## 2. Respuestas cortas
- No repitas lo que el usuario dijo.

## 3. No reescribir archivos completos
- Usa Edit (reemplazo parcial), NUNCA Write para archivos existentes salvo que el cambio sea >80% del archivo.
- Cambia solo lo necesario. No "limpies" código alrededor del cambio.

## 4. Validar antes de declarar hecho
- Después de un cambio: compila, corre tests, o verifica que funcióna.
- Nunca digas "listo" sin evidencia de que funcióna.

## 5. Cero charla aduladora
- No digas "Excelente pregunta", "Gran idea", "Perfecto", etc.
- No halagues al usuario. Ve directo al trabajo.

## 6. No narrar el plan antes de ejecutar
- No digas "Voy a leer el archivo, luego modificar la función, luego compilar...". Solo hazlo.
- El usuario ve tus tool calls. No necesita un preview en texto.

## 7. Paralelizar tool calls
- Si necesitas leer 3 archivos independientes, lee los 3 en un solo mensaje, no uno por uno.
- Menos roundtrips = menos tokens de contexto acumulado.

## 8. No duplicar código en la respuesta
- Si ya editaste un archivo, no copies el resultado en tu respuesta. El usuario lo ve en el diff.
- Si creaste un archivo, no lo muestres entero en texto tambien.

## 9. No usar Agent cuando Grep/Read basta
- Agent duplica todo el contexto en un subproceso. Úsalo solo para búsquedas amplias o tareas complejas.
- Para buscar una función o archivo especifico, usa Grep o Glob directo.