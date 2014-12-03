## Käyttötapaukset

* Määritä tänne järjestelmän loppukäyttäjät
* Käyttötapauskaavio, jossa järjestelmän keskeiset käyttötapaukset
* Kuvaile tärkeimmät käyttötapauksista käyttötapausskenaarioina mallipohjaan perustuen
  * mallipohja: määritä alkutila (initial state), normaali kulku (normal flow), lopputila (end state)
  * kerro myös kuinka normaali kulku voi mennä pieleen sekä
  * mahdolliset vaihtoehtoiset kulut (alternate flow)
---------------  

##Käyttäjäryhmät
Järjestelmän käyttäjäryhmät ovat "muurahaiset", "kyylät" ja ylläpitäjät. 

**Muurahaiset** ovat tilan käyttäjät. He eivät suoraan vuorovaikuta sovelluksen kanssa, he pitävät etäluettavaa tunnistetta mukanaan. Käyttäessään tiloja järjestelmä etälukee tunnisteiden sijainnit, jotka tallennetaan tietokantaan. 

**Kyylät** ovat analyysisovelluksen pääkäyttäjäryhmä. Heillä on pääsy järjestelmän tuottamaan analyysitietoon tilojen käytöstä. He hyödyntävät järjestelmän tuottamaa tietoa, esim. tilojen tehokkaampaa käyttöä suunniteltaessa.

**Ylläpitäjät** hallinnoivat järjestelmää: lisäävät käyttäjiä ja muokkaavat käyttäjien oikeuksia, lisäävät muurahaisten tunnisteet järjestelmään.

## Käyttötapaukset

![Käyttäjätapaukset](http://users.metropolia.fi/~katikal/files/ohtu-projekti-UseCaseD.png)

## Keskeiset käyttötapaukset


### "Kyylät"
##### Hae tila
- alkutila
- normaali kulku:
- lopputila:
- vaihtoehtoinen kulku:
- pieleen meno:

##### Hae tilan käyttöhistoria
- alkutila (initial state): Käyttäjä on kirjautunut järjestelmään
- normaali kulku (normal flow): 
    1. Valitse valikosta hakutoiminto
    1. Järjestelmä siirtyy hakusivulle
    1. Valitse haluttu tila, jonka data esitetään:
        * valitse tallennettu tilahaku
        * muokkaa valittuja huoneita aktivoimalla/deaktivoimalla ne pohjapiirroksesta
        - TAI tee uusi tilahaku:
            -  tarkempi kuvaus
    1. Valitse tarkastelun aikaväli
    1. Valitse datan esitystapa mahdollisten joukosta: heat map, kuvaaja (käyttäjät/aika), taulukko, raakadata **(muita?)**
    1. Valitse esitystapa valitsemalla sitä vastaava painike: näytä tai tallenna tiedostoon. 
    1. Järjestelmä hakee tietokannasta valitut tiedot ja piirtää mahdolliset valitut visualisoinnit
- lopputila (end state): 
    -  Järjestelmä näyttää haetut tiedot ja valitussa muodossa: jos valittiin tallenna tiedostoon, käyttöjärjestelmän dialogi kysyy tiedostojen tallennuspaikan. 
    - Jos valittiin näytä kuva, kuvan yhteydessä painikkeet, 1: tallenna kuvat/kuvaajat tiedostoon, ja käyttäjä voi tallentaa haun omiin hakuvalintoihin.
- kuinka normaali kulku voi mennä pieleen sekä
- mahdolliset vaihtoehtoiset kulut (alternate flow)



##### Hae tilan käyttöennuste
