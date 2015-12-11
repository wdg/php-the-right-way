---
isChild: true
anchor:  command_line_interface
---

## Opdrachtregel {#command_line_interface_title}

PHP is gemaakt om webapplicaties te schrijven, maar is ook handig voor scripting command line interface (CLI) programma's.
Command line PHP-programma's kan helpen bij het automatiseren van veel voorkomende taken, zoals het testen, implementatie, en applicatiebeheer.

CLI PHP-programma's zijn krachtig, omdat u de code van uw app kunt gebruiken direct zonder te maken en zorgen voor een web-
GUI voor. Zet zeker **niet** uw CLI PHP scripts in uw publieke web root!

Probeer het uitvoeren van PHP uit uw opdrachtregel:

{% highlight console %}
> php -i
{% endhighlight %}

De `-i` optie zal uw PHP configuratie af te drukken, net als de [`phpinfo()`][phpinfo] functie.

De `-a` optie biedt een interactieve shell, vergelijkbaar met Ruby's IRB of python interactieve shell. Er zijn een aantal andere [opdrachtregel opties][cli-options].

Laten we schrijven een eenvoudige "Hallo, $naam" CLI-programma. Om het uit te proberen, maak dan een bestand met de naam `hallo.php`, zoals hieronder.

{% highlight php %}
<?php
if ($argc !== 2) {
    echo "Gebruik: php hallo.php [naam].\n";
    exit(1);
}
$name = $argv[1];
echo "Hallo, $name\n";
?>
{% endhighlight %}

PHP stelt twee speciale variabelen op basis van de argumenten van je script wordt uitgevoerd met. [`$argc`][argc] is een integer
variabele met het argument *count* en [`$argv`][argv] is eenvariabele met elk argument van *waarde*.
Het eerste argument is altijd de naam van uw PHP-script, in dit geval `hallo.php`.

De `exit()` uitdrukking wordt gebruikt met een niet-nul getal laat het reservoir dat de opdracht is mislukt. Algemeen gebruikt
exit codes kunnen [hier][exit-codes] gevonden worden.

Om ons bovenstaande script uit te voeren, vanaf de opdrachtregel type:

{% highlight console %}
> php hallo.php
Gebruik: php hallo.php [naam]
> php hallo.php wereld
Hallo, Wereld
{% endhighlight %}


 * [Leer meer over php vanaf de opdrachtregel][php-cli]
 * [Leer meer over het opzetten van PHP op de windows opdrachtregel][php-cli-windows]


[phpinfo]: http://php.net/function.phpinfo
[cli-options]: http://php.net/features.commandline.options
[argc]: http://php.net/reserved.variables.argc
[argv]: http://php.net/reserved.variables.argv
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: http://php.net/features.commandline
[php-cli-windows]: http://php.net/install.windows.commandline
