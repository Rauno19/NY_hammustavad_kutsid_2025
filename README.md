# NY_hammustavad_kutsid_2025
Andmetehnika projekt

**Andmesitku kirjeldus**  
Andmestik on pärit leheküljelt: https://data.cityofnewyork.us/Health/DOHMH-Dog-Bite-Data/rsgh-akpg/about_data  
Tegu on New Yorgis registreeritud koerarünnakute andmetega. Andmeid uuendatakse kord aastas. Andmed on tabelikujul, numbrilsed ja tekstilised. 
Andmed saab alla laadida tabeli kujul (.csv, .xlsx jm)   
Algses andmefailis on 9 veergu, mis sisaldavad infot järgnevate tunnuste kohta: 
* UniqueId - rünnaku id, mis tegelikult pole unikaalne  
* DateOfBite - rünnaku kuupäev  
* Species - liik    
* Breed -  tõug 
* Age - vanus   
* Gender - sugu 
* Spray/Neutered - steriliseeritud/kastreeritud
* Borough - piirkond
* ZipCode - postiindeks
Ridu oli algses faili 29992 

Andmestiku pealt on võimalik analüüsida, millised koeratõud on kõige agressiivsemad, kas agressiivsus sõltub koera soost/tõust/steriliseeritusest, kas hammustustel on ajaline trend, hammustuste geograafiline jaotus. 
Andmestik on puhastamata, andmestik tuleb puhastada.
 
**Andmete puhastamine** 
Andmed tuleb puhastada nt OpenRefinega, problemaatiliseks kujuneb see, et enamik veerge on vabavastuselised, mitõttu vastuste varieeruvus on suur. 

**Valikuline**  
Selleks, et andmeid paremini analüüsida võib lisada faili uued veerud (nimed võivad olla teised), mis vajalikud andmeanalüüsi jaoks    
Näiteks GeoPoint - mis on rünnaku asukoha koordinaadid  
DogType - koera tüüp (nt jahikoer, karjakoer) 

**Andmete visualiseerimine** 
Devcontaineri ja Superseti ülesseadmine -> vt täpsemalt fail **how_to_build_superset** ja **Data_visualisation_in_Superset**  
Kui devcontainer ja superset on üles seatud tuleb fail transformeerida DuckDB jaoks .parquet failiks  
Faili transformeerimiseks saab Devcontaineris kasutada valmis skripti **parquet_failiks_pythoni_kood**, mis transformeerib .csv, .xlsx (või .txt) faili DuckDB jaoks .parquet failiks (antud projekti raames on tegu väikese andmestikuga, saab kasutada ka .csv faili)

   



								

    
    



 















