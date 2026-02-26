Kurssi: Linux palvelimet ICI003AS2A-3016

Tekijä: Henri Äikäs

Alusta: Intel i5 Macbook Pro MacOs Sequaoia 15.7.2 / Debian 13 trixie (VirtualBox)

Päivämäärä: 24.2.2026


_Tämä raportti on osa Haaga-Helian Linux Palvelimet kurssia keväällä 2026. Tehtävänanto on h6 Salataampa. Opettajana toimi Tero Karvinen._

________________________________________________________________________________________________________________________________________________________________________________________


x) Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä alakohdassa ei tarvitse tehdä testejä tietokoneella)
Let's Encrypt 2024: How It Works
The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example (Ei "Cipher Suites and Enforcing Strong Security" eteenpäin. Certbot tekee meillä automaattisesti kaikki salaukseen liittyvät asetukset.

________________________________________________________________________________________________________________________________________________________________________________________

a) TLS-sertifikaatti Let's Encryptilta

Aloitin kirjautumalla palvelimelleni 

    ssh henri@IP_osoite

Seuraavaksi asennettiin Certbot. Certbot on vapaan lähdekoodin työkalu, jolla voidaan hankkia Let's Encrypt -sertifikaatteja webbisivuille (Certbot.eff.org). Asentaminen toteutettiin komennoilla komennoilla

    sudo apt update
    sudo apt install certbot python3-certbot-apache

    

Tämän jälkeen hain ja asensin itse Let's Encrypt -sertifikaatin

    sudo certbot --apache -d sauna41.site -d www.sauna41.site

Sain ilmoituksen, että sivulle www.sauna41.site ei löydy vhostia. Piti valita kahden eri virtuaalihostin väliltä, jolloin valitsin vaihtoehdon 2 (henri-le-ssl.conf  Multiple Names     HTTPS   Enabled)

Tämän jälkeen sain ilmoituksen, että sertifikaatio onnistui sivuilleni www.sauna41.site ja sauna.site. 

![certti](kuvia/certsuccess.png)

![lukko](kuvia/lukonkuva.png)

________________________________________________________________________________________________________________________________________________________________________________________


b) A-rating. Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)

![SSLtest](kuvia/SSLLABStest.png)


c) Vapaaehtoinen: Tee weppilomake, jossa on käyttäjätunnus ja salasana. Käytä salaamatonta http-yhteyttä. Sieppaa liikennettä (esim. Wireshark, ngrep). Mitä havaitset? Mitä vaikutuksia tällä on tietoturvaan?

________________________________________________________________________________________________________________________________________________________________________________________

Lähdeluettelo:

Karvinen T. Linux palvelimet kurssimateriaali. Luettavissa: https://terokarvinen.com/linux-palvelimet/. Luettu 24.2.2026.

About Certbot. Luettavissa: https://certbot.eff.org/pages/about. Luettu 24.2.2026.

SSL Labs. SSL Server Test. Luettavissa: https://www.ssllabs.com/ssltest/. Luettu 24.2.2026.

SSL/TLS Strong Encryption: How-To. Apache.org. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample. Luettu 24.2.2026.

How It Works. Let's Encrypt. 2.8.2025 .Luettavissa: https://letsencrypt.org/how-it-works/. Luettu 24.2.2026.

