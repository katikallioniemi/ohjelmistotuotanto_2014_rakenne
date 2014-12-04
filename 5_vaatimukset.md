## Vaatimukset 

* Kuvaile tänne funktionaaliset ja ei-funktionaaliset vaatimukset
* Funktionaaliset vaatimukset
  * Tarkentavat käyttötapauksia
* Ei-funktionaaliset vaatimukset
  * Esim käytettävyyteen, tietoturvaan, tehokkuuteen, skaalautuvuuteen, hintaan ja prosessimalliin liittyvät vaatimukset
* **Muista esittää vaatimukset jäljitettävässä muodossa, yksiselitteisesti**
* Keskeinen tapa (erityisesti ei-funktionaalisiin vaatimuksiin) yksiselitteisille kuvauksille on vaatimusten **mitattavuus** (software metrics)

----------------------------------------

### Funktionaaliset vaatimukset

##### tilojen haku
- ennen haun suorittamista käyttäjä lisää tiloja tilavalintaan
- tilan voi lisätä tilavalintaan korostamalla huoneen pohjapiirroksesta
- tilan voi lisätä tilavalintaan kirjoittamalla tilan nimen (alun) tai tunnuksen hakuruutuun
    - järjestelmä ehdottaa kolmen merkin kirjoittamisen jälkeen täydennystä tilan nimelle 
    - käyttäjä voi valita ehdotusten joukosta yhden tai useamman
- tilan voi lisätä tilavalintaan valitsemalla sen luettelosta
- luettelossa näytettäviä tiloja voi rajata toiminnallisuuksittain
- hakuvalinnat voi tallentaa 
- tallennetun haun voi nimetä
- tallennetun hakuvalinnan saa uuden haun pohjaksi

##### tulosten näyttäminen
- tulokset voidaan näyttää raakadatana
- tulokset voidaan näyttää taulukkona
- tulokset voidaan näyttää heat map -esityksenä
- tulokset voidaan näyttää kuvaajana, aika / käyttäjät
- haetut raportit tallentuvat käyttäjän omalle sivulle katsottavaksi myöhemmin

##### ylläpito
- ylläpitäjä voi tarkastella/rajata/lisätä käyttäjän oikeuksia tarkastella tiloja 
- ylläpitäjä voi poistaa käyttäjän
- ylläpitäjä voi lisätä käyttäjän


### Ei-funktionaaliset vaatimukset
- uuden käyttäjän on voitava suorittaa tilahaku ilman ohjekirjaa <3 minuutissa
- paikannusjärjestelmä voi lukea/paikantaa 2000 tunnistetta kerralla
- paikannustukiasemien verkko kattaa rakennuksen kaikki tilat