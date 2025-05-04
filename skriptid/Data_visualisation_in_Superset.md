**Juhised andmete saamiseks Superseti (DuckDB andmebaasi), et saaks luua graafikuid ja töölauda**  
Käivita Docker Desktop ja loodud konteiner "minu-superset" (nimi võib varieeruda)  
Mine veebibrauseriga:  
````bash
localhost:8088
````
Kui valisid mõne muu pordi supersetile, siis sisesta teine number (nt :8080). NB! Ühel pordil saab joosta üks teenus 
Sisesta enda superseti kasutajanimi ja parool  

**Oled sisenenud Superseti**   
Andmetabeli sidumiseks vali ülevalt menüüst SQL -> SQL Lab  
Sisesta oma andmefaili sisselugemiseks käsk
````bash
Select * FROM read_parquet('/data/andmefaili_asukoht/andmefailinimi.parquet');
````  
NB! Kui andmefail on .csv kujul, siis 
````bash
SELECT * FROM  read_csv('/data/andmefaili_asukoht/andmefailinimi.csv');
````  
Vajuta "Run Selection" ja "Save dataset" (väikene nool alla "Save" nupu juures) ja "Save and Explore"  
Nüüd saad hakata joonistama graafikuid, koostama tabeleid jm  


