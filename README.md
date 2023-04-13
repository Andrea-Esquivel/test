# Test plan

## Test process

El proceso de prueba se realizará de la siguiente manera: Una vez completados todos los elementos que componen el software, se llevará a cabo una etapa de pruebas en ambiente de desarrollo; una vez resuletas las posibles incidencias, se realizará el pase del proyecto a ambiente productivo, seguido una nueva serie de pruebas en este ambiente y por último, se mantendrá el monitoreo constante de los nuevos flujos mediante pruebas aitomatizadas. 

## Types of tests

Los tipos de pruebas que se llevarán a cabo durante este proyecto, así como los detalles de las mismas, se listan a continuación:

* **`PRUEBAS AUTOMATIZADAS (E2E):`** Se ejecutarán a partir de la liberación del proyecto en ambiente productivo, de Lunes a Viernes, de 8 am a 6:00 pm, cada media hora. Las pruebas abarcan los flujos de creación de vacante en base a una plantilla y creación de vacante desde cero (pruebas end to end).
* **`PRUEBAS DE REGRESIÓN:`** Se ejecutarán postiormente a la liberación del software, en ambiente de desarrollo y ambiente productivo; con la finalidda de verificar que los procesos que forman parte del administrador de vacantes no se vean aletradas con la integración de la nueva funcionalidad. 
* **`PRUEBAS FUNCIONALES Y DE ACEPTACIÓN:`** Se ejecutarán posteriormente a la liberación del software en ambiente de desarrollo y en ambiente productivo; esto con el objetivo de verificar el funcionamiento de las nuevas funcionalidades agregadas en el administrador de vacantes (nueva vacante desde plantilla).

## Testing tools

Entre las herramientas que se usarán para la ejecución de pruebas, se encuentran:

* **`Cypress:`** Permite ejecutar las pruebas automatizadas de manera periódica y hacer un registro del histórico en el dashboard de la herramienta.
* **`Navegador:`** Permite replicar el comportamiento de los usuarios ingresando a la plataforma de OCC Mundial.
* **`Registro del resultado de pruebas:`** Documento para almacenar los resultados de las pruebas efectuados, tanto en ambiente de desarrollo como en ambiente productivo.

## Test cases

### Caso de prueba - Administrador de vacantes `PRUEBAS DE REGRESIÓN`

**Escenario de prueba:** Ambiente productivo, ambiente de desarrollo

**Descripción:** Caso de prueba para verificar el correcto funcionamiento del administrador de vacantes, el cual abarca las siguientes acciones: Carga de vacantes, creación de una nueva vacante desde cero, edición de vacante, Compartir, autorepublicar, republicar, desactivar y eliminar.

**Condiciones anteriores a la prueba**
* Contar con una cuenta que tenga créditos de publicación de vacantes.

**Pasos de la prueba**

| Pasos                                                                                             |
|---------------------------------------------------------------------------------------------------|
| 1. Se inicia sesión con las credenciales correspondientes a la cuenta con créditos disponibles    |
| 2. Ingresar a la sección de `VACANTES`                                                            |
| 3. Verificar la carga correcta de las vacantes `publicadas, inactivas, expiradas y borradores`    |
| 4. Crear una nueva vacante desde cero, revisando que se tengan que llenar todos los datos         |
| 5. Editar la vacante recién creada y publicarla revisando que el id sea el mismo                  |
| 6. Compartir la vacante publicada, verificando que el link permita ver correctamente la oferta    |
| 7. Programar la autorepublicación de la vacante recién creada                                     |
| 8. Republicar una vacante ya existente, siguiendo el proceso de edición y comprobando la vigencia |
| 9. Desactivar la vacante recién creada, verificando que se encuentre en la sección `Inactivas`    |
| 10. Eliminar la vacante recién creada, verificando que no aparezca en ninguna de las secciones    |

**Criterios de aceptación**
* Se espera que se cumplan de manera correcta todos los pasos detallados anteriormente.
* Se espera que la vacante creada en esta prueba ya no exista.

### Caso de pruebas automatizadas `PRUEBAS E2E`

Para consultar la cocumentación de las pruebas automatizadas, haga [clic aquí](https://backstage.occdeep.io/docs/default/Component/recruiters-integration-test/Casos%20de%20prueba%20-%20CAJA/)

## Document test results

Para documentar los resultados de las pruebas realizadas, ingresar al siguiente [documento]()
