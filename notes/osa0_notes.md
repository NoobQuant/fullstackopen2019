

## Eka appi

### Apin pääsivu
https://fullstack-exampleapp.herokuapp.com/

 - "Perinteinen" web-sovellus
    - Mentäessä sivulle, selain hakee palvelimelta sivun strukturoinnin ja tekstuaalisen sisällön määrittelevän HTML-dokumentin.
    - Perinteisissä websovelluksissa selain on "tyhmä", se ainoastaan pyytää palvelimelta HTML-muodossa olevia sisältöjä, kaikki sovelluslogiikka on palvelimessa.
 - Tekee avattaessa Get-metodilla pyynön, saa 2 vastausta palvelimelta
    - 'index' html-sivun fullstack-exampleapp. On tyyppiä 'document', silä ei näy tiedostopäätettä
    - kuvan
    
### Muistiinpanot-sivu

 - Hakee neljä tiedostoa
    - main.js sisältää event handlerin joka parsii uudet muistiinpanot listaan.
    - Sekvenssikaavio mitä tapahtuu: https://fullstackopen-2019.github.io/osa0/web_sovelluksen_toimintaperiaatteita#javascriptia-sisaltavan-sivun-lataaminen-kertaus
    - **Lomakkeen lähettäminen (POST) aiheuttaa yllättäen yhteensä viisi HTTP-pyyntöä!!**

#### Lomakkeen lähettäminen
 - new_note pyyntö: HTTP POST, tehty palvelimen osoitteeseen new_note. Palvelimella oleva koodi huolehtii POSTin toteuttamisesta: se puskee taulukkoon *notes* POSTin mukana tuleen viestin. Palvelin vastaa pyyntöön statuksella 302, eli uudelleenohjauspyynöllä, minkä avulla palvelin kehottaa selainta tekemään automaattisesti uuden GET-pyynnön osoitteeseen notes.
 - Selain tekee uuden GETin notes, eli siis **lataa udelleen** muistiinpanojen sivun.
 - Sivunlataus saa aikaan samat muut kolme pyyntöä kuin aikaisemminkin.
    
## AJAX
 - Termi, joka lanseerattiin vuoden 2005 helmikuussa kuvaamaan selainten kehityksen mahdollistamaa vallankumouksellista tapaa, missä HTML-sivulle sisällytetyn Javascriptin avulla oli mahdollista ladata sivulle lisää sisältöä lataamatta itse sivua uudelleen.
 - Ennen AJAX:in aikakautta jokainen sivu toimi aiemmassa luvussa olevan perinteisen web-sovelluksen tapaan, eli oleellisesti ottaen kaikki sivuilla näytettävä data tuli palvelimen generoimassa HTML-koodissa.
 
## Single-page style muistiinpanot app
https://fullstack-exampleapp.herokuapp.com/spa

 - Viimeisten vuosien aikana on noussut esiin tyyli tehdä web-sovellukset käyttäen Single-page application (SPA) -tyyliä, missä sovelluksilla ei enää ole esimerkkisovelluksemme tapaan erillisiä, palvelimen sille lähettämiä sivuja, vaan sovellus koostuu ainoastaan yhdestä palvelimen lähettämästä HTML-sivusta, jonka sisältöä manipuloidaan selaimessa suoritettavalla Javascriptillä.
 - Sovelluksemme muistiinpanosivu muistuttaa jo hiukan SPA-tyylistä sovellusta, sitä se ei kuitenkaan vielä ole, sillä vaikka muistiinpanojen renderöintilogiikka on toteutettu selaimessa, käyttää sivu vielä perinteistä mekanisimia uusien muistiinpanojen luomiseen, eli se lähettää uuden muistiinpanon tiedot lomakkeen avulla ja palvelin pyytää uudelleenohjauksen avulla selainta lataamaan muistiinpanojen sivun uudelleen.
 - **Lomakkeen lähettäminen aiheuttaa vain yhden pyynnön palvelimelle**, eli koko sivu ei siis lataudu uudelleen.
 
## Javascriot-kirjastot
 - JQuery on kehitetty aikana, jolloin web-sivut olivat vielä suurimmaksi osaksi perinteisiä, ja joiden toiminnallisuutta rikastettiin selaimessa JQueryllä kirjoitetun Javascript-koodin avulla.
 - Single page app -tyylin noustua suosioon on ilmestynyt useita JQueryä "modernimpia" tapoja sovellusten kehittämiseen. Nykyisin React tai Vue.