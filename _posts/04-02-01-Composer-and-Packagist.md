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

<strong>Let Op:</strong> Als u direct een code download via de opdrachtregel lees dan eerst de code om te kijken of deze veilig is.

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

### How to Define and Install Dependencies

Composer keeps track of your project's dependencies in a file called `composer.json`. You can manage it
by hand if you like, or use Composer itself. The `composer require` command adds a project dependency 
and if you don't have a `composer.json` file, one will be created. Here's an example that adds [Twig]
as a dependency of your project.

{% highlight console %}
composer require twig/twig:~1.8
{% endhighlight %}

Alternatively the `composer init` command will guide you through creating a full `composer.json` file
for your project. Either way, once you've created your `composer.json` file you can tell Composer to
download and install your dependencies into the `vendor/` directory. This also applies to projects 
you've downloaded that already provide a `composer.json` file:

{% highlight console %}
composer install
{% endhighlight %}

Next, add this line to your application's primary PHP file; this will tell PHP to use Composer's 
autoloader for your project dependencies.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Now you can use your project dependencies, and they'll be autoloaded on demand.

### Updating your dependencies

Composer creates a file called `composer.lock` which stores the exact version of each package it
downloaded when you
first ran `composer install`. If you share your project with other coders and the `composer.lock` file
is part of your distribution, when they run `composer install` they'll get the same versions as you. 
To update your dependencies, run `composer update`.

This is most useful when you define your version requirements flexibly. For instance a version 
requirement of `~1.8` means "anything newer than `1.8.0`, but less than `2.0.x-dev`". You can also use 
the `*` wildcard as in `1.8.*`. Now Composer's `composer update` command will upgrade all your
dependencies to the newest version that fits the restrictions you define.

### Update Notifications

To receive notifications about new version releases you can sign up for [VersionEye], a web service
that can monitor your GitHub and BitBucket accounts for `composer.json` files and send emails with new
package releases.

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
