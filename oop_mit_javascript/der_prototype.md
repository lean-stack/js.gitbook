## Der Prototype

Wer in einer REPL-Konsole mit den Objekten gearbeitet hat, wird festgestellt haben, dass mehr als unsere definierten Properties auf den Punktoperator vorgeschlagen werden.

Jedes Objekt verfügt über eine interne Property ```__proto__``` (doppelte Unterstriche!). Intern, weil diese nicht offiziell spezifiziert wurde - und in ES5 sogar deprecated wurde (in ES6 aber offiziell wird). Diese Property verweist auf ein Prototyp-Objekt. Eigenschaften dieses Objektes werden mit berücksichtigt, wenn das Objekt nicht über die Eigenschaft selbst verfügt.

    var kontoProto = {
      einzahlen: function (betrag) {this.stand += 0}
      toString: function () { return "Konto Nr " + nr;}
    }

    var konto1 = {
      __proto__: kontoProto,
      nr: 1001
    }

    var konto2 = {
      __proto__: kontoProto,
      nr: 1002
    }

Und nun können unsere Konten wie folgt verwendet werden:

    konto1.einzahlen(1000);
    console.log(konto1.toString());

Es gilt übrigens:

    konto2.hasOwnProperty("nr"); // true
    konto2.hasOwnProperty("stand"); // false

    // aber
    konto1.hasOwnProperty("stand"); // true

Dynamische Änderungen am Prototyp-Objekt sind natürlich sofort über alle Objekte abrufbar (solange diese keine eigene Property eines solchen Namens haben!).

    kontoProto.BLZ = "12345678";
    kontoProto.stand = 5;

    konto1.BLZ; // "12345678"
    konto1.stand; // 1000
    konto2.stand; // 5

Für den Property-Zugriff gilt also:

* Lesend: falls das Objekt keine eigene Property dieses Namens hat, wird die Suche im Prototypen fortgesetzt. Und danach im Prototypen des Prototypen - bis dieser ```null``` ist. Im letzteren Fall wird ```undefined``` zurückgegeben.
* Schreibend: falls das Objekt keine eigene Property dieses Namens hat, wird eine neue erstellt. Sonst natürlich die eigene geändert.

Dieses lesende Verhalten nennt man *prototype chain*.

In ECMAscript 5 erfolgte der Zugriff auf den Prototypen übrigens wie folgt:

    // Setzen:
    var konto3 = Object.create(kontoProto);
    konto3.nr = 1003;

    // Lesend:
    Object.getPrototypeOf(konto3);

Properties in JavaScript verfügen übrigens auch über Aspekte wie "Writeable" und "Enumerable", dazu siehe aber ensprechende Artikel im Netz.

