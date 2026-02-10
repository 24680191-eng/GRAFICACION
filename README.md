# GRAFICACION

# Sistema opoperativo 
- windows - wuawei notebook 14
  
# Instalacion de Blender 
1. lo primero que realice fue prender la computadora
 
2.  fui al sitio oficial de blender : https://www.blender.org/download/
   
   <img width="2063" height="1673" alt="image" src="https://github.com/user-attachments/assets/4dec2521-5206-4712-bd2d-2b4169c87b57" />
   
3.Descargar la versión recomendada para el sistema operativo Windows.

4.Ejecutar el archivo descargado con extensión `.exe`.

5. Seguir las instrucciones del asistente de instalación, manteniendo las opciones predeterminadas.
   
6.Finalizar el proceso de instalación

7.Abrir Blender desde el menú de inicio para comprobar su correcto funcionamiento.

8.ya estando en la appm BLENDER 

9. Una vez entrado ala app te iras ala parte ddonde dice (SCRIPTING)

10.Ya entrando te aparecera esto

11. <img width="2875" height="1835" alt="image" src="https://github.com/user-attachments/assets/b15e4013-f695-4fe7-8f63-24fabd3c0640" />

12. Te iras donde dice

13.( Tex) y escribiras el codigo

El siguiente código fue desarrollado en Python utilizando la librería bpy de Blender, con el objetivo de generar un polígono regular en dos dimensiones de manera programada.


```bash

import bpy
import math


Se importan las librerías necesarias.
bpy permite interactuar con Blender mediante scripts, mientras que math se utiliza para realizar cálculos matemáticos, específicamente funciones trigonométricas.


def crear_poligono_2d(nombre, lados, radio):



Se define una función llamada crear_poligono_2d, la cual recibe tres parámetros:
nombre: nombre del objeto que se creará en Blender.
lados: número de lados del polígono.
radio: distancia del centro del polígono a cada vértice.


malla = bpy.data.meshes.new(nombre)
objeto = bpy.data.objects.new(nombre, malla)



Se crea una nueva malla y un nuevo objeto en Blender utilizando el nombre proporcionado.



bpy.context.collection.objects.link(objeto)




El objeto creado se vincula a la colección actual de la escena para que sea visible.



vertices = []
aristas = []




Se inicializan dos listas:

vertices: almacenará las coordenadas de cada vértice.
aristas: almacenará las conexiones entre los vértices.



for i in range(lados):
    angulo = 2 * math.pi * i / lados
    x = radio * math.cos(angulo)
    y = radio * math.sin(angulo)
    vertices.append((x, y, 0))
```



En este ciclo se calculan las coordenadas de los vértices del polígono.
Se utiliza la conversión de coordenadas polares a cartesianas, donde:

El ángulo se distribuye de manera uniforme alrededor del círculo.
El valor z se mantiene en 0 para conservar el polígono en dos dimensiones (plano XY).


```bash




for i in range(lados):
    aristas.append((i, (i + 1) % lados))




Se definen las aristas del polígono, conectando cada vértice con el siguiente.
El operador módulo (%) permite que el último vértice se conecte con el primero, cerrando la figura.



malla.from_pydata(vertices, aristas, [])
malla.update()



Se cargan los datos de vértices y aristas en la malla y se actualiza para reflejar los cambios en la escena.



bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()




Antes de crear el polígono, se eliminan todos los objetos de la escena para evitar interferencias con figuras previas.



crear_poligono_2d("Poligono2D", lados=6, radio=5)




Finalmente, se llama a la función para crear un hexágono regular con un radio de 5 unidades, el cual se genera automáticamente en la escena de Blender.
```

YA TENIENDO TODO ESTO ESTA LISTO LOS PASOS 

Terminando los pasos deciados se tiene que ver asi

<img width="2879" height="1834" alt="image" src="https://github.com/user-attachments/assets/b1dd0619-61cf-4631-8982-3253bbc60e87" />



A continuacion te dejo el codigo completo


```bash

import bpy
import math

def crear_poligono_2d(nombre, lados, radio):
    # Crear una nueva malla y un nuevo objeto
    malla = bpy.data.meshes.new(nombre)
    objeto = bpy.data.objects.new(nombre, malla)

    # Vincular el objeto a la escena actual
    bpy.context.collection.objects.link(objeto)

    vertices = []
    aristas = []

    # Cálculo de vértices usando coordenadas polares a cartesianas
    for i in range(lados):
        angulo = 2 * math.pi * i / lados
        x = radio * math.cos(angulo)
        y = radio * math.sin(angulo)
        vertices.append((x, y, 0))  # Z = 0 para mantenerlo en 2D

    # Definir las conexiones (aristas) entre los vértices
    for i in range(lados):
        aristas.append((i, (i + 1) % lados))

    # Cargar los datos en la malla
    malla.from_pydata(vertices, aristas, [])
    malla.update()

# Limpiar la escena antes de empezar
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()

# Llamada a la función: un hexágono de radio 5
crear_poligono_2d("Poligono2D", lados=6, radio=5)

```
