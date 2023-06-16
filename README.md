<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Priporočljivo je, da najprej namestite nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) in nato `direnv allow` po vstopu v imenik ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) se bo samodejno izvedel po vstopu v imenik).

Pomen je: kitajski prevod v japonščino, korejščino, angleščino, angleški prevod v vse druge jezike. Če želite podpirati samo kitajščino in angleščino, lahko samo napišete `zh: en` .

Pomen je: kitajski prevod v japonščino, korejščino, angleščino, angleški prevod v vse druge jezike. Če želite podpirati samo kitajščino in angleščino, lahko samo napišete `zh: en` .

* [sprednja koda](https://github.com/xxai-art/web)
* [Jezikovni paketi za spletno mesto kot celoto](https://github.com/xxai-art/web/tree/main/i18n)
* [Jezikovni paketi za prijavne module](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Večjezična dokumentacija spletne strani](https://github.com/xxai-doc)

Sprednji programski jezik je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , ki doda nekaj funkcij, ki temeljijo na sintaksi coffeescript, glejte [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizacija spletnih mest in dokumentov

Gradite na naslednjih 3 projektih

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Pripona je `.mdt` , lahko uporabite sintakso, ki je podobna `<+ ./coffee_plus/import.js>` , da se sklicujete na zunanje datoteke in ustvarite markdown s pripono `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown prevod ne bo prevedel kod in povezav ter bo predpomnil prevedene stavke. Če je prevod spremenjen, vendar izvirno besedilo ni spremenjeno, ponovna izvedba ne bo prepisala spremembe prevoda.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Jezikovne datoteke za prevajanje spletnih mest, ustvarjenih `yaml` .

### Navodila za avtomatizacijo prevajanja dokumentov

Oglejte si repozitorij kod [xxai-art/doc](https://github.com/xxai-art/doc)

Priporočljivo je, da najprej namestite nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) in nato `direnv allow` po vstopu v imenik ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) se bo samodejno izvedel po vstopu v imenik).

Da bi se izognil veliki kodni bazi, prevedeni v stotine jezikov, sem ustvaril ločeno kodno bazo za vsak jezik in ustvaril organizacijo za shranjevanje kodne baze

Če nastavite spremenljivko okolja `GITHUB_ACCESS_TOKEN` in nato zaženete [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) , boste samodejno ustvarili repozitorij kode.

Seveda ga lahko postavite tudi v bazo kod.

Referenca prevodnega skripta [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Koda skripta se razlaga na naslednji način:

[bunx](https://bun.sh/docs/cli/bunx) je zamenjava za npx, ki je hitrejši. Seveda, če nimate nameščenega bun, lahko namesto tega uporabite `npx` .

`bunx mdt zh` upodablja `.mdt` v imeniku zh kot `.md` , glejte 2 povezani datoteki spodaj

* [kava_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [kava_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` je osnovna koda za prevajanje (če imate nameščen samo `nodejs` , vendar `bun` in `direnv` nista nameščena, lahko zaženete tudi `npx i18n` za prevajanje).

Razčlenil bo [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfiguracija `i18n.yml` v tem dokumentu je naslednja:

```
en:
zh: ja ko en
```

Pomen je: kitajski prevod v japonščino, korejščino, angleščino, angleški prevod v vse druge jezike. Če želite podpirati samo kitajščino in angleščino, lahko samo napišete `zh: en` .

Zadnji je [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , ki izvleče vsebino med glavnim naslovom in prvim podnaslovom `README.md` vsakega jezika, da ustvari vnos `README.md` . Koda je zelo preprosta, lahko si jo ogledate sami.

Google API se uporablja za brezplačno prevajanje. Če ne morete dostopati do Googla, konfigurirajte in nastavite proxy, kot je:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Prevajalski skript bo ustvaril preveden predpomnilnik v imeniku `.i18n` , preverite ga s `git status` in dodajte v repozitorij kode, da se izognete ponovnim prevodom.

Za posodobitev predpomnilnika zaženite `bunx i18n` vsakič, ko spremenite prevod.

Če sta izvirno besedilo in prevod spremenjena hkrati, bo predpomnilnik zmeden, tako da, če želite spremeniti, lahko spremenite samo enega in nato zaženete `bunx i18n` , da posodobite predpomnilnik.
