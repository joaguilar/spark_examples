# Instalación usando Conda

## Requisitos

* Python 3.8+ 
* Conda
* Java 8+ 
* Scala 2.13+

### Versiones utilizadas:

Para el presente ejemplo se utilizaron las siguientes versiones de los pre-requisitos:

```
❯ conda --version
conda 4.12.0
❯ python --version
Python 3.12.2
❯ java --version
openjdk 17.0.3 2022-04-19
OpenJDK Runtime Environment Temurin-17.0.3+7 (build 17.0.3+7)
OpenJDK 64-Bit Server VM Temurin-17.0.3+7 (build 17.0.3+7, mixed mode)
❯ scala --version
Scala code runner version 3.4.2 -- Copyright 2002-2024, LAMP/EPFL
```

## Crear el ambiente

Creamos el ambiente usando conda, en este caso vamos a usar la version de python 3.12.2.
```
$ conda create --prefix ./spark-env python=3.12.2
```

## Activar el ambiente e instalar dependencias

```
$ conda activate ./spark-env
```
Dependencias:

```
pip install jupyter
pip install py4j
pip install pyspark
pip install findspark
```

## Instalar Spark

Obtener la versión más reciente de Spark de: [Downloads | Apache Spark](https://spark.apache.org/downloads.html)

Para estos ejemplos usaremos la versión 3.5.1.

Descomprimir el archivo `spark-3.5.1-bin-hadoop3.tgz` y guardar la ubicación.

## Variables de ambiente:

Fijar las siguientes variables de ambiente necesarias para ejecutar programas de Spark:

**Recuerde substituir |path| por la ruta apropiada para su instalación.**

```
export SPARK_HOME=|path|/spark-3.5.1-bin-hadoop3
export PATH=$SPARK_HOME:$PATH
export PYTHONPATH=$SPARK_HOME/python:$PYTHON_PATH
export PYSPARK_DRIVER_PYTHON='jupyter'
export PYSPARK_DRIVER_PYTHON_OPTS='notebook'
export PYSPARK_PYTHON=python3
```

## Ejecutar Jupyter Notebook

### Opción 1: Directorio de Spark:

Ejecutar el Jupyter notebook en el directorio `$SPARK_HOME/python`:

En mi caso `$SPARK_HOME/python` es `~/Documents/Development/spark/spark-3.5.1-bin-hadoop3/python`

```
$ cd ~/Documents/Development/spark/spark-3.5.1-bin-hadoop3/python
$ jupyter notebook
```

Probarlo ejecutando:

```
import pyspark
```

### Opción 2: Utilizar findspark

Ejecutar el Jupyter notebook en el ambiente creado anteriormente, pero pasarle la ubicación a findspark del directorio `$SPARK_HOME`.

En mi caso `$SPARK_HOME` es `~/Documents/Development/spark/spark-3.5.1-bin-hadoop3`

```
import findspark
findspark.init('~/Documents/Development/spark/spark-3.5.1-bin-hadoop3')
import pyspark
```
Y deberia de poder cargarlo.

## Notas

Nota: En caso que de un error sobre `py4j`, tratar de reinstalarlo.
