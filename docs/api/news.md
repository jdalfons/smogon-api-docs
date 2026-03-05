# Noticias (News)

Mantente al tanto de los cambios en el simulador y anuncios de torneos oficiales.

## Endpoints

### 1. Todas las noticias recientes
Obtiene un resumen de las últimas noticias publicadas.

- **URL:** `https://pokemonshowdown.com/news.json`

### 2. Noticia individual
Obtiene el contenido completo de una entrada específica mediante su ID.

- **URL:** `https://pokemonshowdown.com/news/[NEWS_ID].json`

---

## Ejemplo: Obtener el título de la última noticia (Python)

```python
import requests

url = "https://pokemonshowdown.com/news.json"
news = requests.get(url).json()

if news:
    last_news = news[0]
    print(f"Última noticia: {last_news.get('title')}")
    print(f"Publicado el: {last_news.get('date')}")
```
