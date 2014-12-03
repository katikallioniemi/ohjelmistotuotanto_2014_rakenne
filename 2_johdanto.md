## Johdanto

* Kerro tässä luvussa yleiskuvaus projektista
* Mitä tehdään?
* Miksi? Projektin taustatiedot, miksi tällainen projekti on olemassa?  

Järjestelmä on analyysisovellus, jonka avulla voidaan kartoittaa, visualisoida ja luoda ennusteita kiinteistön eri tilojen ja huoneiden todellisista käyttöasteista. Järjestelmän tuottamat analyysit ja ennusteet perustuvat paikannusjärjestelmän tilan käyttäjistä keräämiin paikannustietoihin. Paikannustietojen keruu, analysointi ja tallentaminen tapahtuu automatisoidusti. Järjestelmä pyrkii turvaamaan tilojen käyttäjien yksityisyydensuojan, eikä järjestelmän keräämien tietojen avulla pystytä esimerkiksi seuraamaan yksittäisen käyttäjän kulkua tiloissa.

Järjestelmän tuottamia visualisointeja ja ennusteita voidaan hyödyntää tilankäytön suunnittelussa, sekä yhdistettynä muihin järjestelmiin, voidaan tilojen käyttöä ja ylläpitoa optimoida.

Yhdistelemällä saatuja tietoja esimerkiksi tilanvaraustietoihin ja opetusryhmien lukujärjestystietoihin, voidaan esimerkiksi tuleville tilavarauksille luoda ennusteita toteumista. Tällöin on mahdollista luoda tilanvaraajille suosituksia opetustilan vaihtamisesta pienempään, tai ennusteita ruokalan ruuhkien muodostumiseen tiettyinä kellonaikoina.

Järjestelmän välttämättömät osat ovat:
- käyttäjien paikallistamisen mahdollistava, jokaisen käyttäjän mukana kulkeva pienikokoinen etäluettava tunnistin. (esim. RFID tai Bluetooth Smart)
- tunnistimien etäluvusta vastaava sisätilapaikannusverkko, joka koostuu joukosta tukiasemia
- tietokantajärjestelmä, johon kerätty paikannusdata tallennetaan
- analyysilogiikka, joka käsittelee tallennetusta datasta käyttäjien pyytämät hakutulokset
- käyttöliittymä, jonka kautta käyttäjät tekevät hakukutsut, ja jonka avulla visualisoidut hakutulokset esitetään.

Lisäksi tarvitaan mm. useita ohjelmistokomponentteja eri kerroksiin, esim. tukiasemien kustomointi ja dataliikenteen hallinta, hakutulosten prosessointi visualisoinneiksi, sekä apudataa järjestelmän toimintaa varten, kuten malli kiinteistön tiloista ja kulkureiteistä.