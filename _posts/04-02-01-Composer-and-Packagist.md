---
isChild: true
anchor:  composer_and_packagist
---

## Composer en Packagist {#composer_and_packagist_title}

Composer is een **briljante** pakket manager voor PHP. Een lijst van afhankelijkheden van uw project in een `composer.json` bestand en met een paar eenvoudige commando's, zal Composer automatisch afhankelijkheden van uw project en setup downloaden. Composer is analoog aan NPM in de node.js wereld of Bundler in de Ruby wereld.

Er zijn al veel van PHP bibliotheken die compatibel zijn met Composer zijn, klaar om te worden gebruikt in uw project. Deze
"pakketten" worden genoteerd op [Packagist], de officiële opslagplaats voor Composer-compatibele PHP bibliotheken.

### Hoe installeer je Composer

U kunt Composer lokaal te installeren (in uw huidige werkmap) of globaal (bijvoorbeeld /usr/local/bin, aanbevolen).
Laten we aannemen dat u wilt Composer systeem-wijd installeren:

{% highlight console %}
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
{% endhighlight %}

<strong>Notitie:</strong> Als het commando niet werkt door een ontbrekende rechten gebruik dan `sudo` voor mv

Dit zal `composer.phar` (een PHP binary archief) te downloaden. U kunt deze openenen met `php` om uw project te beheren.

<strong>Let op:</strong> Als u direct een code download via de opdrachtregel lees dan eerst de code om te kijken of deze veilig is.

#### Installeren op Windows

Voor Windows gebruikers is [ComposerSetup] het makkelijkst, na installatie is deze bruikbaar in de opdrachtregel.

### Hoe installeer je Composer (Handmatig)

Handmatig installeren van Composer is een geavanceerde techniek; Er zijn echter verschillende redenen waarom een ontwikkelaar Deze methode kan de voorkeur heeft in tegenstelling met de interactieve installatieprocedure. De interactieve installatie controleert uw PHP-installatie om ervoor te zorgen dat:

- Een goede versie van PHP wordt gebruikt
- `.phar` Bestanden correct kan worden uitgevoerd
- Bepaalde map permissies zijn ingesteld
- Bepaalde problematische extensies zijn niet geladen
- Bepaalde `php.ini` instellingen zijn ingesteld

Aangezien een handmatige installatie geen van deze controles uitvoerd, moet u beslissen of de trade-off is de moeite waard voor u. Als zodanig, hieronder staat hoe Composer handmatig te verkrijgen is:

{% highlight console %}
curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
chmod +x $HOME/local/bin/composer
{% endhighlight %}

Het pad `$HOME/local/bin` (of een map van uw keuze) moet in uw `$PATH` voorkomen. Dit resulteert in een 'composer` commando.
Als je documentatie tegenkomt, die aangeeft Composer draaien als `php composer.phar install`, kunt u dat vervangen dat met:

{% highlight console %}
composer install
{% endhighlight %}

Deze sectie zal aannemen dat u Composer systeem-breed geïnstalleerd hebt.

### Hoe defineren en Installeren van Vereisten (Dependencies)

Composer houd een oogje op de vereisten van uw project in een bestand genaamd `composer.json`, U kunt het handmatig bewerken of via Composer zelf. Het `composer require` commando voegt een vereiste toe aan uw project.
Als u geen `composer.json` bestand heeft dan maakt Composer deze voor u aan.
Hieronder een voorbeeld om [Twig] te vereisen

{% highlight console %}
composer require twig/twig:~1.8
{% endhighlight %}

U kunt ook de opdracht van de `composer init` leidt u door het creëren van een volledig `composer.json` bestand voor uw project. Hoe dan ook, als je eenmaal je `composer.json` kun je Composer vertellen om de vereisten te downloaden en te installeren in de `vendor/` map. Dit geld ook voor projecten die je gedownload hebt die al een `composer.json` bestand bevatten:

{% highlight console %}
composer install
{% endhighlight %}

Vervolgens voeg deze regel aan primaire PHP-bestand van uw toepassing; dit zal PHP vertellen Composer's autoloader te gebruiken voor uw project vereisten.

{% highlight php %}
<?php
require 'vendor/autoload.php';
?>
{% endhighlight %}

Nu kunt u uw project vereisten te gebruiken, en ze zullen worden on-demand worden geladen.

### Updaten van vereisten

Composer creërt een bestand `composer.lock` waarin de exacte versie van elk pakket in woord opgeslagen het woord gecreërt waneer je voor het eerst `composer install` uitvoerd. Als je je project deelt dan zullen andere programmeurs ook jouw `composer.lock` bestand nodig hebben waneer hun `composer install` uitvoeren dan krijgen zij dezelfde versie als u. Om de vereisten te updaten voert u `composer update` uit.

This is most useful when you define your version requirements flexibly. For instance a version 
requirement of `~1.8` means "anything newer than `1.8.0`, but less than `2.0.x-dev`". You can also use 
the `*` wildcard as in `1.8.*`. Now Composer's `composer update` command will upgrade all your
dependencies to the newest version that fits the restrictions you define.

Dit is het gemakkelijkst als uw versie vereisten flexibel zijn. Als voorbeeld als een project een eis heeft van versie `~1.8` dan betekend dit "Alles nieuwer dan `1.8.0` maar `2.0.x-dev` niet". Je kan ook `*` als joker gebruiken als in `1.8.*`. Nu is `composer update` zo ingesteld dat ze naar de nieuwste versie van uw eis geüpdatet worden

### Update Kennisgeving

Om meldingen over nieuwe versies te ontvangen kunt u zich aanmelden voor [VersionEye], een webservice dat je GitHub en BitBucket accounts kunnen monitoren voor `composer.json` bestanden en stuurt e-mails als er een nieuwere versie beschikbaar is.

### Checking your dependencies for security issues

The [Security Advisories Checker] is a web service and a command-line tool, both will examine your `composer.lock`
file and tell you if you need to update any of your dependencies.

### Handling global dependencies with Composer

Composer can also handle global dependencies and their binaries. Usage is straight-forward, all you need
to do is prefix your command with `global`. If per example you wanted to install PHPUnit and have it 
available globally, you'd run the following command:

{% highlight console %}
composer global require phpunit/phpunit
{% endhighlight %}

This will create a `~/.composer` folder where your global dependencies reside. To have the installed
packages' binaries available everywhere, you'd then add the `~/.composer/vendor/bin` folder to your 
`$PATH` variable.

* [Learn about Composer]

[Packagist]: http://packagist.org/
[Twig]: http://twig.sensiolabs.org
[VersionEye]: https://www.versioneye.com/
[Security Advisories Checker]: https://security.sensiolabs.org/
[Learn about Composer]: http://getcomposer.org/doc/00-intro.md
[ComposerSetup]: https://getcomposer.org/Composer-Setup.exe
