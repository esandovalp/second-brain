#parallelcomputing 
**CUDA:** Compute Unified Device Architecture

Como el GPU sólo soporta con código compilado, lo que usaremos con python es "compilado", CUDA es lo que permite esto. 
# ¿Por qué usar el GPU?

Usando el CPU cada core (y hay pocos) tiene asignada una tarea diferente. En el GPU con los hasta mil de cores más, cada uno de ellos corren la misma tarea, con datos diferentes.

Para [[python]] usaremos [[NUMBA]]
# Comentarios del profe 

- Los GPU's son malos para tareas largas (e.g. operaciones con vectores), las operaciones matriciales son las que si son buenas en GPU's.
- Tamaño ***mínimo*** de planificación (WARP size): 32 threads.
- Se tiene que entender el modelo de programación para poder programar usando GPU's
- **Bloques tridimensionales $\implies$ rejillas (grid) tridimensionales
	- Se asignan a [[Streaming Multiprocessors]], hasta 32 bloques.
		- El GPU está dividido en SMs
	- Podemos definir la dimensión del bloque.
	- Los identificadores de los hilos se reinician por bloque, en función de la dimensión definido. 
	- ```id_thread + dimension * id_bloque```
	- Hilos en diferentes bloques no interactúan.
- Necesitamos el grid para tener más leisure de paralelismo. Para que todos los hilos sean utilizados. Se gana eficiencia con la estructura del grid.
	- **Con vectores conviene un grid de una dimensión.**
	- **Con matrices conviene un grid multidimensional.**
- El GPU por si sólo tiene una memoria global (global memory)
- Los return no se permiten ya que cambian el flujo. 
- Todos los hilos ejecutan la misma instrucción
- Usar varios ``if`` en un kernel arruina el rendimiento.
- Interrupciones, bifurcaciones son fatales para GPU's
- **Single-Instruction, Multiple Threads:** los hilos en algún punto se pueden detener. Similar al que vimos con CPU's, la diferencia es esa.
- Al menos que especifiques que se ejecute en GPU, todo lo demás se ejecuta en CPU

# Conceptos básicos

- **host:** CPU 
- **Device:** GPU
- **host memory:** memoria principal del sistema
- **device memory:** la memoria integrada en el GPU
- **Kernel:** una función GPU lanzada por el host y ejecutada en el device. Esto es el WRAP. Es lo que hace que ejecute en el CPU 
- **Device function:** una función GPU en el device que solo puede ser llamada desde el device.

# Intro a CUDA (programación)

```python
import numpy as np
from numba import cuda

cuda.gpus
cuda.detect()
#cuda.select_device(0) #en este caso estamos agarrando el id 0
```

output
```bash
Found 1 CUDA devices
id 0             b'Tesla T4'                              [SUPPORTED]
                      Compute Capability: 7.5
                           PCI Device ID: 4
                              PCI Bus ID: 0
                                    UUID: GPU-7482aed6-bf32-8903-021d-4f52c2351f0f
                                Watchdog: Disabled
             FP32/FP64 Performance Ratio: 32
Summary:
	1/1 devices are supported

True
```

Código que explica la capacidad de computo que tiene la tarjeta que tenemos.
```python
from numba import cuda
cc_cores_per_SM_dict = { (2,0) : 32, (2,1) : 48, (3,0) : 192, (3,5) : 192, (3,7) : 192, (5,0) : 128, (5,2) : 128, (6,0) : 64, (6,1) : 128, (7,0) : 64, (7,5) : 64, (8,0) : 64, (8,6) : 128, (8,9) : 128, (9,0) : 128 }
device = cuda.get_current_device()
sms = getattr(device, "MULTIPROCESSOR_COUNT")
cc = device.compute_capability
cores_por_sm = cc_cores_per_SM_dict.get(cc)
cores_totales = cores_por_sm * sms
print("GPU compute capability: ", cc)
print("Número de SM: ", sms)
print("Número de cores: ", cores_totales)
```

output
```bash
GPU compute capability: (7, 5) Número de SM: 40 Número de cores: 2560
```

```python
from numba.cuda.cudadrv import enums
from numba import cuda

device = cuda.get_current_device()
attribs = [name.replace("CU_DEVICE_ATTRIBUTE_", "") for name in
dir(enums) if name.startswith("CU_DEVICE_ATTRIBUTE_")]

for attr in attribs:
	print(attr, "=", getattr(device, attr))
```

output
```bash
ASYNC_ENGINE_COUNT = 3 CAN_MAP_HOST_MEMORY = 1 CAN_USE_HOST_POINTER_FOR_REGISTERED_MEM = 1 CLOCK_RATE = 1590000 COMPUTE_CAPABILITY_MAJOR = 7 COMPUTE_CAPABILITY_MINOR = 5 COMPUTE_MODE = 0 COMPUTE_PREEMPTION_SUPPORTED = 1 CONCURRENT_KERNELS = 1 CONCURRENT_MANAGED_ACCESS = 1 COOPERATIVE_LAUNCH = 1 COOPERATIVE_MULTI_DEVICE_LAUNCH = 1 ECC_ENABLED = 1 GLOBAL_L1_CACHE_SUPPORTED = 1 GLOBAL_MEMORY_BUS_WIDTH = 256 GPU_OVERLAP = 1 HOST_NATIVE_ATOMIC_SUPPORTED = 0 INTEGRATED = 0 IS_MULTI_GPU_BOARD = 0 KERNEL_EXEC_TIMEOUT = 0 L2_CACHE_SIZE = 4194304 LOCAL_L1_CACHE_SUPPORTED = 1 MANAGED_MEMORY = 1 MAX_BLOCK_DIM_X = 1024 MAX_BLOCK_DIM_Y = 1024 MAX_BLOCK_DIM_Z = 64 MAX_GRID_DIM_X = 2147483647 MAX_GRID_DIM_Y = 65535 MAX_GRID_DIM_Z = 65535 MAX_MAX_TEXTURE_2D_MIPMAPPED_HEIGHT = 32768 MAX_PITCH = 2147483647 MAX_REGISTERS_PER_BLOCK = 65536 MAX_REGISTERS_PER_MULTIPROCESSOR = 65536 MAX_SHARED_MEMORY_PER_BLOCK = 49152 MAX_SHARED_MEMORY_PER_BLOCK_OPTIN = 65536 MAX_SHARED_MEMORY_PER_MULTIPROCESSOR = 65536 MAX_SURFACE_1D_LAYERED_LAYERS = 2048 MAX_SURFACE_1D_LAYERED_WIDTH = 32768 MAX_SURFACE_1D_WIDTH = 32768 MAX_SURFACE_2D_HEIGHT = 65536 MAX_SURFACE_2D_LAYERED_HEIGHT = 32768 MAX_SURFACE_2D_LAYERED_LAYERS = 2048 MAX_SURFACE_2D_LAYERED_WIDTH = 32768 MAX_SURFACE_2D_WIDTH = 131072 MAX_SURFACE_3D_DEPTH = 16384 MAX_SURFACE_3D_HEIGHT = 16384 MAX_SURFACE_3D_WIDTH = 16384 MAX_SURFACE_CUBEMAP_LAYERED_LAYERS = 2046 MAX_SURFACE_CUBEMAP_LAYERED_WIDTH = 32768 MAX_SURFACE_CUBEMAP_WIDTH = 32768 MAX_TEXTURE_1D_LAYERED_LAYERS = 2048 MAX_TEXTURE_1D_LAYERED_WIDTH = 32768 MAX_TEXTURE_1D_LINEAR_WIDTH = 268435456 MAX_TEXTURE_1D_MIPMAPPED_WIDTH = 32768 MAX_TEXTURE_1D_WIDTH = 131072 MAX_TEXTURE_2D_GATHER_HEIGHT = 32768 MAX_TEXTURE_2D_GATHER_WIDTH = 32768 MAX_TEXTURE_2D_HEIGHT = 65536 MAX_TEXTURE_2D_LAYERED_HEIGHT = 32768 MAX_TEXTURE_2D_LAYERED_LAYERS = 2048 MAX_TEXTURE_2D_LAYERED_WIDTH = 32768 MAX_TEXTURE_2D_LINEAR_HEIGHT = 65000 MAX_TEXTURE_2D_LINEAR_PITCH = 2097120 MAX_TEXTURE_2D_LINEAR_WIDTH = 131072 MAX_TEXTURE_2D_MIPMAPPED_WIDTH = 32768 MAX_TEXTURE_2D_WIDTH = 131072 MAX_TEXTURE_3D_DEPTH = 16384 MAX_TEXTURE_3D_DEPTH_ALT = 32768 MAX_TEXTURE_3D_HEIGHT = 16384 MAX_TEXTURE_3D_HEIGHT_ALT = 8192 MAX_TEXTURE_3D_WIDTH = 16384 MAX_TEXTURE_3D_WIDTH_ALT = 8192 MAX_TEXTURE_CUBEMAP_LAYERED_LAYERS = 2046 MAX_TEXTURE_CUBEMAP_LAYERED_WIDTH = 32768 MAX_TEXTURE_CUBEMAP_WIDTH = 32768 MAX_THREADS_PER_BLOCK = 1024 MAX_THREADS_PER_MULTI_PROCESSOR = 1024 MEMORY_CLOCK_RATE = 5001000 MULTIPROCESSOR_COUNT = 40 MULTI_GPU_BOARD_GROUP_ID = 0 PAGEABLE_MEMORY_ACCESS = 0 PCI_BUS_ID = 0 PCI_DEVICE_ID = 4 PCI_DOMAIN_ID = 0 SINGLE_TO_DOUBLE_PRECISION_PERF_RATIO = 32 STREAM_PRIORITIES_SUPPORTED = 1 SURFACE_ALIGNMENT = 512 TCC_DRIVER = 0 TEXTURE_ALIGNMENT = 512 TEXTURE_PITCH_ALIGNMENT = 32 TOTAL_CONSTANT_MEMORY = 65536 UNIFIED_ADDRESSING = 1 WARP_SIZE = 32
```
*Nos interesan las dimensiones de los bloques, y warp_size*
```bash
MAX_BLOCK_DIM_X = 1024 MAX_BLOCK_DIM_Y = 1024
```


# Ejercicio de paralelización con GPU's

## Lanzamiento de un Kernel 

No hace nada 
```python
import numpy as np
from numba import cuda

@cuda.jit
def un_kernel(arreglo):
"""
Aquí iría el código de mi kernel
"""
pass

a = np.ones(320)
#hilos por bloque debe de estar en función del WARP size (min 32)
hilos_por_bloque = 32
#practica comun para definir grid, se puede buscar en que tamaño hay mas rendimiento
bloques_por_rejilla = a.size // hilos_por_bloque
bloques_por_rejilla
un_kernel[bloques_por_rejilla, hilos_por_bloque](a)
```

output
```bash
/usr/local/lib/python3.10/dist-packages/numba/cuda/dispatcher.py:536: NumbaPerformanceWarning: Grid size 10 will likely result in GPU under-utilization due to low occupancy.
  warn(NumbaPerformanceWarning(msg))
/usr/local/lib/python3.10/dist-packages/numba/cuda/cudadrv/devicearray.py:886: NumbaPerformanceWarning: Host array used in CUDA kernel will incur copy overhead to/from device.
  warn(NumbaPerformanceWarning(msg))

---
```

kernel doblador
```python
import numpy as np
from numba import cuda

@cuda.jit
def un_kernel_doblador(arreglo):
	i = cuda.threadIdx.x + cuda.blockIdx.x * cuda.blockDim.x
	if i < arreglo.size: #protego
		arreglo[i] *= 2

a = np.ones(320)
#hilos por bloque debe de estar en función del WARP size (min 32)
hilos_por_bloque = 32
#practica comun para definir grid, se puede buscar en que tamaño hay mas rendimiento
bloques_por_rejilla = a.size // hilos_por_bloque
bloques_por_rejilla
un_kernel_doblador[bloques_por_rejilla, hilos_por_bloque](a)
print(a)
```
- ```jit```: just in time device.

Ejercicio mapa de memoria 
```python
import numpy as np
from numba import cuda
import math

@cuda.jit
def un_kernel_doblador(arreglo, estructura):
	i = cuda.threadIdx.x + cuda.blockIdx.x * cuda.blockDim.x
	# esto lo evitamos con `position = cuda.grid(1)`
	if i < arreglo.size: # protego
		arreglo[i] *= 2
		estructura[i][0] = i
		estructura[i][1] = cuda.threadIdx.x
		estructura[i][2] = cuda.blockIdx.x
		estructura[i][3] = cuda.blockDim.x
  
a = np.ones(320, dtype=np.float32)

estructura = np.zeros((320,4), dtype=np.int32)

# hilos por bloque debe de estar en función del WARP size (min 32)
 
un_kernel_doblador[bloques_por_rejilla, hilos_por_bloque](a, estructura)
print(a)
for renglon in estructura:
	print(renglon)
```

- ```cuda.device_array```: se crea un Array en el GPU, esto es para procesar.
- ```cuda.device_array_like```: se crea un Array en el CPU, en función de una estructura
	- ```device_array = cuda.device_array_like(a)```: lo genera en el GPU (device)
- ```device_array.copy_to_host```: copiar al CPU, con esto accedemos a los datos, porque sino el CPU te manda una dirección de memoria. Se manda del GPU (device) al CPU (host).

- ```i = cuda.grid(1)``` $=$ ```i = cuda.threadIdx.x + cuda.blockIdx.x * cuda.blockDim.x```

[[Proyecto clausura]]

- Cuando se generan variables en python se guardan del lado del CPU (host)

## Ejercicio: suma de matrices con grid de una sola dimensión 


*completar con el código del profesor*
```python
import numpy as np
from numba import cuda
import math

# CUDA kernel definition
@cuda.jit
def sum_kernel(a, b, c):
    position = cuda.grid(1)
    if position < a.size:
        c[position] = a[position] + b[position]

# Constants and input data
VECTOR_SIZE = 321
a = np.ones(VECTOR_SIZE, dtype=np.float32)
b = np.ones(VECTOR_SIZE, dtype=np.float32)

# Allocation of GPU memory
device_a = cuda.to_device(a)
device_b = cuda.to_device(b)
device_c = cuda.device_array(VECTOR_SIZE, dtype=np.float32)  # Specifying dtype is good practice

# Configuration of blocks and grid
threads_per_block = 32
blocks_per_grid = math.ceil(a.size / threads_per_block)

# Kernel launch
sum_kernel[blocks_per_grid, threads_per_block](device_a, device_b, device_c)

# Copy result back to host and print
result = device_c.copy_to_host()
print(result)

```

- Al trabajar con matrices tenemos que definir:
	1. Threads per Block 
	2. Grid 

## Ejercicio multiplicacion de matrices 

```python
import numpy as np
from numba import cuda
import math

# CUDA kernel for matrix multiplication
@cuda.jit
def matmul_kernel(A, B, C):
	# Calculate the row index of the C element and the column index of the C element
	row, col = cuda.grid(2)
	if row < C.shape[0] and col < C.shape[1]:
		tmp = 0
		for k in range(A.shape[1]): # Or B.shape[0], since A.shape[1] should equal B.shape[0]
			tmp += A[row, k] * B[k, col]
		C[row, col] = tmp

# Input matrices dimensions
A = np.array([[1, 2, 3], [4, 5, 6]], dtype=np.float32) # 2x3 matrix
B = np.array([[7, 8], [9, 10], [11, 12]], dtype=np.float32) # 3x2 matrix

# Allocation of GPU memory
device_A = cuda.to_device(A)
device_B = cuda.to_device(B)
result_shape = (A.shape(), 2) # Resultant matrix size based on A's rows and B's columns
device_C = cuda.device_array(result_shape, dtype=np.float32) # Resultant matrix 2x2

# Threads per block and blocks per grid configurations
threads_per_block = (16, 16)
blocks_per_grid_x = math.ceil(result_shape[0] / threads_per_block[0])
blocks_per_grid_y = math.ceil(result_shape[1] / threads_per_block[1])
  

# Kernel launch
matmul_kernel[(blocks_per_grid_x, blocks_per_grid_y), threads_per_block](device_A, device_B, device_C)

# Copy result back to host and print
result = device_C.copy_to_host()
print(result)
```

## Aplicaciones típicas

![[Pasted image 20240418190138.png]]

### Filtros 

- El grid lo definimos, por ejemplo en este caso, grid(250,250) en cada bloque sabemos que hay threads. 
- El filtro es una simplificación de la imagen. 

Código de filtros:
```python
from numba import cuda
import matplotlib.pyplot as plt
from skimage import io
import math
import numpy as np

@cuda.jit
def conv(pixels, output, size):
    row, col = cuda.grid(2)
    # Check if the pixels array has a third dimension, if not, it's grayscale
    is_grayscale = (pixels.ndim == 2)
    channels = 1 if is_grayscale else pixels.shape[2]

    # Adjust boundary check for grayscale or color
    if row >= 2 and col >= 2 and row < (size[0] - 2) and col < (size[1] - 2):
        divisor = 75
        for ch in range(channels):  # Iterate over color channels
            sum = 0.0
            for dr in range(-2, 3):  # 5x5 neighborhood
                for dc in range(-2, 3):
                    if is_grayscale:
                        sum += pixels[row+dr, col+dc] / divisor
                    else:
                        sum += pixels[row+dr, col+dc, ch] / divisor
            if is_grayscale:
                output[row, col] = round(sum / 15)
            else:
                output[row, col, ch] = round(sum / 15)

eagle = io.imread("/mnt/data/eagle.png").astype(np.float32)
print(eagle.min(), eagle.max(), eagle.shape)
plt.imshow(eagle / 255)  # Normalize for display purposes
plt.show()

host_pixels = eagle
device_pixels = cuda.to_device(host_pixels)
device_output = cuda.device_array(host_pixels.shape)

threads_per_block = (16, 16)
blocks_x = math.ceil(eagle.shape[0] / threads_per_block[0])
blocks_y = math.ceil(eagle.shape[1] / threads_per_block[1])
grid = (blocks_x, blocks_y)

conv[grid, threads_per_block](device_pixels, device_output, eagle.shape)

output_image = device_output.copy_to_host()
plt.imshow(output_image / 255 if output_image.ndim == 3 else output_image, cmap="gray" if output_image.ndim == 2 else None)
plt.show()
```

### Ejercicio de pixelización de imagenes 
*Buscarlo en el repo del grupo*

```python
from numba import cuda
import matplotlib.pyplot as plt
from skimage import data, io
import math
import numpy as np

@cuda. jit
def conv(pixels, output, size):
	row, col = cuda.grid (2)
	if (row + 2) < size[0] and (col + 2) < size[l] and row > 2 and col > 2:
		divisor = 75
	sum = pixels[row-2][col-1]/divisor + pixels[row-2][col]/divisor + pixels|row-2][col+1]/divisor + \
	pixels[row-1][col-1]/divisor + pixels[row-1][col]/divisor + pixels[row-1][col+1]/divisor + \ pixels[row-0][col-1]/divisor + pixels[row-0][col]/divisor + pixels[row-0][col+1]/divisor + \ pixels[row+1][col-1]/divisor + pixels[row+1][col]/divisor + pixels[row+1][col+1]/divisor + \
	
	pixels[row+2][col-1]/divisor + pixels[row+2][col]/divisor + pixels[row+2][col+1]/divisor
	output [row] [col] = round (sum/15)

#eagle = data.eagle().astype(np.float32)
eagle = io. imread("eagle.png").astype(np.float32)
print(eagle.min(), eagle.max(), eagle)
plt. imshow(eagle, cmap="gray")
plt. show ( )
##(2019, 1826)
host pixels = eagle
device_pixels = cuda.to_
_device (host_pixels)
device_output = cuda.device_array (host_pixels.shape)
threads_per_block = (16, 16)
blocks_x = math.ceil(eagle.shape[0] / threads_per_block[0])
blocks_y = math.ceil(eagle.shape|1] / threads_per_block[11)
grid = (blocks_x, blocks_y)

convigrid, threads_per_block](device_pixels, device_output, eagle.shape)
pIt.imshow(device_output.copy_to_host(), cmap="gray")
plt. show ()
```

De aquí vimos [[Computo Intensivo INPUT OUTPUT]]
