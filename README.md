# Login test cases

## 📋 Contents
* [Conditions for execution of tests](#conditions)
* [Login successful with xmx](#login-xmx)
* [Login successful with email](#login-email)
* [Login with incorrect credentials](#login-incorrect-credentials)

## <a id="conditions">✅ Conditions for execution of tests</a>

| Condición de ejecución  | Valor de ejecución                                   |
|-------------------------|------------------------------------------------------|
| Navegadores             | Chrome                                               |
| Frecuencia de ejecución |                                                      |
| Grabación de video      | Sí                                                   |
| Número de reintentos    | `Flujos críticos`: 2  `Flujo secundario:` 1          |
| Etiqueta(s) de prueba   | `Inicio de sesión` `Flujo crítico`/`Flujo secundario`|
| Interfaz gráfica        | Sí                                                   |

## <a id="login-xmx">🔐 Login with xmx</a>  **`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar el inicio de sesión exitoso de un usuario relutador, usando el xmx y tomando en cuenta un flujo completo, el cual incluye las siguientes acciones: verificar el refresh del token, redirección del home al dashboard (con sesión activa) y el logout.

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
| 5. Interceptar la petición `/api/userVerification` esperando un 200 en el body      |                     |
| 6. Verificar que el campo `Contraseña` se encuentra visible                         |                     |
| 7. Escribir en el campo `Contraseña` el valor de la variable `password`             |                     |
| 8. Dar clic en el botón `INICIAR SESIÓN`                                            |                     |
| 9. Interceptar la petición `/api/oauthLogin` esperando un 200 en el body            |                     |
| 10. Request a `Hydra` para comprobar disponibilidad (en caso de falla del paso 9)   |                     |
| 11. Request al `iam` esperando una respuesta correcta (en caso de falla del paso 9) |                     |
| 12. Request para obtener el `tokenInterchange` (en caso de falla del paso 9)        |                     |
| 13. Verificar la redirección al dashboard de empresas                               |                     |
| 14. Verificar que el JWT contenga el campo `rid` y tenga una expiración correcta    |                     |
| 15. Verificar que las cookies `sr` y `occidr11` existan                             |                     |
| 16. Interpectar la petición `/api/refresh` esperando un status 200                  |                     |
| 17. Ir al home de empresas, esperando que el flujo redirija al dashboard            |                     |
| 18. Dar clic en el menú del usuario                                                 |                     |
| 19. Dar clic en cerrar sesión                                                       |                     |

### **Resultados esperados:**
Se espera que el inicio y el cierre de sesión sean exitosos.

### **Condiciones posteriores:**
- El usuario debe ser dirigido a la página del home de empresas.
- Al dar clic en el botón `INICIA SESIÓN` debe redirigir al formulario del login.
- No deben existir las cookies de sesión (`sr` y `occidr11`).

## <a id="login-email">🔐 Login with email</a>  **`Flujo crítico`**

### **Descripción:**
Caso de prueba para verificar el inicio de sesión exitoso de un usuario relutador, usando el email de su cuenta y después de 10 minutos de inactividad en el formulario de inicio de sesión.

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
| 3. Esperar 10 minutos en inactividad                                                |                     |
| 4. Escribir en el campo `Correo electrónico/usuario` el valor de la variable `email`| Default             |
| 5. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 6. Interceptar la petición `/api/oauthLogin` esperando un 200 en el body            |                     |
| 7. Request a `Hydra` para comprobar disponibilidad (en caso de falla del paso 9)    |                     |
| 8. Request al `iam` esperando una respuesta correcta (en caso de falla del paso 9)  |                     |
| 9. Request para obtener el `tokenInterchange` (en caso de falla del paso 9)         |                     |

### **Resultados esperados:**
Se espera que el inicio de sesión sea exitoso.

### **Condiciones posteriores:**
- El usuario debe ser dirigido a la página del dashboard de empresas.
- La cookie sr debe contener el token JWT con el campo rid y una fecha de expiración válida.

## <a id="login-incorrect-credentials">🔒 Login with incorrect credentials</a>  **`Flujo secundario`**

### **Descripción:**
Caso de prueba para verificar que al ingresar las credenciales incorrectas, el flujo impida el inicio de sesión. Entre las consideraciones de credenciales se encuentran: Email no registrado, email con formato inválido, password incorrecto y credenciales de candidato.

### **Condiciones del caso de prueba:**
- Contar con un email no registrado en occ empresas.
- Contar con un email que se encuentre registrado pero de formato inválido.
- Contar con un email válido y una contraseña incorrecta.
- Contar con credenciales de candidato.
- Ingresar al home de empresas
- Dar clic en el botón "INICIA SESIÓN"

### **Datos de prueba:**
| Nombre de variable  | Valor                        |
|---------------------|------------------------------|
| unregistered-email  | pruebas.mictlan001@gmail.com |
| invalid-email       | mabocu@getnada               |
| registered-email    | mabocu@getnada.com           |
| incorrect-password  | Test12345                    |
| candys-email        | glendag2026@gmail.com        |
| candys-password     | Glenda20                     |

### **Pasos a ejecutar:**

| Pasos                                                                               | Tiempo de espera    |
|-------------------------------------------------------------------------------------|---------------------|
| 1. Verificar que el texto `Ingresa como reclutador` se encuentre visible            | Default             |
| 2. Verificar que la url del login cuente con el parámetro `challenge`               |                     |
| 3. Escribir en el campo `Correo electrónico/usuario` el valor `unregistered-email`  | Default             |
| 4. Dar clic en el botón `CONTINUAR`                                                 |                     |
| 5. Interceptar la petición `/api/userVerification` esperando que devuelva error 404 |                     |
| 6. Verificar el texto `No hay una cuenta vinculada con este usuario` esté visible   |                     |
| 7. Verificar que el botón `CONTINUAR` se encuentre deshabilitado                    |                     |
| 8. Dar clic en el botón `X` del campo `Correo electrónico/usuario`                  |                     |
| 9. Escribir en el campo `Correo electrónico/usuario` el valor `invalid-email`       |                     |
| 10. Dar clic en el botón `CONTINUAR`                                                |                     |
| 11. Interceptar la petición `/api/userVerification` esperando que devuelva error 404|                     |
| 12. Verificar el texto `No hay una cuenta vinculada con este usuario` esté visible  |                     |
| 13. Verificar que el botón `CONTINUAR` se encuentre deshabilitado                   |                     |
| 14. Dar clic en el botón `X` del campo `Correo electrónico/usuario`                 |                     |
| 15. Escribir en el campo `Correo electrónico/usuario` el valor `registered-email`   | Default             |
| 16. Interceptar la petición `/api/userVerification` esperando que devuelva un 200   |                     |
| 17. Verificar que el campo `Contraseña` se encuentra visible                        |                     |
| 18. Escribir en el campo `Contraseña` el valor de la variable `incorrect-password`  |                     |
| 19. Dar clic en el botón `INICIAR SESIÓN`                                           |                     |
| 20. Interceptar la petición `/api/oauthLogin` esperando un error 401                |                     |
| 21. Dar clic en el botón `X` del campo `Correo electrónico/usuario`                 |                     |
| 22. Escribir en el campo `Correo electrónico/usuario` el valor `candys-email`       |                     |
| 23. Interceptar la petición `/api/userVerification` esperando que devuelva un 200   |                     |
| 24. Verificar que el campo `Contraseña` se encuentra visible                        |                     |
| 25. Escribir en el campo `Contraseña` el valor de la variable `candys-password`     |                     |
| 26. Dar clic en el botón `INICIAR SESIÓN`                                           |                     |
| 27. Interceptar la petición `/api/oauthLogin` esperando un error 401                |                     |
| 28. Verificar el texto `Por tu seguridad la liga anterior ha expirado, favor de...` |                     |

### **Resultados esperados:**
Se espera que no se permita iniciar sesión.

### **Condiciones posteriores:**
- El usuario debe permanecer en la misma pantalla de autenticación.
- No deben existir las cookies `sr` y `occidr11`.
- El campo de constraseña y el botón de INICIAR SESIÓN debe mantenerse ocultos.
