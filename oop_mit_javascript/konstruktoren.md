## Konstruktoren

Um Objekte vereinfacht anzulegen, lassen sich auch in JavaScript Konstruktoren definieren. Im Grunde kann jede JavaScript-Funktion als Konstruktor dienen, denn dem Funktionsaufruf wird einfach das Schlüsselwort ```new``` vorangestellt, zurückgeben wird dann immer ein neu angelegtes Objekt.

    function Konto (nr) {
      this.nr = nr;
      this.stand = 0.0;
      this.einzahlen = function (betrag) {this.stand += betrag};
    }

    var konto1 = new Konto(1001);
    var konto2 = new Konto(1002);

    konto1.einzahlen(1000);
    konto1.nr; // 1001
    konto1.stand; // 1000
    konto2.stand; // 0

    konto1 instanceof Konto; // true

Merkmale eines Konstruktors sind der Großbuchstabe zu Beginn des Namens sowie die Verwendung des ```this``` im Rumpf.

Aber es gilt nun:

    konto1.hasOwnProperty("einzahlen"); // true
    konto2.hasOwnProperty("einzahlen"); // true

Wie vermeiden wir die erneute Redundanz?

Jede Funktion (Objekte!) verfügt über eine Eigenschaft ```prototype```. Das darin abgelegte Objekt wird zum Prototypen des mit dem Konstruktor angelegten Objektes.

    function Konto (nr) {
      this.nr = nr;
    }

    Konto.prototype.stand = 0.0;
    Konto.prototype.einzahlen = function (betrag) {
      this.stand += betrag
    };

    var konto1 = new Konto();
    konto1.hasOwnProperty("nr"); // true
    konto1.hasOwnProperty("stand"); // false

Der ```instanceof```-Operator prüft übrigens, ob der Konstruktor-Prototyp in der Prototyp-Chain des Objektes vorkommt.


