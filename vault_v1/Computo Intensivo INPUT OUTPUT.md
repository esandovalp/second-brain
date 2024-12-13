#parallelcomputing 
Usamos [[flask]], que es una libreria de python
# Descarga de archivos de un server
```python
from flask import Flask, request, send_file, render_template

app = Flask(__name__)
  
@app.route('/archivo', methods=['GET'])
def archivo():
	print(request.args['nombre'])
	archivo = request.args['nombre'] + '.dat'
	return send_file('files/' + archivo, download_name = archivo)

@app.route("/")
def index():
	return render_template('index.html')

# Verificamos que pertenezca al main
if __name__ == '__main__':
	app.run("0.0.0.0", port = 90, threaded = True) #threaded = True hace que el servidor pueda atender a varios clientes a la vezsou
```
Complementar con el código del profe en su repo. 

# Libraries que usamos 

```python
from multiprocessing import Process
from threading import Thread
import time 
import requests

def download_file (url):
	local_file = url.split('=')[-1] + ".dat"
	print (local_file)
	with requests.get(url, stream=True) as request:
		request.raise_for_status()
		with open (local_file, "wb") as file:
			for chunk in request.iter_content(chunk_size=8192):
				file.write(chunk)
	return local_file

if __name__ == '__main__':
	inicio = time.time()
	#archivo = download_file("http://10.10.20.128:90/archivo?nombre=uno")
	#download_file("http://10.10.20.128:90/archivo?nombre=dos")
	#download_file("http://10.10.20.128:90/archivo?nombre=tres")
	#download_file("http://10.10.20.128:90/archivo?nombre=cuatro")
	#download_file("http://10.10.20.128:90/archivo?nombre=cinco")
	fin = time.time()
	print(fin - inicio)
	
	inicio = time.time()
	descarga1 = Process(target=download_file, args=("http://10.10.20.128:90/archivo?nombre=uno",))
	descarga2 = Process(target=download_file, args=("http://10.10.20.128:90/archivo?nombre=dos",))
	descarga3 = Process(target=download_file, args=("http://10.10.20.128:90/archivo?nombre=tres",))
	descarga4 = Process(target=download_file, args=("http://10.10.20.128:90/archivo?nombre=cuatro",))
	descarga5 = Process(target=download_file, args=("http://10.10.20.128:90/archivo?nombre=cinco",))
	descarga1.start()
	descarga2.start()
	descarga3.start()
	descarga4.start()
	descarga5.start()
	descarga1.join()
	descarga2.join()
	descarga3.join()
	descarga4.join()
	descarga5.join()
	fin = time.time()
	print(fin - inicio)
```
## Versión paralela 
```python
import time
import requests
import concurrent.futures

CHUNK_SIZE = 1024 * 1024  # 1 MB chunk size

def download_file(url):
    local_file = url.split('=')[-1] + ".dat"
    with requests.get(url, stream=True) as response:
        response.raise_for_status()
        with open(local_file, "wb") as file:
            for chunk in response.iter_content(chunk_size=CHUNK_SIZE):
                file.write(chunk)
    return local_file

def main():
    inicio = time.time()
    urls = [
        "http://10.10.20.128:90/archivo?nombre=uno",
        "http://10.10.20.128:90/archivo?nombre=dos",
        "http://10.10.20.128:90/archivo?nombre=tres",
        "http://10.10.20.128:90/archivo?nombre=cuatro",
        "http://10.10.20.128:90/archivo?nombre=cinco"
    ]
    with concurrent.futures.ThreadPoolExecutor() as executor:
        # Download files concurrently
        futures = [executor.submit(download_file, url) for url in urls]
        # Wait for all downloads to complete
        concurrent.futures.wait(futures)
    fin = time.time()
    print("Time taken:", fin - inicio)

if __name__ == '__main__':
    main()
```

