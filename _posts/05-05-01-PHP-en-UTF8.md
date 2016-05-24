---
title:   Working with UTF-8
isChild: true
anchor:  php_and_utf8
---

## Werken met UTF-8 {#php_and_utf8_title}

_Deze sectie werd oorspronkelijk geschreven door [Alex Cabal](https://alexcabal.com/) over bij [PHP Best Practices](https://phpbestpractices.org/#utf-8) en is gebruikt als basis voor onze eigen UTF-8 advies._

### Er is geen one-liner. Wees voorzichtig, gedetailleerd en consistent.

PHP ondersteunt nu noh geen Unicode op een laag niveau. Er zijn manieren om ervoor te zorgen dat UTF-8 strings worden verwerkt, maar het is niet gemakkelijk, en het vereist veel kunde in bijna alle niveaus van de web applicatie, van HTML naar SQL PHP. We zullen streven een korte, praktische samenvatting.

### UTF-8 op PHP niveau

De basis string operaties, als het samenvoegen van 2 strings en strings toewijzen aan variabelen, hebben niets speciaals nodig voor UTF-8. Ahoewel de meeste stringfuncties als `strpos()` en `strlen()`, hebben geen speciale aandacht nodig, deze functies hebben meestal een `mb_*` tegenhanger: als voorbeeld `mb_strpos()` en `mb_strlen()`. Deze `mb_*` strings zijn gemaakt voor u en beschikbaar via de [Multibyte String Extensie], en zijn specifiek ontworpen voor het gebruik met Unicode strings.

U moet de `mb_*` functies gebruiken waneer u een werkt met een Unicode-tekenreeks, Bijvoorbeeld, als u `substr()` gebruikt op een UTF-8 tekenreeks, dan is er een grote kans dat het resultaat een aantal onleesbaar halve karakters bevat. De juiste manier om het te gebruiken is de tegenhanger met multibyte ondersteuning namenlijk `mb_substr()`.

Het moeilijke deel is onthouden dat u de `mb_*` functies ten alle tijde moet gebruiken. Als u het maar een keer vergeet dan is u Unicode string niet goed verwerkt, en daardoor dus onleesbaar en onmogelijk om (juist) verder te verwerken.

Niet alle string functies hebben een `mb_*` tegenhanger. Als er niet een is voor wat je wilt doen, dan heeft u helaas pech.

U moet de `mb_internal_encoding()` functie in het begin van elk PHP-script zetten (of in de top van een bestand wat u included/required), en de `mb_http_output()` functie moet u uitvoeren zodra u de code een uitvoer naar de browser stuurt.
Expliciet definiëren van de codering van de strings bespaart u een hoop hoofdpijn gaande de weg.

Bovendien zijn er veel PHP-functies voor verwerken van strings, die een optionele parameter hebben zodat u de teken 
codering kan opgeven. U moet altijd expliciet UTF-8 aangeven als de optie. Bijvoorbeeld, `htmlentities()` heeft een optie voor tekencodering, en je moet altijd UTF-8 te geven als het omgaan met dergelijke strings. Merk op dat met ingang van PHP 5.4.0, UTF-8 de standaard codering voor `htmlentities ()` en `htmlspecialchars ()` is.

Tot slot, als u een applicatie uitbrengt is het niet zeker dat alle systemen de `mbstring` extensie geladen hebben, Overweeg dan om het [patchwork/utf8] Composer pakket te gebruiken. Deze gebruikt de `mbstring` extensie als deze beschikbaar is en valt anders terug op niet-specifiek voor UTF-8 functies.

[Multibyte String Extensie]: http://php.net/book.mbstring
[patchwork/utf8]: https://packagist.org/packages/patchwork/utf8

### UTF-8 op Database niveau

Als uw PHP-script toegang tot MySQL heeft, er is een kans dat je stings kan worden opgeslagen als niet-UTF-8 strings in de database, zelfs als u al het bovenstaande voorzorgsmaatregelen gevolgd.

Om er zeker van te zijn dat u PHP strings in MySQL als UTF-8 worden opgeslagen, wees er dan zeker van dat uw database en tabellen zijn ingesteld op de `utf8mb4` karakter set, En dat u de `utf8mb4` heeft meegegeven aan uw PDO verbindingsstring. Zie de voorbeelden hier beneden dit is _Erg Belangrijk_

Merk op dat u de `utf8mb4` tekenset voor volledige UTF-8 ondersteuning, en niet de` utf8` tekenset moet gebruiken! Zie Verderop waarom.

### UTF-8 op browser niveau

Gebruik de `mb_http_output()` functie om ervoor te zorgen dat uw PHP-script uistuurd als UTF-8 strings in uw browser.

De browser moet door de HTTP-response verteld worden dat deze pagina UTF-8 is, vroeger deed men dat via de [charset `<meta>` tag](http://htmlpurifier.org/docs/enduser-utf8.html) in de `<head>` tag van uw pagina. Dit is een correcte manier maar om de `Content-Type` in te stellen in de HTTP-header is [stukken sneller (engels)](https://developers.google.com/speed/docs/best-practices/rendering#SpecifyCharsetEarly).

{% highlight php %}
<?php
// Vertel het PHP dat wij UTF-8 strings gebruiken tot het einde van het script
mb_internal_encoding('UTF-8');
 
// Vertel PHP dat we UTF-8 naar de browser sturen
mb_http_output('UTF-8');
 
// Onze UTF-8 test string 
$string = 'Êl síla erin lû e-govaned vîn.';
 
// Transformeren de string op een bepaalde manier met een multibyte-functie
// Merk op hoe we snijden de string op een niet-ASCII-teken voor demonstratiedoeleinden
$string = mb_substr($string, 0, 15);
 
// Verbinding maken met een database om de getransformeerde reeks op te slaan
// Zie de PDO voorbeeld in dit document voor meer informatie
// Let op de `charset = utf8mb4` in de Data Source Name (DSN)
$link = new PDO(
    'mysql:host=uw-hostname;dbname=uw-db;charset=utf8mb4',
    'uw-gebruikersnaam',
    'uw-wachtwoord',
    array(
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
        PDO::ATTR_PERSISTENT => false
    )
);
 
// Opslaan van onze getransformeerde string als UTF-8 in onze database
// Uw DB en tabellen zijn in de utf8mb4 tekenset, toch?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();
 
// Ophalen van de string om te bewijzen het was juist opgeslagen
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();
 
// Bewaar het resultaat in een object dat we later in onze HTML zetten
$result = $handle->fetchAll(\PDO::FETCH_OBJ);

header('Content-Type: text/html; charset=UTF-8');
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>UTF-8 test pagina</title>
    </head>
    <body>
        <?php
        foreach($result as $row) {
            print($row->Body); // Dit moet de juiste verwerking van onze getransformeerde UTF-8-tekenreeks naar de browser moeten zijn
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Lees meer
_De artikelen hieronder zijn Engelstalig_

* [PHP Manual: String Operations](http://php.net/language.operators.string)
* [PHP Manual: String Functions](http://php.net/ref.strings)
    * [`strpos()`](http://php.net/function.strpos)
    * [`strlen()`](http://php.net/function.strlen)
    * [`substr()`](http://php.net/function.substr)
* [PHP Manual: Multibyte String Functions](http://php.net/ref.mbstring)
    * [`mb_strpos()`](http://php.net/function.mb-strpos)
    * [`mb_strlen()`](http://php.net/function.mb-strlen)
    * [`mb_substr()`](http://php.net/function.mb-substr)
    * [`mb_internal_encoding()`](http://php.net/function.mb-internal-encoding)
    * [`mb_http_output()`](http://php.net/function.mb-http-output)
    * [`htmlentities()`](http://php.net/function.htmlentities)
    * [`htmlspecialchars()`](http://php.net/function.htmlspecialchars)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Handling UTF-8 with PHP](http://www.phpwact.org/php/i18n/utf-8)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Bringing Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
* [Stack Overflow: DOMDocument loadHTML does not encode UTF-8 correctly](http://stackoverflow.com/questions/8218230/php-domdocument-loadhtml-not-encoding-utf-8-correctly)
