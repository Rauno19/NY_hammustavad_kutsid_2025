# NY_hammustavad_kutsid_2025
Andmetehnika projekt

**Andmete puhastamine.** 
Algselt oli vanuse (Age) veerg antud erinevas formaadis. Oli märgitud ühte lahtrisse nii numbrid kui tähed. Mõni lahter oli tühi. Puhastamise tulemusena on AGE tulp teadaolevad väärtused konverteeritud vanuseks aastates 2 kohta peale koma. Vanused, millel oli antud vahemik (nt 2-3 aastat) on võetud väärtuseks aritmeetiline keskmine.
Üksikud väärtused, mida openRefinega polnud võimalik eemaldada, on eemaldatud MS-Exceliga

Erinevat versiooni andmed asuvad kaustas "andmetikud"

Puhastatud failist tehtud NY_hammustavad_kutsid.parquet fail (kood repositooriumis)

Repos kaks faili "NY_Kutsid.xmls", kus on AGE väärtustes tühjad lahtrid ja "NY_kutsid-v2_AGE.csv", kus on AGE lahtrites väärtused 

Muudetud 24.04 20.50

Repos uus puhastatud csv fail NY_kutsid_puhastatud_v3.csv
Muudetud 25.04 13.02

02.05.25:  v4: less dogbreeds, added size, breed group, geopoint
* UUS flat andmefail: NY_kutsid_puhastatud_v4.csv, fail loodud NY_kutsid_puhastatud_v3.csv pealt, muudatused tehtud excelis, algfailile lisatud uued veerud:  
  Breed_v4 - veel rohkme kokku grupeeritud koeratõud.  
  DogSize_v4 - medium, large jne.  
  DogType_v4 - nt hunting, herding, toy, companion jmt.  
  ZipCode_v4 - puhastatud/täiendatud zipcode.  
  GeoPoint_v4 -  ZipCode_v4 järgi latitude ja longitude.  
* NY_kutsid_puhastatud_v4_workfile.xlsx: tavaline excel tööfail, mille data alusel genereeritud NY_kutsid_puhastatud_v4.csv.

02.05.25 
Updated NY_kutsid_puhastatud_v4.parquet DuckDB jaoks
Kustutatud vanad andmefailid, mida enam ei ole tarvis. 
Andmestiku lõppversioon NY_kutsid_puhastatud_v4.1.csv(või .parquet) 

03.05.25 20:53
Lisatud skriptide alla .md fail **how_to_build_superset**, mis sisaldab: 
1. Detailseid juhiseid, kuidas alla laadida Docker Desktopi
2. Kuidas Docker Desktopi seadistada (sh projekti jaoks vajaminevaid laiendusi) 
3. Kuidas luua devcontainerit koos faili sisu, koodi ja selgitusega 
4. Kuidas ehitada Apache Superseti ja siduda seda DuckDB andmebaasiga

04.05 17.02 
Uuendatud fail Data_visualisation_in_Superset

04.05 21.21
Uuendatud .parquet fail Superseti jaoks: NY_kutsid_puhastatud_v4.2.parquet

**05.05.25** 21:11 mari  
lisatud andmestiku kausta failid:  
* ALGDATA_DogBit.csv  
* ALGDATA_DogBite_working.xlsx - fail mis sisaldab nii algallikast laetud andmetabelit ja puhastatud+täiustatud DATATRANSFORM tabelit.
  
**Andmetöötluse protsess** (*see on ära toodud ka ALGDATA_DogBite_working.xlsx sheedil DataTransStep*):  
  1.	Algandmestiksu veerg UniqueID pole unikaalne, vaid iga aasta on alustatud uuesti 1'st  		
	  Andmetesse lisatud uus veerd ID, mis on unikaalne: 1 kuni 29992.

  3. OpenRefine esialgne koeratõugude nimede ühtlustamine, mitu puhastusringi.  		
	  Algandmete tõunimetusi oli 1887, peale openrefine puhastust u 800.

  4. Excelis puhastatud AGE veerg, kus andmete sisestamine on olnud mittereeglipärane.  
     AGE veerus oli ka palju täitmata lahtreid, sinna märgitud NULL.  
     Andmestikule lisatud uus veerg AGE2, kus vanused on teisendatud aastateks numbri formaadis. Näiteks puhastatud: 

| AGE         | AGE2  |
|-------------|-------|
| 41          | 4     |
| 0.2         | 0.2   |
| 04M         | 0.33  |
| 1 & 3       | 1.25  |
| 1 1/2 YRS   | 1.5   |
| 1 Y         | 1.67  |
| 1 YR        | 1     |
| 1 YR 8 MON  | 1.67  |
| 1 YRS       | 1     |
| 1/12M       | 1     |
| 10 & 9      | 10    |

  4. Excelis koeratõugude nimede järelühtlustamine suuremasse koeratõugude gruppi, lisatud andmestikku uus veerg **Breed2**,  										
    eesmärk oli segaverelised grupeerida suuremasse gruppi, grupinimeks jäi tõug, mis oli algandmetes esimesel kohal:    								
    nt 	GERMAN SHEPHERD/GOLDEN RETRIEVER X -> GERMAN SHERHERD MIX.    
    Peale grupeerimist järgi u 420 koeratõugu (algandmetes oli 1887).

  5. Andmeanalüüsi (Superset) jaoks on algandmestikule juurde lisatud uusi andmeveerge:  
    * DogSize - koerad grupeerida suurustesse (small, medium jne)  
    * DogType - koerad grupeerida aretuse eesmärgi gruppidesse (guardian, herding, companion jne)  
    * GeoPoint - andmestiku postiindeksi (zipcode) järgi lisatuid; kui superset võimaldab, siis saaks joonistada kaarti.  
   



								

    
    



 















