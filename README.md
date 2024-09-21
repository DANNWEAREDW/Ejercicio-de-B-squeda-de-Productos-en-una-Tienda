# Ejercicio-de-B-squeda-de-Productos-en-una-Tienda
Este repositorio contiene un programa en Python que permite buscar productos en una tienda utilizando parámetros opcionales como nombre, marca y categoría. Admite búsquedas avanzadas usando operadores lógicos y maneja errores en las entradas. El programa está diseñado para ser flexible y robusto, permitiendo búsquedas eficientes.


# Lista de productos: Cada producto es representado por un diccionario
productos = [
    {'nombre': 'Laptop', 'marca': 'Dell', 'categoria': 'Electrónica'},
    {'nombre': 'Smartphone', 'marca': 'Samsung', 'categoria': 'Electrónica'},
    {'nombre': 'Televisor', 'marca': 'Sony', 'categoria': 'Electrónica'},
    {'nombre': 'Zapatillas', 'marca': 'Nike', 'categoria': 'Calzado'},
    {'nombre': 'Sandalias', 'marca': 'Adidas', 'categoria': 'Calzado'},
    {'nombre': 'Lavadora', 'marca': 'LG', 'categoria': 'Electrodomésticos'},
    {'nombre': 'Refrigerador', 'marca': 'Whirlpool', 'categoria': 'Electrodomésticos'}
]

# Función para buscar productos con parámetros opcionales
def buscar_productos(nombre=None, marca=None, categoria=None):
    try:
        # Filtro de productos según los parámetros proporcionados
        resultado = [producto for producto in productos if
                     (nombre is None or nombre.lower() in producto['nombre'].lower()) and
                     (marca is None or marca.lower() == producto['marca'].lower()) and
                     (categoria is None or categoria.lower() == producto['categoria'].lower())]
        
        if not resultado:
            raise ValueError("No se encontraron productos que coincidan con los criterios de búsqueda.")
        
        return resultado
    
    except Exception as e:
        return f"Error en la búsqueda: {str(e)}"

# Llamada a la función para probar diferentes combinaciones de búsqueda
print(buscar_productos(nombre='Laptop'))  # Búsqueda por nombre
print(buscar_productos(marca='Nike'))     # Búsqueda por marca
print(buscar_productos(categoria='Electrónica'))  # Búsqueda por categoría
print(buscar_productos(nombre='Phone', marca='Samsung'))  # Búsqueda por nombre parcial y marca

# Desafíos adicionales:

# Búsqueda avanzada: Parámetros opcionales con operadores lógicos (OR en lugar de AND)
def buscar_productos_avanzado(nombre=None, marca=None, categoria=None):
    try:
        # Filtro usando OR en lugar de AND para la búsqueda más flexible
        resultado = [producto for producto in productos if
                     (nombre is None or nombre.lower() in producto['nombre'].lower()) or
                     (marca is None or marca.lower() == producto['marca'].lower()) or
                     (categoria is None or categoria.lower() == producto['categoria'].lower())]
        
        if not resultado:
            raise ValueError("No se encontraron productos que coincidan con los criterios de búsqueda.")
        
        return resultado
    
    except Exception as e:
        return f"Error en la búsqueda avanzada: {str(e)}"

# Llamadas a la función avanzada
print(buscar_productos_avanzado(nombre='Phone', categoria='Electrónica'))  # Búsqueda flexible con OR
print(buscar_productos_avanzado(marca='Adidas', categoria='Electrodomésticos'))  # Prueba con marca y categoría

![image](https://github.com/user-attachments/assets/6ccb6259-448d-4d4c-91b1-96a5df30a233)
