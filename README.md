# Hash Table

Una tabla hash, **matriz asociativa**, hashing, mapa hash, tabla de dispersión o tabla fragmentada es una estructura de datos que asocia llaves o claves con valores. La operación principal que soporta de manera eficiente es la búsqueda: permite el acceso a los elementos (teléfono y dirección, por ejemplo) almacenados a partir de una clave generada (usando el nombre o número de cuenta, por ejemplo). Funciona transformando la clave con una función hash en un hash, un número que identifica la posición (casilla o cubeta) donde la tabla hash localiza el valor deseado.

Idealmente, la función hash asignará cada clave a un depósito único, pero
la mayoría de los diseños de tablas hash emplean una función hash imperfecta,
que puede causar colisiones hash donde la función hash genera el mismo índice
para más de una clave. Tales colisiones deben ser acomodadas de alguna manera.

## Importante
**Este código solo es de propósito investigativo**

## Información
![Hash Table](https://upload.wikimedia.org/wikipedia/commons/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg)

Colisión hash resuelta por encadenamiento separado.

![Hash Collision](https://upload.wikimedia.org/wikipedia/commons/d/d0/Hash_table_5_0_1_1_1_1_1_LL.svg)

## Estructura del proyecto

```
javascript-hashmap/
├── src/
│   └── HashMap.js      # Implementación de la tabla hash
├── test/
│   └── HashMap.test.js # Suite de pruebas con Mocha + unit.js
├── package.json
└── pnpm-lock.yaml
```

## Requisitos

- **Node.js** >= 18
- **pnpm** >= 10 (gestor de paquetes recomendado)

## pnpm

Este proyecto utiliza [pnpm](https://pnpm.io/) como gestor de paquetes. La versión está fijada en `package.json` mediante el campo `packageManager` (`pnpm@10.22.0`), por lo que [Corepack](https://nodejs.org/api/corepack.html) usará automáticamente la versión correcta.

### Instalación de pnpm

Habilita Corepack (incluido con Node.js):

```bash
corepack enable
corepack prepare pnpm@10.22.0 --activate
```

Alternativamente, vía npm:

```bash
npm install -g pnpm
```

### Comandos comunes

| Acción                       | Comando                  |
| ---------------------------- | ------------------------ |
| Instalar dependencias        | `pnpm install`           |
| Agregar una dependencia      | `pnpm add <paquete>`     |
| Agregar dependencia de dev   | `pnpm add -D <paquete>`  |
| Eliminar una dependencia     | `pnpm remove <paquete>`  |
| Ejecutar un script           | `pnpm <script>`          |
| Ejecutar tests               | `pnpm test`              |
| Auditar dependencias         | `pnpm audit`             |
| Actualizar dependencias      | `pnpm update`            |

### ¿Por qué pnpm?

- **Eficiencia en disco:** usa un almacén global con enlaces simbólicos, evitando duplicar paquetes entre proyectos.
- **Velocidad:** instalación más rápida que `npm` o `yarn` clásico.
- **Estricto por defecto:** evita el acceso a dependencias no declaradas (`phantom dependencies`).
- **Lockfile determinista:** `pnpm-lock.yaml` garantiza instalaciones reproducibles.

## Instalación del proyecto

```bash
git clone https://github.com/ecaminero/javascript-hashmap.git
cd javascript-hashmap
pnpm install
```

## Uso

```javascript
const HashMap = require('./src/HashMap');

const map = new HashMap();

map.insert('nombre', 'Edwin');
map.insert('rol', 'developer');

const resultado = map.get('nombre');
console.log(resultado); // { key: <hash>, data: 'Edwin' }

console.log(map.getAllKeys()); // ['<hash1>', '<hash2>']
```

### API

| Método           | Descripción                                                            |
| ---------------- | ---------------------------------------------------------------------- |
| `insert(k, v)`   | Inserta un par clave/valor en el bucket correspondiente.               |
| `get(k)`         | Recupera el valor asociado a la clave. Devuelve `{ key, data }`.       |
| `length()`       | Tamaño actual del arreglo interno de buckets.                          |
| `getAllKeys()`   | Devuelve la lista de hashes generados como claves.                     |
| `hash(k)`        | Función hash interna que calcula el índice de la clave.                |

## Tests

El proyecto utiliza **Mocha** como runner y **unit.js** para las aserciones. Las pruebas insertan un millón de elementos para evidenciar el manejo de colisiones.

```bash
pnpm test
```

Para ejecutar Mocha directamente:

```bash
pnpm exec mocha test/
```

## References

- [Wikipedia](https://en.wikipedia.org/wiki/Hash_table)
- [YouTube](https://www.youtube.com/watch?v=shs0KM3wKv8&index=4&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [pnpm — Documentación oficial](https://pnpm.io/)

## Authors

*  **Edwin Caminero** - *Initial work* - [github](https://github.com/ecaminero)
