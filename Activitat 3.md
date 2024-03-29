# Activitat 3 - Storage Engine


## ACTIVITAT 1. REALITZA I/O RESPON ELS SEGÜENTS APARTATS (obligatòria) (1 punts)
### 1. Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra al comanda utilitzada i el resultat d’aquesta.

* * Es pot veure amb la comanda SHOW ENGINES; al Mysql

![image](https://user-images.githubusercontent.com/101892290/169871096-f07dcd06-d64d-4279-a558-44af8aa89681.png)

### 2. Com puc saber quin és el motor d’emmagatzematge per defecte. Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?

* * Es pot saber quin és el motor d’emmagatzematge per defecte ja que al costat del nom dels motors, posa NO / YES / DEFAULT, al que posa DEFAULT és el que està per defecte

![image](https://user-images.githubusercontent.com/101892290/169871860-22961fde-bbbc-4044-824d-bf1d3e280f49.png)

* * Es pot fer de diverses maneres:

* Una, especificant quin motor de emmagatzematge volem utilitzar al crear una table, per exemple = CREATE TABLE (X) ENGINE MyISAM;
* Una altra es modificar el fitxer my.cnf afegint el següent: default-storage-engine=MyISAM
* També es pot especificar només per a la sessió en la que estem: SET defaul_storage_engine=MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871732-03b0720a-e397-4950-b6bf-be6aa5c05b70.png)

![image](https://user-images.githubusercontent.com/101892290/169871913-c4d5692c-f8ea-44b4-ae91-bc942cafb1c5.png)

* * Si entrem seguidament al Mysql, veurem que el nostre storage-engine per defecte es InnoDB, això es per que no em reiniciat el servei mysql.

![image](https://user-images.githubusercontent.com/101892290/169871951-e10e93a7-5bb5-4eed-a9ca-268d56fd176b.png)

* * Un cop fet, si entren un altre cop a mysql, podrem observar que ara el nostre storage-engine per defecte és MyISAM

![image](https://user-images.githubusercontent.com/101892290/169871991-89b1a52c-4019-4fff-8840-7e84f9564da8.png)

### 3. Com podem saber quin és el motor d'emmagatzematge per defecte?

* * Es pot veure amb l'anterior comanda: SHOW ENGINES; Hem de buscar quin es el sistema que té un parametre: DEFAULT (En aquest cas, INNODB)

![image](https://user-images.githubusercontent.com/101892290/169872121-37bde9b4-39c0-4df6-a914-6030f9879c4b.png)

### 4. Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor). Aquest tipus d’emmagatzematge està optimitzat per ser molt eficient en les escriptures amb lectures acceptables.

* * Ho descarragarem amb la segunet comanda: 

![image](https://user-images.githubusercontent.com/101892290/169872198-042727f1-fcf3-487b-8ce2-7b8cf1a9ce53.png)

* * I l’activarem:

![image](https://user-images.githubusercontent.com/101892290/169872210-4cc87fef-66ad-4aef-aa52-e7ec874014ae.png)

* * Entrem al Mysql i podrem observar que ja el tenim:

![image](https://user-images.githubusercontent.com/101892290/169872226-e465f3b7-c88a-49e3-ac48-4a49d5a9201a.png)

## ACTIVITAT 2 – STORAGE ENGINE CSV (0,5 punts)

* * El motor d'emmagatzematge CSV emmagatzema dades en fitxers de text utilitzant el format de valors separats per comes. Quan es crea una CSV taula, el servidor crea un fitxer de dades de text sense format amb un nom que comença amb el nom de la taula i té una extensió .CSV. Quan emmagatzema dades a la taula, el motor d'emmagatzematge les desa al fitxer de dades en format de valors separats per comes

### Exemple:

* * Important: Hem de posar ENGINE = CSV;

* * Part DDL,DML, creem 2 taules i afegim valors

![image](https://user-images.githubusercontent.com/101892290/169872407-d305daeb-2ae1-4670-92e4-1bcfb9fde103.png)

* * Si entrem a /var/lib/mysql, podem observar que el nostre fitxer s’ha guardat en format .CSV.

* * Dintre del fitxer, están els valors que hem afegit separats per comes

![image](https://user-images.githubusercontent.com/101892290/169872427-2f3f2a0e-1a69-4804-9832-2b7dd38dac8c.png)

## ACTIVITAT 3 – STORAGE ENGINE MyRocks (1 punt)

### 1. Documenta i posa exemple de com utilitzar ENGINE MyRocks. Crea una Base de dades amb 2 o 3 taules i insereix-hi contingut.

### 2. Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

* * MyRocks és una base de dades MySQL optimitzada per a l'espai i el rendiment d'escriptura

### Exemple:

* * Part de DDL i DML;

* * Important, hem de posar ENGINE = RocksDB (i tenirla previamente instalada)

![image](https://user-images.githubusercontent.com/101892290/169872737-0e082e2e-eaec-4311-ac4b-52239a04fcbc.png)

### 3. A quin directori es guarden els fitxers de dades? Fes un llistat de a on són els fitxers i què ocupen.

* * Es guarden en el directori cd /var/lib/mysql, y dintre de la nostre base de dades. Amb el format .sdi

![image](https://user-images.githubusercontent.com/101892290/169872811-1b76c8a6-1da8-4874-9653-7f651bddf74b.png)


### 4. Quina és la compressió per defecte que utilitza per les taules? Com ho faries per canviarlo. Per exemple utilitza Zlib o ZSTD o sense compressió.

* * Están en format JSON

## ACTIVITAT 4. INNODB part I. REALITZA ELS SEGÜENTS APARTATS (obligatòria) (2 punts)

### 1. Desactiva l’opció que ve per defecte de innodb_file_per_table

* * Per desactivarla, hem d'entrar al my.cnf i possar innodb_file_per_table = 0. (Per activarla, = 1)

![image](https://user-images.githubusercontent.com/101892290/169874241-7fa55e1e-cb90-42bf-8cbf-60bc2b52907d.png)

### 2. Quins són els permisos i l'usuari i grup de la carpeta que conté el directori de dades (datadir)

* * Per poder ver-los, hem d'entrar a cd /var/lib/mysql, i executar la comanda ls -alis per veure els permisos

![image](https://user-images.githubusercontent.com/101892290/169874573-1275cc3c-f380-4a64-8386-da322dd6f2fa.png)

### 3. Mostra quina és la mida del tablespace de sistema (System Tablespace). Per què té aquesta mida inicial?

* * La mida inicial es la del ibdata1 (subrayat en groc)

![image](https://user-images.githubusercontent.com/101892290/169875186-26b66252-fb67-47a8-81e2-1ff4201eab66.png)

* * Te aquesta mida inicial ja que així esta especificat, ho podem veure amb la seguent comanda:

![image](https://user-images.githubusercontent.com/101892290/169875294-370aa532-7699-43a1-b9fd-341812a98597.png)

### 4. Importa la BD Sakila com a taules InnoDB (https://dev.mysql.com/doc/index-other.html)

### 5. Quin/quins són els fitxers de dades? A on es troben i quina és la seva mida?

* * Per defecte mysql guarda els fitxers a: /var/lib/mysql/(nom de la base de dades). Si entrem a la carpeta de la base de dades de sakila podem veure tots els fitxers que té:

![image](https://user-images.githubusercontent.com/101892290/169875444-2a4a4451-2987-4794-b6f5-e7fd5b35e68a.png)

* * Podem veure la seva mida i permisos amb la comanda ls -alis:

![image](https://user-images.githubusercontent.com/101892290/169875536-a0abc21e-3678-4be3-90e4-c5f0a04e53e6.png)

### 6. Canvia la configuració del MySQL per:


  #### o Canviar la localització del directori de dades a /hd-mysql/

  #### o Tenir dos fitxers corresponents al tablespace de sistema complint:

  #### ▪ Tots dos han de tenir la mateixa mida inicial (50MB)

  #### ▪ El tablespace ha de créixer de 5MB en 5MB.

  #### ▪ Situa aquests fitxers en una nova localització simulant el següent:

  #### • /disk1/primer fitxer de dades → simularà un disc dur
  #### • /disk2/segon fitxer de dades → simularà un segon disc dur.
  
  
* * Primer, crearem la carpeta /hd-mysql/

![image](https://user-images.githubusercontent.com/101892290/169876111-f426f5c0-55ba-4364-8fda-b9996b8a8c7d.png)

* * També els disk's 1 i 2 (a l'arrel) i donem permisos:

![image](https://user-images.githubusercontent.com/101892290/170301757-564bf229-cdfa-4fd0-83ca-24808ac58f21.png)

* * Després, hem d'escriure la següent configuració al fitxer de configuració del mysql.

![image](https://user-images.githubusercontent.com/101892290/170510864-a0be5acf-6053-4a73-bad6-ab53d511cd4f.png)

* * I ja estaría, comprovació:

![image](https://user-images.githubusercontent.com/101892290/170302082-13ff642f-28ac-4336-bf84-1512def949d3.png)

![image](https://user-images.githubusercontent.com/101892290/170302108-6cb85c84-b274-416e-a1cc-8f65c8bcb828.png)

## ACTIVITAT 5. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria) (1 punt)

### 1. Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vULgueu).

#### Indica quins són els canvis de configuració que has realitzat

* * Creem la taula tspace

![image](https://user-images.githubusercontent.com/101892290/170375839-bdc44d49-9304-4c86-b238-8477b205a8d3.png)

* * Hem de modificar la següent configuració (al my.cnf):

![image](https://user-images.githubusercontent.com/101892290/170509447-3e87b58e-2277-4764-9649-14a63c7d01c9.png)

* * Ara podem fer la seguent comanda a dins del Mysql per activar el file per table.

![image](https://user-images.githubusercontent.com/101892290/170368058-386231af-f58e-41b0-8e65-f7c662d9846c.png)

* * Per que cada taula generi el seu propi tablespace en tspace, hem de posar que el ADD DATAFILE; apunti al nostre /tspace:

![image](https://user-images.githubusercontent.com/101892290/170509404-976262af-97d1-4b32-be55-a2ab089cb5e8.png)

* * I ja cada taula generarà el seu propi tablespace al directori on li diguem amb el ADD DATAFILE;

## ACTIVITAT 6. INNODB part III. REALITZA ELS SEGÜENTS APARTATS (obligatòria) (1 punt)

### 1. Crea un tablespace anomenat 'ts1' situat a /discs-mysql/disc1/ i col·loca les taules actor, address i category de la BD Sakila.

### 2. Crea un altre tablespace anomenat 'ts2' situat a /discs-mysql/disc2/ i col·loca-hi la resta de taules

* * Creem primer els nostres dos disc's (disc1 i disc2)

![image](https://user-images.githubusercontent.com/101892290/170383897-9d396acf-e6c6-4eb6-a135-752695d8ac3d.png)

### 3. Comprova que pots realitzar operacions DML a les taules dels dos tablespaces.

![image](https://user-images.githubusercontent.com/101892290/170383970-12f065c5-9353-4498-9342-63247b68f834.png)

### 4. Quines comandes i configuracions has realitzat per fer els dos apartats anteriors?

* * Primer, he creat les dues carpetes disc1 i disc2, despres, he canviat el arxiu de configuracio de my.cnf i he posat el seguent:

![image](https://user-images.githubusercontent.com/101892290/170384015-954d4e66-3a9f-478a-b217-012210056ec7.png)

* * Ara hem de crear els tablespaces.

![image](https://user-images.githubusercontent.com/101892290/170384057-d2056e2c-1f28-43f0-8671-c00dcd58a56c.png)

* * Per últim hem de canviar el tablespace de cada taula per el nou que acabem de crear.

![image](https://user-images.githubusercontent.com/101892290/170384093-c5a240a9-db59-4c80-944d-4614ebf6bdaf.png)

## ACTIVITAT 7. REDOLOG. REALITZA ELS SEGÜENTS APARTATS (2 punts)

### 1. Com podem comprovar (Innodb Log Checkpointing):
#### • LSN (Log Sequence Number)
#### • L'últim LSN actualitzat a disc
#### • Quin és l'últim LSN que se li ha fet Checkpoint

* * El red log és una estructura de dades basada en el disc que s'utilitza durant la recuperació de fallades per corregir les dades escrites per transaccions incompletes

* * Tot això ho podrem trobar executant la comanda:

* * "SHOW ENGINE INNODB STATUS\G" I tenim que anar a buscar l'apartat de LOG

![image](https://user-images.githubusercontent.com/101892290/170387454-bf2fe188-1cd5-4586-82ed-e2e4eb597abf.png)

* * El LSN en el nostre cas és el 21111676 L'última que ha actualitzat a disc 21111676 I l'ultima checkpoint que ha fer és el 21111676

### 2. Proposa un exemple a on es vegi l'ús del redolog

* * Si per exemple posem que el innodb_log_file_size sigui de 50M:

![image](https://user-images.githubusercontent.com/101892290/170388134-2046173f-310c-4b30-ba43-93322b5d2531.png)

* * InnoDB detecta que la mida d'innodb_log_file_size difereix de la mida del fitxer de registre, escriu un punt de control de registre, tanca i elimina els fitxers de registre antics, crea nous fitxers de registre amb la mida sol·licitat i obre els nous fitxers de registre.

![image](https://user-images.githubusercontent.com/101892290/170388215-fb671d38-f7d7-4d3f-8774-9936e75cb422.png)

* * Com podem observar ha canviat, ara, per exemple, el nostre LSN es 21138774, quan abans era de 21111676

### 3. Com podem mirar el número de pàgines modificades (dirty pages)? I el número total de pàgines?

* * Utilitzem la mateixa comanda "SHOW ENGINE INNODB STATUS\G". En aquest cas tenim que buscar l'apartat de BUFFER POOL AND MEMORY

![image](https://user-images.githubusercontent.com/101892290/170387692-9b5fe25b-9205-4bed-bc79-538f31b3999b.png)

* * El numero total de pàgines es el Database pages 1055, Modified db pages són les pàgines pendents, en el meu cas no en tinc cap pendent.











