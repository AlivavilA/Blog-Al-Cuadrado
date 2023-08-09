---
title: "Web Scraping Pt.1"
date: 2023-08-01T10:54:44-06:00
---
## Proyecto Web Scrapping, parte 1.

Mi plan es hacer un simple programa de web scraping en python para que sitio todavia no se.
Necesitare hacer uso de las librerias Beautifulsoup para analizar el HTML y extraer datos
Y Requests para realizar solicitudes HTTP y obtener el contenido de la pagina web
Primero los instalare:
```
pip install beautifulsoup4 
pip install requests 
```
Primero simplemente obtendremos todos los URL del sitio asignado. Esto es para ver hasta donde podemos llegar. Importamos las librerias tambien:
```
import requests
from bs4 import BeautifulSoup

url=' '
response = requests.get(url) 
```
Necesitaremos un condicional para verificar si la solicitud fue exitosa o no:
```
if response.status_code == 200:
    html_content = response.content
else:
    print("Error al obtener el contenido de la pagina") 
```  
El atributo status_code contine el codigo de estado HTTP devuelto por el servidor al que fue mandado, el codigo 200 implica que la solicitud fue exitosa, en otro caso significa que hay diferentes errores.

Ahora analizaremos el contenido de la pagina web y lo convertiremos en un objeto tipo BeautifulSoup
```
soup = BeautifulSoup(html_content, 'html.parser')
```
Seleccionaremos todos los enelaces en el documento HTML analizado y los almacenaremos en una lista llamada Links:
```
links = soup.select('a')
```
Ahora iteramos para obtener el titulo de cada enlace 
```
for link in links:
    print(link['href'])
```    
Por ultimo extraermos estos titulos y los imprimiremos:
```
title = soup.title.text
print(title)
```
Primero empezo como un proyecto de Web Scraping para Rateyourmusic pero parece que son bien cuidadosos
con sus datos por los que no los puedo sacar tan facilmente.
