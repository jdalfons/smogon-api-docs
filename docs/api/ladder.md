# Clasificaciones (Ladder)

Consulta el "Top 100" de cualquier formato activo en el servidor principal.

## Endpoint

- **URL:** `https://pokemonshowdown.com/ladder/[FORMAT_ID].json`
- **Ejemplo:** [gen9ou.json](https://pokemonshowdown.com/ladder/gen9ou.json)

---

## Ejemplo: Listar el Top 5 (JavaScript)

```javascript
async function printTop5(format) {
    const url = `https://pokemonshowdown.com/ladder/${format}.json`;
    const response = await fetch(url);
    const data = await response.json();
    
    console.log(`--- TOP 5 EN ${format.toUpperCase()} ---`);
    data.toplist.slice(0, 5).forEach((user, index) => {
        print(`${index + 1}. ${user.username} (${user.elo} ELO)`);
    });
}
```

---

## Estructura de la Tabla de Clasificación

| Campo | Descripción |
|-------|-------------|
| `formatid` | ID del formato consultado |
| `toplist` | Lista de objetos de usuario con su posición |
| `toplist[].username` | Nombre del jugador |
| `toplist[].elo` | Puntuación Elo |
| `toplist[].gxe` | GXE (Glicko X-Score Estimate) |
