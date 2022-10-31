# Login test cases

## 📋 Contents
* [Conditions for execution of tests](#conditions)
* [Login successful with xmx](#login-xmx)
* [Login successful with email](#login-email)
* [Login with unregistred email](#login-unregistred-email)
* [Login with invalid email format](#login-invalid-email)
* [Login with incorrect password](#login-incorrect-pass)
* [Token refresh successful](#refresh-successful)
* [Redirection from home to dashboard while the session is active](#login-active-session)
* [Logout successful](#logout-successful)
* [Login attempt with candidate credentials](#login-candidate)
* [Login after 10 minutes of inactivity](#login-inactivity)

## <a id="conditions">✅ Conditions for execution of tests</a>

| Condición de ejecución  | Valor de ejecución                |
|-------------------------|-----------------------------------|
| Navegadores             |                                   |
| Frecuencia de ejecución |                                   |
| Grabación de video      |                                   |
| Número de reintentos    |                                   |
| Etiqueta(s) de prueba   |                                   |
| Interfaz gráfica        |                                   |

## <a id="login-xmx">🔐 Login with xmx</a>
**`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar el correcto inicio de sesión de un usuario relutador, usando el xmx de su cuenta.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario reclutador (xmx y contraseña)
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor               |
|---------------------|---------------------|
| xmx                 | xmxpruebas78x       |
| password            | pruebasQA1          |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `xmx`  | Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que no devuelva errores|                     |
| 6. Verificar que el campo `Contraseña` se encuentra visible                         |                     |
| 7. Escribir en el campo `Contraseña` el valor de la variable `password`             |                     |
| 8. Dar clic en el botón `INICIAR SESIÓN`                                            |                     |
| 9. Interceptar la petición `/api/oauthLogin` esperando un 200                       |                     |
| 10. Hacer un request directo a `Hydra` para comprobar su disponibilidad             |                     |
| 11. Hacer un request al servicio `iam` esperando una respuesta satisfactoria        |                     |
| 12. Hacer una petición para obtener el `tokenInterchange`                           |                     |

### **Resultados esperados:**
Se espera que el inicio de sesión sea exitoso.

### **Condiciones posteriores:**
- El usuario debe ser dirigido a la página del dashboard de empresas.
- La cookie sr debe contener el token JWT con el campo rid y una fecha de expiración válida.

## <a id="login-email">🔐 Login with email</a>
**`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar el correcto inicio de sesión de un usuario relutador, usando el email de su cuenta.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario reclutador (email y contraseña)
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor               |
|---------------------|---------------------|
| email               |                     |
| password            | pruebasQA1          |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `email`| Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que no devuelva errores|                     |
| 6. Verificar que el campo `Contraseña` se encuentra visible                         |                     |
| 7. Escribir en el campo `Contraseña` el valor de la variable `password`             |                     |
| 8. Dar clic en el botón `INICIAR SESIÓN`                                            |                     |

### **Resultados esperados:**
Se espera que el inicio de sesión sea exitoso.

### **Condiciones posteriores:**
- El usuario debe ser dirigido a la página del dashboard de empresas.
- La cookie sr debe contener el token JWT con el campo rid y una fecha de expiración válida.

## <a id="login-unregistred-email">🔒 Login with unregistred email</a>

### **Descripción:**
Caso de prueba para verificar que no se permita continuar con el inicio de sesión, cuando el email no está registrado.

### **Condiciones del caso de prueba:**
- Contar con un email no registrado en occ empresas.
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor                        |
|---------------------|------------------------------|
| email               | pruebas.mictlan001@gmail.com |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `email`| Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que devuelva error 404 |                     |
| 6. Verificar el texto `No hay una cuenta vinculada con este usuario` esté visible   |                     |
| 7. Verificar que el botón `CONTINUAR` se encuentre deshabilitado                    |                     |
| 8. Dar clic en en el campo `Correo electrónico/usuario` y borrar la última letra    |                     |
| 9. Verificar que el botón `CONTINUAR` se encuentre habilitado                       |                     |

### **Resultados esperados:**
Se espera que no se pueda proceder con el inicio de sesión.

### **Condiciones posteriores:**
- El usuario debe permanecer en la misma pantalla de autenticación.
- El campo de constraseña y el botón de INICIAR SESIÓN debe mantenerse ocultos.

## <a id="login-invalid-email">🔒 Login with invalid email format</a>

### **Descripción:**
Caso de prueba para verificar que no se permita continuar con el inicio de sesión, cuando el email tiene un formato inválido.

### **Condiciones del caso de prueba:**
- Contar con un email registrado en occ empresas, con un formato incorrecto generado con efecto de ésta prueba.
- Ingresar al home de empresas.
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor                        |
|---------------------|------------------------------|
| email               | xakox47983@haboty            |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `email`| Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que devuelva error 404 |                     |
| 6. Verificar el texto `No hay una cuenta vinculada con este usuario` esté visible   |                     |
| 7. Verificar que el botón `CONTINUAR` se encuentre deshabilitado                    |                     |
| 8. Dar clic en el botón `X` del campo `Correo electrónico/usuario`                  |                     |
| 9. Verificar que el botón `CONTINUAR` se encuentre habilitado                       |                     |
| 10. Dar clic en el botón `CONTINUAR`                                                |                     |
| 11. Verificar el texto `Este correo electrónico o usuario no es válido` sea visible |                     |

### **Resultados esperados:**
Se espera que no se pueda proceder con el inicio de sesión.

### **Condiciones posteriores:**
- El usuario debe permanecer en la misma pantalla de autenticación.
- El campo de constraseña y el botón de INICIAR SESIÓN debe mantenerse ocultos.

## <a id="login-incorrect-pass">🔒 Login with incorrect password</a>

### **Descripción:**
Caso de prueba para verificar el error al intentar iniciar sesión con una contraseña incorrecta.

### **Condiciones del caso de prueba:**
- Contar con el xmx de un reclutador y una contraseña incorrecta para la cuenta.
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor               |
|---------------------|---------------------|
| xmx                 | xmxpruebas78x       |
| password            | Test12345           |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `xmx`  | Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que no devuelva errores|                     |
| 6. Verificar que el campo `Contraseña` se encuentra visible                         |                     |
| 7. Escribir en el campo `Contraseña` el valor de la variable `password`             |                     |
| 8. Dar clic en el botón `INICIAR SESIÓN`                                            |                     |
| 9. Interceptar la petición `/api/oauthLogin` esperando un error 401                 |                     |

### **Resultados esperados:**
Se espera que se bloquee el inicio de sesión

### **Condiciones posteriores:**
- El usuario debe permanecer en la pantalla de inicio de sesión.
- Se debe mostrar un alert con el mensaje `Usuario o contraseña incorrectos.`

## <a id="refresh-successful">🔓 Token refresh successful</a>
**`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar que el refresh del token se realice de manera exitosa.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario reclutador (xmx y contraseña).
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor                  |
|---------------------|------------------------|
| email               | xmxpruebas78x          |
| password            | pruebasQA1             |


### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `xmx`  | Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que no devuelva errores|                     |
| 6. Verificar que el campo `Contraseña` se encuentra visible                         |                     |
| 7. Escribir en el campo `Contraseña` el valor de la variable `password`             |                     |
| 8. Dar clic en el botón `INICIAR SESIÓN`                                            |                     |
| 9. Interceptar la petición `/api/oauthLogin` esperando un status 200                |                     |
| 10. Interceptar la petición `/api/refresh` esperando un status 200                  |                     |

### **Resultados esperados:**
Se espera que la sesión permanezaca activa después del inicio de sesión.

### **Condiciones posteriores:**
- El usuario debe ser redirigido a la pantalla del dashboard de empresas.
- La pertición de refresh token debe contestar con el status correcto.

## <a id="login-active-session">🔓 Redirection from home to dashboard while the session is active</a>
**`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar que la sesión permanezca activa en la página del home de empresas.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario reclutador (xmxpruebas78x/pruebasQA1).
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"
- Hacer el proceso de inicio de sesión con las credenciales anteriores.

### **Datos de prueba:**
| Nombre de variable  | Valor                                |
|---------------------|--------------------------------------|
| url-home            | https://www.occ.com.mx/empresas/     |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar la url actual `https://www.occ.com.mx/empresas/hirer-center/actividad/`| Default             |
| 2. Redireccionar a la url con el valor de la variable `url-home`                    | Default             |
| 3. Verificar que la cookie `sr` contenga el valor del JWT                           |                     |
| 4. Verificar que la cookie `occidr11` contenga el valor del token legacy            |                     |
| 5. Verificar que se realice la redirección al dashboard de empresas                 |                     |

### **Resultados esperados:**
Se espera que la sesión permanezaca activa después de la redirección en el home de empresas.

### **Condiciones posteriores:**
- El usuario debe ser redirigido a la pantalla del dashboard de empresas.
- Las cookies sr y occidr11 deben existir y contener un valor.

## <a id="logout-successful">🔒 Logout successful</a>
**`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar que el cierre de sesión se haga de manera exitosa.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario reclutador (xmxpruebas78x/pruebasQA1).
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"
- Hacer el proceso de inicio de sesión con las credenciales anteriores.

### **Datos de prueba:**
| Nombre de variable  | Valor                                |
|---------------------|--------------------------------------|
| N/A                 | N/A                                  |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar la url actual `https://www.occ.com.mx/empresas/hirer-center/actividad/`| Default             |
| 2. Dar clic en el botón que contiene el nombre del usuario                          | Default             |
| 3. Dar clic en la opción `Cerrar sesión`                                            |                     |
| 4. Verificar que no existan las cookies `sr` y `occidr11`                           |                     |

### **Resultados esperados:**
Se espera que la sesión se cierre de manera satisfactoria después de la ejecución de los pasos.

### **Condiciones posteriores:**
- El usuario debe ser redirigido a la pantalla del home de empresas.
- Al dar clic en el botón de INICIA SESIÓN se debe redirigir al usuario a la pantalla del login.

## <a id="login-candidate">🔒 Login attempt with candidate credentials</a>

### **Descripción:**
Caso de prueba para verificar que no sea posible iniciar sesión en el login de empresas con credenciales de reclutador.

### **Condiciones del caso de prueba:**
- Contar con las credenciales de un usuario candidato (correo y contraseña).
- Ingresar al home de empresas.
- Dar clic en el botón "INICIA SESIÓN".

### **Datos de prueba:**
| Nombre de variable  | Valor                                |
|---------------------|--------------------------------------|
| email               | glendag2026@gmail.com                |
| password            | Glenda20                             |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `email`| Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando un error 404           |                     |
| 6. Verificar que exista el texto `No hay una cuenta vinculada con este usuario`     |                     |
| 7. Verificar que el botón `CONTINUAR` esté deshabilitado                            |                     |

### **Resultados esperados:**
Se espera que no se permita continuar con el inicio de sesión.

### **Condiciones posteriores:**
- El usuario debe permanecer en la pantalla de inicio de sesión con los errores correspondientes y el botón CONTINUAR deshabilitado
- El campo "Contraseña" y el botón "INICIAR SESIÓN" se deben mantener ocultos.
