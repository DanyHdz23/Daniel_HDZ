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

- Crear un nuevo flow:
    - Hacer clic en + del editor visual
    - Cambiar el nombre flow a Estación Climática y cerrar en el botón Done
    