# Repeticiones (Replays)

El sistema de repeticiones permite acceder a los registros históricos de las batallas jugadas en Pokémon Showdown.

## Endpoints

### 1. Datos de una repetición
Obtén el registro completo de una batalla específica.

- **URL:** `https://replay.pokemonshowdown.com/[REPLAY_ID].json`
- **Ejemplo:** [gen8doublesubers-1097585496.json](https://replay.pokemonshowdown.com/gen8doublesubers-1097585496.json)

### 2. Registro de batalla (Log)
Si solo necesitas el log de eventos línea por línea usado por el simulador.

- **URL:** `https://replay.pokemonshowdown.com/[REPLAY_ID].log`

---

## Ejemplo de implementación (Python)

Supongamos que quieres extraer el nombre de los jugadores de una repetición.

```python
import requests

replay_id = "gen8doublesubers-1097585496"
url = f"https://replay.pokemonshowdown.com/{replay_id}.json"

response = requests.get(url)
if response.status_code == 200:
    data = response.json()
    # Los jugadores están en los campos 'p1' y 'p2'
    print(f"Jugador 1: {data.get('players')[0]}")
    print(f"Jugador 2: {data.get('players')[1]}")
```

---

## Estructura del JSON de Repetición

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `id` | String | ID único de la repetición |
| `p1` | String | Nombre del jugador 1 |
| `p2` | String | Nombre del jugador 2 |
| `format` | String | Formato de la batalla (ej: gen9ou) |
| `log` | String | El registro completo de la batalla en formato texto |
| `inputlog` | String | (Opcional) Las acciones exactas realizadas por los jugadores |
