---
anchor: code_style_guide
---

# Code-stijl Gids {#code_style_guide_title}

De PHP-gemeenschap is groot en divers, bestaande uit talloze bibliotheken, frameworks en componenten. Het is gebruikelijk dat PHP ontwikkelaars een aantal van deze en te combineren in een enkel project. Het is belangrijk dat PHP-code werken aan een manier om (zo dicht als mogelijk) een gemeenschappelijke code stijl om het makkelijk maken, zodat het voor ontwikkelaars makkelijker is om te mixen en matchen tussen verschillende componenten in hun projecten.

De [Framework Interop Group][fig] heeft een reeks aanbevelingen qua code-stijl goedgekeurd. Niet alle van hen zijn gerelateerd aan de code-stijl, maar die dat wel doen zijn [PSR-0][psr0], [PSR-1][psr1], [PSR-2][psr2] en [PSR-4][psr4]. Deze aanbevelingen zijn slechts een set van regels die sommige projecten zoals Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, etc gebruiken. U kunt ze gebruiken voor je eigen projecten, of doorgaan met uw eigen gebruik persoonlijke stijl.

Idealiter moet je PHP-code schrijven die voldoet aan een bekende standaard. Dit kan een combinatie van PSR's zijn of een van hen, of code-stijl zoals aangegeven door PEAR of Zend. Dit maakt het voor andere ontwikkelaars makkelijker om jouw code te lezen en deze te gebruiken in hun applicaties.

* [Lees over PSR-0][psr0]
* [Lees over PSR-1][psr1]
* [Lees over PSR-2][psr2]
* [Lees over PSR-4][psr4]
* [Lees over PEAR Coding Standards][pear-cs]
* [Lees over Symfony Coding Standards][symfony-cs]

Je kan [PHP_CodeSniffer][phpcs] gebruiken om jouw code te controleren of deze voldoet aan een van deze aanbevelingen, en plugins voor tekst bewerkers zoals [Sublime Text 2][st-cs] geven continue feedback.
Je kan de code-stijl laten repareren door [PHP Coding Standards Fixer][phpcsfixer] dit tooltje heeft een zeer goed getest code bestand.
Een andere optie is [php.tools][phptools], die populair is geworden door de [sublime-phpfmt][sublime-phpfmt] plugin.
Terwijl het nieuwere, het maakt grote verbeteringen in de prestaties, waardoor de code real-time en vloeiender woord gecontroleerd.

Je kan phpcs zelf laten testen door:

    phpcs -sw --standard=PSR2 file.php

Het zal de fouten laten zien, en ook hoe je deze kan oplossen.
Het kan ook nuttig zijn om dit commando in een git hook te doen.
Op die manier zorg je altijd dat de code de gekozen standaard bevatten, en eraan voldoet.

Engels heeft de voorkeur voor alle symbool namen en code-infrastructuur. Reacties kunnen in elke taal geschreven worden gemakkelijk leesbaar door alle huidige en toekomstige partijen die kunnen werken op de codebase.


[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
[phptools]: https://github.com/phpfmt/php.tools
[sublime-phpfmt]: https://github.com/phpfmt/sublime-phpfmt
