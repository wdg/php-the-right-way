---
isChild: true
title:   MySQL Extension
anchor:  mysql_extension
---

## MySQL Extensie {#mysql_extension_title}

 
De [mysql] extensie voor PHP is verschrikkelijk oud en is vervangen voor 2 andere extensies:

- [mysqli]
- [pdo]

Niet alleen is de ontwikkeling lang geleden gestopt, maar het is [verouderd in PHP 5.5.0][mysql_deprecated], en **[verwijderd in PHP 7.0][mysql_removed]**.

Om graven in `php.ini` te besparen om de module te zoeken, de beste optie is om te zoeken naar `mysql_*` in uw code en in de editor van uw keuze. Als u functies als `mysql_connect()` en/of `mysql_query()` komen voor, dan is de `mysql` extensie in gebruik.

Zelfs als u PHP 7.0 nog niet gebruikt, is er een gevaar dat uw code niet meer werkt zodra u PHP 7.0 of hoger gaat gebruiken.
De beste optie is om uw `mysql_*` functies te vervangen voor [mysqli] of [pdo] functies te vervangen, zodat u later geen problemen heeft als u *moet* updaten.

**If you are upgrading from [mysql] to [mysqli], beware lazy upgrade guides that suggest you can simply find and replace `mysql_*` with `mysqli_*`. Not only is that a gross oversimplification, it misses out on the advantages that mysqli provides, such as parameter binding, which is also offered in [PDO][pdo].**

* [PHP: Choosing an API for MySQL][mysql_api]
* [PDO Tutorial for MySQL Developers][pdo4mysql_devs]

[mysql]: http://php.net/mysql
[mysql_deprecated]: http://php.net/migration55.deprecated
[mysql_removed]: http://php.net/manual/en/migration70.removed-exts-sapis.php
[mysqli]: http://php.net/mysqli
[pdo]: http://php.net/pdo
[mysql_api]: http://php.net/mysqlinfo.api.choosing
[pdo4mysql_devs]: http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers
