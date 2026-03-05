# Introducción al API de Pokémon Showdown

Bienvenido a la documentación del API web de Pokémon Showdown. La mayoría de los servicios de PS están disponibles en formato JSON simplemente agregando `.json` al final de la URL convencional.

Esta sección te ayudará a configurar tu entorno para empezar a realizar peticiones programáticas.

---

## Guía de Inicio: Python

Python es una de las mejores opciones para interactuar con APIs debido a su legibilidad y potentes librerías. Recomendamos usar `uv` para gestionar tus dependencias.

### 1. Preparación del entorno
Si no tienes `uv` instalado, instálalo primero. Luego, inicializa tu proyecto:

```bash
uv init my-project
cd my-project
uv add requests
```

### 2. Primer código: Hola Mundo API
Este script obtiene los datos básicos de un usuario y los imprime en consola.

```python
import requests

def get_user_data(username):
    url = f"https://pokemonshowdown.com/users/{username}.json"
    response = requests.get(url)
    
    if response.status_code == 200:
        data = response.json()
        print(f"Usuario: {data.get('username')}")
        print(f"Registro: {data.get('registertime')}")
    else:
        print("Error al conectar con el API")

if __name__ == "__main__":
    get_user_data("zarel")
```

---

## 📜 Guía de Inicio: JavaScript (Node.js)

Para Node.js, utilizaremos la API nativa `fetch` (disponible en versiones modernas) o la librería `axios`.

### 1. Preparación del entorno
```bash
npm init -y
# O si usas bun
bun init -y
```

### 2. Código de ejemplo (using Fetch)
Este ejemplo es ideal para scripts rápidos o para integrar en el navegador.

```javascript
async function getLadderData(format) {
    const url = `https://pokemonshowdown.com/ladder/${format}.json`;
    
    try {
        const response = await fetch(url);
        if (!response.ok) throw new Error('Error en la petición');
        
        const data = await response.json();
        console.log(`Top 1 en ${format}:`, data.toplist[0].username);
    } catch (error) {
        console.error("Hubo un error:", error);
    }
}

getLadderData('gen9ou');
```

---

## Estructura de Datos (JSON)

Casi todos los endpoints devuelven objetos JSON. Como desarrollador, debes estar familiarizado con:
- **Diccionarios/Objetos:** Pares clave-valor (ej: `{"name": "Pikachu"}`).
- **Listas/Arrays:** Colecciones ordenadas (ej: `["Electric", "Normal"]`).

Explora las secciones en el menú de la derecha para ver los detalles de cada endpoint.
