---
isChild: true
anchor:  mac_setup
---

## Mac Setup {#mac_setup_title}

OS X komt met PHP al geinstalleerd, deze loopt normaal een beetje acter op de laatste stabiele versie, Mac OS X Mavericks komt met versie 5.4.17, Mac OS X Yosemite komt met versie 5.5.9, en Mac OS X komt met 5.5.29, maar nu PHP 7.0 uit is is, is dat meestal niet goed genoeg.

Er zijn verschillende manieren om PHP in Mac OS X te installeren.

### Installeer PHP via Homebrew

[Homebrew] is een krachtige package manager foor Mac OS X, wat je kan helpen om PHP en extensies makkelijk te installeren.
[Homebrew PHP] is een 'bron' waar veel PHP-verwante "formules" zijn voor Homebrew, en zal je helpen om PHP te installeren

Op dit punt, kun je `php53`, `php54`, `php55` of `php56` installeren via het commando `brew install`, en switchen tussen verschillende versies door je `PATH` aan te passen. Anders kun je altijd nog de [brew-php-switcher][brew-php-switcher] installeren, deze helpt je om snel tussen verschillende PHP versies te wisselen.

### Installeer PHP via Macports

Het [MacPorts] Project is een open-source community die een systeem om makkelijk te compileren, installeren, en upgraden heeft gemaakt, dit alles werkt via de commandline, om o.a. X11 of Aqua gebaseerde open-source applicaties voor het Mac OS X bestuuringssysteem te installeren.

MacPorts ondersteund van te voren gecompileerde bestanden, zodat je niet elk bestand hoeft te compileren van de broncode in de tarball bestanden, het bespaart je energie als je een pakket op uw systeem geïnstalleerd.

Op dit punt, kun je `php54`, `php55`, `php56` of `php70` installeren via het `port install` commando. Als voorbeeld:

    sudo port install php56
    sudo port install php70

En je kunt `select` uitvoeren om snel van PHP versie te wisselen:

    sudo port select --set php php70

### Installeer PHP via phpbrew

[phpbrew] is een tool om PHP te installeren en snel te wisselen tussen verschillende PHP versies. Dit kan erg makkelijk zijn als je verschillende applicaties/projecten hebt die een andere versie van PHP nodig hebben, zonder een virtuele machine aan te maken.

### Installeer PHP via Liip's binary installer

Een andere populaire oplossing is [php-osx.liip.ch] deze ondersteund makkelijke installatie methoden voor versie 5.3 tot en met 5.6.
Het overschrijft niet de meegeleverde php bestanden die er door Apple op gezet zijn, maar installeert alles in een andere map namelijk (/usr/local/php5).

### Compileren vanaf de broncode

Een andere optie die je volledige controle geeft over de geinstalleerde PHP versie, is door deze [zelf te compileren][mac-compile].
In dat geval wees er zeker van dat je [Xcode][xcode-gcc-substitution] of Apple's 
["Command Line Tools for XCode"] hebt gedownload en geinstalleerd via Apple's Mac Developer Center.

### Alles-in-Een Installers

The bovengenoemde oplossingen zijn voornamelijk om het zelf te doen, en hebben niet standaard Apache, Nginx, of een SQL Server.
"Alles-in-Een" oplossingen zoals [MAMP][mamp-downloads] en [XAMPP][xampp] zullen alles voor je installeren, maar de makkelijkheid van de setup heeft als negatieve kant dat deze installaties minder flexibel zijn.


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
