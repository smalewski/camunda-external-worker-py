# Consultar Indicadores

![BPMN Diagram](process.png)

|   Nr. | Tópico                                      | Actividad                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| :---: | :---                                        | :---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     1 | **StartEvent**                              | 1. En la pestaña 'General', configura el parámetro **Initiator** = 'starter'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|     2 | **'Mostrar indicadores User Task**          | 1. En la pestaña 'General', configura el parámetro **Assignee** = '${starter}'.<br>2. En la pestaña 'Forms', agrega las siguientes variables del siguiente modo:<br>2a. **ID** = 'uf, **Type** = 'string', **Label** = 'UF', **Add Constraint** -> **Name** = 'readonly'.<br>2b. **ID** = 'dolar', **Type** = 'string', **Label** = 'Dolar', **Add Constraint** -> **Name** = 'readonly'.<br>                                                                                                                                                                                                                                                                                                                                                                                                                     |
|     3 | **'Obtener valor UF y Dolar' Service Task** | 1. Configura el parámetro 'Implementation' = 'Connector'. <br> 2. Muévete a la pestaña **Connector**. Configura el parámetro **Connector Id** = 'http-connector'.<br> 3. Agrega los siguientes **Input Parameter**:<br> 3a. **Name** = 'method'. **Type** = 'Text'. **Value** = 'GET'. <br> 3b. **Name** = 'url'. **Type** = 'Text'. **Value** = 'http://indicadoresdeldia.cl/webservice/indicadores.json'. 4. Agrega los siguientes **Output Parameter**:<br> 4a. **Name** = 'uf'. **Type** = 'Script'. **Script Format** = 'javascript'. **Script Type** = 'Inline Script'. **Script** = 'S(response).prop('indicador').prop('uf').value()'. <br> 3b. **Name** = 'dolar'. **Type** = 'Script'. **Script Format** = 'javascript'. **Script Type** = 'Inline Script'. **Script** = 'S(response).prop('moneda').prop('dolar').value()'. |