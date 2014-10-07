## Innere Funktionen und Closures

Funktionsdeklarationen und -ausdrücke können auch innerhalb von Funktionen stehen:

    // addiert nur positive Zahlen!
    function add (a, b) {
      var result = a;

      while( b-- > 0 )
        addOne();

      return result;

      function addOne (a) {
         result += 1;
      }
    }

Die Hilfsfunktion ```addOne``` ist nur innerhalb von ```add``` bekannt.

Zu beachten ist aber hier besonders, dass die lokale Variable ```result``` in der inneren Funktion bekannt ist!

### Closures

Betrachten wir nun das folgende Beispiel:

    function createCounter () {

      var count = 0;

      function inc() {
        return ++count;
      }

      return inc;
    }

Zur Erklärung: wir returnieren eine Funktion, die auf eine lokale Variable zugreift.

Also deklarieren die folgenden zwei zeilen jeweils eine Variable, die einen Funktionsausdruck erhält:

    var inc1 = createCounter();
    var inc2 = createCounter();

Über Aufrufe erhöhen beide jeweils ihren eigenen Zähler:

    inc1(); // 1
    inc1(); // 2;
    inc1(); // 3;
    inc2(); // 1; !!

Zu dem Zeitpunkt der Deklaration der Funktion "sieht" sie die lokale Variable ```count```. Was ist aber wenn wir die Funktion "später" aufrufen? Nun, die Engine rettet für uns die Variable, in dem sie einen *Closure-Scope* erstellt und die Variable darin der Funktion zur Verfügung stellt. Mit dem nächsten Aufruf von ```createCounter``` wird eine neue lokale Variable ```count``` erstellt, die nun ihrerseits in den Sichtbarkeitsbereich der innerern Funktion eingeschlossen wird. (Closure = Funktionsabschluss).

* Zitat (frei) aus der [Perl FAQ](http://perldoc.perl.org/perlfaq7.html#What%27s-a-closure?): Closure ist ein Begriff aus der Programmierung, der präzise definiert aber schwer zu beschreiben ist. :-)
* Zitat (Quelle vergessen): Closure is a notion out of the Lisp world that says if you define an anonymous function in a particular lexical context, it pretends to run in that context even when it's called outside the context.
* Wikipedia: Als Closure oder Funktionsabschluss bezeichnet man eine Programmfunktion, die sich ihren Erstellungskontext „merkt“. Beim Aufruf kann die Funktion dann auf diesen zugreifen, selbst wenn der Kontext außerhalb der Funktion schon nicht mehr existiert.

Häufig werden Closures (unbewusst) bei DOM-Eventhandlern eingesetzt. Und natürlich bei allen Formen der Modul-Patterns.



