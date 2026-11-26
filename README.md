# Aula virtual

Página para compartir material de clase, mostrar el portafolio docente y llevar las notas de los estudiantes con el SIEE del colegio.

- **Pública:** inicio, material de clase, portafolio docente.
- **Notas y evidencias:** estudiantes y acudientes entran con un código personal de 8 caracteres.
- **Panel docente:** se entra con el usuario de la Agenda docente (Supabase Auth).

Los datos se guardan en Supabase (proyecto «Plataforma de notas», tablas `aula_*`). Las notas no son públicas: solo se consultan con el código de cada estudiante o con la sesión del docente.

## Configuración

Al inicio del script de `index.html`, en el objeto `CONFIG`:

- `SUPABASE_URL` y `SUPABASE_KEY`: conexión al proyecto. La clave es la pública (anon), así que puede ir en el código.
- `SITIO`: identificador del perfil que se muestra en la parte pública. Debe coincidir con el que se guarda en **Panel docente → Perfil**.

## Cálculo de notas (SIEE)

- Nota del periodo: conocimiento (promedio) 30 %, examen 10 %, procedimental (promedio) 30 %, heteroevaluación 10 %, autoevaluación 10 % y coevaluación 10 %.
- Una actividad sin nota cuenta como 0.
- Si un componente todavía no tiene actividades, la nota del periodo se muestra como «parcial».
- Nota del año: periodo 1 30 %, periodo 2 30 %, periodo 3 40 %.
