---
sidebarDepth: 3
---

# Popis prostředí

[[TOC]]

---

Stránky jsou postaveny na následných technologiích. Pokud chceš přispět, je nutné si podstané nastudovat v dokumetaci nebo se zeptat.
* **PHP** framevork Laravel (aktuálně 5.8) | [dokumentace](https://laravel.com/docs)
* **CSS** používá Tailwind CSS (utility-first CSS framework) [dokumentace](https://tailwindcss.com/docs/what-is-tailwind/) | [inspirace jak na to](https://tailwindcomponents.com/) | [Awesome Tailwindcss](https://github.com/aniftyco/awesome-tailwindcss)
  * **SASS** CSS preprocesor | [dokumentace](https://sass-guidelin.es/cz/)
* **javascrip** čistý javascript + js framework Vue.js (ver 2.x) | [dokumentace](https://vuejs.org/v2/guide/)

## Používané balíky PHP
O aktualizaci knihoven se stará dependency manager [composer](https://getcomposer.org/) (dependency manager). Do Laravelu je možné dostat klasické PHP knihovny nebo ty, u kterých už někdo nachystal integraci, takové lze najít na stránkách [Packalistu](https://packalyst.com/).

### PHP knihovny
Knihovny používané nad rámec Laravel frameworku, najdeš je v `./composer.json`
* **laravelcollective/html** - Jednoduší zápis formulářových komponent - [dokumentace](https://github.com/LaravelCollective/docs/blob/5.6/html.md), je na zvážení. Pro formuláře je možné použít klasických zápisů html 5.
* **spatie/laravel-permission** - Řeší ACL, role, oprávnění aplikace - [GitHub](https://github.com/spatie/laravel-permission) | [Dokumentace](https://docs.spatie.be/laravel-permission/v2/introduction/)
* **laravel-frontend-presets/tailwindcss** - Řeší kompilaci CSS Tailwind CSSu projektu
* **intervention/image** - Manipulace s obrázky [GitHub](https://github.com/Intervention/image) | [Dokumentace](http://image.intervention.io/)
* **simplesoftwareio/simple-qrcode** - Tvorba QR kódu [GitHub](https://github.com/SimpleSoftwareIO/simple-qrcode) | [Dokumentace](https://www.simplesoftware.io/#/docs/simple-qrcode)

### JavaScrip knihovny
Knihovny používané nad výchozí [Laravel Mix](https://laravel.com/docs/5.7/mix) najdeš v `./package.json`
* **tilwindcss** - CSS Framework
* **moment** - manipulace s časem datumem [Dokumentace](https://momentjs.com/)
* **vuejs** - JavaScriptový framework
  * **vue-toasted** - Flash Messages pro vue.js [GitHub + dokumentace](https://github.com/shakee93/vue-toasted)
  * **vue-js-dropdown** - tool tip, dropdown menu[ Dokumentace ](http://vue-js-dropdown.yev.io/)
  * **vue-datetime** - doplnění data a času [Dokumentace](https://www.npmjs.com/package/vue-datetime) - aktuálně pouze na backendu
  * **vue-moment** - manipulace s datem [Dokumentace](https://www.npmjs.com/package/vue-moment)
  * **vue-password-strength-meter** - ukazatel síly hesla [Dokumentace](https://www.npmjs.com/package/vue-password-strength-meter)
* **tynimce** - WYSIWYG HTML Editor
* **tilwindcss** - CSS Framework
