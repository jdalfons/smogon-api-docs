# Recursos de la Pokédex (Dex)

Acceso directo a los diccionarios de datos que alimentan el simulador. Son archivos JSON pesados que contienen toda la lógica de tipos, habilidades, movimientos y estadísticas.

## Principales Archivos

- **Pokédex completa:** `https://play.pokemonshowdown.com/data/pokedex.json`
- **Movimientos:** `https://play.pokemonshowdown.com/data/moves.json`
- **Habilidades:** `https://play.pokemonshowdown.com/data/abilities.json`
- **Objetos (Items):** `https://play.pokemonshowdown.com/data/items.json`
- **Formatos:** `https://play.pokemonshowdown.com/data/formats.json`

---

## Ejemplo: Buscar estadísticas de un Pokémon (JavaScript)

```javascript
async function getStats(pokemonName) {
    const resp = await fetch("https://play.pokemonshowdown.com/data/pokedex.json");
    const dex = await resp.json();
    
    // Normalizar el nombre (minúsculas, sin espacios ni símbolos)
    const key = pokemonName.toLowerCase().replace(/[^a-z0-9]/g, "");
    
    if (dex[key]) {
        console.log(`Estadísticas de ${pokemonName}:`, dex[key].baseStats);
    } else {
        console.log("Pokémon no encontrado");
    }
}

getStats("Iron Valiant");
```

---

> **Aviso Importante:** Estos archivos no cambian con mucha frecuencia. Si estás construyendo una aplicación, se recomienda **cachear** los datos localmente en lugar de realizar una petición fetch cada vez que tu app inicie.
