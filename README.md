# České svátky v JSON formátu

České svátky (jmeniny a státní svátky) podle dnů v roce ve formátu JSON (pro offline použití).

## Příklad použití v PHP:

```php
<?php
$jsonFile  = file_get_contents( __DIR__ . DIRECTORY_SEPARATOR . 'svatky.json' );
$array     = json_decode( $jsonFile, true );

// echo $array[ MĚSÍC ][ DEN ];
echo $array[12][31]; // Zobrazí svátek 31.12 'Silvestr'
echo $array[7][30];  // Zobrazí svátek 30.7  'Bořivoj'
echo $array[1][1];   // Zobrazí svátek 1.1   'Nový rok'
```
## Příklad použití v JS:

```js
// Načtení svátků
const holidaysPromise = fetch('svatky.json')
    .then(response => {
        if (!response.ok) {
            throw new Error('Nepodařilo se načíst svátky.');
        }

        return response.json();
    });

// Získání svátku podle měsíce a dne
async function getHoliday(month, day) {
    try {
        const holidays = await holidaysPromise;
        return holidays[month]?.[day] ?? null;
    } catch (error) {
        console.error(error);
        return null;
    }
}

// Použití
getHoliday(12, 31).then(holiday => {
    console.log(holiday); // Zobrazí svátek 31.12 'Silvestr'
});
```

## Podpora

**České svátky** jsou **open source** a **zdarma**. Podpořte proto prosím práci autora:

**BTC**: `bc1qznjr2949n6297307ct7exprr5n77l9dlnzd698`

## Licence

České svátky v JSON formátu jsou poskytovány pod licencí [MIT](https://opensource.org/license/mit/).