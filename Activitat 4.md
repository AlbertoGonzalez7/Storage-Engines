# Activitat 3 - Storage Engine


## ACTIVITAT 1. REALITZA I/O RESPON ELS SEGÜENTS APARTATS (obligatòria) (1 punts)
### 1. Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra al comanda utilitzada i el resultat d’aquesta.

* *Es pot veure amb la comanda SHOW ENGINES; al Mysql

![image](https://user-images.githubusercontent.com/101892290/169871096-f07dcd06-d64d-4279-a558-44af8aa89681.png)

### 2. Com puc saber quin és el motor d’emmagatzematge per defecte. Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?

* *Es pot saber quin és el motor d’emmagatzematge per defecte ja que al costat del nom dels motors, posa NO / YES / DEFAULT, al que posa DEFAULT és el que està per defecte

![image](https://user-images.githubusercontent.com/101892290/169871860-22961fde-bbbc-4044-824d-bf1d3e280f49.png)

* *Es pot fer de diverses maneres:

* Una, especificant quin motor de emmagatzematge volem utilitzar al crear una table, per exemple = CREATE TABLE (X) ENGINE MyISAM;
* Una altra es modificar el fitxer my.cnf afegint el següent: default-storage-engine=MyISAM
* També es pot especificar només per a la sessió en la que estem: SET defaul_storage_engine=MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871732-03b0720a-e397-4950-b6bf-be6aa5c05b70.png)

![image](https://user-images.githubusercontent.com/101892290/169871913-c4d5692c-f8ea-44b4-ae91-bc942cafb1c5.png)

* *Si entrem seguidament al Mysql, veurem que el nostre storage-engine per defecte es InnoDB, això es per que no em reiniciat el servei mysql.

![image](https://user-images.githubusercontent.com/101892290/169871951-e10e93a7-5bb5-4eed-a9ca-268d56fd176b.png)

* *Un cop fet, si entren un altre cop a mysql, podrem observar que ara el nostre storage-engine per defecte és MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871991-89b1a52c-4019-4fff-8840-7e84f9564da8.png)

### 3. Com podem saber quin és el motor d'emmagatzematge per defecte?

* *Es pot veure amb l'anterior comanda: SHOW ENGINES; Hem de buscar quin es el sistema que té un parametre: DEFAULT (En aquest cas, INNODB)

![image](https://user-images.githubusercontent.com/101892290/169872121-37bde9b4-39c0-4df6-a914-6030f9879c4b.png)

### 4. Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor). Aquest tipus d’emmagatzematge està optimitzat per ser molt eficient en les escriptures amb lectures acceptables.

* *Ho descarragarem amb la segunet comanda: 

![image](https://user-images.githubusercontent.com/101892290/169872198-042727f1-fcf3-487b-8ce2-7b8cf1a9ce53.png)

* *I l’activarem:

![image](https://user-images.githubusercontent.com/101892290/169872210-4cc87fef-66ad-4aef-aa52-e7ec874014ae.png)

* *Entrem al Mysql i podrem observar que ja el tenim:

![image](https://user-images.githubusercontent.com/101892290/169872226-e465f3b7-c88a-49e3-ac48-4a49d5a9201a.png)

## ACTIVITAT 2 – STORAGE ENGINE CSV (0,5 punts)

* *El motor d'emmagatzematge CSV emmagatzema dades en fitxers de text utilitzant el format de valors separats per comes. Quan es crea una CSV taula, el servidor crea un fitxer de dades de text sense format amb un nom que comença amb el nom de la taula i té una extensió .CSV. Quan emmagatzema dades a la taula, el motor d'emmagatzematge les desa al fitxer de dades en format de valors separats per comes

### Exemple:

* *Important: Hem de posar ENGINE = CSV;

* *Part DDL,DML, creem 2 taules i afegim valors

![image](https://user-images.githubusercontent.com/101892290/169872407-d305daeb-2ae1-4670-92e4-1bcfb9fde103.png)

* *Si entrem a /var/lib/mysql, podem observar que el nostre fitxer s’ha guardat en format .CSV.

* *Dintre del fitxer, están els valors que hem afegit separats per comes

![image](https://user-images.githubusercontent.com/101892290/169872427-2f3f2a0e-1a69-4804-9832-2b7dd38dac8c.png)

## ACTIVITAT 3 – STORAGE ENGINE MyRocks (1 punt)

### 1. Documenta i posa exemple de com utilitzar ENGINE MyRocks. Crea una Base de dades amb 2 o 3 taules i insereix-hi contingut.

### 2. Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

* *MyRocks és una base de dades MySQL optimitzada per a l'espai i el rendiment d'escriptura

### Exemple:

* *Part de DDL i DML;

* *Important, hem de posar ENGINE = RocksDB (i tenirla previamente instalada)

![image](https://user-images.githubusercontent.com/101892290/169872737-0e082e2e-eaec-4311-ac4b-52239a04fcbc.png)

### 3. A quin directori es guarden els fitxers de dades? Fes un llistat de a on són els fitxers i què ocupen.

* *Es guarden en el directori cd /var/lib/mysql, y dintre de la nostre base de dades. Amb el format .sdi

![image](https://user-images.githubusercontent.com/101892290/169872811-1b76c8a6-1da8-4874-9653-7f651bddf74b.png)


### 4. Quina és la compressió per defecte que utilitza per les taules? Com ho faries per canviarlo. Per exemple utilitza Zlib o ZSTD o sense compressió.

* *Están en format JSON

## ACTIVITAT 4. INNODB part I. REALITZA ELS SEGÜENTS APARTATS (obligatòria) (2 punts)

### 1. Desactiva l’opció que ve per defecte de innodb_file_per_table
