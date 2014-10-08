## Arrays

Mit den Arrays führe ich hier die ersten Objekte(?) in JavaScript ein. Dazu passt die Bemerkung, dass auch zum Beispiel Funktionen in JavaScript Objekte sind. Weitere vordefinierte Objekttypen sind: ```Date```, ```RegExp```, ```Number```, ```Boolean```, ```String```, ...

Ok, aber zurück zu Arrays.

### Definition

    var zahlen = new Array( 1,2,3,4,5,6 );
    var primZahlen = [ 2,3,5,7,11,13,17 ];

Letztere (literale) Variante ist vorzuziehen. Arrays verfügen über Eigenschaften (z.B. ```length```) und Methoden ( ```push```, ```pop```, ```unshift```, ```shift```, ```map```, ```reduce```, ```forEach```, ...). Siehe [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Array_instances).

Und natürlich lässt sich auf Arrays über Indizes auf die Elemente zugreifen:

    var erstePrimzahl = primZahlen[0];
    zahlen[6] = 7;

    for( var i = 0; i < zahlen.length; i++ ) {
        console.log( zahlen[i] );
    }

