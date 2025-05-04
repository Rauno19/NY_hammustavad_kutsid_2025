**Juhend, kuidas installeerida Docker Desktopi, luua dockerfaili ja seada üles Apache Superseti**

Installeeri Docker Desktop (https://www.docker.com/products/docker-desktop/), mille sees saab hakata kasutama isoleeritud keskkonnas konteinerit, milles töötada projektiga.  
NB! Kui Docker on juba ennem olemas võib olla vajalik Dockeri uuendamine.  
Installeeri Docker Desktopile vajalikud laiendused (devcontainers, docker, remote-SHH, remote- development, remote explorer).  

1. Käivita Docker Desktop (peab jooksma taustal)
2. Ava Githubist (või Gitlabist) oma projekti repositoorium (vali Clone repository from Github) ja ava see oma arvutist (VS Code Open Folder)  
3. Loo devcontainer: 
a. VS Code vajuta windows (ctrl + shift + P) (IOS command + shift + P) 
b. vali DevContainers: Add devcontainer Configuration file -> Add Configuration to workspace (soovitatav) -> Debian -> bullseye -> Python devcontainers -> keep defaults (valikud võivad varieeruda vastavalt eesmärgile, aga antud projekti jaoks pole rohkem vaja). Tekib devcontainer ja sinns sisse devcontainer.json seadistusfail 
Valida -> Reopen devcontainer ja avab devcontaineri ja töökeskkond on valmis, jätka töötamist selles. Saad jooksutada nt skripti, mis tekitab .csv failist .parquet (skript reps parquet_failiks_pythoni_kood) 

**Superseti kasutamine**
Superseti kasutamiseks tekita oma projekti kausta uus kaust nimega "superset" (võib olla ka mõni muu nimi).
1. Tekita Dockerfail, mille sisuks kopeeri järgmine sisu:  
(juhendis kasutatud skript on natukene täiendatud kujul võetud Priit Adleri Github repositooriumist: 
https://github.com/adlerpriit/DECM_WS_Docker_ETL_AS/blob/main/superset_build/Dockerfile)


````bash
FROM apache/superset:master-py310 
# If using IOS with M1/M2/M3 chip use FROM apache/superset:master-py310-arm 
# Switching to root to install the required packages
USER root
# Example: installing the MySQL driver to connect to the metadata database
RUN pip install duckdb==1.2.1 duckdb-engine==0.17.0
# Example: installing a driver to connect to Redshift
# Find which driver you need based on the analytics database
# you want to connect to here:
# https://superset.apache.org/installation.html#database-dependencies
# RUN pip install sqlalchemy-redshift
# Switching back to using the `superset` user
USER superset
````

2. Salvesta fail

3. Kui dockerfile on loodud tuleb hakata üles seadma Apache Superseti 
(käivita järgnevad käsud VS Code Terminalis directoris, kus asub Dockerfail, mis üleeelmises punktis loodi).  Vajalik navigeerimine tekitatud kausta nt cd.. \users\Username\Desktop\Reponimi\superset  
Jooksuta 
````bash
docker build -t minu-superset .
````   
Ehitab Superseti nimega minu-superset kasutades olemasolevat dockrefaili
````bash   
docker run -d -v ${PWD}:/data:rw -p 8080:8088 -e "SUPERSET_SECRET_KEY=sinu_salasona" --name superset minu-superset
````  
Käivitab superseti konteineri nimega minu-superset  
Suunab liikluse arvuti pordilt (vasakpoolne) 8088 kontrineri sees töötava Superseti pordile 8088.  
Võib kasutada ka arvuti porti 8080
-d käivitab konteineri 
-v ${PWD}:/data:rw ${PWD} tuleb asenda täieliku teekonnaga arvutis, kus hoitakse andmefaile Nt: -v /Users/yourusername/superset_data:/data:rw failidele on antud käsuga :rw nii lugemis kui kirjutamisõigused
"SUPERSET_SECRET_KEY=sinu_salasona" osa *sinu_salasona* asemel tuleb sisestada mingi unikaalne väärtus.   
Loo administraatori konto:
````bash
docker exec -it minu-superset superset fab create-admin \
  --username admin \
  --firstname Admin \
  --lastname User \
  --email admin@superset.com \
  --password admin
````
Uuenda Superseti sisemist andmebaasi 
````bash
docker exec -it minu-superset superset db upgrade
````
Initsieeri Superset luues vajalikud kasutajad jm
````bash
docker exec -it superset superset init
````

Tulemusena käib konteineri sees Superset. Kontrolliks tuleb minna veebibrauseris 
````bash 
localhost:8088
```` 
sisestada seadistatud kasutajanimi ja paroool