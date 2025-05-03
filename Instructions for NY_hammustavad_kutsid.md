**Instructions for NY_hammustavad_kutsid**


Lae alla .csv (või mõnes muus formaadis) fail leheküljelt https://data.cityofnewyork.us/Health/DOHMH-Dog-Bite-Data/rsgh-akpg/about_data
Andmefaili uuendatakse **kord?** aastas, enamik veerge on vabavastuselised, mis teeb transformeerimise (ühest andmetüübist teise) keerulisemaks ja puhastamise aeganõudvamaks 


Failis on veerud, mis vajavad puhastamist ja transformatsioone. 
Puhastamiseks ja transformeetimiseks kasutada OpenRefine, lisaveergude tegemiseks on selles projektis kasutatud MS Excelit.  
Eemaldada read, milles on tühjad lahtrid.  Transformeerida vanus (age) ühtsele kujule (vanus aastates) -> tegu on vaikimisi tekstilise veeruga (OpenRefine).  Transformeeritud postiindeks (zipcode) numbriliseks (OpenRefine).  Puhastada ja grupeerida koeratõud nime alusel kasutades OpenRefine text facet - **group funktsiooni (nt KNN)?**  (OpenRefine).  Kasutades MS Excelit (või mõnda muud programmi, antud projektis on kasutatud MS Excelit)  
Lisada faili uued veerud (nimed võivad olla teised), mis vajalikud andmeanalüüsi jaoks  
Breed_v4 - täiendavalt grupeeritud koeratõud.    
  DogSize_v4 - lisaveerg koera suuruse kohta: medium, large jne.      
  DogType_v4 - lisaveerg koera funktsiooni kohta nt hunting, herding, toy, companion jm.    
  ZipCode_v4 - lisaveerg NY postiindeksi kohta puhastatud/täiendatud zipcode.    
  GeoPoint_v4 - lisaveerg postiindeksi järgi lisatud geograafiline pikkus- ja laiuskraad.


Devcontaineri ja Superseti ülesseadmine -> vt täpsemalt fail **how_to_build_superset**  
Kui devcontainer ja superset on üles seatud tuleb fail transformeerida DuckDB jaoks .parquet failiks


Faili transformeerimiseks saab Devcontaineris kasutada valmis skripti **parquet_failiks_pythoni_kood**, mis transformeerib .csv (või .xlsx faili) DuckDB jaoks .parquet failiks (antud projekti raames on tegu väikese andmestikuga, saab kasutada ka .csv faili)  