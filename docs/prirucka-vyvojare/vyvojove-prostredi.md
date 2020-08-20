---
sidebarDepth: 2
---

# Vlastní devel prostředí

Popíšu jak je možné spustit vývoj na lokálu. V zásadě jsou dvě možnosti. Než se pustím do spolupráce skrze gitlab, je vhodné nejdříve projekt rozjet na lokále trochu si ho osahta a pohrát si sním. Následně pak spolupracovat standardně skrze git GitLab

Celkem pěkný návod na GItHub (GitLab je podobné) najdete [tady](https://github.com/firstcontributions/first-contributions/blob/master/translations/README.cs.md).

Pro vývojové prostředí v konfiguraci **1** je potřeba PHP (>7.1.3) a MySQL (5.7). Do databáze je možné koukat skrze **phpMyadmin** nebo **MySQL Workbench** nebo jiného klienta. Záleží na každém jak je zvyklý. Dále je nutné zprovoznit composer, nejlépe globálně volaný odkudkoliv `composer`, nebo alespoň lokálně `php composer phar`.
Pokud bude potřeba kompilovat CSS a javascript, je nutné mít zprovozněny [npm](https://www.npmjs.com/) a [Node.js](https://nodejs.org/en/).
Pro konfiguraci **2** je pak nutné pouze **PHP** a rozchodit **composer**. 

## Prostředí localhost-u

::: warning Upozornění
Nejprve je nutné zprovoznit PHP >7.1.3 a MySQL 5.7 na lokále, vhodný bude i nějaký klient pro práci s databází (phpMyAdmin, MySQL Workbench ...)
:::


1.  Vytvořím adresář projektu - do něj naklonoju (nebo v první fázi pouze stáhnu) soubory projektu.
2.  V rootu projektu spustím `composer update`, projekt si natáhne aktuální knihovny
3.  Pokud si budu hrát s *css* nebo *javascriptem*, musím nakonfigurovat prostředí webpack-u se všemi závislostmi. Klasicky spustím `npm install`, který mi stáhne všechno potřebné.
4.  Ve vlastním souboru .env nakonfiguruji potřebné, minimálně spojení s databází `DB_`
5.  Spustím **Migration** skrze vnitřní CLI Artisan rozhranní `php artisan migrate:fresh` - databáze by se měla naplnit tabulkami
6.  Spustím **Seed** naplnění databáze výchozími daty `php artisan db:seed`
7.  Pak už jen stačí spustit vývojové prostředí `php artisan serve` - spustím vývojové prostředí, v konsoli vidím adresu vývojového serveru _Laravel development server started: <http://127.0.0.1:8000>_, tu pak už dám jen do prohlížeče a měl bych vidět stránku projektu
8.  Pokud upravuji CSS a JS v bodě 4., spustím v druhém terminálovém okně příkaz `npm run watch-poll`, měla by se mi skompilovat všechna css a js vždy do jednoho souboru umístěných v `./public/css` a `./public/js`, navíc při každé změně v `*.css`, `*.sass` a `*.vue` souboru se automaticky public soubory zkompilují.
9. Super!! mám vyhráno a mohu nerušeně vyvýjet.

## Prostředí Laravel Homestead
V této variantě musím mít ze začítku minimálně zprovozněno PHP a composer. Dále mi musí na počítaží běžet [VirtualBox](https://www.virtualbox.org/) a [Vagrant](https://www.vagrantup.com/). Dále musím mít aktivní ssh (Vagrant koomunikuje na ssh portu) a vytvořen vlastní pár rsa klíčů.

1.  Vytvořím adresář projektu - do něj naklonoju (nebo v první fázi pouze stáhnu) soubory projektu.
2.  Edituji soubor ./composer.json a mezi "require-dev" vložím `"laravel/homestead": "^8.0",`
3.  V rootu projektu spustím `composer update`, projekt si natáhne aktuální knihovny
4.  V rootu projektu spustím `php vendor/bin/homestead make`, měl by se mi vytvořit soubor `./vagrant.yaml`, soubor bude na Linuxu vypadat zhruba takto (pro představu je tam i phpMyAdmin).
```yaml
ip: 192.168.10.10
memory: 2048
cpus: 1
provider: virtualbox
authorize: ~/.ssh/id_rsa.pub
keys:
    - ~/.ssh/id_rsa
folders:
    - map: /Users/username/projects/devel.abmbrno.cz
      to: /home/vagrant/code
    - map: /Users/username/projects/phpmyadmin
      to: /home/vagrant/code/phpmyadmin
sites:
    - map: devel.abmbrno.cz
      to: /home/vagrant/code/public
    - map: db-devel.abmbrno.cz
      to: /home/vagrant/code/phpmyadmin
databases:
    - homestead
name: devel.abmbrno.cz
hostname: devel.abmbrno.cz
```
* znamená že bude virtuál běžet na adrese 192.168.10.10 s pamětí a X jádry CPU, v sekci _folders_ mapujete **map* co chci na lokále aby bylo v **to** ve vyrtuální mašine na cestě. V _sites_ opět mapuji URL v **map** na adresář **to** virtuálu. Paku už jedn definuju název databáze, nechte homestead nebo se po prvním přihlášení nastavte novou a používejte tuto.
* v souboru _hosts_ (např. v Linuxu na /etc/hosts) je nutné uvedené přidat:
```
192.168.10.10 devel.abmbrno.cz
192.168.10.10 db-devel.abmbrno.cz
```
5. Poté spustím v rootu projektu `vagrant up`, při prvním spuštění se stáhne [homestead box](https://app.vagrantup.com/laravel/boxes/homestead) cca 2GB, bude se to ptát na virtualizaci, zvolím virtualbox.
6. Po stažení by virtuál spustí, uvidíte ho ve VirtualBoxu, přepnout se do virtuálu jde skrze `vagrant ssh`, v boxu se pohybujete stejně jako na linuxové mašině, normálně tam můžete doinstalovat balíky ...
7. Jakoukoliv změnu uděláte v projektu, je tato promítnuta do virtuálu, existuje oboustranná provázanost. Pokud změnu udělám ve virtuálu, promítne se mi do lokálních souborů.
8. Pak už pracuji jako v předešlém případě.

### Údržba boxu
Sem tam od času` bude potřeba udělat nějakou údržbu nebo operaci.
*  `vagrant up` - spustí vagrant box
*  `vagrant halt` - zastaví vagrant box
*  `vagrant box` update - stáhne aktuální verzi wagratn boxu pro laravel/homestead
*  `vagrant ssh` - přepne do virtuálu
*  `vagrant port` - zjistí porty a jejich namapování
*  `vagrant provision` - pokud jsem provedl změnu nastavení v `vagrant.yaml` souboru
