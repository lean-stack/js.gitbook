## Querying

### Selektoren

Document-API: https://developer.mozilla.org/en-US/docs/Web/API/document

* document.getElementById('eltId')
* document.getElementsByClassName('class')
* document.getElementsByTagName('tagname')

Die letzteren beiden Methoden existieren auch in der Element-Schnittstelle:
https://developer.mozilla.org/en-US/docs/Web/API/Element

* element.getElementsByClassName('class')
* element.getElementsByTagName('tagname')

### jQuery to the Rescue

* $('#eltId'), $('.class'), $('tagname')
* $('', context)

### HTML5 to rule them all

* document.querySelector('CSS selector wie bei jQuery')
* document.querySelectorAll('')

* element.querySelector
* element.querySelectorAll
