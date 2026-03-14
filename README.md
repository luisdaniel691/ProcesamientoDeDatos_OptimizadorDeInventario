# Ejercicio resuelto - Optimizador de Inventario

**Alumno:** Luis Daniel Acevedo Herrera

**Materia:** Procesamiento Inteligente de Datos

<br><br>

Este repositorio contiene los puntos resueltos del ejercicio propuesto.


Contiene exactamente 3 archivos:
1. **ProcesamientoDeDatos_OptimizadorDeInventario_LuisAcevedo.ipynb :** Este archivo contiene el ejercicio en formato .ipynb, listo para ejecutarse en cualquier entorno de jupyter.
   
2. **ProcesamientoDeDatos_OptimizadorDeInventario_LuisAcevedo_Texto.ipynb.txt :** Este archivo contiene el archivo en formato .ipynb.txt, por si se desea ver rápidamente en un editor de texto como bloc de notas, sin necesitar un entorno de jupyter.

3. **ProcesamientoDeDatos_OptimizadorDeInventario_LuisAcevedo.ipynb:** Este archivo contiene el archivo en formato .pdf, para tener una vizualización mas clara del codigo y las explicaciones.


<br><br>

A continuación se definen los puntos del ejercicio resuelto:

<br><br>

 
## El Optimizador de Inventario

Contexto: Trabajas en el equipo de datos de una tienda online. Recibes un "dump" (descarga) de los productos que han entrado al almacén hoy, pero los datos vienen desordenados y con duplicados debido a errores en los escáneres de código de barras.

<br><br>

Datos de entrada:



```python
#Formato: (ID_Producto, Categoría, Precio, Stock_Actual)

entradas_almacen = [

    ("PROD-001", "Electrónica", 150.0, 5),
    
    ("PROD-002", "Hogar", 25.0, 10),
    
    ("PROD-001", "Electrónica", 150.0, 5),  # Duplicado
    
    ("PROD-003", "Ropa", 12.0, 0),
    
    ("PROD-004", "Electrónica", 300.0, 2),
    
    ("PROD-002", "Hogar", 25.0, 10),        # Duplicado
    
    ("PROD-005", "Ropa", 45.0, 15)
]
```

<br><br>


## Instrucciones del Reto

### 1. Depuración de Inventario (Sets)
El sistema registró productos dos veces por error.
* Convierte la lista `entradas_almacen` en un `set` llamado `productos_unicos`.
* **Pregunta técnica:** ¿Por qué podemos convertir una lista de tuplas a un set sin errores, pero no podríamos hacerlo si fuera una lista de listas? (Pista: Inmutabilidad).

---

### 2. Localización Fija (Tuplas)
Crea una tupla llamada `ubicacion_almacen` que guarde la Latitud 19.4326 y la Longitud -99.1332.
* Intenta cambiar la latitud a 20.0 y captura el error (o coméntalo) explicando por qué esto protege la integridad de los datos de geolocalización.

---

### 3. Filtro de Reposición (Listas)
Necesitamos una lista de los IDs de productos que tienen Stock_Actual igual a 0 para pedir más.
* Crea una lista vacía llamada `pedidos_urgentes`.
* Recorre `productos_unicos` con un bucle `for` y, si el stock (índice 3 de la tupla) es igual a 0, añade el ID del producto (índice 0) a la lista de pedidos.

---

### 4. Dashboard de Categorías (Diccionarios)
Crea un diccionario llamado `resumen_almacen` que contenga:

* **total_items**: La cantidad total de productos únicos encontrados.
* **categorias**: Un `set` con los nombres de las categorías únicas (puedes extraerlas de tus productos únicos).
* **alerta_stock**: Un valor booleano (`True`/`False`) que sea `True` si la lista `pedidos_urgentes` contiene al menos un elemento.

#### Ejemplo de cómo debería verse el resultado al imprimir `resumen_almacen`:

```python
{
    'total_items': 5,
    'categorias': {'Electrónica', 'Ropa', 'Hogar'},
    'alerta_stock': True
}



