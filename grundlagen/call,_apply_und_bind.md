## call, apply und bind

In *realworld*-Code begegnen uns oft die die im Titel genannten Methoden. Dabei rufen ```call``` und ```apply``` jeweils die betroffenen Methoden direkt auf währen ```bind``` eine *neue* Funktion definiert.

### call und apply

Unterschiede diesen beiden  ist die Übergabe der Parameter:

    function add (a, b) {
      return a+b;
    }

    add.call( null, 17, 4 );   // 21
    add.apply( null, [17, 4]); // 21

Das erste Argument - in diesem Beispiel jeweils ```null``` - setzt den Wert des ```this```-Schlüsselwortes in der Funktion. Unsere arbeite nicht mit diesem, also irrelevant.

Sinn?

* Aufruf von Methoden (Objekt-Methoden) für Objekte, die über diese Methode nicht verfügen. ??

Beispiele:

    // Anwendung der forEach-Methode auf ein nicht Array
    // - aber es ist Array-like (length und Index-Zugriff)
    [].forEach.call( arguments, function(elt) {});

    // macht aus dem Array-like arguments ein Array
    var args = [].slice.call(arguments);

    var numbers = [5, 6, 2, 3, 7];
    /* using Math.min/Math.max apply */
    var max = Math.max.apply(null, numbers);

* Interessantere Anwendungsfälle finden sich in der OOP.

### bind

Zunächst ein Beispiel mit der add-Funktion von oben:

    var addiereFuenf = add.bind( null, 5);
    addiereFuenf(7); // 12

Hier wird eine neue Funktion erstellt, indem Parameter der Ausgangsfunktion an Werte gebunden werden. Man nennt dies auch *partial application*. Der ```null```-Wert setzt wieder den ```this```-Wert.

