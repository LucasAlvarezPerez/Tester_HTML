# 📋 Cuestionario Interactivo y Plataforma de Autoevaluación
Entorno interactivo universal para autoevaluarse, simulando exámenes y consolidando conocimientos. Diseñado para funcionar de forma desacoplada con cualquier tipo de input, para cualquier contexto. Adapta sus temas, interfaz y banco de contenidos mediante este mismo input.

---
## Objetivo de este repositorio
Aportar utilidad a usuarios que requieran una herramienta del estilo, permitiendo clonarla como plantilla para su actualización / ampliación. 
Herramienta de utilidad para usuarios medios/bajos en el sector de la informática. 

Conocimientos mínimos: XML básico (se requiere para conseguir rellenar el XML con las preguntas que deseamos).

---

## 🎮 Contenido del Repositorio
[cuestionario.html] : Contenido que abrirá la interfaz interactiva tipo test
[preguntas.xml]: Archivo que sirve como caso de prueba formato necesario para cualquier XML que queramos usar en esta aplicación

---

## 💡 Características y Funcionamiento

* **Banco dinámico basado en XML**: Al iniciar, deberemos cargar un archivo mediante la opción **📂 Cargar XML** disponible arriba a la derecha. 
* **Modo Estudio vs. Modo Examen**:
  * **Modo Estudio** *(default)*: Al seleccionar una respuesta se comprueba de inmediato, marcando en verde la correcta, en rojo el fallo y desplegando la justificación técnica de la solución.
  * **Modo Examen** *(desactivando la casilla)*: Permite realizar un simulacro fluido sin interrupciones, calculando la nota final sobre 10 y mostrando el desglose pormenorizado al terminar.
* **🎯 Repaso de Preguntas Falladas**: Cada fallo se registra automáticamente en el almacenamiento local del navegador (`localStorage`), individualizado por banco o materia. Pulsando en *🎯 Repasar Preguntas Falladas*, podrás realizar rondas focalizadas exclusivamente en los conceptos que más te han costado; cada pregunta acertada en este modo se retira de la lista de pendientes.
* **Personalización del cuestionario**: Configura tandas cortas (5 o 10 preguntas) o exámenes profundos (15, 20, 30 o todas), activando o desactivando la aleatorización de orden y opciones.
* **Modo Claro / Oscuro**: El botón **🌓 Tema** ajusta el contraste a las preferencias de visualización.

---

## 🛠️ Cómo Añadir Preguntas o Crear Nuevos Cuestionarios

Deberemos modificar o crear un archivo que siga la misma estructura que el archivo de ejemplo [`preguntas.xml`](preguntas.xml). 
La estructura a seguir (recomendado enseñarla a la IA para que sepa cómo hacerlo) es la que se describe en el siguiente apartado. 
No necesariamente debemos editar el archivo preguntas XML, también podemos crear uno nuevo que siga esta misma estructura.

### Estructura General del Archivo XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<banco_preguntas>
  <metadatos>
    <asignatura>Nombre de la Asignatura</asignatura>
    <descripcion>Descripción concisa del alcance del temario o contenidos</descripcion>
    <version>1.0</version>
    <total_preguntas>Número total estimado</total_preguntas>
  </metadatos>

  <!-- Definición de temas o unidades didácticas -->
  <temas>
    <tema id="tema1" nombre="Nombre descriptivo del Tema 1" />
    <tema id="tema2" nombre="Nombre descriptivo del Tema 2" />
  </temas>

  <!-- Banco de preguntas -->
  <preguntas>
    <!-- Pregunta individual -->
    <pregunta id="tema1-01" tema="tema1">
      <enunciado>¿Escribe aquí el enunciado de la pregunta?</enunciado>
      <opciones>
        <opcion id="a">Opción incorrecta 1</opcion>
        <opcion id="b" correcta="true">Opción correcta</opcion>
        <opcion id="c">Opción incorrecta 2</opcion>
        <opcion id="d">Opción incorrecta 3</opcion>
      </opciones>
      <explicacion>Explicación técnica que justifica la respuesta correcta.</explicacion>
    </pregunta>
  </preguntas>
</banco_preguntas>
```

### Reglas y Recomendaciones:
1. **Atributo `tema`**: Debe concordar con el atributo `id` declarado en el bloque `<temas>`. Si se omite en `<temas>`, el cuestionario lo detectará y capitalizará automáticamente.
2. **Atributo `correcta="true"`**: Debe asignarse a la opción válida de cada pregunta.
3. **Identificador `id` de pregunta**: Se recomienda usar prefijos ordenados (ej. `patrones-01`, `bdd-05`) para que el registro de preguntas falladas identifique de manera inequívoca cada ítem.
4. **Carga en la aplicación**: Guarda el archivo como `.xml` y utiliza el botón **📂 Cargar XML** en la cabecera del cuestionario.
