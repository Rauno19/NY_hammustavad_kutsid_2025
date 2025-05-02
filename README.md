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
Updated NY_kutsid_puhastatud_v4.parquet for DuckDB