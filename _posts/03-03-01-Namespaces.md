---
isChild: true
anchor:  namespaces
---

## Namespaces {#namespaces_title}

Zoals hierboven vermeld, de PHP-gemeenschap heeft veel ontwikkelaars die veel code. Dit betekent dat PHP een bibliotheek code kan dezelfde klasse naam te gebruiken als een andere bibliotheek. Wanneer beide bibliotheken worden gebruikt in dezelfde naamruimte, kunnen ze botsen en problemen te veroorzaken.

_Namespaces_ dit probleem op. Zoals beschreven in de PHP manuel kan namespaces worden vergeleken operating
systeem mappen die _namespace_ bestanden; twee bestanden met dezelfde naam kunnen naast elkaar bestaan in afzonderlijke mappen. Hetzelfde,
twee PHP klassen met dezelfde naam kunnen naast elkaar bestaan in afzonderlijke PHP naamruimten. Het is zo simpel als dat.

Het is belangrijk voor u om uw code dat u namespaces gebruikt, zodat deze door andere ontwikkelaars kan worden gebruikt zonder angst van problemen met andere bibliotheken.

Een aanbevolen manier om namespaces gebruiken is geschetst in [PSR-4][psr4], die streeft naar een standaard bestandsformaat, klasse te bieden en namespace conventie om plug-and-play-code te creëren.

In oktober 2014 is de vorige PHP-autoloading standaard: [PSR-0][psr0] vervallen, en is vervangen door
[PSR-4][psr4]. Momenteel zijn beide zijn nog steeds perfect bruikbaar en PSR-0 is niet weg. PSR-4 vereist PHP 5.3 en veel PHP 5.2-only projecten die implementeren momenteel PSR-0. Gelukkig gebruiken projecten die beginnen aan hun versievereisten, wat betekent PSR-0 wordt minder gebruikt.

Als je een autoloader standaard te gebruiken voor een nieuwe toepassing of pakket, dan wil je bijna zeker kijken naar PSR-4.

* [Lees meer over Namespaces][namespaces]
* [Lees meer over PSR-0][psr0]
* [Lees meer over PSR-4][psr4]


[namespaces]: http://php.net/language.namespaces
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
