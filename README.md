# Plantilla para casos de prueba
Se recomienda incluir en el nombre del archivo el flujo que se desea probar.
~~~
Ejemplo:

Casos de prueba del Login
~~~

## Contenido
* [Condiciones para ejecución de pruebas](#execution-conditions)
* [Título(s) de caso de prueba](#test-one)
* [Ejemplo: Login successful as admin](#test-two)

## <a id="suite-conditions">Condiciones para ejecución de pruebas</a>

| Condición de ejecución  | Valor de ejecución                                                        |
|-------------------------|---------------------------------------------------------------------------|
| Navegadores             | Navegadores en los que se ejecutará la prueba. Ej. Chrome, Edge, etc.     |
| Frecuencia de ejecución | Periodicidad en que se ejecutará la prueba. Ej. Todos los días, cada hora.|
| Grabación de video      | Definición de grabación de video para los casos de prueba. Ej. Sí/No      |
| Número de reintentos    | Número de reintentos en caso de que la prueba falle.                      |
| Etiqueta(s) de prueba   | Clasificar las pruebas de acuerdo al flujo. Ej. Login, Vacantes, etc.     |
| Interfaz gráfica        | Se requiere interfaz gráfica para la ejecución de esta prueba. Ej. Sí/No  |


## <a id="test-one">Título de caso de prueba</a>
El título de la prueba corresponde a un id descriptivo que permita responder dos preguntas: ¿Qué flujo se está probando? y ¿Cuál es el resultado esperado del caso de prueba? Este título puede ser una base para detenerminar los nombres del describe y el it de la prueba.
~~~
Ejemplo:

Login successful as admin
~~~

#### Descripción
***
Detalla qué se está probando, qué se está verificando y sobre qué unidad.

~~~
Ejemplo:

Caso de prueba para verificar el correcto inicio de sesión de un usuario administrador, usando el email de su cuenta.
~~~

#### Condiciones del caso de prueba
---
Son las condiciones que se deben cumplir antes de la ejecución del caso de prueba.

~~~
Ejemplo:

- Contar con las credenciales de un usuario administrador (email y contraseña)
- Ingresar al home de empresas
- Dar clic en el botón con el texto "INICIA SESIÓN"
~~~

#### Datos de prueba
---
Se relaciona con las variables y valores necesarios para el caso de prueba.

~~~
Ejemplo:

| Nombre de variable  | Valor               |
|---------------------|---------------------|
| email               | pruebas@getnada.com |
| password            | pruebasQA1          |
~~~

#### Pasos a ejecutar
---
Serie de pasos para llevar a cabo el caso de prueba, con un enfoque en el usuario final.

~~~
Ejemplo:

1. Ingresar en el campo `Usuario/Coreo electrónico` el valor de la variable `email`
2. Ingresar en el campo `Contraseña` el valor de la variable `password`
3. Dar clic en el botón `INICIAR SESIÓN`
4. Interceptar la petición al servicio `/api` esperando un resultado 200
5. Hacer un request al servicio de autenticación
~~~

#### Resultados esperados
---
Esto indica el resultado esperado después de la ejecución de los pasos del caso de prueba.

~~~
Ejemplo:

Se espera que el inicio de sesión sea exitoso.
~~~

#### Condiciones posteriores
---
Lo que se espera que suceda después de obtener el resultado de los pasos.

~~~
Ejemplo:

- El usuario debe ser dirigido a la página del dashboard de empresas.
- La cookie sessionR debe contener un valor.
~~~

## <a id="test-two">🔐 Login successful as admin</a>

### ***Descripción:***
Caso de prueba para verificar el correcto inicio de sesión de un usuario administrador, usando el email de su cuenta.

### ***Condiciones del caso de prueba:***
- Contar con las credenciales de un usuario administrador (email y contraseña)
- Ingresar al home de empresas
- Dar clic en el botón con el texto "INICIA SESIÓN"

### ***Datos de prueba:***
| Nombre de variable  | Valor               |
|---------------------|---------------------|
| email               | pruebas@getnada.com |
| password            | pruebasQA1          |

### ***Pasos a ejecutar:***
1. Ingresar en el campo `Usuario/Coreo electrónico` el valor de la variable `email`
2. Ingresar en el campo `Contraseña` el valor de la variable `password`
3. Dar clic en el botón `INICIAR SESIÓN`
4. Interceptar la petición al servicio `/api` esperando un resultado 200
5. Hacer un request al servicio de autenticación

### ***Resultados esperados:***
Se espera que el inicio de sesión sea exitoso.

### ***Condiciones posteriores:***
- El usuario debe ser dirigido a la página del dashboard de empresas.
- La cookie sessionR debe contener un valor.
