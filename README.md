<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Del kode spletnega mesta je odprtokoden, dobrodošli, da pomagate optimizirati prevod.

## sprednja koda

* [sprednja koda](https://github.com/xxai-art/web)
* [Jezikovni paketi za spletno mesto kot celoto](https://github.com/xxai-art/web/tree/main/i18n)
* [Jezikovni paketi za prijavne module](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Večjezična dokumentacija spletne strani](https://github.com/xxai-doc)

Sprednji programski jezik je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , ki doda nekaj funkcij, ki temeljijo na sintaksi coffeescript, glejte [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizacija spletnih mest in dokumentov

Gradite na naslednjih 3 projektih

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Pripona je `.mdt` , lahko uporabite sintakso, podobno `<+ ./coffee_plus/import.js>` , da se sklicujete na zunanje datoteke in ustvarite markdown s pripono `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown prevod ne bo prevedel kod in povezav ter bo predpomnil prevedene stavke. Če je prevod spremenjen, vendar izvirno besedilo ni spremenjeno, ponovna izvedba ne bo prepisala spremembe prevoda.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Jezikovne datoteke za prevajanje spletnih mest, ustvarjenih `yaml` .
