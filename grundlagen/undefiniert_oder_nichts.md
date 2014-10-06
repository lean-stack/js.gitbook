## JavaScript:  ```undefined``` und ```null```

### ```null```

* ```null``` ist ein Schlüsselwort und steht für das Fehlen eines Wertes
  bzw. einen leeren Wert.
* ```null``` wird verwendet, um einen Null-Wert für Strings, Zahlen oder
  Objekte anzuzeigen
* Interessanterweise liefert ```typeof(null)``` als Ergebnis "object". Laut
  David Flanagan, um das spezielle Null-Objekt zu betonen. Das MDN hält es für einen ECMAscript-Bug.

### ```undefined```

* ```undefined``` ist eine vordefinierte globale Variable:

        undefined === window.undefined; // true

* Eine nicht initialisierte Variable hat den Wert ```undefined```
* Nicht existierende Objekt-Properties oder Array-Elemente sind ```undefined```
* Funktionen ohne Rückgabe-Wert liefern ```undefined```
* Funktions-Parameter ohne Argument sind ```undefined```
* ```typeof(undefined)``` liefert "undefined".

### Gleichheit der beiden Werte

Es gilt:

    null == undefined; // true
    null === undefined; // false

### Resümee

Bei der Verwendung sollte ```null``` für einen erwarteten Wert stehen,
```undefined``` eher für einen Fehler.

### Links

* [Web Tools Weekly #62](http://webtoolsweekly.com/)
* [MDN zu ```null```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null)
* [MDN zu ```undefined```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined)

