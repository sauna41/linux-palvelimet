_Kurssi: Linux palvelimet ICI003AS2A-3016_

_Tekijä: Henri Äikäs_

_Alusta: Intel i5 Macbook Pro MacOs Sequaoia 15.7.2 / Debian 13 trixie (VirtualBox)_

_Päivämäärä: 4.3.2026_

<br>

_Tämä raportti on osa Haaga-Helian Linux Palvelimet kurssia keväällä 2026.Tehtävänanto on h4 Maailma kuulee. Opettajana toimii Tero Karvinen._

________________________________________________________________________________________________________________________________________________________________________________________

## h7 Maalisuora

a) "Hei maailma" kolmella eri ohjelmointikielellä

Loin toiminnoille omat hakemistot: 

![tree](kuvia/heimaailmatree.png)

Valitsin kieliksi C:n, Pythonin ja Bashin. 

#### C

Loin uuden .c -tiedoston

    nano heimaailma.c

Kirjoitin tiedostoon skriptin toiminnan.

    #include <stdio.h>
    int main() {
        printf("Hei maailma\n");
        return 0;
    }

Ohjelma täytyi kääntää, jotta se olisi ajettava

    gcc -o heimaailma heimaailma.c

- gcc toimii kääntäjänä
- o heimaailma luo suoritettavan tiedoston nimeltään heimaailma
- heimaailma.c toimii lähdekoodina

Ohjelma ajettiin ja se tulosti halutun tekstin

    ./heimaailma.c

![c](kuvia/heimaailma.c.png)


### Python

Loin tiedoston ja lisäsin sinne tulostuksen

    nano heimaailma.py
    print("Hei maailma")
    
![python](kuvia/heimaailma.py.png)


### Bash

Loin tiedoston ja lisäsin sinne tulostuksen

    nano heimaailma.sh
    #!/bin/bash
    echo "Hei maailma"

    chmod +x  heimaailma.sh

chmod, eli _change mode_ muuttaa oikeuksia. Lisäsin +x, eli suoritusoikeuden. Tämä mahdollistaa tiedoston ajamisen. 

Ajoin lopulta skriptin komennolla

    ./heimaailma.sh

![bash](kuvia/heimaailma.sh.png)


________________________________________________________________________________________________________________________________________________________________________________________

## Oma skripti

Tehtävänä oli luoda uusi, itse tekemä komento, jota kaikki koneen käyttäjät voisivat hyödyntää. Komento sai olla vapaavalintainen. Linuxin aktiivinen päivittäminen on tärkeää ja se tulee tehtyä joka kerta kun konetta käyttää. Päätinkin siis luoda ohjelman, joka tarkistaa päivitykset, asentaa ne ja poistaa vanhat, turhat paketit kaikki kerralla.

Aloitin luomalla uuden tiedoston. Jotta komento olisi kaikille saatavilla, oli tärkeää luoda skripti oikeaan hakemistoon. Käytin /usr/local/bin -hakemistoa, jotta se se tulisi käyttöön kaikille käyttäjille.

        sudo nano /usr/local/bin/update

Kirjoitin tiedostoon päivitysten hakemisen, asentamisen ja turhuuksien poistamisen

        #!/bin/bash

        echo "Päivitetään pakettilista..."
        sudo apt update
        
        echo
        echo "Asennetaan päivitykset..."
        sudo apt upgrade -y
        
        echo
        echo "Poistetaan turhat paketit..."
        sudo apt autoremove -y
        
        echo
        echo "Päivitys valmis."

Skriptistä piti tämän jälkeen vielä tehdä suoritettava. Se tapahtui lisäämällä siihen käyttöikeudet komennolla

        sudo chmod +x /usr/local/bin/update

Nyt uusi komento oli käytettävissä

![update](kuvia/update.png)

### Lähteet

Karvinen, T. Linux Palvelimet. Luettavissa https://terokarvinen.com/linux-palvelimet/#h5-nimekas. Luettu 4.3.2026.

Karvinen, T. Final Lab for Linux Palvelimet 2023. Luettavissa: https://terokarvinen.com/2023/linux-palvelimet-2023-arvioitava-laboratorioharjoitus/. Luettu 8.3.2026.

Karvinen, T. Django introduction. MDN Web Docs. Luettavissa: https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Server-side/Django/Introduction. Luettu 8.3.2026.

Karvinen, T. Django Tutorial. Luettavissa: https://www.geeksforgeeks.org/python/django-tutorial/. Luettu 8.3.2026. 
