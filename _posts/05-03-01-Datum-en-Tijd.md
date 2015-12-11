---
isChild: true
anchor:  date_and_time
---

## Datum en Tijd {#date_and_time_title}

PHP heeft een klasse met de naam DateTime om je te helpen bij het lezen, schrijven, vergelijken en berekenen met datum en tijd. Er
zijn veel datum en tijd-gerelateerde functies in PHP naast DateTime, maar het biedt object-georiënteerde interface
de meest voorkomende toepassingen. Het kan tijdzones behandelen, maar dat valt buiten deze korte introductie.

Om te beginnen werken met DateTime, zetten ruwe datum en tijd string naar een object met de `createFromFormat()` methode of via `new DateTime` om de huidige datum en tijd te krijgen.
Gebruik de `format` functie om de datum en of tijd om te zetten naar een string om deze op het scherm te tonen.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start datum: ' . $start->format('Y-m-d') . "\n";
{% endhighlight %}

Rekenen met DateTime is mogelijk door de DateInterval klasse. DateTime heeft methodes/functies als `add()`(toevoegen) en `sub()`. 
Schrijf geen code die dezelfde datum/tijd/seconde vereisen, zo ook zomer/winter tijd en alternative tijdzones, dit wel gebruiken zal uw script niet ten goede komen. Gebruik daarom een datum interval doormiddel van de `diff()` functie. Dit zal een nieuwe DateInterval creëren die makkelijk te tonen is op het scherm.

{% highlight php %}
<?php
// Creër een kopie van $start en voeg één maand en 6 dagen toe
$end = clone $start;
$end->add(new DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Verschil: ' . $diff->format('%m Maand, %d Dagen (Totaal: %a dagen)') . "\n";
// Verschil: 1 Maand, 6 Dagen (Totaal: 37 dagen)
?>
{% endhighlight %}

Met DateTime objecten kan je standaard vergelijkingen gebruiken:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is eerder dan het einde!\n";
}
?>
{% endhighlight %}

Een laatste voorbeeld om de DatePeriode klasse te tonen. Het wordt gebruikt om itereren over terugkerende gebeurtenissen. Het kan 2 DateTime objects krijgen, start en end (einde), en het interval waarvoor alle gebeurtenissen terug daartussen.

{% highlight php %}
<?php
// Print alle Donderdagen tussen $start en $end
$periodInterval = DateInterval::createFromDateString('first thursday');
$periodIterator = new DatePeriod($start, $periodInterval, $end, DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('d-m-Y') . ' ';
}
?>
{% endhighlight %}

* [Lees meer over DateTime][datetime]
* [Lees meer date formaten][dateformat] (geaccepteerde datum notaties door PHP)

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date
