## Literale und Variablen

### Primitive Literale

Folgende primitive Literale stehen zur Verfügung:

| Typ | Werte (beispielhaft) | typeof Ausgabe
| -- | -- | -- |
| Number | ```42``` oder ```3.14``` | ```"number"``` |
| Boolean | ```true``` oder ```false```| ```"boolean"``` |
| String | ```"JavaScript"``` oder ```'ECMAscript``` | ```"string"``` |
| null | ```null``` | ```"object"``` **!!** |
| undefined | ```undefined``` | ```"undefined"``` |

Zu ```null``` und ```undefined``` folgt näheres im nächsten Abschnitt.

Daneben existieren in JavaScript noch Varianten um Arrays, reguläre Ausdrücke und Objekte im Allgemeinen literal zu initialisieren. Dazu aber ebenfalls gesonderte Betrachtungen in späteren Abschnitten.

### Variablen

Variablen in JavaScript werden über das Schlüsselwort ```var``` definiert. Die Anweisung erzeugt je nach Kontext entweder eine globale Variable oder eine lokale Variable in einem definierten lexikalischen *Scope* (Gültigkeitsbereich). Falls ```var``` entfällt wird immer eine globale Variable angelegt.

Beispiele:

    var piGrob = 3.14;
    var vorname = "Klaus";
    var nachname = "Lage";
    var flag = true;
    var leer = null;
    var unbelegt;  // undefined

Wie hier zu erkennen ist, werden JavaScript-Anweisungen durch Semikolon getrennt; der Doppelslash ```//``` leitet einen Kommentar ein.

Natürlich ist auch eine etwas kürzere Form gültig:

    var a = 17,
        b = 4,
        c = 42;

Aber Achtung: ein versehentlich gesetztes Semikolon macht die folgende Variablendefinition unbedingt zu einer globalen(!) Variablen-Definition.
