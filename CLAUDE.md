# MATCH!CORE — contexto para Claude

## Proyecto
- Aplicación web para seguir partidos en tiempo real: eventos por jugador, uso desde tablet o móvil, estadísticas y sensores.
- Deportes: fútbol, fútbol sala, baloncesto, balonmano y voleibol. Flujo común y un **reglamento por deporte** (tiempo, eventos, cambios y avisos).
- Equipo: David Araiz Saez, Daniel Bernal Anzano (dueño del repo) y Aaron Hernandez Ocejo. Ciclo DAW2D, CPIFP Los Enlaces, curso 2026-27. Tutor: Roberto Marín López.
- Entregas cada 15–20 días en Aeducar, en Word con la plantilla oficial; calificación apto o no apto. Entrega final en julio de 2027.

## Cómo trabajar
- Responder en español, paso a paso. Ejecutar los comandos uno mismo siempre que se pueda.
- Aplicar los cambios directamente, sin pedir confirmación, salvo que se pida no modificar nada.
- **Hacer siempre lo más barato:** subagentes Haiku para consultas, Sonnet para redactar y editar; nada de subagentes para tareas pequeñas.
- Hacer push directo a `main`.

## Documentación: solo en Google Drive
- Carpeta «proyecto fin de grado» (id `1e8qFkJ_0cvfr3F51A9JXBqp8yw3yRne_`). Subcarpetas: Trabajos (aquí está el Word de la Tarea 2), Plantillas, Backup.
- Archivos: guía del módulo, enunciado de la Tarea 2, propuesta en PDF, diagrama de flujo en SVG (versión antigua), `sensor.md` (de Aaron) y `MATCHCORE_integracion_sensores.md`.
- En el repo no se suben documentos (`docs/` y los Word están en `.gitignore`).
- Con el conector de Drive se pueden subir archivos de texto (md, svg) y verificarlos por tamaño. Los binarios (docx, png) los sube el usuario, y no se pueden editar los Word que ya están en Drive.

## Normas de la memoria (guía del módulo)
- Tercera persona y verbos en presente. Pasar el corrector. Usar saltos de página.
- Calibri 12, texto justificado, sangría de primera línea, interlineado sencillo. Márgenes: 2,75 cm arriba, 1,5 abajo, 1,5 a la izquierda y 1,25 a la derecha.
- Encabezado con el nombre del proyecto y los autores; pie con el número de página; índice paginado; títulos numerados.

## Estado
- Tarea 2: apartados 1.1 a 1.4 escritos, con número de página en el pie e índice.
- David la editó en Google Docs. Valoración pendiente de corregir:
  - Contradicción: el 1.1.1 habla de varios deportes y el resto del documento solo de fútbol y fútbol sala. Falta el baloncesto.
  - Errores: «esfuerzo mental» (debe ser físico), «se trate» y una coma entre sujeto y complemento.
  - La motivación ha quedado débil.
  - Revisar el formato en Word y actualizar el índice.
- Diagrama de flujo en `diagramas/`: Mermaid, SVG y PNG, más el artifact https://claude.ai/artifact/46VkBC4rQ6edA9wkCb7RUy
- Sensor físico: Polar H10 o H9 (sin confirmar). Se lee con Web Bluetooth (servicio Heart Rate 0x180D). Los demás sensores se simulan con el mismo formato de lectura.

## Pendiente
- Corregir la Tarea 2 según la valoración y decidir el alcance de deportes en todos los apartados.
- Subir a Drive el diagrama nuevo (el que hay es el antiguo).
- Confirmar el modelo del Polar. Elegir tablet Android o portátil (iPad no admite Web Bluetooth).
- Añadir a David y Aaron como colaboradores en GitHub. Decidir qué hacer con `tienda/`, que no es de MATCH!CORE.
