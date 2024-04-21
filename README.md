### DAT255-prosjekt



# Personalized fashion recommendations
Av Susanne Å. Løtvedt

## Sammendrag
Det finnes mange måter å lage et system for å anbefale klær. Denne rapporten fokuserer på tre ulike måter. Den ene er å anbefale basert på hva andre har kjøpt sammen med et valgt produkt. Denne måten ga gode resultater og krevde ikke maskinlæring. Den andre måten er å bruke “Collaborative filtering” for å anbefale produkter til en kunde basert på hva lignende kunder også har kjøpt. Dette viste seg å være vanskelig å få til og ble derfor mislykket. Den siste metoden var å prøve bildeklassifisering og analysere resultatene av denne. Denne ga gode og interessante resultater, som kunne fortelle noe om hvordan denne kan bli brukt i et anbefalingssystem.  

## Innledning
### Problem beskrivelse
Det finnes mange måter å anbefale et produkt til en kunde, og som innebærer ulike utgangspunkter og situasjoner. Anbefalingene avhenger av hvilke oppsett butikkjedene har valgt å bruke for produktinformasjon og hvilke muligheter kundene har. Dette kan være hvilke kategorier produktene er sortert under, som kan beskrive utseende, materiale, avdeling osv. For kunder kan det være mulig å lage en bruker eller bestille varer som gjest. Noen butikker gir mulighet for kundene å ha et medlemskap som gir dem ekstra fordeler både fysisk og på nett. Nettbutikker gir ofte mulighet for kunder å kunne lagre en handleliste, legge til produkter i en ønskeliste, gi dem poeng for kjøp og/eller å legge til en vurdering av produktene de har kjøpt. Utgangspunkt for anbefalinger kan være basert på kunden eller produktet. Ved å ta utgangspunkt i kunden kan anbefalingene være basert på hva kunden har kjøpt før, hva andre lignende kunder har kjøpt før eller ved å se på hvilke vurderinger kunden ga. Det går også an å anbefale med utgangspunkt i selve varen ved å finne lignende varer, ut fra tilhørende sesong, tilhørende kategorier, basert på hva andre har kjøpt samtidig eller ved å se på hvilke varer som ligner osv.
Dette prosjektet vil utforske tre ulike løsninger på noen av disse utgangspunktene og diskutere hvorvidt de fungerer. 

### Eksisterende løsninger
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/6b941294-d049-4b9b-824b-70963a08bbf9)
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/372b0ed1-d03c-4d41-974e-acdc95fb8ce6)
https://www2.hm.com/no_no/productpage.1138084011.html

H&M gir to ulike typer av anbefalinger. “Styles med” gir et utvalg av andre produkter dette plagget passer sammen med for å bli et helt antrekk. “Andre har også kjøpt” viser hva andre også har kjøpt sammen med dette plagget. 

![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/d9eaa965-152e-458e-8953-71df479a867d)
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/e4407435-8582-46ad-aaee-9fc72e4faf56)
https://cubus.com/no/p/skjortekjole-med-krage-svart-kjoler-dameklar/7359049_F990

Cubus har også to måter de anbefaler lignende produkter på, men det er litt usikkert hva  disse er basert på. “Kanskje du også liker?” ser ut til å ta utgangspunkt i klær som ligner mest på det valgte plagget. “Mange elsker disse” er mest sannsynlig basert på hva andre har kjøpt sammen med dette plagget. 


## Prosjektbeskrivelse og oppbygging
### Avgrensninger
Prosjektet har ulike krav for hvordan det skal utføres.
Dette prosjektet skal bruke Python som kodespråk. Det vil også bare ta i bruk et datasett, og er derfor avgrenset av hva denne inneholder.
Utføring av prosjektet er også begrenset av egen kunnskap og kapabiliteter. 

### Ressurser
Ulike ressurser vil bli tatt i bruk for å gjennomføre prosjektet.
Prosjektet tar i bruk datasettet fra “H&M Personalized Fashion Recommendations” konkurransen på Kaggle(3). Notatbøker fra denne konkurransen og FastAI kurset er blitt brukt for inspirasjon til løsninger. 
Prosjektet har tilgang til datamaskin og iPad for å lage og utforske prosjektet.

### Verktøy
Prosjektet skrives i Kaggle og blir gjort tilgjengelig på GitHub. Prosjektet tar også i bruk fastai biblioteket for å lage metodene og modellene. 

### Metoder
#### Anbefale basert på valgt produkt
Dette er en løsning som handler om finne anbefalte produkter basert på hva det valgte produktet oftest kjøpes sammens med. Denne ligner løsningene “Andre har også kjøpt” fra H&M, og “Mange elsker disse”. Det er ikke nødvendig å bruke maskinlæring for å få til denne løsningen. 

#### Collaborative filtering
“Collaborative filtering” er en teknikk som handler om å finne anbefalinger basert på andre brukere. Dette gjør den ved å se på hva brukeren liker, finner andre brukere som liker de samme produktene og deretter gir anbefalinger basert på andre produkter disse brukerne også liker(1). For å finne ut hva diverse brukere liker kan den se på ulike vurderinger brukere har gitt produktene de har brukt. Denne delen av prosjektet er sterkt basert på et eksempel fra fastai kurset. Det ble prøvd ut både en vanlig maskinlæring modell og en “deep learning" modell. 

#### Bildegjenkjenning 
Denne metoden handler om å gjenkjenne innholdet av bildet av produktet. Dette prosjektet vil lage en modell for bildeklassifisering, som handler om å identifisere og kategorisere bilder under spesifikke klasser. 
Denne metoden vil altså ikke bli brukt til å lage en løsning for å finne anbefalinger i dette prosjektet, men heller bli brukt til å analysere hvorvidt denne metoden kan brukes til å generere anbefalinger.
Resultatene vurderes ved hjelp av en “confusion matrix”, som er en matrise som viser hvor mange ganger en modell klassifiserte bilder i feil kategori. Kolonnene til matrisen viser den faktiske kategorien, og radene viser de kategoriene den forutså. Den hjelper altså på å vise hvordan klassifiseringsmodeller presterer når den er ferdig trent(2). Hvis modellen ofte klassifiserer en spesifikk kategori av bilder under den samme ukorrekte kategorien, vil dette vises som et høyt tall og ruten vil ha en mørk farge. 
Bildene ble klassifisert under “product_type_name”, som inneholder 130 ulike kategorier.
Dette er også den metoden som tar lengst tid å kjøre. Derfor vil resultatene i denne rapporten bare vise at den er trent to ganger. 


## Resultater
### Andre har også kjøpt
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/fd970c1e-1971-461a-baf3-c4f72a35d775)

Kjøp som ble gjennomført etter 3.7.2020 ble filtrert ut for å gjøre datasettet mindre, og for å bedre reflektere de nyeste trendene. Basert på bildene av resultatet kan vi se at det inneholder mange produkter som ser ut til å passe sammen, eller tilhøre samme type. Dette ser vi spesielt på det tredje eksempelet på bildet der man ser at det er en klar sammenheng mellom samme rutete mønster og brune farge, og at de tilhører samme stil. 

### Collaborative filtering
Resultatene fra denne delen av prosjektet var dessverre ganske dårlig. 
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/8e47354d-6ddf-4a83-af0b-34b690e348d9)

“Accuracy”, som betyr nøyaktighet eller presisjon, blir brukt til å måle hvor ofte en modell klarer å forutse riktig resultat. Denne er kalkulert ved å ta antall riktige forutsigelser, og dele dem på antallet av alle forutsigelsene. For eksempel, hvis en modell utfører 100 forutsigelser, og har riktig på 50 av dem, så vil den ha 50% “accuracy”. Jo høyere prosent, jo bedre er modellen.  
Begge modellene i dette tilfellet hadde 0% “accuracy”. Jeg klarte heller ikke finne ut hvordan det var mulig å vise resultatene fra modellene. 

### Bildegjenkjenning
Tabellen med produktartikler ble her koblet til tilhørende bilder. Det ble nødvendig å fjerne produkter som ikke hadde tilhørende bilde. 
Det første resultatet som oppsto ved å bruke bildeklassifisering var at modellen ga en error under testfasen om at den ikke hadde lært hva en "washing bag” var. Det var derfor nødvendig å fjerne produkter innenfor kategorier 
Dermed ble det bestemt at hvis det er under 20 produkter innenfor en kategori, så blir disse fjernet. Dette endte opp med 86 gjenværende kategorier som bildene kan klassifiseres innenfor.
![image](https://github.com/602114/DAT255-prosjekt/assets/89074496/fa1e54f9-a05b-4e01-8a18-65e0d5ab7877)

Ettersom at det er veldig mange kategorier, er det ikke mulig å lese de konkrete verdiene i matrisen. Man kan derimot se ved hjelp av fargene at det er noen kategorier som oftere klassifiseres feil enn andre. 
De top 20 kategoriene som ble klassifisert feil flest ganger var:

  'Top' og 'T-shirt': 147
  'Leggings/Tights' og 'Trousers': 143
  'Top' og 'Sweater': 133
  'Sweater' og 'Hoodie': 123
  'Top' og 'Blouse': 122
  'Blouse' og 'Dress': 111
  'Sweater' og 'T-shirt': 77
  'Top' og 'Dress': 74
  'Top' og 'Vest top': 74
  'Blouse' og 'Shirt': 72
  'T-shirt' og 'Top': 70
  'Sweater' og 'Top'. 68
  'Jumpsuit/Playsuit' og 'Dress': 62
  'T-shirt' og 'Sweater': 61
  'Trousers' og 'Leggings/Tights': 57
  'Shirt' og 'Blouse': 56
  'Shorts' og 'Trousers', 49
  'Swimwear bottom' og 'Shorts': 43
  ‘Coat' og 'Jacket': 37
  'Trousers' og 'Jumpsuit/Playsuit': 35


## Diskusjon
### Andre har også kjøpt
Dette viste seg å være en enkel metode som ikke krever noen form for maskinlæring for å gi gode resultater. Dette er fordi den bruker kundenes meninger direkte til å finne resultater. Dette betyr også at denne metoden ikke får problemer når trender forandrer seg. Problemene kan derimot oppstå når nye produkter legges til. Dette kan løses ved å supplere med andre metoder som vist med hvordan H&M og Cubus gjør sine anbefalinger. 
Gjennom disse resultatene kan man også analysere kundenes kjøpsmønster, som for eksempel at det er mer vanlig for kunder å kjøpe lignende plagg enn å kjøpe hele antrekk. 

### Collaborative filtering
Det var under denne metoden det ble åpenbart at jeg hadde undervurdert prosjektet. Når man først ser på denne oppgaven og datasettet er det lett å tenke seg at "collaborative filtering” vil passe perfekt til å finne produktanbefalinger til individuelle kunder. Det er derimot noen problemer som gjorde at denne ble vanskelig å bruke og fikk så dårlig resultat.
Et av problemene er innholdet i datasettet fra H&M sin konkurranse. Et annet problem var forståelse rundt bruken av metoden, som dermed endte opp med at det ble prøvd å løse det på samme måte som fastai kurset(1). Fastai forklarer et eksempel som går ut på å anbefale filmer basert på rangeringer gitt av diverse brukere for filmer de har sett. Dette vil si at en bruker har vurdert en film fra 1 til 5, der 0 betyr at de ikke har gitt filmen en vurdering. Man kan si det er tre viktige elementer her; at det er mulig å se om brukeren likte produktet, at brukeren ikke likte produktet, og at brukeren ikke har vurdert produktet.  
For at denne metoden skal kunne fungere i dette prosjektet, må de samme elementene være tilgjengelig. 
Dersom en bruker har kjøpt et produkt, fikk denne verdien “1”, og hvis de da ikke har kjøpt et produkt vil dette vises som “0”. Det er derimot ingen verdi som viser om en bruker ikke likte produktet. Dette gjorde at det ble veldig komplisert å lage en "collaborative filtering” modell for dette datasettet. 
Ettersom det heller ikke ble funnet en måte å skrive ut noen anbefalinger gjort av denne modellen, og lite tid, ble den ikke ferdig og derfor mislykket.
Hvis det er ønskelig å lage en løsning som bruker "collaborative filtering”, kan det derfor være best å finne et datasett som spesifikt inneholder rangeringer.  

### Bildegjenkjenning
Denne metoden ble egentlig utført som et desperat forsøk etter å få til noe innenfor maskinlæring. Resultatene viser at dette ble oppnådd. 
Selv om det var en del kategorier som ble fjernet, er 86 fortsatt et ganske høyt antall kategorier. Dette betyr at det er mye rom for modellen og ta feil, som da kan gi en indikasjon på hvordan bildegjenkjenning vil fungere i et anbefalingssystem. Resultatene viser at modellen gjorde en generell god jobb med å tildele de riktige kategoriene. Det er derimot noen kategorier den sliter med. Basert på resultatene ser vi at disse feilene er mest vanlig for produkter som ligner mye på hverandre. Dette kan bety at et anbefalingssystem som bruker bildegjenkjenning, kan fungere til å anbefale lignende produkter. 

Utfordringer med denne løsningen kan derimot oppstå dersom bildet inneholder flere produkter eller en person som har på seg produktet. Dette er fordi den kan anbefale produkter med bilder som viser lignende personer, i stedet for et lignende produkt. Det kan derfor være nødvendig at et bilde som bare inkluderer produktet er tilgjengelig, slik at modellen ikke mister fokus. Det er også mulig dette kan løses ved å utføre bildeklassifisering først, for så å anbefale produkter basert på den klassifiseringen.

### Egen vurdering
Under dette prosjektet ble det merkbart at jeg hadde undervurdert oppgaven. Dette var fordi jeg synes var vanskelig å forestille seg hvordan datasettet kunne bli brukt til å oppnå det resultatet jeg ønsket. Et annet problem var at det var mange ulike måter man kunne løse oppgaven på. Dette gjorde det vanskelig å velge og finne den metoden som passet best til å løse oppgaven. Resultatene ble også påvirket av at det bare var en person som tok dette prosjektet, og at jeg synes det er vanskelig å spørre om hjelp. Dette gjorde at det tok lang tid før noe ble forstått og at jeg ofte satt fast der jeg ikke visste hvordan jeg skulle gå videre med prosjektet. Jeg opplevde derfor mye frustrasjon, spesielt siden det var vanskelig å finne enkle eksempler på det jeg ønsket å gjøre. Det var derfor også veldig gøy å få til bildeklassifisering, og som dermed skapte høy mestringsfølelse. 

## Konklusjon
De tre ulike forsøkene på å finne en løsning på et anbefalingssystem for klesbutikker ga varierende resultater. 
Anbefalinger basert på hva andre har kjøpt mest sammen med det valgte produktet, er den enkleste løsningen å gjennomføre og gir gode resultater. 
Løsninger som bruker “collaborative filtering” kan være kompliserte, og krever at riktig informasjon er tilgjengelig i datasettet, eller at den som lager løsningen er veldig god med maskinlæring. 
Bildeklassifisering fungerte ganske bra for dette datasettet og ga gode resultater. Videre arbeid kan være å bygge videre på denne modellen og bruke den til å lage et anbefalingssystem.

Jeg har lært fra dette prosjektet at det kan være lurt å utforske grundigere på hvordan man kan lage en løsning for et prosjekt før man velger. Jeg har også lært at det er lurt å spørre tidlig om hjelp fra andre hvis man sitter fast. 


## Kilder
1. https://www.kaggle.com/code/jhoward/collaborative-filtering-deep-dive/notebook
2. https://rasbt.github.io/mlxtend/user_guide/evaluate/confusion_matrix/
3. https://www.kaggle.com/c/h-and-m-personalized-fashion-recommendations/overview
