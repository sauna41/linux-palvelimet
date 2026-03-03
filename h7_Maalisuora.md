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

Luodaan uusi skripti. 

    nano heimaailma.c

Kirjoitetaan skripti

    #include <stdio.h>
    int main() {
        printf("Hei maailma\n");
        return 0;
    }

Käännetään ohjelma

    gcc -o heimaailma heimaailma.c

- gcc toimii kääntäjänä
- o heimaailma luo suoritettavan tiedoston nimeltään heimaailma
- heimaailma.c toimii lähdekoodina

Ajetaan ohjelma

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


### Lähteet

Karvinen, T. Linux Palvelimet. Luettavissa https://terokarvinen.com/linux-palvelimet/#h5-nimekas. Luettu 4.3.2026.

