# 🔍Test plan

## 📋Test process

El proceso de ejecución de pruebas se planea de la siguiente manera:
* Una vez completados todos los elementos que conforman el software, se llevará a cabo una etapa de pruebas en ambiente de desarrollo.
* Una vez resuletas las posibles incidencias en ambiente de desarrollo, se realizará el pase del proyecto a ambiente productivo.
* En ambiente productivo, se ejecutará una nueva serie de pruebas para garantizar la funcionalidad del software.
* Una vez probado el sofware y determinando que se cumple con los criterios de aceptación, se mantendrán los cambios en ambiente productivo, al igual que el monitoreo constante mediante pruebas aitomatizadas.

## 📊 Types of tests

Los tipos de pruebas que se llevarán a cabo durante este proyecto, así como los detalles de las mismas, se listan a continuación:

* **`PRUEBAS AUTOMATIZADAS (E2E):`** Se ejecutarán a partir de la liberación del proyecto, en ambiente productivo, de Lunes  a Viernes, de 8 am a 6:00 pm, cada media hora. Estas pruebas tienen la finalidad de mantener un monitoreo constante de los nuevos flujos.
* **`PRUEBAS DE REGRESIÓN:`** Se ejecutarán posteriormente a la liberación del software en ambiente de desarrollo y ambiente productivo; con la finalidad de verificar que los procesos del administrador de vacantes no se vean alterados con la integración de la nueva funcionalidad en el sistema.
* **`PRUEBAS FUNCIONALES Y DE ACEPTACIÓN:`** Se ejecutarán posteriormente a la liberación del software en ambiente de desarrollo y en ambiente productivo; esto con el objetivo de verificar el funcionamiento del nuevo flujo agregado en el administrador de vacantes (nueva vacante en base a una plantilla).

## 🛠Testing tools

Entre las herramientas que se usarán para la ejecución de pruebas, se encuentran:

* **`Cypress:`** Permite ejecutar las pruebas automatizadas de manera periódica y hacer un registro del histórico en el dashboard de la herramienta.
* **`Navegador:`** Permite replicar el comportamiento de los usuarios ingresando a la plataforma de OCC Mundial y servirá para las pruebas de funcionalidad, aceptación y regresión.
* **`Registro del resultado de pruebas:`** Documento para almacenar los resultados de las pruebas efectuados, tanto en ambiente de desarrollo como en ambiente productivo.

## 🔍Test cases

### Caso de prueba - Administrador de vacantes `PRUEBAS DE REGRESIÓN`

**Escenario de prueba:** Ambiente productivo, ambiente de desarrollo.

**Descripción:** Caso de prueba para verificar el correcto funcionamiento del administrador de vacantes, el cual abarca las siguientes acciones: Carga de vacantes, creación de una nueva vacante desde cero, edición de vacante, compartir, autorepublicar, republicar, desactivar y eliminar.

**Condiciones anteriores a la prueba**
* Contar con una cuenta que tenga créditos de publicación de vacantes.

**Pasos de la prueba**

| Pasos                                                                                             |
|---------------------------------------------------------------------------------------------------|
| 1. Se inicia sesión con las credenciales correspondientes a la cuenta con créditos disponibles    |
| 2. Ingresar a la sección de `VACANTES`                                                            |
| 3. Verificar la carga correcta de las vacantes `publicadas, inactivas, expiradas y borradores`    |
| 4. Crear una nueva vacante desde cero, revisando que todos los datos se encuentren vacíos         |
| 5. Editar la vacante recién creada y publicarla revisando que el id sea el mismo                  |
| 6. Compartir la vacante publicada, verificando que el link permita ver correctamente la oferta    |
| 7. Programar la autorepublicación de la vacante recién creada                                     |
| 8. Republicar una vacante ya existente, siguiendo el proceso de edición y comprobando la vigencia |
| 9. Desactivar la vacante recién creada, verificando que se encuentre en la sección `Inactivas`    |
| 10. Eliminar la vacante recién creada, verificando que no aparezca en ninguna de las secciones    |

**Criterios de aceptación**
* Se espera que se cumplan de manera correcta todos los pasos detallados anteriormente.
* Se espera que la vacante creada en esta prueba ya no exista.

### Caso de prueba - Crear nueva vacante en base a una plantilla `PRUEBAS FUNCIONALES Y DE ACEPTACIÓN`

**Escenario de prueba:** Ambiente productivo, ambiente de desarrollo.

**Descripción:** Caso de prueba para verificar la creación de una nueva vacante, en base a una plantilla de las últimas vacantes de la cuenta.

**Condiciones anteriores a la prueba**
* Contar con una cuenta que tenga créditos de publicación de vacantes.

**Pasos de la prueba**

| Pasos                                                                                               |
|-----------------------------------------------------------------------------------------------------|
| 1. Se inicia sesión con las credenciales correspondientes a la cuenta con créditos disponibles      |
| 2. Ingresar a la sección de `VACANTES`                                                              |
| 3. Dar clic en el botón `CREAR NUEVA VACANTE`                                                       |
| 4. Verificar que se cargue la interfaz de plantillas con la lista de las últimas vacantes           |
| 5. Seleccionar una de las plantillas cargadas                                                       |
| 6. Verificar la pantalla `Nueva publicación` con los datos de la plantilla seleccionada             |
| 7. Verificar que todos los datos se encuentren llenos y editables (editar al menos uno de ellos)    |
| 8. Dar clic en el botón `SIGUIENTE`                                                                 |
| 9. Verificar que todos los datos se encuentren llenos y editables (editar al menos uno de ellos)    |
| 10. Dar clic en el botón `PUBLICAR`                                                                 |
| 12. Verificar la redirección a la pantalla de publicación y esperar que se complete el proceso      |
| 13. Ir al administrador de vacantes                                                                 |
| 14. Verificar que se encuentre la vacante publicada con un id distinto al de la plantilla           |

**Criterios de aceptación**
* Se debe encontrar la vacante creada en base a una plantilla en la sección de vacantes publicadas, con un id diferente al de la plantilla.
* NOTA: En caso de que no se cuenten con créditos de publicación, se espera que se cree un carrito en base al tipo de vacante y que la vacante se encuentre en la sección de BORRADORES con un id diferente al de la plantilla.

### Pruebas automatizadas `PRUEBAS E2E`

Para consultar la documentación de las pruebas automatizadas, haga [clic aquí](https://backstage.occdeep.io/docs/default/Component/recruiters-integration-test/Casos%20de%20prueba%20-%20CAJA/)

## 📘Document test results

Para documentar los resultados de las pruebas realizadas, ingresar al siguiente [documento](https://occmundialmx-my.sharepoint.com/:x:/r/personal/aesquivel_occ_com_mx/Documents/Resultados%20de%20pruebas%20-%20PLANTILLAS%20CAJA.xlsx?d=w4c80a3ce456b4be88f29459aacffec11&csf=1&web=1&e=oA5nI8)
