## Dies ist ```this```

Vorneweg ein Link: [Erklärung im MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

Eine grobe Zusammenfassung der Werte, die ```this``` annehmen kann:

* Im globalen Kontext: das globale Objekt ```window``` (im Browser).
* In Funktionen, die einfach aufgerufen werden: das globale Objekt ```window```
* In Funktionen, die über ```call``` oder ```apply``` aufgerufen werden oder über ```bind``` gebunden werden: der erste Parameter (thisArg).
* In Funktionen, die als DOM-Eventhandler definiert werden: das Element, dass das Event auslöste.
* In der OOP in Methoden und Konstruktoren: die Objektinstanz.

