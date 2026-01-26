## h2_Komentaja Pingviini

### Command Line 
Tero Karvisen _Command Line basic revisited_ -artikkeli vuodelta 2020 kertoo, että jo ennen internetin syntyä käytössä ollut komentorivi on nopea ja käytännöllinen työkalu. 

Komentorivillä liikutaan aina hakemistoissa. Erilaisia komentoja ovat esimerkiksi _pwd, ls, cd, ja less._ Myös tiedostoja voidaan hallita komentorivillä esimerkiksi avaamalla editoreita (esim. _nano_, siirtämällä _mv_, kopioimalla _cp_ tai poistamalla _rm_. Tärkeitä hakemistoja ovat esimerkiksi root /, home (/home), home/user/, /etc/, /media/ ja (/var/log).

SSH etäyhteys saadaan muodostettua turvallisesti komentorivin avulla _ssh_ komennolla.

Tab-painikkeen ja nuolinäppäimien voimin pystytään käyttämään "automaattitäyttöä" tai tutkia komentorivin historiaa. 

Hallinnollisilla komennoilla (Adminisrative Commands) voidaan tehdä koko systeemiä koskevia toimintoja. Ne vaativat riittävästi oikeuksia, joita saadaan ajamalla _sudo_ komentoja, kuten _sudo apt-get update_.

Koen itse komentorivin nopeana työkaluna silloin, kun tiedän mitä olen tekemässä ja mitä komentoja tarvitsen. Komentoja on valtava määrä opeteltavaksi ja väärillä komennnoilla saatan aiheuttaa ongelmia itselleni. Tästä syystä sen opettelu on tärkeää ja mitä paremmin sen käytön osaa, sitä tehokkaampaa ja vähemmän riskialtista komentorivi surffailu on.




### Micro-editorin asentaminen

Asensin Micron komennolla _curl https://getmic.ro | bash_.

![Micro installed](kuvia/micro_installed.png)

<br>
<br>

## Kolmen uuden komentoriviohjelman asentaminen

Kaikki kolme saatiin asennettua yhdellä komennolla: _sudo apt-get install htop tmux mc_. Terminaali pyysi käyttäjän salasanaa, jonka jälkeen se vielä varmisti, että 10,9 MB levytilaa otetaan käyttöön. Valintani olivat Tree, Tmux & Midnight Commander, joista kaikista alla lisää.


#### Tree

Hakemiston näyttäminen puuna. Tämä voi auttaa hahmottamaan kansioiden ja tiedostojen sisällöt. Jos halutaan näyttää vain tietyn kansion sisältö, voidaan lisätä komennon perään halutun kansion nimi. 

Käytetään _tree_ -komennolla. 

![Tree](kuvia/treeEsimerkki.png)

<br>

#### tmux
Terminaalin moniajo. Komennon avulla voidaan pitää useita terminaaleja auki yhdessä ikkunassa. tmux mahdollistaa, että terminaalit voidaan pilkkoa sessioihin ja paneeleihin, jotka jatkavat toimintaansa vaaikka terminaali suljettaisiin. Näin esimerkiksi SSH-yhteydet pysyvät hengissä estämällä katkeamisen vaikutukset. Saadaan käyttöön _tmux_ -komennolla.

![tmux](kuvia/tmux.png)

<br>

#### Midnight Commaander (mc)
Kaksipaneelinen tiedostonhallinta. Sen perusidea on kaksi rinnakkaista paneelia, joista toinen on lähdehakemisto ja toinen kohdehakemisto. Se mahdollistaa helposti tiedostojen siirtämisen paneelien välillä on aloittelijaystävällinen, sillä se tarjoaa graafista käyttöliittymää muistuttavan tavan hallita tiedostoja.

Paneelit saadaan käyttöön _mc_ -komennolla

![commander](kuvia/mc.png)




### FHS. Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". 

/
/home/
/home/henri/
/etc/
/media/
/var/log/

Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.



### Grep

grep -komennon avulla pystytään etsimään tekstiä tiedostoista. Perusmuodossaan se on _grep [vaihtoehdot] "hakusana" tiedosto_. Hakua pystytään muotoilemaan erilaisilla optioilla, kuten -i, jolloin haku ei välitä kirjainkoosta tai -v, jolloin etsitään vain rivit jotka eivät sisällä hakusanaa.

Kuvan esimerkissä etsitään tiedostosta "kotka" -tekstiä ja optio -c palauttaa rivien määrän, joilla etsitty merkkijono esiintyy.

![greppaus](kuvia/grep-c.png)





### Pipe

Putkilla on mahdollista yhdistää useita komentoja niin, että aiempi komento ketjuttuu seuraavaan. Komentorivillä putki merkataan | -merkillä.

komento1 | komento2 | komento3

![pipes](kuvia/pipe_esimerkki.png)

Kyseisessä komennossa siis kirjoitetaan tiedostoon "tiedosto.txt", etsitään sieltä kaikki "koira" teksti ja korvataan kaikki "koira" teksti "kissalla". 




###Rauta

Aloitin koneen raudan testaamisen asentamalla lshw:n komennolla _sudo apt install lshw_. 
Listaa testaamasi koneen rauta (‘sudo lshw -short -sanitize’). Asenna lshw tarvittaessa. Selitä ja analysoi listaus.




g) Vapaaehtoinen: Valitse muutama rivi lokeista. Tulkitse ja analysoi.
h) Vapaaehtoinen: Asenna jokin plugin micro-editorille ja kokeile sitä. Vaikkapa palettero, cheat tai runit.

### Lähteet
https://terokarvinen.com/linux-palvelimet/#h1-oma-linux. Tehtävänanto h2_Komentaja_Pingviini. 
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited. Karvinen, T. Command Line Basics Revisited artikkeli.
https://www.geeksforgeeks.org/linux-unix/piping-in-unix-or-linux/. Piping in Unix and Linux. 2024.
https://www.redhat.com/en/blog/introduction-tmux-linux. Geradi, R. A beginnner's guide to tmux. 2022.X¢
