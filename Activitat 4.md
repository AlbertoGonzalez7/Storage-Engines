# Activitat 3


## ACTIVITAT 1. REALITZA I/O RESPON ELS SEGÜENTS APARTATS (obligatòria) (1 punts)
### 1. Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra al comanda utilitzada i el resultat d’aquesta.

* * Es pot veure amb la comanda SHOW ENGINES; al Mysql

![image](https://user-images.githubusercontent.com/101892290/169871096-f07dcd06-d64d-4279-a558-44af8aa89681.png)

### 2. Com puc saber quin és el motor d’emmagatzematge per defecte. Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?

Es pot saber quin és el motor d’emmagatzematge per defecte ja que al costat del nom dels motors, posa NO / YES / DEFAULT, al que posa DEFAULT és el que està per defecte

![image](https://user-images.githubusercontent.com/101892290/169871860-22961fde-bbbc-4044-824d-bf1d3e280f49.png)

Es pot fer de diverses maneres:

* Una, especificant quin motor de emmagatzematge volem utilitzar al crear una table, per exemple = CREATE TABLE (X) ENGINE MyISAM;
* Una altra es modificar el fitxer my.cnf afegint el següent: default-storage-engine=MyISAM
* També es pot especificar només per a la sessió en la que estem: SET defaul_storage_engine=MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871732-03b0720a-e397-4950-b6bf-be6aa5c05b70.png)

![image](https://user-images.githubusercontent.com/101892290/169871913-c4d5692c-f8ea-44b4-ae91-bc942cafb1c5.png)

Si entrem seguidament al Mysql, veurem que el nostre storage-engine per defecte es InnoDB, això es per que no em reiniciat el servei mysql.

![image](https://user-images.githubusercontent.com/101892290/169871951-e10e93a7-5bb5-4eed-a9ca-268d56fd176b.png)

Un cop fet, si entren un altre cop a mysql, podrem observar que ara el nostre storage-engine per defecte és MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871991-89b1a52c-4019-4fff-8840-7e84f9564da8.png)

### 3. Com podem saber quin és el motor d'emmagatzematge per defecte?

Es pot veure amb l'anterior comanda: SHOW ENGINES; Hem de buscar quin es el sistema que té un parametre: DEFAULT (En aquest cas, INNODB)

![image](https://user-images.githubusercontent.com/101892290/169872121-37bde9b4-39c0-4df6-a914-6030f9879c4b.png)

### 4. Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor). Aquest tipus d’emmagatzematge està optimitzat per ser molt eficient en les escriptures amb lectures acceptables.

Ho descarragarem amb la segunet comanda: 

![image](https://user-images.githubusercontent.com/101892290/169872198-042727f1-fcf3-487b-8ce2-7b8cf1a9ce53.png)

I l’activarem:

![image](https://user-images.githubusercontent.com/101892290/169872210-4cc87fef-66ad-4aef-aa52-e7ec874014ae.png)

Entrem al Mysql i podrem observar que ja el tenim:

![image](https://user-images.githubusercontent.com/101892290/169872226-e465f3b7-c88a-49e3-ac48-4a49d5a9201a.png)

## ACTIVITAT 2 – STORAGE ENGINE CSV (0,5 punts)



