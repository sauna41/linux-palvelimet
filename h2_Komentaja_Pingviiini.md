## h2_Komentaja Pingviini

### Command Line 
Tero Karvisen Command Line basic revisited artikkeli vuodelta 2020 kertoo, että jo ennen internetin syntyä käytössä ollut komentorivi on nopea ja käytännöllinen työkalu. 

Komentorivillä liikutaan aina hakemistoissa. Erilaisia komentoja ovat esimerkiksi _pwd, ls, cd, ja less._ Myös tiedostoja voidaan hallita komentorivillä esimerkiksi avaamalla editoreita (esim. _nano_, siirtämällä _mv_, kopioimalla _cp_ tai poistamalla _rm_. Tärkeitä hakemistoja ovat esimerkiksi root /, home (/home), home/user/, /etc/, /media/ ja (/var/log).

SSH etäyhteys saadaan muodostettua turvallisesti komentorivin avulla _ssh_ komennolla.

Tab-painikkeen ja nuolinäppäimien voimin pystytään käyttämään "automaattitäyttöä" tai tutkia komentorivin historiaa. 

Hallinnollisilla komennoilla (Adminisrative Commands) voidaan tehdä koko systeemiä koskevia toimintoja. Ne vaativat riittävästi oikeuksia, joita saadaan ajamalla _sudo_ komentoja, kuten _sudo apt-get update_.

Koen itse komentorivin nopeana työkaluna silloin, kun tiedän mitä olen tekemässä ja mitä komentoja tarvitsen. Komentoja on valtava määrä opeteltavaksi ja väärillä komennnoilla saatan aiheuttaa ongelmia itselleni. Tästä syystä sen opettelu on tärkeää ja mitä paremmin sen käytön osaa, sitä tehokkaampaa ja vähemmän riskialtista komentorivi surffailu on.




### Micro-editorin asentaminen

Asensin Micron komennolla _curl https://getmic.ro | bash_.

![Micro installed](kuvia/micro_installed.png)


### Kolmen uuden komentoriviohjelman asentaminen
Kokeile kutakin ohjelmaa sen pääasiallisessa käyttötarkoituksessa. Ota ruutukaappaus. 

Kaikki kolme saatiin asennettua yhdellä komennolla: _sudo apt-get install htop tmux mc_. Terminaali pyysi käyttäjän salasanaa, jonka jälkeen se vielä varmisti, että 10,9 MB levytilaa otetaan käyttöön. 


#### Tree

Hakemistorakenteen näyttäminen puuna (CLI). 

#### tmux
Terminaalin moniajo. Mahdollistaa useita ikkunoita yhdessä SSH-istunnossa. 

#### Midnight Commaander (mc)
Kaksipaneelinen tiedostonhallinta (TUI). 




### FHS. Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". 

/
/home/
/home/henri/
/etc/
/media/
/var/log/

Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.



d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

e) Pipe. Näytä esimerkki putkista (pipes, "|").

f) Rauta. Listaa testaamasi koneen rauta (‘sudo lshw -short -sanitize’). Asenna lshw tarvittaessa. Selitä ja analysoi listaus.




g) Vapaaehtoinen: Valitse muutama rivi lokeista. Tulkitse ja analysoi.
h) Vapaaehtoinen: Asenna jokin plugin micro-editorille ja kokeile sitä. Vaikkapa palettero, cheat tai runit.

### Lähteet
https://terokarvinen.com/linux-palvelimet/#h1-oma-linux. Tehtävänanto h2_Komentaja_Pingviini. 
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited. Command Line Basics Revisited artikkeli.
