# flow4-Node-RED-MQTT
Este repositorio contiene el flow 4 del curso de NodeRed, visto en en los contenidos de Internet de las cosas de Codigo IoT

## Introducción

Este flow consiste en un tablero que presente la información de temperatura y humedad locales. Este flow recibe la información por MQTT con un broker local.

## Material Necesario

Para realizar este flow necesitas lo siguiente

- [Ubuntu 20.04](https://releases.ubuntu.com/20.04/)
- [NodeJS](https://nodejs.org/es/)
    - [NPM](https://www.npmjs.com/)
    - [NodeRed](https://nodered.org/docs/getting-started/local)
    - [Nodos Dashboard](https://flows.nodered.org/node/node-red-dashboard)
- [Mosquitto](https://mosquitto.org/)

## Material de referencia

En los siguientes enlaces puedes encontrar cursos en la plataforma de edu.codigoiot.com que te permitirán realiar las configuraciones necesarias

- [Instalación de Virutal Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
- [Instalación de NodeRed](https://edu.codigoiot.com/course/view.php?id=817)
- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)
- [Introducción a Mosquitto](https://edu.codigoiot.com/course/view.php?id=851)

## Instrucciones

### Requisitos previos

Para que este flow funcione, debes cumplir con los siguientes requisitos previos
1. Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17.0LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM
2. Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2
3. Instalar los nodos node-red-dashboard. Para ello, dirigete a la opcion "Manage Palet" de NodeRed y en la pestaña Install busca node-red-dashboard. Finalmente haz clic en instalar.
4. Instalación de Broker local Mosquitto MQTT.

### Instrucciones de preparación del entorno

Para ejecutar este flow, es necesario lo siguiente
1. Arrancar NodeRed con el comando `node-red`
2. Importar el flow del repositorio
3. Hacer clic en el boton Deploy

### Instrucciones de operación

- Configución de mqtt in node

![image](https://user-images.githubusercontent.com/83924529/187842443-40847dc1-79e3-450e-808c-cd37c4d81144.png)

- Configución de json node

![image](https://user-images.githubusercontent.com/83924529/187842649-ebf86e6d-1e07-49fb-a550-ea67ae04cacb.png)

- Configución de node funtion temperature & humidity (con correspondientes cambios)

    msg.payload = msg.payload.temp;
    msg.topic = "Temperature";
    return msg;

- Crear tab y grupos

![image](https://user-images.githubusercontent.com/83924529/187843108-2e3fdb6f-e85a-4478-9b7f-ed2a1b9c3408.png)

- Configución de node gauge

![image](https://user-images.githubusercontent.com/83924529/187843217-b7f4a1fc-a216-4119-91aa-2f608adf3854.png) ![image](https://user-images.githubusercontent.com/83924529/187843291-e22c78da-d8af-4e10-ba9c-770897fd50a6.png)

- Configución de node chart

![image](https://user-images.githubusercontent.com/83924529/187843369-cf41560a-0b30-4644-88a4-50c470b09084.png)

- Para observar el resutlado de este flow, abre un navegador y dirígete a localhost:1880/ui
-  Enviar por MQTT un mensaje que contenga un JSON con las variables ID, temp y hum

### Notas

- Este Flow se suscribe al tema codigoIoT/Mor/mqtt/flow4
- El mensaje mqtt usado para probar este flow es `mosquitto_pub -h localhost -t codigoIoT/Mor/mqtt/flow4 -m '{"ID":"Amy Malavar","temp":21,"hum":78}'`
- Para que la gráfica historica muestre información, deben enviarse al menos 2 puntos

## Resultados

A continuación puedes ver los nodos del flow.

![image](https://user-images.githubusercontent.com/83924529/187841691-a2c6d238-b9c4-45d1-a2c9-88c9bbf9fe49.png)

A continuación puede ver el tablero resultante.

![image](https://user-images.githubusercontent.com/83924529/187843595-397046bb-8234-43df-9331-a214c32a1e46.png)

## Evidencias

La evidencia se encuentra en el archivo de flow4.json

# Créditos
Flow developed by Amy Malavar
* [GitHub](https://github.com/amymalavar)
* [LinkedIn](https://www.linkedin.com/in/amy-malavar)
* [GitHub de instructor](https://github.com/hugoescalpelo)
