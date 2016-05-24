---
title:  Databases
anchor: databases
---

# Databases {#databases_title}

Vaak heeft uw PHP code een verbinding met een database om informatie op te slaan. U heeft een paar opties om te verbinden en te communiceren.
De beste manier **tot PHP 5.1.0** was [mysqli], [pgsql], [mssql], etcetera, de beste optie

Ingebouwde drivers zijn geweldig als u alleen gebruik maakt van _een_-database in uw toepassing, maar als u bijvoorbeeld, die u gebruikt
MySQL en een beetje van MSSQL, of je nodig hebt om verbinding te maken met een Oracle-database, dan zal je niet in staat zijn om het te gebruiken
Dezelfde drivers. Je moet een nieuwe API voor elke database leren &mdash; en dat kan domweg vervelend irritant zijn.

[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql
