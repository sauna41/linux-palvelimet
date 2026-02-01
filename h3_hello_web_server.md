_Opintojakso: Linux palvelimet ICI003AS2A-3016_

_Tekijä: Henri Äikäs_

_Alusta: Intel i5 Macbook Pro MacOs Sequaoia 15.7.2 / Debian 13 trixie (VirtualBox)_

_Päivämäärä: 29.1.2025_

<br>
<br>

## h3 Hello Web Server

### Name-based Virtual Host

Name-based virtual host hyödyntää hostname-tietoa (ServerName/ServerAlias), jotta useat eri sivustot voivat jakaa saman IP-osoitteen. IP-pohjainen virtual host taas puolestaan vaatii jokaiselle sivustolle oman IP-osoitteensa. 


Apache on web-palvelinohjelmisto, joka mahdollistaa useamman verkkotunnuksen käytön yhdellä IP-osoitteella. Seuraavalla komennolla saadaan asennettua Apache ja korvattua Apachen etusivu omalla testietusivulla.

    $ sudo apt-get -y install apache2
    $ echo "Default"|sudo tee /var/www/html/index.html



    




### a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta

Webbipalvelimen toimintaa testattiin komennolla

_curl http://localhost_

Komento tulosti tekstin, "Hello world" virheilmoituksen sijaan, joka tarkoitti, että webbipalvelin vastaa localhost-osoitteesta.

<br>
_______________________________________________________________________________________________________________________
<br>

### b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä).

Lokit etsittiin komennolla

    sudo tail /var/log/apache2/access.log

Komento palautti kuvan mukaiset rivit:



![localhost_log](kuvia/localhost_log.png)

        127.0.0.1 - - [27/Jan/2026:14:19:11 +0200] "GET / HTTP/1.1" 200 3383 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0"


1. 127.0.0.1 on palvelimen eli tässä tapauksessa localhostin IP-osoite.
2. "- -" on käyttäjän identiteetti. Tässä tapauksessa tyhjä.
3. Päivämäärä ja aikavyöhyke pyynnölle.
4. "GET / HTTP/1.1"
    GET = pyynnön tyyppi
    / = pyydetty resurssi, eli etusivu
    HTTP/1.1 = HTTP-versio
5. 200 on HTTP-statuskoodi. 200 merkitsee, että pyyntö onnistui
6. 3383 on saadun sisällön koko tavuina
7. "-" on Referrer, eli mistä sivulta pyyntö tuli. Tässä tapauksessa tyhjä, sillä pyyntö ei tullut toiselta sivulta.
8. Mozilla/5.0 onn User-Agent. Se kertoo käytössä olevan selaimen ja käyttöjärjestelmän.

<br>
_______________________________________________________________________________________________________________________

### c) Etusivu uusiksi. Tee uusi name based virtual host. Sivun tulee näkyä suoraan palvelimen etusivulla http://localhost/. Sivua pitää pystyä muokkaamaan normaalina käyttäjänä, ilman sudoa. Tee uusi, laita vanhat pois päältä. Uusi sivu on hattu.example.com, ja tämän pitää näkyä: asetustiedoston nimessä, asetustiedoston ServerName-muuttujassa sekä etusivun sisällössä (esim title, h1 tai p).

Uuden name based virtual hostin luominen aloitettiin luomalla uusi DocumentRoot, jota käyttäjä voi muokata ilman root-oikeuksia. Sivulle luotiin oma hakemisto ja omistajuus normaalille käyttäjälle.

    sudo mkdir -p /var/www/hattu.example.com
    sudo chown -R $USER:$USER /var/www/hattu.example.com
    sudo chmod -R 755 /var/www/hattu.example.com

Seuraavaksi luotiin uusi etusivu, eli .html tiedosto. Tiedostoon kirjoitettin normaali HTML-sisältö. 

    nano /var/www/hattu.example.com/index.html

    <!DOCTYPE html>
    <html lang="fi">
    <head>
        <meta charset="UTF-8">
        <title>hattu.example.com</title>
    </head>
    <body>
        <h1>hattu.example.com</h1>
        <p>Tämä on uusi etusivu, name based virtual hostilla.</p>
    </body>
    </html>

Seuraavaksi luotiin uusi Virtual Host -asetustiedosto.

    sudo nano /etc/apache2/sites-available/hattu.example.com.conf

    <VirtualHost *:80>
    ServerName hattu.example.com
    ServerAlias localhost
    DocumentRoot /var/www/hattu.example.com

    <Directory /var/www/hattu.example.com>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/hattu.example.com_error.log
    CustomLog ${APACHE_LOG_DIR}/hattu.example.com_access.log combined
    </VirtualHost>

Uusi sivu otettiin käyttöön komennolla

    sudo a2ensite hattu.example.com.conf
    sudo systemctl reload apache2

Testattiin sivua vierailemalla http://localhost/ ja todettiin se tehtävänannon mukaiseksi. 

![hattu_etusivu](kuvia/etusivu_hattu.png)

Toimiva hattu.example.com

_______________________________________________________________________________________________________________________


### e) Tee validi HTML5 sivu. 

Varmistettiin, että sivu täyttää HTML5-vaatimukset, eli sivulta tuli löytyä.

  - `<!DOCTYPE html>`

  - `<html lang="fi>`

  - `<meta charset="UTF-8">`

  - Tarvittavat elementit:
      - header, main, footer
  - Oikeat rakenteet:
      - head & body

Käytin HTML-sivun validointiin W3C Markup Validation Serviceä. Syötin sivulle hattu.examplen HTML-koodin ja se meni validaattorista läpi ilman virheitä. 

![validaattori](kuvia/validaattori.png)

<br>
_______________________________________________________________________________________________________________________

<br>

### f) Anna esimerkit 'curl -I' ja 'curl' -komennoista. Selitä 'curl -I' muutamasta näyttämästä otsakkeesta (response header), mitä ne tarkoittavat.

curl -työkalu ottaa yhteyttä palvelimeen ja vastaanottaa siltä dataa. curl ei renderöi webbisivuja vaan palauttaa niiltä raakadataa komentoriville. Sen avulla voidaan esimerkiksi testata vastaako webbisivu, ladata tai lähettää tiedostaja tai debugata verkkoyhteyksiä. 

_curl_ -komento näyttää HTML-sivun sisällön komentorivillä. Esimerkiksi: 

        curl localhost

![curl](kuvia/curl.png)

<br>
<br>
<br>

 _curl  -i_ -komento näyttää sisällön lisäksi myös otsakkeet eli response headerit. 

         curl -i localhost

![curl_i](kuvia/curl_i.png)

<br>

1. HTTP/1.1 200 OK
    - HTTP/1.1 on käytetty HTTP-versio
    - Statuskoodi 200 OK merkitsee onnistunutta vastausta palvelimelta.


2. Date: Fri, 30 Jan 2026 00:41:21 GMT

    - Milloin palvelin lähetti vastauksen.

3. Server: Apache/2.4.66 (Debian)
   
    - Ohjelmisto, joka käsitteli pyynnön.


5. Last-Modified: Thu, 29 Jan 2026 19:33:29 GMT

    - Milloin sivua on viimeksi muokattu.


6. ETag: "18d-6498bee67cc36"

    - Tunniste versiohallintaa varten. Jos sisältö muuttuu, muuttuu myös ETag. 

7. Accept-Ranges: bytes

    - Kertoo, pystyykö palvelin käsittelemään osittaisia latauksia. Tässä tapauksessa kyllä.


8. Content-Length: 397

    - Vastauksen rungon koko tavuina.


9. Vary: Accept-Encoding

    - Ilmaisee, että lähetetyn sisällön pakkausmuooto voi vaihtua. Palvelimelta voi pyytää esimerkiksi _gzip _ pakkausmuotoa. 

9. Content-Type: text/html

    - Palautetun datan tyyppi. Tässä kohdassa siis text/HTML.

_______________________________________________________________________________________________________________________


Lähteet:

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support. https://httpd.apache.org/docs/2.4/vhosts/name-based.html

Karvinen, T 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

curl Command in Linux with Examples. 2025. https://www.geeksforgeeks.org/linux-unix/curl-command-in-linux-with-examples/

Girvin, D. 2025. Understanding the Apache access log: how to view, locate, and analyze. https://www.sumologic.com/blog/apache-access-log



