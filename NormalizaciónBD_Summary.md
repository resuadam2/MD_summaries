La normalización de bases de datos relacionales es un proceso importante para organizar datos de manera eficiente y minimizar la redundancia. Aquí tienes un resumen de los principios y etapas de la normalización hasta la forma normal de Boyce-Codd (FNBC), junto con ejemplos:

### Normalización de Bases de Datos Relacionales hasta la FNBC

#### Principios Generales

La normalización de bases de datos se basa en las siguientes formas normales (FN):

- **Primera Forma Normal (1FN)**: Todos los atributos de una relación deben ser atómicos (indivisibles).
- **Segunda Forma Normal (2FN)**: Debe estar en 1FN y no debe tener dependencias parciales.
- **Tercera Forma Normal (3FN)**: Debe estar en 2FN y no debe tener dependencias transitivas.
- **Forma Normal de Boyce-Codd (FNBC)**: Debe estar en 3FN y cualquier dependencia funcional debe ser una dependencia funcional de clave candidata.

#### Ejemplo de Normalización

Supongamos una base de datos con la siguiente relación inicial no normalizada:

**EmpleadoProyecto (ID_empleado, Nombre_empleado, ID_proyecto, Nombre_proyecto, Horas_asignadas)**

1. **Primera Forma Normal (1FN)**

   Aseguramos que todos los atributos sean atómicos. Dividimos la relación en dos:

   **Empleado (ID_empleado, Nombre_empleado)**

   **Proyecto (ID_proyecto, Nombre_proyecto, Horas_asignadas)**

2. **Segunda Forma Normal (2FN)**

   Eliminamos dependencias parciales asegurando que cada atributo no clave dependa completamente de la clave:

   **Empleado (ID_empleado, Nombre_empleado)**

   **Proyecto (ID_proyecto, Nombre_proyecto)**

   **Asignación (ID_empleado, ID_proyecto, Horas_asignadas)**

3. **Tercera Forma Normal (3FN)**

   Eliminamos dependencias transitivas asegurando que ningún atributo no clave dependa de otro atributo no clave:

   **Empleado (ID_empleado, Nombre_empleado)**

   **Proyecto (ID_proyecto, Nombre_proyecto)**

   **Asignación (ID_empleado, ID_proyecto, Horas_asignadas)**

4. **Forma Normal de Boyce-Codd (FNBC)**

   Garantizamos que todas las dependencias funcionales sean dependencias de clave candidata:

   En este ejemplo, si consideramos que ID_empleado e ID_proyecto forman la clave candidata en la tabla Asignación, entonces ya estamos en FNBC, ya que Horas_asignadas depende directamente de la combinación de ID_empleado e ID_proyecto.

### Consideraciones Adicionales

- **Anomalías de Actualización**: La normalización reduce las anomalías de actualización al minimizar la redundancia de datos.
  
- **Rendimiento**: Aunque la normalización mejora la estructura de datos, puede afectar el rendimiento en operaciones de consulta complejas que requieren unir múltiples tablas.

La normalización de bases de datos es un proceso iterativo y depende de la comprensión profunda del dominio de la aplicación y de las relaciones entre los datos. Los ejemplos proporcionados ilustran cómo se pueden aplicar los principios de normalización hasta alcanzar la Forma Normal de Boyce-Codd (FNBC) en una base de datos relacional.