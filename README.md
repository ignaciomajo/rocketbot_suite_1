# Rocketbot Suite 1: Búsqueda Mercado Libre

![rpa_foto_portada](https://github.com/user-attachments/assets/5856b017-6874-4660-8dd6-6d0b7e582bd8)

## Índice 📋

1. Descripción del proyecto.
2. Acceso al proyecto
3. Demostración del funcionalidades y aplicaciones.
4. Tecnologías utilizadas.
5. Agradecimientos.
6. Desarrollador del proyecto.

## 1. Descripción del proyecto 📚

Este proyecto mustra tan solo una parte de la capacidad de automatizar un proceso de web scrapping utilizando tencología RPA (Robot Process Automation), en particular **Rocketbot** 🚀. En él, se puede ver como es posible abrir una pagina web y realizar una búsqueda de, en este caso, artículos en la página de Mercado Libre, extrayendo la información relevante que buscamos analizar, como puede ser: criterio de búsqueda, artículos encontrados, precio, descuento que poseen dichos artículos y el link correspondiente para llegar a ellos. Finalmente, envia un correo con el archivo generado y luego, lo lee y descarga el archivo en una nueva carpeta.

Resulta importante remarcar que esto es tan solo un ejemplo, ya que es posible extraer cualquier información de un sitio web usando RPA.

## 2. Acceso al proyecto 📂

Para obtener el proyecto tienes dos opciones:

1. Clonar el repositorio utilizando la línea de comandos. Solo debes dirigirte al directorio donde deseas clonar el mismo e ingresar el comando:
   `git clone https://github.com/ignaciomajo/rocketbot_suite_1`

2. O puedes descargarlo directamente desde el repositorio en GitHub en el siguiente enlace:
   <p><a href="https://github.com/ignaciomajo/rocketbot_suite_1">https://github.com/ignaciomajo/rocketbot_suite_1</p>

   Esto te llevará a la siguiente pantalla, donde deberás seguir los siguientes pasos:
   
Esto descargará un archivo comprimido `.zip`, que podras alojar en el directorio que desees.

Para utilizarlo, solo debes cargar el archivo `robot.db`📄 a Rocketbot Studio 🚀


## 3. Demostración de funcionalidades y aplicaciones 📝


![pantalla_inicial](https://github.com/user-attachments/assets/1d3a6160-2775-43c2-9a00-98724c82aee4)



Esta es la pantalla inicial una vez ingresamos al menú del robot. Ejecutarlo, solo debemos presionar el botón marcado en un recuadro rojo que dice **Run**. Este ejecutará el robot con las variables predeterminadas.

A su vez, podemos ver que los pasos que sigue el robot están enumerados en el lado izquierdo encerrados en un recuadro verde, comenzando con el número 1. Esto nos permite entender la lógica que sigue el robot.

Cuando existen pasos dentro de otro, vemos como se produce una pequeña indentación en el panel, y el contador empieza desde el número 1 nuevamente, esto nos dice que dichos pasos, son *hijos* de un paso *padre*. Esto es de suma importancia para poder entender como el robot ejecuta cada actividad.

En este caso, el robot está diseñado para buscar productos que podríamos caracterizar como **"Suplementos Deportivos"**. 

![variable_buscar](https://github.com/user-attachments/assets/54bc2397-8518-41b6-ae1b-066a16dcdbbb)

Como vemos en este paso, se asigna a la variable **{producto}** el valor de 'whey protein' que será el artículo que buscará la automatización dentro de la página de Mercado Libre.

Si se desea que el robot busque otro producto, podemos hacer doble click en el comando, que abrirá la siguiente pantalla:

![cambio_variable](https://github.com/user-attachments/assets/1b8dc7fe-a0d8-44b1-955e-39ddd5562143)

Una vez aquí solo debemos cambiar el valor que se le asigna a la variable.

![abrir_archivo](https://github.com/user-attachments/assets/2e7df83a-72cc-471d-b2c1-81560bde04d5)


Una vez que el robot se asegura que ha encontrado la página, intentará buscar el archivo "suplementos_deportivos.xlsx" en la ruta correspondiente, aquí se debera modificar la ruta hacia donde tengamos el robot guardado. Pero es buena práctica dejar el archivo en la carpeta **resources**📁 dentro de **busqueda_mercadolibre**📁.

Si este no encuentra un archivo existente, creará uno nuevo con los siguientes encabezados de celda: **id, producto**(correspondiente a la búsqueda realizada), **nombre_articulo, precio**(en pesos), **descuento y link**(correspondiente a dicho artículo).


![while](https://github.com/user-attachments/assets/346aa100-e0fa-4b38-b013-20e1f8753473)

Aquí el robot comenzará a iterar sobre cada uno de los artículos encontrados en la búsqueda. De forma predeterminada, este extraerá la información de los primeros 10 artículos encontrados. 

![image](https://github.com/user-attachments/assets/fcf188c5-a231-47b9-9581-d292f2e58222)

Si se desea cambiar el numéro de artículos de los cuales queremos extraer información, solo se necesita hacer doble click en el comando **while** y cambiar el 10 por el número de artículos deseados.

*Nota: Mercado Libre muestra un máximo de 58 productos por página. Actualmente, el robot no cuenta con el comando para pasar de página.*


![paso_8_iteracion](https://github.com/user-attachments/assets/73a527b8-92b6-45b4-95d3-1fbbfa292d6f)


*Nota: El comando que se muestra en la imagen anterior (paso n°8 dentro del ciclo while), esta destinado a modificar la notación del precio ya que mi Excel está en inglés, puedes deshabilitar este comando si tu Excel se cuentra en idioma español.*

![guardado_archivo](https://github.com/user-attachments/assets/a3f24a06-76ca-4001-926f-4f22606c4ce7)


Una vez que el robot haya extraído la información de los artículos delimitados, guardará el archivo en la ruta correspondiende. Este comando tambien debe ajustarse para seleccionar la ruta donde este almacenado el robot. Se mostrará un mensaje en pantalla informando si el archivo se ha guardado o no correctamente.

*Nota: En caso de recibir un error, revisar el formato en que se ha escrito la ruta donde el robot debe guardar el archivo.*


El archivo Excel que contiene toda la información extraída quedará guardado en la carpeta **resources**📁 que se encuentra dentro de **busqueda_mercadolibre** 📁.


Luego, el robot envía un correo con el archivo creado.

**El correo electrónico y la contraseña han sido encriptados para conservar la privacidad de datos sensibles.**

![enviar_correo](https://github.com/user-attachments/assets/9fa8720c-2240-4e5e-91b1-ce065201befc)

Como vemos en esta imagen, primero se realiza la conexión al servidor de Gmail, utilizando las variables `{correo}` y `{pass}` que han sido encriptadas.
Después de validar que la conexión al servidor ha sido exitosa, se establece en la variable `{subject}` el asunto del correo, que también será utilizada a la hora de leer el correo (se mostrará posteriormente).
Como último paso de esta sección, se envia el correo al destinatario especificado (en este caso es igual al remitente), con el archivo de los artículos encontrados adjunto.

![listar_correos](https://github.com/user-attachments/assets/d9005be8-561e-4588-95b7-189d4df300f4)

Luego, se esperaran 20 segundos para dar tiempo a que el correo haya llegado, y se creará una carpeta llamada **descargas**📁 dentro de la carpeta **busqueda_mercadolibre**📁 en caso de que esta no exista.

![listar_correos2](https://github.com/user-attachments/assets/a6cfe6fb-25a1-4a8a-8c8a-2777bde4cab0)

Se obtendrán todos los correos no leidos que correspondan al asunto especificado anteriormente, y se iterará uno por uno descargando los archivos dentro de la carpeta que el robot acaba de crear.

Por último, se informa que la descarga fue exitosa, se informa que finaliza el proceso, y se mata el proceso Rocketbot y Excel para evitar procesos zombies.

## 4. Tecnologías utilizadas 🛠️

* `Rocketbot Studio (v.2025.01.06)`
* `Git and GitHub`
* `OBS` (screen recorder)
* `HTML`
* `Python`
* `Excel` (requerido para ejecutar el robot)

## 5. Agradecimientos 🏗️

Quiero agradecer a:

![Rocketbot](https://github.com/user-attachments/assets/5e61e12c-8fe3-4505-8463-0cf648ecda96)

#### Rocketbot

Por desarrollar la herramienta y proveer cursos gratuitos para aprender a utilizarla.


## 6. Desarrollador del proyecto 👷

![imagen-readme](https://github.com/user-attachments/assets/133bc743-0424-4120-a7a6-7245d2f28f8c)

**| Ignacio Majo | Data Scientist Junior | Junior RPA Developer |**


