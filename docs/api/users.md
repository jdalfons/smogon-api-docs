# Usuarios y Perfiles

Este endpoint permite consultar la información pública de cualquier entrenador en Pokémon Showdown.

## Endpoint

- **URL:** `https://pokemonshowdown.com/users/[USERNAME].json`
- **Ejemplo:** [zarel.json](https://pokemonshowdown.com/users/zarel.json)

---

## Información devuelta

El JSON contiene:
- **`username`**: Nombre del usuario.
- **`registertime`**: Fecha de registro (Unix timestamp).
- **`ratings`**: Un objeto donde las llaves son los formatos y los valores contienen el Elo, GXE y desviación.

---

## Ejemplo: Verificar el Elo de un usuario (Python)

```python
import requests

def get_elo(username, format_id):
    url = f"https://pokemonshowdown.com/users/{username.lower()}.json"
    data = requests.get(url).json()
    
    ratings = data.get('ratings', {})
    if format_id in ratings:
        return ratings[format_id].get('elo')
    return "Usuario no encontrado o sin ranking en este formato"

print(f"Elo de Zarel en Gen 8 OU: {get_elo('zarel', 'gen8ou')}")
```
