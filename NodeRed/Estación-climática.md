# Estación Climática
Estación climática que recibe un Json con valores de temperatura y humedad por MQTT y generar un grafico con dashboard.

__1. Preparación de NodeRed y MQTT__

- Para visualizar el contenedores:
    - docker ps -a
- Inicializar el contenedor docker:
    - docker start _ID DEL CONTENEDOR "NodeRed"_
- Inicializar el contenedor MQTT "mosquitto":
    - docker start _ID DEL CONTENEDOR "mosquitto"_

__2. Ingresar a localhost:1880__

- __Crear un nuevo flow__:

    - Hacer clic en + del editor visual
    - Cambiar el nombre flow a Estación Climática y cerrar en el botón Done
    ![](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2014-11-42.png)

- __Nodo MQTT in__

- Este nodo nos permite utilizar diversos protocolos de internet para recibir datos.
    - Agregar el nodo _mqtt in_ de la sección (__network__) de paletas de nodos al editor visual.
    - Editar el nodo _mqtt in_ haciendo doble clic, editar el server y hacer Add. 
    ![](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2014-36-21.png)
    - Cambiar las propiedades, _name_, _Port_, como lo indica la siguiente imagen y hacer Update:
    ![](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2016-37-27.png)
    - Indicar el tema a suscribirse **Topic**: _codigoIoT/mqtt/clima_. Para guardar hacer Done.
    ![](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2016-37-52.png)

- __Nodo JSON__
- Los mensajes enviandos a través de MQTT seran cadenas (*strings*) en notación de un objeto JSON.
    - Isertar un nodo JSON de la sección (__parser__) y conectar a la salida del nodo _mqtt in_.
    - Hacer doble click sobre el nodo y asegúrarse que el campo **Action** tenga seleccionado **Always convert to JavaScript object** y hacer Done.
    ![](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2016-40-03.png)

- __Nodo function__
- Para redirigir la información de manera correcta, se agragará dos nodos _function_, así se podra obtener una visualización de la temperatura y humedad.
    
    - Insertar el primer nodo _function_
    - Modificar nobre a **Temperatura** y agregar el siguiente codigo en __On Message__:
    ```JavaScript
    msg.payload = msg.payload.temp;
    msg.topic = "Temperatura";
    return msg; 
    ```
    - Hacer Done para cerrar.

    - Insertar el segundo nodo _function_
    - Modificar nobre a **Humedad** y agregar el siguiente codigo en __On Message__:
    ```JavaScript
    msg.payload = msg.payload.hum; 
    msg.topic = "Humedad"; 
    return msg;
    ```
    - Hacer Done para cerrar.
    ![Conexión de los nodos](https://github.com/DanyHdz23/Daniel_HDZ/blob/main/NodeRed/Imagenes/Screenshot%20from%202023-07-24%2019-27-03.png)