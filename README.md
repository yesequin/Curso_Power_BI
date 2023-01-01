# POWER BI

[Version en notion](https://www.notion.so/POWER-BI-27e00116efcc415fabb4a5fbefb2474d) ![notion](images_Power_BI/notion.PNG)

## INTRODUCCIÓN

Power BI:

Power BI es una solución integral de Business Intelligence, que proporciona una vista detallada de los datos más críticos dentro de una organización. Para hacerlo hace uso de su suite de negocio.

Business Intelligence (BI):

Es la habilidad de transformar los datos en información, y la información, en conocimiento, para agilizar el tiempo en cuanto a la toma de decisiones. Para hacerlo, necesitamos pasar por un flujo técnico.

Flujo de BI:

1. **ETL (Extract - Transform - Load):** Se refiere a la extracción, transformación y carga de los datos. Es un proceso requerido para convertir los datos en información. Algunas herramientas son:
    - Power Center
    - Integration Services
    - ODI (Oracle)
    
    Estas herramientas permiten establecer un flujo de procesos que ayuda a homologar y limpiar datos, para luego cargarlos en un data mar o data warehouse; lo que nos lleva al modelado de datos.
    
    ETL es un proceso intermedio entre las fuentes de datos originales de donde extraemos información, y el modelado de datos para su posterior análisis. ETL consta de tres pasos:
    
    1. Extract: Extraer datos desde cualquier fuente (operacionales internas o externas).
    2. Transform: Transformar, limpiar o enriquecer la información extraída sin modificar la fuente. Es en este paso que se ajustan los datos según el modelo de datos (el cual se diseña previo a la creación del ETL).
    3. Load: Cargar los datos ya transformados al modelo de datos.
2. **Modelado:** A través de relaciones creación de métricas e indicadores se establece el modelo de datos para responder a las preguntas de negocio, ya sea de forma diaria, mensual, semanal, etc. Algunas herramientas son:
    - Erwin Data modeler
    - Power Designer
- Reporting: Pasamos a la visualización de datos, reportes, dashboards y storyelling. Algunas herramientas son:
    - Power BI
    - Tableau
    - MicroStrategy

Suite de negocio de Power BI:

- Power BI Desktop: Herramienta de escritorio orientada al ambiente de desarrollo. Es donde empieza el flujo del proceso de una solución de BI con Power BI. Este se centra en el desarrollo del informe.
- Power BI Service: En la nube, con ambiente colaborativo (te permite establecer el delivery de la información). Esto se usa cuando ya tenemos el informe terminado en el Desktop.
- Power BI Mobile: para dispositivos móviles.

Componentes de Power BI:

- Power Query: para el proceso de ETL.
- Power Pivot: para el modelamiento con el fin de responder las preguntas de negocio.

Estructura de Power BI:

Existen distintas arquitecturas/planes que incorporan los componentes de Power BI de distinta manera.

- Power BI Free: Capa gratuita de Power BI
- Power BI PRO: Power BI Free + herramientas colaborativas.
- Power BI Premium: Power BI PRO con algunas mejoras.

Tipos de conexión:

- Importación: se copian del local. Es el tipo más común.
- Direct Query: los datos no se copian, cada interacción hace una consulta a la base de datos. Recomendable para datos que cambian con frecuencia.
- Live Connection o dinámica: lectura desde SSAS o desde un conjunto de datos de Power BI Service.
- Modelos compuestos: Combina las tecnologías de importación y Direct Query. Permite utilizar múltiples conjuntos de datos.
    
    Nota: siempre hay que conectarse a formatos tipo tabla, para mantener las buenas prácticas.
    

## POWER QUERY

Power Query es una tecnología de conexión de datos que permite detectar, conectar, combinar y refinar distintos orígenes de datos para satisfacer las necesidades de análisis.

¿Qué hace?: En escencia, hace un proceso de ETL en Power BI los datos para su posterior análisis. Ojo, el objetivo de Power Query no es analizar los datos.

En Power Query se habla de “Magia”, que es una colección de pasos para llegar a un resultado, que permite retroceder o avanzar sin modificar el origen de datos. Es similar a los macros de Excel.

Power Query maneja distintos tipos de datos que Excel. Al conectarse a una fuente de datos, crea diversos pasos aplicados (Applied Steps). Uno de estos pasos aplicados es Tipo Cambiado/Changed Type, que asigna un tipo de dato a cada columna.

Usar Power Query:

1. Seleccionamos la tabla que queremos procesar
2. Click en “Transformar datos”.

Pasos aplicados:

- Tipo cambiado: Le da un tipo de dato a cada columna de excel, es decir, recategoriza el tipo de dato de la información.

### Transformaciones

Las transformaciones más comunes que podemos realizar en Power Query son:

- Cambiar tipo de dato
- Anexar consultas
- Dividir columnas
- Combinar consultas
- Reemplazar valores

También podemos hacer combinaciones:

- Combinar binarios
- Agregar columnas
- Filtrar datos

De manera similar a como ocurre en las bases de datos relacionales donde cada columna tiene que tener bien definido su tipo apra evitar errores, en Power BI los tipos de datos senecesitan definir bien antes de utilizarlos.

Tips al transformar datos:

- Lo hacemos en el Editor de Power Query.
- Nos aparecen dos tablas: la original y otra con el error.
- Debemos eliminar el paso Tipo cambiado para darle a los datos el tipo de dato correcto. Al hacer esto toda la información en nuestra tabla se vuelve tipo texto.
- Tener en cuenta que en Power Query NO le podemos dar Ctrl + Z, por lo que hay que ser cuidadosos con las modificaciones que hagamos.
- Nos situamos al lado izquierdo de cada columna para darle el tipo de dato apropiado.
- Por cada acción, paso o transformación que hagamos se va a ir generando un paso aplicado, el cual contiene la información.
- Validamos en la otra tabla de errores si aun hay, ya que en la tabla original solo nos muestra las primeras 1000 filas. Esta tabla debe quedar vacía.
- Para pasar todos los cambios hechos en el editor le damos Inicio > Cerrar y aplicar.

Como transformar datos y pivotar tablas: clase #7

### Combinaciones

Combinar fuentes de datos es fundamental para poder cruzar la información y hacer un análisis con todos los datos necesarios.

Tipos de combinaciones en Power BI:

- Anexar: Permite unir dos o más tablas de manera “vertical” (es decir, se añaden filas).
    - Se recomienda que ambas tablas tengan la misma estructura. Si este no es el caso, el sistema añade al conjunto final los campos de todas las demás con valores nulos.
        - Principalmente significa que los nombre de las COLUMNAS deben 100% iguales
    - Anexar es similar a una operación UNION de SQL.
    - Los resultados pueden ser una nueva consulta o ser agregada a un paso de la existente.
- Combinar consultas: Nos permite tomar 2 tablas y cruzarlas mediante una columna en común.
    - Usualmente es utilizado para complementar información de una tabla.
    - Es el equivalente más cercano a la función JOIN del estándar SQL.
    - Los distintos tipos de combinaciones (y su equivalente en SQL) son:
        - Externa izquierda → LEFT JOIN
        - Externa derecha → RIGHT JOIN
        - Externa completa → FULL OUTER JOIN
        - Interna (INNER JOIN)
        - Anti izquierda (LEFT EXCLUSIVE JOIN)
        - Anti derecha (RIGHT EXCLUSIVE JOIN)
        
        ![Untitled](images_Power_BI/Untitled.png)
        
- Combinar binarios: permite extraer las tablas de los archivos mediante un proceso automatizado.
    - Usualmente utilizado mediante el conector de carpeta.
    - Es de especial utilidad cuando la fuente de información se encuentra demasiado fragmentada como para la operación de anexar.

Pasos para anexar:

1. Cargamos ambas tablas.
2. Transformar datos > transformar datos.
3. Seleccionamos la tabla a la que le queremos agregar datos (tabla principal).
4. Inicio > anexar consultas > anexar consultas
5. Elegimos la tabla de la cual va a salir la información nueva a la tabla principal.
    1. Verificamos antes que la columna que tiene la información que queremos agregar tenga EXACTAMENTE el mismo nombre que la columna en la tabla principal.
6. Con esto se crea un paso aplicado a la derecha llamado consulta anexada.

Pasos para combinar consultas:

1. Cargamos ambas tablas
2. Transformar datos > transformar datos
3. Elegimos la tabla donde queremos que esté toda la información
4. Inicio > combinar > combinar consultas > combinar consultas para crear una nueva. Esto quiere decir que el resultado va a terminar en una nueva consulta.
5. La tabla de arriba es donde queremos que esté toda la información y la de abajo es la tabla con la que queremos cruzarla.
6. Para cruzarla tenemos que seleccionar un campo en común que no necesariamente tiene que tener el mismo nombre. La ventaja de este tipo de combinaciones es que puedes seleccionar más de un campo en común en caso de que lo requiera.
7. Elegimos el tipo de combinación
8. Aceptar. Con esto se genera una nueva consulta (tabla) el cual tiene todas las columnas de la tabla principal y una columna expandible donde le podemos decir que valores queremos ver.

Pasos para combinar binarios:

1. Cargamos la carpeta que contenga los excel que necesitamos. Esta opción va a identificar todos los archivos que tienes en la carpeta.
2. Flecha al lado de combinar > combinar y cargar. Con esto generamos un paso automático la extracción de todos los archivos que yo quiera a partir de un parámetro constante en cada uno de los files.
3. Aceptar. De forma automática estamos extrayendo y anexando, es decir, voy a tener como resultado final una consulta el cual va a tener la información ya anexada de forma automática.

## MODELADO DE DATOS

El modelado de datos en Power BI consiste en realizar análisis complejos entre varias tablas conectadas por un campo en común. Este se realiza con Power Pivot.

El modelado de datos se refiere a transformar los datos a un formato que haga las labores de reporting más sencillas.

![Untitled](images_Power_BI/Untitled%201.png)

### Relaciones

Las relaciones se refieren a la correspondencia que hay entre tablas.

Cuando hablamos de relaciones entre tablas, tenemos 2 conceptos claves:

- Llaves primarias (Primary Keys): definen la clave principal de la tabla. No pueden contener valores nulos ni duplicados.
- Llaves foráneas (Foreign Keys): es una columna, o conjunto de columnas, que contiene un valor que hace referencia a una fila de otra tabla.

Tipos de relaciones:

- 1 a 1 (1-1): ambas tablas se conectan con sus llaves primarias.
- 1 a muchos (1-*): cuando se conecta una llave primaria con una llave foránea de otra tabla. Es la que se debe buscar en Power BI.
- Muchos a muchos (* - *): cuando ambas tablas se relacionan por sus llaves foráneas (ninguna de las columnas tiene valores únicos). Se recomienda evitar este tipo de relación a menos que sea estrictamente necesario, porque te puede dar un valor completamente irreal, ya que Power BI está diseñado para buscar relaciones 1-*.

Por defecto, cuando nosotros cargemos tablas con información dentro de Power BI esta va a buscar crear relaciones de forma automática. Esto se puede dejar activo o desactivar, pero siempre es recomendable validar todas las relacionea que se generan.

### Filtros

Los filtros se refieren a incluir (o no) ciertos registros al consultar una base de datos, en función de ciertos criterios.

### Modelos de datos: modelo de estrella.

En cuanto a Power BI, el modelo más eficiente es el de estrella, debido a que resulta en tablas con relaciones uno a muchos. El modelo de estrella se compone de:

- Tabla dimensión (de búsqueda): tiene descripciones de la tabla de hechos. Las dimensiones añaden contexto a los hechos. Por ejemplo: fehcas, ubicación, etc.
- Tabla de hechos (transaccionales o fact): tiene el grueso de la información. Por ejemplo: ventas, subscripciones, órdenes, etc.

Siempre vamos a tratar de tener un modelo estrella: una o más tablas de hechos en el centro  y tablas de búsqueda o de dimensión alrededor, todo ello generando la relación uno a muchos.

Lo necesitamos poque si cargamos un único tablón de información, se tendrá un mal rendimiento en volúmenes grandes y redundancia de datos.

### Motor del modelo de datos

Es lo que está detrás del modelo de datos dentro del Power BI. Su nombre es Vertipaq y se encarga de todas las operaciones de análisis de datos (DAX). Además, utiliza tecnología in-memory que provee un elevado desempeño para almacenamiento y consulta de datos.

También permite ciclos de desarrollos cortos, esto frente a su uso del usuario de negocio.

## LENGUAJE DAX

Data Analysis Expression o DAX (lenguaje de expresiones analíticas de Power BI, NO es un lenguaje de programación), nos permite crear fórmulas analíticas. Fue creado para manipular un modelo de datos tabular. Originalmente, fue generado como extensión de excel. Es una colección de funciones y operadores que pueden ser utilizados en expresiones que permiten calcular uno o más valores.

Podemos encontrar este lenguaje en en PBI, Excel y SSAS Tabular.

### Ventajas

- Está pensado para alcanzar mayor cantidad de usuarios BI
- Posee una menor curva de aprendizaje para analistas de datos.
- Aprovecha el conocimiento de trabajar con fórmulas de Excel, añadiéndole más capacidades como:
    - Relaciones de navegación
    - Cálculo dinámico de dimensiones.
    - Manejo de dimensiones de tiempo (Time Intelligence).

### Formato general de DAX

‘*Nombre de tabla*’[*Nombre de columna*]

El nombre de la tabla puede ser omitido al usarse en oclumnas calculadas, más no se recomienda hacerlo por cuestiones de ambiguedad.

### Qué podemos generar con DAX:

- Columnas calculadas: crea nuevas columnas en el modelo de datos. Es un método para conectar tablas con múltiples columnas clave.
- Tablas calculadas: crea una tabla derivada de otra tabla.
- Medidas: Es lo más usado en Power BI. Crea cálculos dinámicos guardados en memoria. Son más eficientes que las columnas calculadas ya que ocupan menos espacio. Soportan la inteligencia de tiempo. Lo ideal es que como podemos crear medidas donde sea, lo hagamos de forma ordenada.
    
    Las medidas (y DAX) funcionan a nivel de columnas y tablas completas, desapareciendo el contexto de filas.
    

### Funciones DAX:

[Funciones DAX](https://interactivechaos.com/es/recursos-educativos/funciones-dax)

### Pasos:

1. Cargamos nuestra(s) tabla(s)
2. Generamos las relaciones
3. Clic en datos > Seleccionamos la tabla que queremos ponerle la medida > Herramientas de tablas > donde:
    
    ![Untitled](images_Power_BI/Untitled%202.png)
    
    - Nueva columna → Columna calculada
    - Nueva tabla → Tablas calculadas
4. Escribimos la fórmula.
5. Clic en el chulito

### Pasos para crear medidas:

1. Inicio > Especificar datos. Permite ingresar data de forma directa a Power BI.
2. Le ponemos el nombre de la tabla. Esta tabla se crea para que sirva de repositorio o almacén y dentro de ellas.
3. En informe > campos > clic derecho a la tabla creada anteriormente > Nueva medida
4. Escribimos las fórmulas.
5. Clic en el chulito
6. Esto crea la información en memoria y se ejecuta cuando creemos alguna visualización.

**¿Qué diferencia hay en crear una nueva tabla desde “Herramientas de tablas>nueva tabla” (cómo se creo la de calendario) e “inicio>Especificar datos” (como se creo la de medidas)?:** La primera es para generar una nueva tabla a partir de DAX y la segunda para insertar datos de forma directa generando un origen tipo Json

### Agregación CALCULATE

La medida conocida como la madre de todas las funciones DAX es `CALCULATE`.

Las medidas DAX se caracterizan por usas agregaciones. `CALCULATE` es una agregación que permite “modificar el contexto de filtro”, así como crear un contexto de fila dentro de nuestros cálculos, iterando fila a fila.

La función `CALCULATE` recibe 2 parámetros como mínimo:

1. La expresión que queremos filtrar
2. Filtros que queremos aplicar.
    1. Si queremos hacer un doble filtro de la misma columna, podemos hacerlo de la siguiente estructura:
    
    ```sql
    [Nombre de medida] = CALCULATE([expresión],[nombre columna] IN {["filtro1","filtro2"})
    ```
    

### Inteligencia de tiempo

Hace referencia a las técnicas, herramientas y metodologías que nos permiten analizar nuestras medidas minuciosamente a través del tiempo. Está presente en todas las soluciones de inteligencia de negocios como **punto de partida para explorar la información**.

La inteligencia de tiempo permite analizar la evolución de nuestras medidas en tiempo, monitorear el crecimmiento de manera detallada y realizar proyecciones.

Para poder implementar inteligencia de tiempo dentro de nuestras soluciones de BI necesitamos como requisito:

- Crear una tabla calendario. Es una tabla de manera continua sin que falta ni un solo día entre las fechas. Esta tabla tiene todo el rango de fechas existentes en nuestro modelo (o al menos las necesarias para el análisis). Funciona ocmo una nueva dimensión para nuestro modelo.

Cómo crear una tabla calendario:

1. Cargamos nuestros excel.
2. Creamos las respectivas relaciones
3. Datos > Nueva tabla. Donde El nombre de la tabla puede ser calendario:
    
    Calendario = CALENDARAUTO()
    

Existe otra manera usando Power Query:

1. Vamos a Modelo > Obtener datos > Consulta en blanco
2. Clic derecho en la parte izquierda donde dice el nombre de la consulta (por lo general es Consulta1) > Editor avanzado
3. Borramos el texto que nos aparezca
4. En los documentos hay uno tipo txt llamado Tabla Calendario. Este es un script desarrollado en lenguaje M o Matchapp (lenguaje de Power Query). Seleccionamos todo el código, copiamos y pegamos en el editor avanzado.
5. Validamos que salga el mensaje “no se han detectado errores de sintaxis. > listo
6. Aquí tenemos la oportunidad de generar una tabla con fechas continuas a partir de la fecha de inicio y fin que coloquemos.
    1. FYStartMonth es en caso de que queramos trabajar con un calendario fiscal (1)
7. Clic en invocar.
8. Cambiamos el nombre
9. Cerrar y aplicar.
10. Generamos la relación entre un campo en común.
11. Esta opción te permite crear una tabla calendario con más columnas.

Después de creada, podemos utilizar nuestras agregaciones o funciones de tiempo.

Funciones:

[Funciones de inteligencia de tiempo (DAX) - DAX](https://learn.microsoft.com/es-mx/dax/time-intelligence-functions-dax)

- Devuelven una sola fecha: `FIRSTDATE`, `LASTDATE`, `STARTOFMONTH`, `STARTOFQUARTER`, `STARTOFYEAR`, etc.
- Devuelven una tabla de fechas: `PARALLELPERIOD`, `DATEADD`, `DATESBETWEEN`, `SAMEPERIODLASTYEAR`, `DATESYTD`, etc.
- Evalúan expresiones a lo largo de un periodo de tiempo: `TOTALMTD`, `TOTALQTD`, `TOTALYTD`.
- Dan apoyo en análisis financieros: `OPENINGBALANCEMONTH`, `OPENINGBALANCEQUARTER`, `CLOSINGBALANCEQUARTER`, `OPENINGBALANCEYEAR`, `CLOSINGBALANCEMONTH`, etc.

Cómo empezar a crear las funciones:

1. Las buenas prácticas frente al uso de DAX nos sugieren crear una nueva tabla con todas las medidas que creemos: nueva página (si ya tenemos datos en otras) > Informe > inicio > especificar datos (es bueno llamarla Tabla_medidas) > cargar.
2. A la derecha en campos > clic derecho en la tabla creada en el paso 1 > Nueva medida.
    1. Hay 2 tipos de medidas:
        1. Medida implícita: El cálculo implícito implica, colocar una columna de una tabla, directamente en un visual e indicar la operación.
        2. Medida explícita: La medida explícita ya implica trabajar con DAX (definida por el usuario que lo creó) y nos permite realizar cualquier cálculo. Es recomendable usar este tipo de medida porque las podemos emplear en códigos más complejos.

### Iteradores X

Las funciones iterativas son especiales dentro de DAX. Nos permiten crear operaciones a nivel de fila y calcular el resultado. A las funciones iterativas también se les conoce como funciones X.

Algunas de estas funciones son: 

- SUMX: permite multiplicar dos valores dentro de una misma fila y sumar los resultados de cada multiplicación.
- AVERAGEX
- MAXX
- MINX
- STDEVX.S
- PERCENTILEX.EXC
- CONCATENATEX

Pasos para SUMX:

1. Cargamos nuestro archivo
2. Inicio > Especificar datos. Esto es para crear una tabla de medidas (buenas prácticas). Le ponemos de nombre Medidas.
    1. La tabla de medidas es simplemente un almacén de fórmulas, por lo que no va relacionado a nada.
3. En campos > clic derecho en nuestra tabla de medidas > nueva medida.
4. Si al crear las medidas no podemos llamar una columna es porque necesitamos de una agregación (agregar una medida de la columna de forma explícita).
5. Para crear el SUMX:
    
    Nombre de medida = SUMX(*tabla sobre la cual vamos a iterar*, *expresión*)
    

## STORYTELLING

El Storytelling es el arte de saber contar una historia. El data storytelling ayuda a captar la atención del usuario y a que él mismo descubra nueva información mediante la interactividad.

Una metodología dentro del data storytelling es SCRAP, que se refiere a:

Spaced: Espaciado. Respetar espacios tanto dentro del gráfico como entre visualizaciones.

Contrast: Contraste. Aplicar colores contrastantes para destacar algo en vez de tener informes monocromáticos ayudará a enfocar la atención del usuario en donde queremos.

Repeat: Repetición. Aplicar de manera consistente tipografías, esquemas de diseño, tamaño de fuente, etc.

Aligned: Alineado. Las visualizaciones deben estar ordenadas y alineadas. Un informe desordenado puede distraer la atención del usuario.

Proximity: Proximidad. Los objetos visuales que estén relacionados deben estar próximos entre sí.

SCRAP está relacionado con los principios de diseño de Gestalt.

Elegir la visualización correcta es una de las partes más importantes de nuestro proyecto. Una buena visualización permite comunicar nuestras ideas o descubrimientos a un público más amplio y de forma dinámica.

### Tips para una buena visualización

- Menos es más
- Los colores son importantes, úsalos bien.
- Mantén tus elementos bien alineados.
- No siempre es bueno mostrar todo en una cifra.
- Muestra solo información relacionada.
- Una mala elección de un visual puede ocasionar que la información no se transmita de manera correcta, llegando incluso a tergiversar el entendimiento de la misma.

### Pasos por hacer al crear la visualización

Para gráfico de columnas:

- Dejar el tamaño de los valores en el eje X y Y en el mínimo
- Desactivar la opción de concatenar etiquetas
- Quitar el título.

Para gráfico de mapa:

- El tamaño de la burbuja lo determina el valor que le pongas en tamaño burbuja
- Es bueno poner algo en el espacio de etiqueta para que se entienda a que lugar del mapa pertenece.
- Podemos aumentar el tamaño de las burbujas para que se entienda a simple vista cual es el más grande. (Formato > burbujas > tamaño)

Para gráfico circular:

- Siempre es bueno tener activada la etiqueta de detalle (formato > Etiquetas de detalle > Activar) para que sea más fácil identificar qué cosa tiene más o menos.
- Este gráfico solo debe ser usado cuando evaluamos 2 categorías o máximo 3.
- Se podría reemplazar por un gráfico de barras agrupadas.

Para gráfico de barras:

- Puedo agregarle más información a la barra sin saturarla poniendo otro valor de columna donde dice Información sobre herramienta, para que aparezcan más datos al pasar el mouse por ahí (tooltip básico).

Para gráfico de dispersión:

- Es bueno desactivar la leyenda y activar Etiqueta de categorías en la parte de dar formato a objeto visual.
- Para la parte de Analytics nos vamos a Agregar más análisis a sus objetos visuales. Aquí podemos:
    - Poner línea de promedio: Le damos en agregar línea y cambiamos la medida que se está evaluando donde dice Serie.
- Existe un eje de reproducción

Para gráfico de líneas:

- Para que nos aparezca la información mes a mes y no semestral en el eje x: Formato > eje x > Tipo > Categórico
- Podemos agregarle también la parte de analytics que agregamos en la gráfica de dispersión más mínimos, máximos, etc.
- Si los datos son tipo continuos en el eje x aparecerán más opciones de analytics, como por ejemplo previsión (forecast o predicción) el cual predice mediante un algoritmo de suavizamiento exponencial el cual funciona sobre series temporales.
    - Los puntos significan lo que el eje x esté manejando (meses, años, etc)
    - Podemos omitir cierta cantidad de información (puntos)
    - Tener en cuenta el cálculo de intervalo de confianza
    - Esta predicción va a estar acompañada de su límite inferior y superior.

## CREAR UN INFORME CON POWER BI

Un informe es una colección de páginas segmentadas por un tema particular, que ofrece una vista resumida e interactiva con la capacidad de filtrado según las necesidades del usuario.

Destacamos 3 herramientas de Power BI para la creación de informes:

- Marcadores: guardan la configuración de la vista actual del informe.
- Botones: permite activar una acción en el informe.
- Tooltips Avanzados: permite mostrar detalle adicional en las visualizaciones.

### Pasos

1. Cargamos el documento.
2. Validamos la carga revisando cada columna de cada tabla subida. Si alguna tiene mal la información podemos cambiarla usando Power Query
3. Revisamos el modelado
4. Creamos la tabla de tiempo (calendario).
5. Creamos la relación entre la tabla de tiempo y el resto de mis datos.
6. Creamos una tabla que almacene nuestras medidas (Tabla_Medidas) usando la opción de especificar datos.
7. Creamos las medidas que necesitemos.
8. Eliminamos la Columna1 que se creo automáticamente en la tabla_Medidas.

A partir de acá podemos empezar con la visualización:

1. Ponemos el título. Inicio > Cuadro de texto > agrandamos el tamaño de la letra > Ponemos la letra en negrita.
2. Agregramos los gráficos pertinentes y seguimos los pasos por hacer al crear la visualización
3. No olvidar agregar indicadores (tarjetas)
4. Es recomendable poner el logo de la empresa para que se sientan identificados con la reporteria:
    1. Insertar > Imagen
    2. Ponerlo al lado del título
5. Es importante usar los colores oficiales de la empresa:
    1. Ver > Temas. Hay varias opciones y también te permite personalizar el tema.

Ahora podemos modificar el tipo de interacción:

1. Seleccionamos la visualización que va a hacer de filtro > Formato > Clic en Editar interacciones
2. Con esto van a aparecer 3 opciones en las demás visualizaciones, excepto en la que has seleccionado:
    1. Filtro: Va a filtrar o acotar la información a la categoría seleccionada.
    2. Resaltar: Resalta la categoría seleccionada
    3. Ninguno: va a eliminar cualquier tipo de interacción.
    
    Es recomendable dejar todas las visualizaciones en filtro. 
    

Podemos crear un Tooltip avanzado o de página completa:

1. Es mejor abrir una nueva página
2. Vamos a Informe > Visualizaciones en la parte derecha > Dar formato a la página del informe > Información de la página > Activamos esta opción:
    
    ![Untitled](images_Power_BI/Untitled%203.png)
    
3. Vamos a Informe > Visualizaciones en la parte derecha > Dar formato a la página del informe >Configuración del lienzo > Elegimos la opción Información sobre herramientas. Esto le da un tamaño mucho menor
4. Creamos una visualización 
5. Ocultamos la página
6. Vamos a la página principal donde están el resto de gráficos y elegimos uno que tenga información a la cual me interese ver más a detalle (el detalle está en la página oculta).
7. Vamos a visualizaciones > Dar formato a su objeto visual > General > Información sobre la herramienta >
    1. Tipo: Página del informe
    2. Página: Elegimos la página que ocultamos.
    
    Esto va a ser dinámico a cada categoría que queramos visualizar.
    

## ANALÍTICA DE DATOS CON POWER BI

Es una fase después de las fases de ETL, modelamiento y visualizaciones.

Con este podemos hacer gráficas y agregarle líneas de promedio, mínimos, máximos, promedios, tendencia, predicciones, etc.

Power BI es una herramienta de Bussines intelligence con la posibilidad de integrar herramientas de Business analytics, en este caso como el lenguaje de programación en Pyhon y R

Para crear visualizaciones de Script de R usamos esta opción

![Untitled](images_Power_BI/Untitled%204.png)

Le damos la opción de habilitar, arrastramos los valores que queramos ver y pegamos el script.

## POWER BI SERVICE

Usamos Power BI Service a la hora de compartir nuestro informe con el equipo. Este es un SAAS (Software as a Service). Un SAAS es un método para ofrecer servicios de IT mediante la nube, con un costo de operación.

Power BI Service es una aplicción web parte de Microsoft 365, que permite visulizar y desarrollar (de manera limitada) informes, así como estableces un entorno colaborativo.

La parte de diseño y construcción está muy limitada, por lo que es recomendable usar el Power BI Desktop para ese tipo de cosas.

Además, es posible descargar tu informe

### Licenciamiento

Requerimiento mínimo: una cuenta de Power BI

Hay 2 niveles de Power BI Service:

Free:

- Permite subir, crear y editar informes de manera pública
- No recomendado para entorno empresarial.

Pro:

- Nos permite establecer el ambiente colaborativo de manera segura y privada.

Pasos para subir el informe a Power BI Service:

1. Iniciamos sesión.
2. Abrimos nuestro informe
3. Inicio > publicar
4. Podemos seleccionar el destino “mi área de trabajo”, que es una carpeta que solo te pertenece a ti.

Una vez hayamos subido nuestro informe, vamos a Mi área de trabajo en Power BI Service

![Untitled](images_Power_BI/Untitled%205.png)

En este apartado vamos a ver 2 reportes del mismo informe, ya que estamos subiendo 2 cosas: la primera es la parte de la reportería (ícono azul); y la segunda es el dataset o conjunto de datos (ícono naranja, pero es mejor editarlo en Power BI Desktop).

### Áreas de trabajo

Las áreas de trabajo en Power BI Service son los lugares para colaborr con colegas para crear colecciones de paneles, informes e informes paginados. En el área de trabajo se define al conjunto de usuarios que tienen acceso a datos, informes y paneles específicos. Es posible asignar roles específicos, separar áreas de la organización y generar aplicaciones o aplicaciones de plantilla.

No podemos establecer un entorno colaborativo en “Mí área de trabajo”, po lo que tenemos que crear una nueva. Para establecer un ambiente colaborativo tanto tu como la persona que va a ver el reporte necesariamente va a tener que tener un licenciamiento propio.

## CREAR UN DASHBOARD

En Power BI un Dashboard tiene un concepto distinto. Un dashboard es un elemento de una sola página, donde encontramos los principales indicadores de nuestra empresa. En un dashboard o panel podemos visualizar datos de distintos conjuntos de datos, sin que estos tengan una relación entre sí. Los dashboards son exclusivos de Power BI Service en la nube.

Una de las ventajas del dashboard es que podemos ir a otros reportes que tienen dataset completamente distintos y podemos anclar las visualizaciones (pero tenemos que publicar el reporte).

El dashboard se graba de manera automática.

Cómo crear un dashboard:

1. Nos vamos a Power BI Service e iniciamos sesión
2. Áreas de trabajo > mi área de trabajo
3. En la parte superior le damos clic en Nuevo > Panel
4. Vamos a Power BI desktop y abrimos el informe que queramos hacer dashboard y validamos que estemos en la cuenta de usuario correcta
5. Le damos en publicar
6. Vamos a nuestra área de trabajo. Ahí encontraremos el dataset y los informes.
7. Abrimos los informes con las visualizaciones que queramos incluir en nuestro dashboard > Buscamos el ícono anclar y le damos clic > Elegimos nuestro dashboard > Aceptar.
    
    ![Untitled](images_Power_BI/Untitled%206.png)
    

Configurando el dashboard:

Podemos agregar títulos, vídeos, imágenes, contenido Web.

- Agregar un título:
    1. Editar > Añadir un ícono > Cuadro de texto. Es recomendable aplicar negrita, centrar y aumentarle el tamaño.
    2. Podemos mover y ajustar el tamaño del cuadro de texto a gusto.
- Mover una visualización dentro del panel:
    1. Buscamos los 3 puntos en la parte superior derecha > Sostenemos > arrastramos
- Darle tema de panel:
    1. Editar > Tema del panel
- El dashboard a diferencia del informe te da la facultad de tener una vista movil ya hecha:
    1. Editar > Diseño para móviles
    2. Para ver el dashboard de ese modo en el celular hay que descargar la aplicación Power BI movil (es gratuita y toca loguearse con la misma cuenta).

### Puerta de enlace con Power BI Service

Una puerta de enlace (o gateway) es un componente que facilita el acceso a los datos de una red. Funciona como controlador de acceso, recibiendo solicitudes de conexión y concediéndolas solo cuando estas cumplen ciertos criterios.

En Power BI se usa las puertas de enlace para actualizar automáticamente nuestros reportes.

Tipos de puesta de enlace:

- Modo personal: solo un usuario puede conectarse a las fuentes de datos, sin que se puedan compartir.
- Modo múltiple: permite que múltiples usuarios se conecten a múltiples fuentes de datos locales.

Actualizar un reporte

Se puede hacer de manera manual en Power BI Desktop, dándole clic al botón Actualizar; pero podemos automatizar esto mediante la puerta de enlace de Power BI.

Automatización:

1. Elegimos el dataset que queremos automatizar (tiene el logo naranja)
2. Actualizar > Programar actualización
3. Es importante validar las credenciales: Credenciales de origen de datos > Clic en editar credenciales > Iniciar sesión
4. Actualización programada > Activar
    1. Definimos la frecuencia de actualización. Por lo general esta actualización se suele dar por las noches o la madrugada