# Ejercicio-NodeRed
Ejercicio NodeRed: Inject y Debug 

## 1. Preparación de NodeRed
- Inicializar el contenedor que contiene NodeRed:
docker start (_ID DEL CONTENEDOR_)
- Para visualizar los contenedores:
docker ps -a

 ## 2. Ingresar a localhost:1880
    
__1. Nodo Inject__
- Insertar un nodo inject y dar doble click
- Propiedades del nodo actual:
    - __Name__: Nombre del nodo 
    - __msg.payload__: Contenido que regresaraá el nodo una vez activado
    - __mfg.topic__: Tema que retornará el nodo cunado se active
    - __Repeat__: Tiempo de activación del nodo

__2. Nodo Debug__
- Este nodo nos permite mandar mensajes a la consola de depuración.
- Insertar nodo debug
- Conectar debug con la salida de timestamp (_Inject_)

__3. Ejecutar el programa__
- Deploy y abrir consola de depuración
- Click en ícono del insecto.
- Enviar mensaje con el nodo inject (_cuadro azul_)
Observará números en la consola de depuración; el tiempo esta marcado en formato UNIX 1970. (Segundos) 

__4. Nodo Funcion__
- Este nodo nos permite manipular el contenido del objeto msg que recibe. En JavaScript.
- Este nodo se conecta entre la saldda de inject y la entrada de debug.
    - __Name__: Nombre del nodo
    - __Setup__: Configura el número de nodos y los modulos externos que usa
    - __On start__: El código escrito correra al iniciar flow
    - __On message__: El código escrito correra al recibir una entrada
    - __On stop__: El código escrito correra para parar el flow
- Insertar este codigo en _On message_:

```javascript
// Lo que está después de "//" son comentarios // Crea un objeto Date a partir del msg.payload enviado por timestamp 
var date = new Date(msg.payload);
// Cambia el payload para que sea una fecha con formato 
msg.payload = date.toString(); 
// Regresa el mensaje para que se envíe al siguiente nodo 
return msg; 
```
Este código nos mermite visualizar hora y fecha en una lectura legible para humanos.
- Dar click en Deploy