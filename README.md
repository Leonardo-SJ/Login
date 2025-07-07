# Login
## Descripcion
Este login te permite introducir una contraseña y un usuario sin son correctos te muestra este repositorio

## Componentes
Se compone de un index.html, el style.css ubicado en la carpeta css y de un js llamado LOGIN.js que esta en la carpeta js

### Metodos
-- TRADUCTOR
Funciones
traducirTexto(texto, idiomaDestino):
Propósito: Esta función async es responsable de hacer una llamada a la API de https://api.mymemory.translated.net/get para traducir una sola pieza de texto del idiomaOrigen (Español, "es") al idiomaDestino.
Retorna: El texto traducido si tiene éxito, o el texto original si el idioma de destino es el mismo que el de origen, o si ocurre un error durante la llamada a la API.
traducirPagina(idiomaDestino):
Propósito: Esta función async itera a través de todos los nodos de texto visibles en la página, recupera su contenido original (del array textosOriginales) y utiliza traducirTexto para actualizarlos al idiomaDestino seleccionado.

Método Llamado: Llama a la función traducirTexto para cada nodo de texto que necesita ser traducido.
Métodos y Event Listeners
document.addEventListener("DOMContentLoaded", ...):

Propósito: Este es un listener de eventos que espera a que todo el documento HTML se cargue y se analice por completo.
Acción: Una vez que el DOM está listo, ejecuta la función de flecha anónima (sin nombre) proporcionada. Dentro de esta función:
Itera a través de todos los elementos relevantes en el body para guardar su contenido de texto original en el array textosOriginales. Esto actúa como una "instantánea" del estado inicial de la página.
Configura otro listener de eventos para la selección de idioma.
idiomaSelect.addEventListener("change", ...):

Propósito: Este es un listener de eventos adjunto al elemento select con el ID "idioma". Escucha el evento change, que se activa cuando el usuario selecciona una opción diferente del menú desplegable.
Acción: Cuando se selecciona un nuevo idioma, obtiene el value de la opción seleccionada y llama a la función traducirPagina con el idiomaDestino elegido.
-- VALIDACION
Función (Expresión de Función Invocada Inmediatamente - IIFE)
(function () { ... })();:

Propósito: Esta es una Expresión de Función Invocada Inmediatamente (IIFE). Es una función anónima que se ejecuta a sí misma inmediatamente después de ser definida. Esto se usa a menudo para crear un ámbito privado para variables (como form en este caso) y evitar contaminar el espacio de nombres global.
Retorna: Nada explícitamente, pero su efecto secundario es configurar el listener de eventos del formulario.

Métodos y Event Listeners
form.addEventListener('submit', function (event) { ... }, false);:

Propósito: Este es el listener de eventos principal para el formulario con el ID "loginForm". Escucha el evento submit, que ocurre cuando se envía el formulario (por ejemplo, al hacer clic en el botón "Entrar").
Acciones:
event.preventDefault(): Método que detiene el comportamiento predeterminado del navegador para un envío de formulario (que sería recargar la página o navegar a la URL action).
event.stopPropagation(): Método que evita que el evento se propague a los elementos padre en el DOM.
form.classList.add('was-validated'): Método que añade la clase was-validated al formulario. Esta clase de Bootstrap activa la visualización de la retroalimentación de validación (como bordes rojos y mensajes de error) basándose en las reglas de validación de HTML5.
form.checkValidity(): Método que comprueba si todos los elementos de entrada del formulario cumplen sus restricciones de validación (por ejemplo, required, pattern, type="email"). Devuelve true si es válido, false en caso contrario.
window.location.href = 'https://github.com/Leonardo-SJ/Login';: Método (establecer una propiedad) que redirige el navegador a la URL especificada cuando el formulario es válido.
