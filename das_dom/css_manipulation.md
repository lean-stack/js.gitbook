## CSS Manipulation

### Manipulation des class-Attributes

* Legacy JavaScript

        elt.getAttribute('class');
        elt.setAttribute('class','class1 class2');

* classList-API

        elt.classList;
        elt.classList.add('class1');

* jQuery API

        $elt.addClass('class1');
        $elt.removeClass('class1');
        $elt.toggleClass('class1');
