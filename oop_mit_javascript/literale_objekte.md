## Literale Objekte

In JavaScript können einzelne Objekte einfach literal erzeugt werden:

    var konto1 = {

        // Eigenschaften
        nr: 1001,
        stand: 0.0,

        // Methoden
        einzahlen: function (betrag) {
            this.stand += betrag;
        }
    }

Leeres Objekt:

    var empty = {};

Objekt-Konstruktor:

    var konto2 = new Object({ nr: 1002, stand: 0.0 });

Objekte sind also Maps ähnlich (Key-Value-Zuordnungen), der Key-Typ ist übrigens String. Methoden sind also Funktionsausdrücke, die an Properties zugewiesen werden. Das ```this```-Schlüsselwort erhält bei der Ausführung das Objekt selbst als Wert.

Der Member-Zugriff erfolgt auf zwei Arten:

* Den Punkt-Operator ```console.log(konto1.stand);```
* Mit eckigen Klammern: ```konto2["stand"] = 1000```

Die zweite Variante ist natürlich insbesondere beim dynamischen Property-Zugriff interessant (bzw. falls der Property-Name z.B. numerisch ist oder Leerzeichen enthält).

Properties können natürlich jederzeit dynamisch ergänzt werden und über das Keyword ```delete``` auch gelöscht werden:

    konto2.einzahlen = function (betrag) {
        this.stand += betrag;
    }

Hier sieht man auch schon die erste Redundanz: die Methode ```einzahlen``` ist für jedes Objekt zu definieren.

Bemerkung: Auch ohne die explizite Definition der Methode lässt sich diese über ```konto1``` und die call- oder apply-Methode aufrufen:

    konto1.einzahlen.call( konto2, 2000);

In JavaScript können Objekte also direkt angelegt werden, Abstraktionsschichten können gegebenenfalls später folgen.
