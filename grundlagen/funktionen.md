## Funktionen

### Definition

    function add (a, b) {
      return a + b;
    }

Aufruf:

    var result = add(17,4);

Dabei nennt man ```a``` und ```b``` die Parameter der Funktion und ```17``` und ```4``` die aktuellen Argumente. In JavaScript gilt im Übrigen nicht, dass die Anzahl der Parameter in der Definition und Argumente beim Aufruf übereinstimmen müssen.

Innerhalb des Funktionsrumpfs ist neben den Parametern die Variable ```arguments``` (die konkreten Arugumente) definiert - sowie über das Schlüsselwort ```this``` ein kontextabhängiger Wert. Zu ```this``` siehe [Dies ist this](grundlagen/dies_ist_this.html).

Beispiel zur Verwendung von ```arguments```:

    function sum () {
      var summe = 0, i;
      for( i=0; i < arguments.length; i++) {
        summe += arguments[i];
      }
      return summe;
    }

Die ```arguments```-Variable ist ein Objekt, das u.a. über die Eigenschaft ```length``` die genaue Anzahl der Argumente liefert und außerdem über einen Array-ähnlichen index-basierten Zugriff verfügt (zu Objekten und Arrays siehe die späteren Abschnitte).

### Funktionsausdrücke

Funktionen können auch in Ausdrücken verwendet werden. Man spricht dann von einer *function expression*. Dabei ist der Funktionsname optional und spielt im wesentlichen bei Rekursion eine Rolle, man spricht dann von einer anonymen Funktion:

    var sub = function (a,b) {
        return a - b;
    }

Ein wesentlicher Unterschied der beiden Varianten zeigt sich beim Aufruf: während eine Funktionsdeklaration auch unterhalb des Aufrufs stehen kann, kann die per Funktionsausdruck an eine Variable zugewiesene Funktion erst hinter der Auswertung aufgerufen werden. Siehe dazu auch **Hoisting** (**TODO oder Link**).

Im übrigen kann man auch deklarierte Funktionen an Variablen zuweisen, über die dann die Funktion aufgerufen werden kann.

    var addiere = add;
    addiere(17,4); // 21

### Lokale Variablen

Variablen, die innerhalb einer Funktion mit ```var``` deklariert werden, erhalten einen lexikalischen Scope, der ihre Gültigkeit auf die Funktion beschränkt. Außerhalb der Funktion sind diese nicht sichtbar - es sei denn wir vergessen das Schlüsselwörtchen ```var```.

    function tueWas() {
      var lokal = 17;
      global = 4;
    }

    tueWas();

    console.log(lokal);  // undefined
    console.log(global); // 4

JavaScript kennt keinen Block-Scope (d.h. lokale Variablen in einem Code-Block, beispielsweise innerhalb eines Schleifenrumpfs)!

### IIFE

*Immediatly Invoked Function Expressions*, kurs **IIFE** (gesprochen "Iffy") stellen ein probates Mittel dar, lokalen Block-Scope zu simulieren. Dabei wird eine anonyme Funktionsdefinition geklammert (runde Klammern) - das zwingt die Engine zur Auswertung - und im Anschluss gleich aufgerufen:

    (function () {

        // code

    })();

Es existiert eine zweite Schreibweise:

    (function () {

    }());

Äußerst sinnvoll sind solche IIFEs insbesondere als komplette "Ummantelung" unserer Skripte, da wir so sehr kontrolliert die Erstellung globaler Variablen handeln können:

    var global1 = 5;
    console.log(global1);  // 5

    (function(){

      var lokal = 10;
      console.log(lokal); // 10

      window.global2 = 15;

    })();

    console.log(lokal);   // undefined
    console.log(global2); // 15

Die Ausgaben 5, 10 und 15 erfolgen genau in dieser Reihenfolge.
