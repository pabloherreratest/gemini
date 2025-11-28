# ejemplo: Producto de Array Excepto Self
## ¡No te compliques! Soluciona eficientemente un problema común de algoritmos.

### El Problema:

Dado un array `nums` de `n` enteros, devuelve un array `output` tal que `output[i]` sea igual al producto de todos los elementos de `nums` excepto `nums[i]`.

**Restricciones:**
* El algoritmo debe ejecutarse en tiempo O(n).
* No se debe usar la operación de división.

**Ejemplo de Entrada:**
`nums = [1, 2, 3, 4]`

---

### Enfoque No Óptimo (Ingenuo): Usando Dos Bucles Anidados

Este enfoque es fácil de entender, pero **no cumple** con la restricción de tiempo O(n).

#### ¿Cómo funciona?
Para cada elemento `nums[i]`, recorremos el array completo (excepto `nums[i]`) para calcular el producto.

```python
def product_except_self_naive(nums):
    n = len(nums)
    output = [1] * n
    for i in range(n):
        current_product = 1
        for j in range(n):
            if i != j:
                current_product *= nums[j]
        output[i] = current_product
    return output
```

### Enfoque Óptimo: : Usando Dos Pasadas

```python
# Ejemplo:
nums = [1, 2, 3, 4]
resultado_naive = product_except_self_naive(nums)
# Salida esperada: [24, 12, 8, 6]



def product_except_self_optimized(nums):
    n = len(nums)
    output = [1] * n

    # Primera pasada: Calcular productos a la izquierda
    # output[i] contendrá el producto de nums[0]...nums[i-1]
    for i in range(1, n):
        output[i] = output[i-1] * nums[i-1]
    # Ejemplo: [1, 1, 2, 6]

    # Segunda pasada: Calcular productos a la derecha y combinarlos
    right_product = 1
    for i in range(n - 1, -1, -1):
        output[i] = output[i] * right_product
        right_product *= nums[i]
    # Ejemplo: [24, 12, 8, 6]

    return output
# Ejemplo:
nums = [1, 2, 3, 4]
resultado_optimized = product_except_self_optimized(nums)
# Salida esperada: [24, 12, 8, 6]
```
