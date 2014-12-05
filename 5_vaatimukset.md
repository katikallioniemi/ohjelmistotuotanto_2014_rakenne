## Vaatimukset 
***
### Funktionaaliset vaatimukset

#### Hakutoiminnot
Hakutoiminnot suoritetaan tekemällä rajauksia hakuehtoihin. Käyttäjä voi valita hakuun kiinteistön tiloja sekä ajanjakson, jolta tiedot haetaan. Hakutulosten esitystapa on valittavissa ennen hakua, ja vaihdettavissa tehdyn haun jälkeen.

##### tilojen valinta

Käyttäjällä on mahdollisuus valita tiloja eri tavoin:

- valitsemalla huoneen pohjapiirroskuvasta klikkaamalla
- valitsemalla useita huoneita pohjapiirroksesta maalaamalla
- tekstihakutoiminnolla, kirjoittamalla huonehakukenttään huoneen nimi tai huoneen numero.
	- kun tekstihakukenttään on kirjoitettu vähintään kolme merkkiä, hakukentän tulee ehdottaa sopivia huoneita tekstijonon alun perusteella
	- kun käyttäjä jatkaa kirjoittamista, ehdotettujen osumien tulee kaventua kohtuullisella viiveellä (esim 1000 ms).
	- mikäli tekstihaun syötteellä ei ole löydettävissä yhtään huonetta, tulee automaattisen täydennystoiminnon vihjeistää käyttäjää esim. palautteella "ei osumia"
    - käyttäjä voi valita ehdotusten joukosta yhden tai useamman klikkaamalla
- tilan voi lisätä tilavalintaan valitsemalla sen luettelosta
	- luetteloa tiloista voi rajata esim. käyttötarkoituksen mukaan, esim. "näytä neuvottelutilat, auditoriot, ATK-luokat"
- tehdyt hakuvalinnat voi tallentaa painikkeella
- tallennetun haun voi nimetä
- tallennetun hakuvalinnan saa uuden haun pohjaksi klikkaamalla painiketta. Tallennetut haut näkyvät käyttäjän omassa työkalupalkissa.
- Jos käyttäjällä on tehtynä hakuvalintoja, ja käyttäjä valitsee tallennetun hakuvalinnan lataamisen, käyttäjälle annetaan varoitus, että tallennettujen hakuvalintojen lataaminen korvaa nykyiset hakuvalinnat.
- Käyttäjälle tarjotaan mahdollisuus poistaa valitsemansa varoitukset käytöstä, ja palauttaa ne myöhemmin takaisin käyttöön.

#####ajanjaksojen valinta
- käyttäjä voi rajata hakuun sisällytettävän ajanjakson liukuvalintasäätimellä. Hakuun sisältyvä ajanjakso esitetään visuaalisesti, esim. värillä
- käyttäjä voi rajata aikajakson syöttämällä alku- ja loppuajan kenttiin, tai valita päivämäärän minikalenterista. Minikalenteri on näkymässä ponnahdusikkunana.

##### hakutulosten näyttäminen
- tulokset voidaan näyttää heat map -esityksenä (käyttäjämäärän mukaan väritetty pohjapiirros)
	- klikkaamalla jotain esitetyistä huoneista, voidaan valittu huone ottaa seuraavan haun tilarajaukseksi. Tällöin valitulle huoneelle haetaan aikasarja käyttäjämääristä viimeisen 14 päivän ajalta, esitysmuotona kuvaaja.
- tulokset voidaan esittää ortograafisen 3d-pohjapiirroksen päällä väreillä ja palkeilla. Kävijämäärät kuvataan palkin korkeutena.
- tulokset voidaan näyttää kuvaajana, aika / käyttäjämäärä
- tulokset voidaan näyttää taulukkona
	- taulukon tiedot voidaan järjestää eri sarakkeiden mukaan
	- taulukko voidaan tallentaa CSV-muodossa tiedostoon
- haetut raportit tallentuvat käyttäjän omalle sivulle katsottavaksi myöhemmin

##### muut hakutoiminnot
- käyttäjä voi hakea ja lajitella tiloja käyttöasteen mukaan tai antamalla raja-arvoja, esim. "näytä viimeisen kuukauden ajalta tiedot tiloista, joissa on ollut keskimäärin alle viisi käyttäjää tunnissa, välillä klo 9.00-16.00".


#### ylläpito
- ylläpitäjä voi tarkastella/rajata/lisätä käyttäjän oikeuksia tarkastella tiloja 
- ylläpitäjä voi poistaa käyttäjän
- ylläpitäjä voi lisätä käyttäjän
- ylläpitäjä voi saada nähtäväkseen statistiikkatietoja paikannusjärjestelmän toiminnasta, kuten tukiasemien virhelokin, paikannusdatan suodatuksen statistiikan (montako epäonnistunutta paikannusta, miltä tukiasemalta)

#### paikannusjärjestelmän toiminta
- paikannusjärjestelmä voi lukea/paikantaa 2000 tunnistetta per hakupyyntö
- etäpaikannus voidaan tehdä onnistuneesti missä tahansa kiinteistön tiloissa varmuudella x.
- yhteyden katkeamisen jälkeen paikannusverkon tukiasemien tulee osata kytkeytyä automaattisesti takaisin verkkoon, ja toimittaa virheraportti.
- paikannusverkon tukiasemien tulee vastata järjestelmän kutsuihin määräajassa (esim. ping alle 200 ms)
- pienin sallittu huonekohtainen paikannusten onnistumisprosentti on x

***

### Ei-funktionaaliset vaatimukset
- Käyttöliittymän on oltava niin helppokäyttöinen, että uuden käyttäjän on voitava suorittaa onnistunut tilahaku ilman ohjekirjaa <3 minuutissa.
- käyttöliittymäsovelluksen, hakulogiikan ja tietokantajärjestelmän täytyy pystyä palvelemaan 500 yhtäaikaista käyttäjää. (1 hakutoiminto per 30 sek, per käyttäjä, jokaisella perättäisellä haulla 1/3 eri hakuvaihtoehdot.
- hakutulosten esittämisen viive ei saa olla yli 3000 ms hakupyynnön lähettämisen jälkeen