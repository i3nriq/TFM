# Trabajo de fin de Master

Detección de outliers en transacciones de retiro de efectivo aplicando un modelo híbrido de ciencia de datos.

# Requisitos

El proyecto fue implementando en un ambiente en Google Colab, permitiendo la interacción, resguardo de resultados, portabilidad y fácil despliegue dentro de un ecosistema controlado. El lenguaje utilizado fue Python en su versión 3.9.16. en conjunto con las siguientes librerías y versiones de estas.

<table>
<thead>
  <tr>
    <th >Categoría</th>
    <th >Librería</th>
    <th >Versión</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td >Métricas</td>
    <td rowspan="3">sklearn</td>
    <td rowspan="3">2.2.0</td>
  </tr>
  <tr>
    <td >Selección de modelos</td>
  </tr>
  <tr>
    <td >Preprocesado</td>
  </tr>
  <tr>
    <td rowspan="2">Visualizaciones</td>
    <td >matplotlib</td>
    <td >3.7.1</td>
  </tr>
  <tr>
    <td >seaborn</td>
    <td >0.12.2</td>
  </tr>
  <tr>
    <td >Manipulación de arreglos</td>
    <td >Numpy</td>
    <td >1.22.4</td>
  </tr>
  <tr>
    <td >Manipulación de datos tabulares</td>
    <td >Pandas</td>
    <td >1.4.4</td>
  </tr>
  <tr>
    <td >Ambiente de trabajo</td>
    <td >Google</td>
    <td >2.0.3</td>
  </tr>
  <tr>
    <td >Exploración de datos</td>
    <td >pandas-profiling</td>
    <td >3.2.0</td>
  </tr>
</tbody>
</table>

## Parametros generales

### Ruta

Se requiere establecer el ecosistema previamente a la ejecución de las libretas, por lo que necesario configurar la ruta del ambiente dentro de Google Drive para la generación de los resultados dentro de cada fichero **.ipynb**. la variable **w_ruta_GD** almacena esta ruta.

```
w_ruta_GD='/content/drive/MyDrive/VIU/TFM/Desarrollo/'
```

### Carpetas

Es necesario contar en la ruta principal las siguientes carpetas, teniendo los permisos necesarios para almacenar los distintos ficheros a lo largo del a investigación del modelo hibrido para la detección de transacciones anómalas de retiro de efectivo.

| Ruta | Descripción |
| ---- | ----------- |
| Data | Almacena los archivos .csv con la informacion |
| Graficas | Por ejecucion se genera el set de graficos  |
| Log | Documenta en fichero la duracion por ejecucion  |
| Resultados | Ficheros de resumen por procesos  |

---

**Importante**

Las ejecuciones en cada ruta son identificadas tanto en carpeta como  ficheros, por la fecha de inicio con formato **YYYY-MM-DD hhmmss**

---

##### Data
Contiene los ficheros **.csv** y los informes que describen el set de datos anonimizado en dos secciones (entrenamiento y prueba) ambos en formato **.html**

##### Graficas
Es una carpeta que documenta la fase de experimentación de forma histórica, en listado cada ejecución por formado de fecha y hora, ejemplo de nombre de carpetas:

*   2023-04-08 220559
*   2023-04-08 212812
*   2023-04-08 210252
*   2023-04-08 205231
*   ...

##### Log
Contiene un unico fichero **log_ejecucion.txt** que documenta cada una de las experimentaciones realizadas de forma historica durante el proyecto:

```
2023-04-08 20:30:13 - 2023-04-08 20:31:26 [0:01:13]
2023-04-08 21:02:52 - 2023-04-08 21:04:28 [0:01:35]
2023-04-08 21:28:12 - 2023-04-08 21:29:19 [0:01:07]
2023-04-08 22:05:59 - 2023-04-08 22:06:56 [0:00:56]
```

##### Resultados
Almacena los ficheros con resultados para posibles análisis externos en formato **.csv** los cuales son:

| Archivo | Descripción |
| ---- | ----------- |
| PREDICCION | Set de anomalías detectadas en la fase de experimentación con el set de datos resumidos etiquetados |
| RESULTADO_IN | Inliers detectados en la fase de experimentación con el set de datos resumidos etiquetados |
| RESULTADO_IN_FINAL | Inliers detectados en la fase de despliegue con el set de datos anonimizado |
| RESULTADO_OUT | Outliers detectados en la fase de experimentación con el set de datos resumidos etiquetados  |
| RESULTADO_OUT_FINAL | Outliers detectados en la fase de despliegue con el set de datos anonimizado  |
| resultado_modelos | Resumen de variables obtenidas por iteración de hiperEparametros |

## Desarrollo del modelo

El proyecto consta de dos secciones, detalladas en ficheros con extensión **.ipynb**:

1.   Datos del modelo, *Seccion A - Datos.ipynb*
2.   Experimentación y desarrollo del modelo, *Seccion B - Modelo.ipynb*



### **Seccion A - Datos.ipynb**

Dicha sección incluye las siguientes secciones de la investigación. teniendo como entrada el fichero **DF_Anonimizado.csv** y obteniendo como resultado el fichero **DF_Resumido_etiquetado.csv**. para la fase de experimentación y desarrollo del modelo hibrido.

> 4.4.3.	Selección de la base de datos de partida

> 4.4.4.	Selección del dataset

#### Descripcion de datos

El modelo hibrido final implementa el set de datos original. **DF_Anonimizado.csv**, detallado en los siguientes dos informes.

[Descarga de informe datos de entrenamiento](https://github.com/i3nriq/TFM/blob/main/Data/RP_Data_Entrenamiento.html)

[Descarga de informe datos de prueba](https://github.com/i3nriq/TFM/blob/main/Data/RP_Data_Prueba.html)

### **Seccion B - Modelo.ipynb**

La fase de experimentación obtiene como entrada el fichero **DF_Resumido_etiquetado.csv**, para obtener el algoritmo y configuración óptima para el modelo hibrido final. El cual implementa el fichero original **DF_Anonimizado.csv** en su despliegue definitivo.

> 4.4.5.	Descripción de las características del dataset

> 4.4.6.	Limpieza de los datos

> 4.4.7.	Transformación de los datos

4.5.	Evaluación de Posibles modelos a utilizar

4.6.	Implementación de Algoritmos de ML

4.7.	Selección de hiper parámetros

> 4.7.1.	Implementación de GridSearch

4.8.	Resultados
> 4.8.1.	Evaluación de hiper parámetros

> 4.8.2.	Evaluación del modelo

> 4.8.3.	Optimización del modelo

4.9.	Creación de modelo hibrido

#### Iteraciones
Las iteraciones dentro del código implementan el concepto de reutilización de código encapsulando su función en la evaluación de hiperparametros permitiendo pasar de lo generala a lo especifico en dos iteraciones, para el enfoque basado en modelos.

1.   Selección de algoritmo
2.   Optimización

##### *Primera iteracion de parametros* **Seleccion de algoritmo**

Dentro del proceso de selección del algoritmo para el enfoque basado en modelos. se evalúan en la sección **4.8.1** los siguiente parámetros bajo el proceso de GridSearch detallado en la sección **4.7.1**.

```
param_grid = [
    [
        ["RF", {"n_estimators": 100, "max_depth": 500, "random_state": w_random, "oob_score":True}],
        ["IF", {"n_estimators": 10}],
        ["SVM", {"kernel": 'rbf',"nu": 0.05,"gamma": 0.1}]
    ],
    [
        ["RF", {"n_estimators": 1000, "max_depth": 100, "random_state": w_random, "oob_score":True}],
        ["IF", {"n_estimators": 100}],
        ["SVM", {"kernel": 'rbf',"nu": 0.1,"gamma": 0.9}]
    ],
    [
        ["RF", {"n_estimators": 5000, "max_depth": 50, "random_state": w_random, "oob_score":True}],
        ["IF", {"n_estimators": 500}],
        ["SVM", {"kernel": 'rbf',"nu": 0.5,"gamma": 0.5}]
    ],
]
```

##### *Segunda iteracion de parametros* **Optimizacion**

El proceso de GridSearch **4.7.1**, es reutilizado implementado el modelo seleccionado **SVM**, en esta fase para la búsqueda de la configuración óptima para el modelo final, del enfoque basado en modelos.

```
param_grid = [
    [
        ["SVM", {"kernel": 'rbf',"nu": 0.05,"gamma": 0.1}]
    ],
    [
        ["SVM", {"kernel": 'linear',"nu": 0.05,"gamma": 0.1}]
    ],
    [
        ["SVM", {"kernel": 'poly',"nu": 0.05,"gamma": 0.1}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.05,"gamma": 0.1}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.04,"gamma": 0.1}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.05,"gamma": 0.01}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.04,"gamma": 0.01}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.05,"gamma": 0.001}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.04,"gamma": 0.001}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.05,"gamma": 0.2}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.04,"gamma": 0.2}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.05,"gamma": 0.5}]
    ],
    [
        ["SVM", {"kernel": 'sigmoid',"nu": 0.04,"gamma": 0.5}]
    ],
]
```
