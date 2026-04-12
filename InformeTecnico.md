# Informe Técnico de Incidencia

## 1. Descripción del problema
El sistema permite el envío de formularios de contacto sin realizar ninguna validación previa de los campos de texto.

## 2. Cómo se reproduce
1. Iniciar la aplicación BuggyWebApp.
2. Enviar el formulario dejando los campos de "Nombre" e "Email" totalmente vacíos.
3. El sistema responde con "Formulario procesado" a pesar de no tener datos.

## 3. Análisis técnico
Al depurar con el Debugger, se observa que en el método `submitContactForm`, las variables `name` y `email` llegan como cadenas vacías (`""`). 

## 4. Causa raíz
Falta de una estructura de control (condicional `if`) que verifique si los parámetros de entrada son válidos antes de instanciar el objeto `ContactForm` y llamar al servicio de procesamiento.

## 5. Propuesta de solución
Implementar una validación básica que compruebe si los Strings están vacíos o son nulos, deteniendo la ejecución y mostrando un mensaje de error en caso de que los datos no sean correctos.
