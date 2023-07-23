# Nodos Dashboard
Instalación de Nodos dashboard

__1. Preparación de NodeRed__

- Para visualizar el contenedores:
    - docker ps -a
- Inicializar el contenedor docker:
    - docker start _ID DEL CONTENEDOR "DOCKER"_

__2. Igresar a localhost:1880__

- Tener inicializado el ejercicio NodeRed (flow 2) con los tres nodos: 
    - Inject, Funcion, Debug.

- __Instalción de nodos dashboard__

    - Hacer clic en el menú que se encunetra a lado del botón deploy y escoger la opción _Manage Palette_
    - Seleccionar la pestaña _Install_
    - En el buscador, escribir la palabra dashboard
    - Seleccionar la opción __node-red-dashboard__ e instalar

- __Configuración del nodo__

    - En la sección del submenu, donde se encuentra el debug, buscar la pestaña dashcboard y dar clic
    - Añadir una nueva pestaña (+lab) y editar nombre: Tab 1 a _flow 3: fecha_, dar clic en update
    - Añadir un grupo (+group) y editar nombre: Group 1 a _Fecha_, dar clic en update
    - Seleccionar el __nodo texto__, (no escoger el nodo __texto input__)  y conectarlo a la salida del nodo function.
    - _Observará un triángulo naranja sobre el nodo, significa que aún necesita configuraciónes_.
    - Hacer doble clic sobre el nodo
    - Seleccionar el unico grupo creado en el paso anterior
    - Editar el apartado label: _text_ por _Fecha y Hora_ y hacer clic en done

__3. Ingresar a localhost:1880/ui__
- Observará un apartado gráfico de la Fecha y Hora.