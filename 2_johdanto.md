## Johdanto


OLAF-järjestelmä on analyysisovellus, jonka avulla voidaan kartoittaa ja visualisoida tietoja kiinteistön eri tilojen todellisista käyttöasteista. Järjestelmän tuottamat hakutulokset ja ennusteet perustuvat tallennetun paikannusdatan analysointiin. Valmiit hakutulokset esitetään käyttäjille ihmislukijalle intuitiivisessa visuaalisessa muodossa.

Järjestelmään kuuluvan paikannusjärjestelmän hoitama paikannusdatan keruu, filtteröinti ja tallentaminen tapahtuu automatisoidusti.

Järjestelmä pyrkii turvaamaan tilojen käyttäjien yksityisyydensuojan, eikä järjestelmän keräämien tietojen avulla pystytä esimerkiksi seuraamaan yksittäisen käyttäjän kulkua tiloissa.

Järjestelmän tuottamia visualisointeja ja ennusteita voidaan hyödyntää tilankäytön suunnittelussa, sekä yhdistettynä muiden käytössä olevien järjestelmien tarjoamiin tietoihin, voidaan tilojen käyttöä ja ylläpitoa optimoida.

Esimerkiksi yhdistelemällä saatuja tietoja tilanvaraustietoihin ja opetusryhmien lukujärjestystietoihin, voidaan tuleville tilavarauksille luoda ennusteita toteumista. Tällöin on mahdollista tarjota tilanvaraajille suosituksia opetustilan vaihtamisesta pienempään, tai ennusteita ruokalan ruuhkien muodostumiseen tiettyinä kellonaikoina.

**OLAF-järjestelmän välttämättömät osat ovat:**
- käyttäjien paikallistamisen mahdollistava, jokaisen käyttäjän mukana kulkeva pienikokoinen etäluettava tunnistin. (esim. RFID tai Bluetooth Smart)
- tunnistimien etäluvusta vastaava sisätilapaikannusverkko, joka koostuu joukosta tukiasemia
- tietokantajärjestelmä, johon kerätty paikannusdata tallennetaan
- analyysilogiikka, joka käsittelee tallennetusta datasta käyttäjien pyytämät hakutulokset
- käyttöliittymä, jonka kautta käyttäjät tekevät hakukutsut, ja jonka avulla visualisoidut hakutulokset esitetään.

Lisäksi tarvitaan mm. useita ohjelmistokomponentteja eri tasoille, esim. tukiasemien kustomointi ja dataliikenteen hallinta, hakutulosten prosessointi visualisoinneiksi, sekä apudataa järjestelmän toimintaa varten, kuten malli kiinteistön tiloista ja kulkureiteistä.