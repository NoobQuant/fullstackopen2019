

## Eka appi

### Apin p��sivu
https://fullstack-exampleapp.herokuapp.com/

 - "Perinteinen" web-sovellus
    - Ment�ess� sivulle, selain hakee palvelimelta sivun strukturoinnin ja tekstuaalisen sis�ll�n m��rittelev�n HTML-dokumentin.
    - Perinteisiss� websovelluksissa selain on "tyhm�", se ainoastaan pyyt�� palvelimelta HTML-muodossa olevia sis�lt�j�, kaikki sovelluslogiikka on palvelimessa.
 - Tekee avattaessa Get-metodilla pyyn�n, saa 2 vastausta palvelimelta
    - 'index' html-sivun fullstack-exampleapp. On tyyppi� 'document', sil� ei n�y tiedostop��tett�
    - kuvan
    
### Muistiinpanot-sivu

 - Hakee nelj� tiedostoa
    - main.js sis�lt�� event handlerin joka parsii uudet muistiinpanot listaan.
    - Sekvenssikaavio mit� tapahtuu: https://fullstackopen-2019.github.io/osa0/web_sovelluksen_toimintaperiaatteita#javascriptia-sisaltavan-sivun-lataaminen-kertaus
    - **Lomakkeen l�hett�minen (POST) aiheuttaa yll�tt�en yhteens� viisi HTTP-pyynt��!!**

#### Lomakkeen l�hett�minen
 - new_note pyynt�: HTTP POST, tehty palvelimen osoitteeseen new_note. Palvelimella oleva koodi huolehtii POSTin toteuttamisesta: se puskee taulukkoon *notes* POSTin mukana tuleen viestin. Palvelin vastaa pyynt��n statuksella 302, eli uudelleenohjauspyyn�ll�, mink� avulla palvelin kehottaa selainta tekem��n automaattisesti uuden GET-pyynn�n osoitteeseen notes.
 - Selain tekee uuden GETin notes, eli siis **lataa udelleen** muistiinpanojen sivun.
 - Sivunlataus saa aikaan samat muut kolme pyynt�� kuin aikaisemminkin.
    
## AJAX
 - Termi, joka lanseerattiin vuoden 2005 helmikuussa kuvaamaan selainten kehityksen mahdollistamaa vallankumouksellista tapaa, miss� HTML-sivulle sis�llytetyn Javascriptin avulla oli mahdollista ladata sivulle lis�� sis�lt�� lataamatta itse sivua uudelleen.
 - Ennen AJAX:in aikakautta jokainen sivu toimi aiemmassa luvussa olevan perinteisen web-sovelluksen tapaan, eli oleellisesti ottaen kaikki sivuilla n�ytett�v� data tuli palvelimen generoimassa HTML-koodissa.
 
## Single-page style muistiinpanot app
https://fullstack-exampleapp.herokuapp.com/spa

 - Viimeisten vuosien aikana on noussut esiin tyyli tehd� web-sovellukset k�ytt�en Single-page application (SPA) -tyyli�, miss� sovelluksilla ei en�� ole esimerkkisovelluksemme tapaan erillisi�, palvelimen sille l�hett�mi� sivuja, vaan sovellus koostuu ainoastaan yhdest� palvelimen l�hett�m�st� HTML-sivusta, jonka sis�lt�� manipuloidaan selaimessa suoritettavalla Javascriptill�.
 - Sovelluksemme muistiinpanosivu muistuttaa jo hiukan SPA-tyylist� sovellusta, sit� se ei kuitenkaan viel� ole, sill� vaikka muistiinpanojen render�intilogiikka on toteutettu selaimessa, k�ytt�� sivu viel� perinteist� mekanisimia uusien muistiinpanojen luomiseen, eli se l�hett�� uuden muistiinpanon tiedot lomakkeen avulla ja palvelin pyyt�� uudelleenohjauksen avulla selainta lataamaan muistiinpanojen sivun uudelleen.
 - **Lomakkeen l�hett�minen aiheuttaa vain yhden pyynn�n palvelimelle**, eli koko sivu ei siis lataudu uudelleen.
 
## Javascriot-kirjastot
 - JQuery on kehitetty aikana, jolloin web-sivut olivat viel� suurimmaksi osaksi perinteisi�, ja joiden toiminnallisuutta rikastettiin selaimessa JQueryll� kirjoitetun Javascript-koodin avulla.
 - Single page app -tyylin noustua suosioon on ilmestynyt useita JQuery� "modernimpia" tapoja sovellusten kehitt�miseen. Nykyisin React tai Vue.