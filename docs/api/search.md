# Búsqueda de Repeticiones

Puedes realizar búsquedas complejas filtrando por usuario, formato o fecha.

## Parámetros de Consulta

| Parámetro | Descripción |
|-----------|-------------|
| `user` | Nombre del usuario principal |
| `user2` | (Opcional) Segundo usuario para buscar enfrentamientos entre ambos |
| `format` | Formato o tier (ej: `gen9ou`, `gen8randombattle`) |
| `before` | Timestamp para paginación (devuelve resultados anteriores a ese tiempo) |

---

## Ejemplos de Búsqueda

- **Por usuario:** `.../search.json?user=zarel`
- **Por formato:** `.../search.json?format=gen8ou`
- **Enfrentamientos directos:** `.../search.json?user=zarel&user2=yuyuko`

---

## Ejemplo de Paginación (JavaScript)

Las búsquedas devuelven un máximo de 51 resultados. Si recibes 51, hay más páginas disponibles.

```javascript
async function searchAllReplays(user) {
    let allReplays = [];
    let lastTimestamp = null;
    let hasMore = true;

    while (hasMore) {
        let url = `https://replay.pokemonshowdown.com/search.json?user=${user}`;
        if (lastTimestamp) url += `&before=${lastTimestamp}`;

        const resp = await fetch(url);
        const data = await resp.json();
        
        allReplays = allReplays.concat(data);
        
        if (data.length === 51) {
            // El resultado 51 nos da el timestamp para la siguiente página
            lastTimestamp = data[50].uploadtime;
        } else {
            hasMore = false;
        }
    }
    console.log(`Total de repeticiones encontradas: ${allReplays.length}`);
}
```
