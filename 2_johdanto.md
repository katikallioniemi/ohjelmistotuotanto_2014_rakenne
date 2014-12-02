## Johdanto

* Kerro tässä luvussa yleiskuvaus projektista
* Mitä tehdään?
* Miksi? Projektin taustatiedot, miksi tällainen projekti on olemassa?  

Järjestelmä on analyysisovellus, jonka avulla tilan hallinnoija saa todellisiin tilan käyttäjien paikannustietoihin perustuvaa dataa siitä, missä tilojen käyttäjät kiinteistössä milloinkin ovat. Näitä tietoja voidaan hyödyntää tilankäytön suunnittelussa, esimerkiksi miettimällä uudelleen vajaakäytölle jäävien tilojen käyttötarkoitusta, lisäsiivouksen kohdistamista eniten käytettyihin tiloihin sekä ennakoida ruokalan ruuhkien syntymistä.

Järjestelmän välttämättömät osat ovat:
- käyttäjien paikallistamisen mahdollistava, jokaisen käyttäjän mukana kulkeva pienikokoinen hardware-laite
- sisätilapaikannuksen toiminnallisesta tasosta vastaava paikannusjärjestelmä
- tietokantajärjestelmä, johon kerätty paikannusdata tallennetaan
- analyysilogiikka, joka toteuttaa tietokantahakuja
- käyttöliittymä, jonka kautta käyttäjä tekee hakuja aineistoon, ja jonka kautta hakujen tulokset esitetään käyttäjille