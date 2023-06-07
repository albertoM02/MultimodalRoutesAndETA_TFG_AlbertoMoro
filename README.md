# MultimodalRoutesAndETA_TFG_AlbertoMoro
Repositorio del TFG realizado por Alberto Moro Carrera en la UC en el que permite obtener la ruta ideal entre dos coordenadas y su ETA, usando transporte multimodal.

Tener en cuenta que el proceso de generación de los set de datos en varias ocasiones ha requerido de transoformaciones manuales con herramientas como Excel, para eliminar columnas, reordenarlas, cambiar su nombre, juntar dos o más datasets en uno solo ... Por lo que el formato de salida de un paso puede no ser exactamente el esperado en el paso siguiente. Sin embargo, en la carpeta "SistemaYVisualizacion" se incluyen los datasets resultantes para permitir su ejecución y observar la versión final.

Tener también en cuenta que hay algunas librerías no nativas que se debe instalar para la ejecución del código y cuya instrucción de instalación se encuentra en el código y en algunos casos podría estar comentada. Descomentar si no estuviera previamente instalada o diera error. 

Se ha desarrollado con la distribución "Anaconda" sobre Python 3.9.13

Resumen de las carpetas:

00.Datasets: Contiene las versiones finales de los Datasets utilizados por el despliegue del sistema.

01.ReduceDatasetValues: Contiene el código necesario para reducir el set de datos original a uno de coordenadas transitables manejable, en primer lugar realiza una reducción aleatoria hasta una cantidad manejable y posteriormente elimina las coordenadas que hayan quedado muy cercanas para favorecer una dispersión equivalente.

02.GenerarDatasetEntrenamiento: A partir del conjunto de coordenadas, genera todos los tramos posibles y en base a varios factores con un grado de variabilidad y casos extremos ficticios, genera un histórico ficticio con datos sucios para su posterior tratamiento y entrenamiento.

03.AnalizarYLimpiarDataset: A partir del conjunto de tramos sucios, realiza el análisis del conjunto de datos y sus posterior limpieza, para generar un set de datos de entrenamiento limpios.

04.EntrenamientYEvaluacionModelos: Prueba varios algoritmos predictivos y obtiene el valor de varias métricas de análisis sobre los mismos para evaluar cuál se adapta mejor a nuestro problema a resolver.

05.Estadias: Realiza el set de datos de entrenamiento de las estadias y evalua el algoritmo que mejor solucione el problema, igual que se habñia realizado previamente.

06.SistemaYVisualizacion: Posee el sistema completo que se utiliza para generar las rutas y el cálculo de etas, también se encuentra un archivo que permite realizar la visualización de las rutas en PowerBI.
  - En primer lugar genera los modelos con los algoritmos que previamente se seleccionaron como los mejores para realizar las predicciones posteriormente.
  - A continuación, obtiene los climas en todas las coordenadas de nuestro dataset de coordenadas transitables.
  - Posteriormente, obtiene todos los tramos posibles entre estos puntos.
  - Para continuar, realiza la limpieza de estos tramos para dejar una cantidad manejable pero con cierta precisión a nivel internacional (unos 15 checkpoints para rutas de     15000 km de distancia) que sirven para describir una ruta en el mapa. El valor escogido parte del menor que lo deja conexo.
  - Realiza las predicciones de ETA en tiempo real de todos los tramos resultantes.
  - Suma el ETA de las estadías a los tramos donde se realiza un cambio de medio de transporte en función de un peso indicado manualmente.
  - Obtiene la coordenada de partida y de destino en función de dos coordenadas indicadas manualmente.
  - Se calcula la ruta óptima y el ETA estimado de la misma.
  - Se extrae la ruta a un CSV que utliza el modelo generado en PowerBI.
  - Se realiza una visualización del grafo resultante de todos los tramos (Atención, tarda unos 20 minutos en ejecutarse)
 Se requiere la herramienta PowerBI para poder visualizar posteriormente la ruta obtenida y almacenada en un CSV.
 
 Alberto Moro Carrera



