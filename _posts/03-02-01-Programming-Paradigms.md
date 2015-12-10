---
isChild: true
anchor:  programming_paradigms
---

## Code Paradigma {#programming_paradigms_title}

PHP is een flexibele, dynamische taal die diverse programmeertechnieken ondersteunt. Het is dramatisch geëvolueerd
Door de jaren, met name de toevoeging van een solide object-georiënteerd model in PHP 5.0 (2004), anonieme functies en naamruimten in PHP 5.3 (2009), en eigenschappen in PHP 5.4 (2012).

### Objectgeoriënteerd Programmeren

PHP heeft een zeer complete set van objectgeoriënteerd programmeren functies, waaronder ondersteuning voor klassen, abstracte klassen, interfaces, erfenis, constructeurs, klonen, uitzonderingen, en nog veel meer.

* [Lees over Object-oriented PHP][oop]
* [Lees over Traits][traits]

### Functioneel Programmeren

PHP ondersteunt eersteklas functies, wat betekent dat een functie kan worden toegewezen aan een variabele. Zowel de gebruiker gedefinieerde en
ingebouwde functies kan worden verwezen door een variabele en dynamisch aangeroepen. Functies kunnen worden doorgegeven als argumenten
andere functies (een functie genaamd _Higher-order Functions_) en functies kunnen andere functies terug te keren.

Recursie, een functie die een functie om zichzelf te bellen mogelijk maakt, wordt ondersteund door de taal, maar de meeste PHP-code
richt zich op iteratie.

Nieuwe anonieme functies (met ondersteuning voor sluitingen) zijn sinds PHP 5.3 (2009) aanwezig.

PHP 5.4 het vermogen om te binden aan sluitingen scope van een object en ook verbeterde ondersteuning voor callables toegevoegd, dat
kan uitwisselbaar worden gebruikt met anonieme functies in vrijwel alle gevallen.

* Lees meer op [Functioneel Programmeren in PHP](/pages/Functional-Programming.html)
* [Lees meer over Anonieme Functies][anonymous-functions]
* [Lees meer over the Sluitings klasse][closure-class]
* [More details in the Closures RFC][closures-rfc]
* [Lees meer over Aanroepbaar][callables]
* [Lees meer over dynamische aanroepen functies `call_user_func_array()`][call-user-func-array]

### Meta Programmeren

PHP ondersteunt verschillende vormen van meta-programmering via mechanismen zoals de Reflection API en Magic Methods. Er zijn
veel Magische methoden beschikbaar, zoals `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, etc. waarmee
ontwikkelaars te haken in de klas gedrag. Ruby ontwikkelaars zeggen vaak dat PHP `method_missing` mist, maar het is verkrijgbaar `__call()` en `__callStatic()`.

* [Lees meer over magische methoden][magic-methods]
* [Lees meer over Reflection][reflection]
* [Lees meer over Overbelasting][overloading]


[oop]: http://php.net/language.oop5
[traits]: http://php.net/language.oop5.traits
[anonymous-functions]: http://php.net/functions.anonymous
[closure-class]: http://php.net/class.closure
[closures-rfc]: https://wiki.php.net/rfc/closures
[callables]: http://php.net/language.types.callable
[call-user-func-array]: http://php.net/function.call-user-func-array
[magic-methods]: http://php.net/language.oop5.magic
[reflection]: http://php.net/intro.reflection
[overloading]: http://php.net/language.oop5.overloading

