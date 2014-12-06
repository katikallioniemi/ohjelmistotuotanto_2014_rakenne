## Käyttöliittymän keskeiset näkymät
- sisäänkirjautuminen
- päänäkymä
- tilahaku
- hakutulosten tarkastelu
- omat tallennetut haut 
- oma hakuhistoria

## Näkymien suhteet

![Näkymästä toiseen siirtyminen](http://users.metropolia.fi/~katikal/files/OLAF-kayttoliittyman_nakymat.png)

#### Sisäänkirjautuminen

Näkymässä on tekstikentät käyttäjän tunnukselle ja salasanalle sekä painike sisäänkirjautumiselle. Sisäänkirjautumisesta siirrytään päänäkymään.

#### Päänäkymä

![Käyttöliittymän mockup](http://users.metropolia.fi/~joonasli/ohtu-2014/OLAF_UI_mockup.jpg)
**Käyttöliittymän havainnekuva**

Päänäkymästä voidaan siirtyä tilahakuun, tallennettuihin hakuihin, omaan hakuhistoriaan tai kirjautua ulos, jolloin palataan sisäänkirjautumisnäkymään.
Sisäänkirjautumisen jälkeen päänäkymässä esitetään valmis hakutulosnäkymä, jossa heat map -kuva, jonka hakuehtoina on kiinteistön aulatilat ja suurimmat käytävät ja ajanjaksona kuluva vuorokausi (tai edelliset kaksi tuntia) alkaen klo 8.00, tai käyttäjän valitsema oletusnäkymä.

#### Tilahakunäkymä

Tilahaku tehdään valitsemalla halutut tilat, tarkastelun aikaväli ja tietojen esitystapa. Erilaisia tilavalintatapoja varten on erilaisia asioita: 
- Tilahakunäkymässä on kiinteistön pohjakuva, joka näyttää korostettuna tällä hetkellä valintaan sisältyvät tilat. Klikkaamalla kiinteistön pohjapiirroskuvaa voidaan huoneita lisätä tai poistaa valinnasta.
- Mikäli kiinteistössä on useita kerroksia, voidaan kerrosta vaihtaa valintapalkista. Valintapalkki kertoo myös visuaalisesti tällä hetkellä näkymässä olevan kerroksen, sekä korostuksella ne kerrokset, joiden tiloja sisältyy tämänhetkiseen valintaan.
- Näkymässä on tekstikenttä, johon kirjoittamalla tilan nimen/tunnuksen tiloja voi liittää valintaan. 
- Näkymässä on valintalista-laatikko, johon on listattu kaikki tilat. Tiloja voi siirtää listalta valintaan. Listaa on mahdollista filtteröidä esim. toiminnallisuuksittain, kerroksittain, ja näiden yhdistelmillä.
- Käyttäjä voi klikata esiin listan, joka sisältää tämänhetkisen valinnan tilat. Käyttäjä voi poistaa yksittäisiä tiloja valinnasta klikkaamalla tilan nimen vieressä olevaa painiketta (esim. punainen ruksi).

Tilavalinnan jälkeen haun aikarajaus tehdään aikajanalta liukusäätimillä, syöttämällä päivämäärät minikalenterin tai tekstikentän avulla tai kirjoittamalla kellonaika tekstikenttään. Uuden haun aikarajauksen myöhempänä rajaehtona on oletuksena nykyhetki.

Tietojen esitystavan valinta tehdään korostamalla halutut esitystavat thumbnail-listalta

Kun käyttäjä on valinnut haluamansa tilat, aikavälin ja tietojen esitystavan, painiketta painamalla siirrytään näkymään hakutulosten tarkastelu.

#### Hakutulosten tarkastelu

Valitut visualisoinnit näytetään, ne voi tallentaa. Hakutulossivu on toiminnaltaan hyvin samankaltainen hakuvalintasivun kanssa, ja hakutulossivulta käyttäjä voi helposti muokata hakuvaihtoehtoja ja tehdä uuden haun.

#### Omat tallennetut haut 

Käyttäjän perusnäkymässä käyttäjälle tarjotaan valintapalkki, jossa on käyttäjän tallentamat valmiit haut. Käyttäjällä on mahdollisuus antaa tallennetuille hauille nimet ja omat värit. Jättämällä kursorin tallennetun hakusymbolin päälle, käyttäjälle tarjotaan mini-ikkunassa tiiviissä muodossa tarkemmat tiedot kyseisen haun hakuparametreista, kuten esim. "Nimi: "uudet neukkarit", huoneita 6 kpl, aikaväli 14 vrk, esitys kuvaajana".