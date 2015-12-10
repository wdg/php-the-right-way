---
isChild: true
anchor:  windows_setup
---

## Windows Installatie {#windows_setup_title}

Je kan de uitvoerbare bestanden van [windows.php.net/download][php-downloads] downloaden. Na installatie van PHP is het verstandig om de [PATH][windows-path] in te stellen naar de map waar `php.exe` zich bevindt zodat je php overal kan uitvoeren.

Voor leren en lokaal publiceren kan je de ingebouwde webserver gebruiken vanaf PHP 5.4 en hoger, zodat je je niet druk hoeft te maken over configuraties. Als je een "Alles-in-Een" oplossing wilt kun je kiezen uit o.a. [Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp] en [WAMP][wamp] deze tools zijn wel iets anders dan een standaard php installatie, wees voorzichting als je bouwt in een Windows omgeving en de server voor publicatie Linux is.

there is a [dedicated area on iis.net][php-iis] for PHP.
Als het productiesysteem op windows draait dan geeft ISS7 je de meest stabiele omgeving en snelheid. Je kan [phpmanager][phpmanager] gebruiken (een Grafishe plugin voor ISS7) om PHP makkelijk te configureren. ISS7 komy standaard met FastCGI ingebouwd en klaar voor gebruik, je hoeft PHP alleen maar als handler in te stellen. Voor support en andere informatie kijk dan op [iis.net][php-iis].

[php-downloads]: http://windows.php.net/download/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html
[easyphp]: http://www.easyphp.org/
[wamp]: http://www.wampserver.com/en/
[phpmanager]: http://phpmanager.codeplex.com/
[php-iis]: http://php.iis.net/
