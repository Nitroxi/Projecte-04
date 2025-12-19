# Guia de còpies de seguretat per a Windows i Linux

L'objectiu d'aquest document és elaborar dues guies tècniques per al client **Muntatges i Serveis Tècnics SL**. En la primera guia es mostra com protegir la informació del director de l'empresa que treballa amb **Windows 11** utilitzant **Duplicati** com a eina de còpia de seguretat i el principi **3‑2‑1** (tres còpies, en dos suports diferents i una fora de l'oficina). La segona guia explica detalladament com configurar còpies de seguretat en un servidor **Ubuntu Server** mitjançant **Duplicity**, amb èmfasi en els usuaris que no tenen experiència en Linux.

## 1. Còpies de seguretat a Windows 11 amb Duplicati

Per protegir el perfil del director es crea una màquina virtual de Windows 11 amb dos discos: el disc primari conté el sistema operatiu i el disc secundari (10 GB) s'utilitza com a destinació local de les còpies. A més, es fa una còpia remota al núbol (Google Drive).

### 1.1 Preparar el disc secundari

1. **Connectar i reconèixer el disc:** quan s'encén la màquina apareix un nou disc de 10 GB. El sistema l'identifica com a «VBOX HARDDISK (E:)»

![Disc reconegut](img/Captura%20de%20pantalla%202025-12-16%20161847.png)

2. **Crear i formatar la partició:** al gestor de discs seleccionem l'opció *Nou volum simple* i seguim l'assistent. S'assigna la lletra de la unitat, en aquest cas **E:**, i es formata en **NTFS** amb format ràpid.
   
![Formatar volum](img/Captura%20de%20pantalla%202025-12-16%20163200.png)

Això crea una partició amb l'etiqueta «Nou vol» preparada per emmagatzemar les còpies.

### 1.2 Instal·lació i configuració inicial de Duplicati

1. **Descàrrega i instal·lació:** descarreguem l'instal·lador des de la web de Duplicati i l'executem. L'assistent indica que està a punt per instal·lar; simplement premem *Install* per començar

![Instal·lació de Duplicati](img/Captura%20de%20pantalla%202025-12-16%20163243.png)

2. **Definir una contrasenya d'administració:** en obrir Duplicati per primera vegada es demana definir una *passphrase*. Aquesta contrasenya protegeix l'accés a la interfície web i és necessària si volem obrir Duplicati remotament

![Definir passphrase](img/Captura%20de%20pantalla%202025-12-16%20163619.png)

3. **Accés a la interfície web:** després de definir la contrasenya, Duplicati obre una interfície web local (http://127.0.0.1:8200/ngclient/) on gestionarem les còpies. A la pantalla inicial apareixen les opcions *Backups* i *Restores* 

![Interfície web de Duplicati](img/Captura%20de%20pantalla%202025-12-16%20163637.png)

### 1.3 Crear una còpia de seguretat local (disc E:)

1. **Afegir un nou backup:** fem clic a **Add** i triem *New backup*. Donem un nom a la còpia (per exemple, `Backup documents`) i una descripció.

2. **Destinació local:** al pas *Destination* seleccionem la ruta on es desaran les còpies. Es tria el disc secundari (**E:\\\**) navegant per l’arbre de carpetes 

![Seleccionar destinació](img/Captura%20de%20pantalla%202025-12-16%20165139.png)

3. **Seleccionar les dades d’origen:** al pas *Source Data* indiquem les carpetes del perfil d’usuari que volem protegir. En aquest cas marquem **My Documents** 

![Seleccionar origen](img/Captura%20de%20pantalla%202025-12-16%20165300.png)

Duplicati també permet afegir rutes directes o aplicar filtres.

4. **Programar la còpia:** a *Schedule* activem l’opció *Automatically run backups* i indiquem que s’executi cada **1 hora**. L’assistent mostra un horari senzill on s’introdueix l’hora inicial (p.ex. 13:00) i l’interval (1 hour) 

![Programar còpia horària](img/Captura%20de%20pantalla%202025-12-16%20165634.png)

Això compleix la política de fer còpies locals del perfil cada hora.

5. **Completar i executar:** revisem les opcions finals i fem clic a *Save*. En la llista de còpies apareix el nou backup. Premem *Start* per executar la primera còpia. Després d’uns segons el resum mostra que s’ha creat **1 versió** i el volum ocupat al disc secundari 

![Backup creat](img/Captura%20de%20pantalla%202025-12-16%20165741.png)

### 1.4 Restauració des del disc local

Com a prova de restauració, creem alguns arxius (p. ex. `prova.txt`) a Documents, executem la còpia i després esborrem la carpeta.

1. **Iniciar restauració:** des de la interfície fem clic a *Restores → Start*. Duplicati pregunta des de quin backup volem restaurar i mostrem les versions disponibles 

![Iniciar restauració](img/Captura%20de%20pantalla%202025-12-16%20165817.png)

2. **Seleccionar la ruta i l’opció de restauració:** escollim la carpeta a restaurar i indiquem que la restauració es faci a la seva ubicació original. Duplicati permet sobreescriure els arxius o guardar-los amb una marca temporal.

3. **Resultat:** en acabar, la carpeta *Documents* torna a contenir els arxius i carpetes que havíem esborrat 

![Documents restaurats](img/Captura%20de%20pantalla%202025-12-16%20171245.png)

### 1.5 Crear una còpia de seguretat a Google Drive

1. **Nou backup al núbol:** creem un altre backup i, al pas *Destination*, seleccionem **Google Drive** com a proveïdor. Es defineix una ruta dins de Drive (p. ex. carpeta `Documents`) i es prem sobre **AuthID** per generar el codi d’autorització

![Configurar destinació al núbol](img/Captura%20de%20pantalla%202025-12-16%20172423.png)

2. **Autoritzar l’accés:** s’obre una finestra del servei OAuth de Duplicati on hem d’iniciar sessió amb el compte de Google i concedir permisos a Duplicati per crear, consultar i modificar fitxers al nostre Drive. Quan finalitza, introduïm el codi a l’apartat *Authorization code* i podem provar la connexió. Un missatge verd confirma que la connexió és correcta i que la carpeta s’ha creat.

3. **Configurar l’horari:** al pas *Schedule* programem que aquesta còpia s’executi cada dia a les **18:00**. L’assistent permet triar els dies de la setmana; en aquesta prova es programen totes les jornades laborals 

![Programar còpia diària](img/Captura%20de%20pantalla%202025-12-16%20173203.png)

4. **Primera execució i verificació:** en iniciar la còpia, Duplicati puja les dades a Google Drive. Si anem a Drive podem veure que s’han creat fitxers `duplicati-…` dins de la carpeta `Documents` que corresponen als trossos de la còpia 

![Fitxers a Google Drive](img/Captura%20de%20pantalla%202025-12-16%20173330.png)

### 1.6 Restaurar des del núbol

La restauració des del núbol és idèntica al procés local. Simplement seleccionem la còpia guardada a Google Drive, triem la versió i la carpeta a restaurar i deixem que Duplicati descarregui i desxifri els arxius. La interfície mostra un missatge **Restore completed** quan finalitza 

![Restauració des del núbol completada](img/Captura%20de%20pantalla%202025-12-16%20173457.png)

## 2. Còpies de seguretat en Ubuntu Server amb Duplicity

Duplicity és una eina de línia d’ordres que permet fer còpies xifrades i incrementalment eficients a diferents destinacions (local o remotes). En aquesta guia utilitzarem un **Ubuntu Server** amb un segon disc de 10 GB que simularà la unitat de backup i explicarem cada pas perquè sigui comprensible per a persones sense experiència en Linux.

### 2.1 Preparació del disc de còpia

1. **Identificar els discos:** amb `sudo fdisk -l` llistem els discs. A més del disc del sistema (`/dev/sda`) apareix `/dev/sdb` de 10 GB.

2. **Crear una partició:** executem `sudo fdisk /dev/sdb`. Amb les opcions `n` (nova partició), `p` (primària) i `w` (guardar) es crea la partició `/dev/sdb1` ocupant tot el disc 

![Crear partició](img/Captura%20de%20pantalla%202025-12-18%20211929.png)

3. **Formatejar en XFS:** per tenir un sistema de fitxers modern i robust, utilitzem `sudo mkfs.xfs /dev/sdb1`. La sortida confirma que s’ha creat un volum XFS 

![Formatejar XFS](img/Captura%20de%20pantalla%202025-12-18%20212029.png)

4. **Crear el punt de muntatge i muntar el disc:** creem una carpeta on muntarem la partició amb `sudo mkdir -p /media/backup` i la muntem amb `sudo mount /dev/sdb1 /media/backup` 

![Muntar disc](img/Captura%20de%20pantalla%202025-12-18%20212113.png)

Aquesta ruta serà la destinació de les còpies.

### 2.2 Instal·lar Duplicity

1. **Actualitzar els repositoris i instal·lar:** executem `sudo apt update` i després `sudo apt install duplicity`. L’APT mostrarà els paquets addicionals que es requereixen i completarà la instal·lació 

![Instal·lar duplicity](img/Captura%20de%20pantalla%202025-12-18%20212137.png)

2. **Verificar la instal·lació:** podem comprovar que està disponible executant `duplicity --version`.

### 2.3 Creació d’usuaris i fitxers de prova

Per simular un entorn amb diverses dades, crearem nous usuaris i fitxers.

1. **Crear usuaris:** amb `sudo useradd -m -s /bin/bash prova1` i `prova2` es generen nous usuaris amb directoris personals. Després assignem una contrasenya amb `sudo passwd` 

![Crear usuaris](img/Captura%20de%20pantalla%202025-12-18%20212305.png)

2. **Generar fitxers de prova:** ens situem al directori `/home/usuari` i creem quatre fitxers de 10 MB amb l’eina `fallocate`, per exemple:

   ```bash
   fallocate -l 10M prova1
   fallocate -l 10M prova2
   fallocate -l 10M prova3
   fallocate -l 10M prova4
   ```

Els fitxers apareixen al llistat de directoris
   
   ![Fitxers de prova](img/Captura%20de%20pantalla%202025-12-18%20212341.png)

### 2.4 Fer una còpia completa de `/home`

1. **Executar la còpia:** des de l’usuari amb permisos d’administrador, fem servir la següent comanda:

   ```bash
   sudo duplicity full /home/ file:///media/backup/
   ```

L’opció `file:///media/backup/` indica que la destinació és la carpeta local del disc secundari. Duplicity mostrarà estadístiques i signarà els arxius xifrats amb GnuPG. Un cop finalitza, si entrem a `/media/backup` veurem tres fitxers: un manifest, un volum `.difftar.gpg` i un fitxer de signatures 
   
![Arxius de còpia completa](img/Captura%20de%20pantalla%202025-12-18%20212455.png)

### 2.5 Restaurar les dades

Per provar la restauració, esborrem els fitxers i els recuperem de la còpia.

1. **Eliminar els fitxers:** entrem a `/home/usuari` i esborrem els fitxers amb `rm prova*` 

![Esborrar fitxers](img/Captura%20de%20pantalla%202025-12-18%20212531.png)

2. **Restaurar:** executem

   ```bash
   sudo duplicity restore file:///media/backup/ /home/usuari
   ```

Duplicity demana la *passphrase* del xifrat i reconstrueix els fitxers al directori d’origen. En acabar, observem que reapareixen els fitxers i una carpeta anomenada `restore` que conté els arxius recuperats 
   
![Restauració de la còpia](img/Captura%20de%20pantalla%202025-12-19%20000015.png)

### 2.6 Còpia incremental

Duplicity detecta els canvis i només desa les diferències.

1. **Afegir un fitxer nou:** creem un fitxer de 4 MB amb:

   ```bash
   sudo fallocate -l 4M prova5
   ```

Ara, al llistar, veiem `prova5` juntament amb la resta de fitxers 
   
   ![Nou fitxer de 4 MB](img/Captura%20de%20pantalla%202025-12-19%20000548.png)

2. **Fer la còpia incremental:** amb la comanda

   ```bash
   sudo duplicity incremental /home/ file:///media/backup/
   ```

   Duplicity analitza els fitxers i detecta que només `prova5` ha canviat, de manera que crea un nou volum incremental ocupant molt menys espai. Al directori de backup apareixen fitxers `duplicity-inc` a més dels fitxers de la còpia completa.

### 2.7 Automatitzar les còpies amb scripts i cron

Per assegurar que la unitat de backup roman desmuntada quan no es fa la còpia (mesura de seguretat), crearem scripts que munten el disc, executen la còpia i el desmunten. També utilitzarem la variable d’entorn `PASSPHRASE` per evitar introduir la contrasenya manualment.

#### 2.7.1 Script de còpia completa (`fullbackup.sh`)

El script següent realitza una còpia completa de `/home`, muntant i desmuntant la unitat. Cal desar-lo al directori `/home/usuari` (o un altre directori accessible) i donar-li permisos d’execució.

```bash
#!/bin/bash

export PASSPHRASE="<contrasenya>"

mount /dev/sdb1 /media/backup

duplicity full /home file:///media/backup/homebackup

umount /media/backup
```

Al fitxer real substituïm `<contrasenya>` per la clau que utilitzarem per xifrar les còpies. La captura mostra l’script obert amb `nano` 

![Script full backup](img/Captura%20de%20pantalla%202025-12-19%20000923.png)

Per donar permisos d’execució utilitzem:

```bash
chmod +x fullbackup.sh
```

#### 2.7.2 Programar la còpia completa amb cron

Com a superusuari executem `sudo crontab -e` i triem l’editor preferit. Afegim la línia:

```cron
0 23 * * 0 /home/usuari/fullbackup.sh
```

Aquesta línia indica que l’script s’executarà tots els diumenges a les **23:00**. La primera part (0 23 \* \* 0) defineix minut, hora, dia del mes, mes i dia de la setmana (0 = diumenge). La captura mostra el fitxer `crontab` editat amb l’script programat 

![Cron copia completa](img/Captura%20de%20pantalla%202025-12-19%20001050.png)

#### 2.7.3 Script de còpia incremental (`incrementalbackup.sh`)

El script per a còpies incrementals és molt similar però utilitza l’opció `incremental`:

```bash
#!/bin/bash

export PASSPHRASE="<contrasenya>"

mount /dev/sdb1 /media/backup

duplicity incremental /home file:///media/backup/homebackup

umount /media/backup
```

La captura mostra el contingut de l’script 

![Script incremental](img/Captura%20de%20pantalla%202025-12-19%20001139.png)

Després de crear-lo, li donem permisos d’execució (`chmod +x incrementalbackup.sh`).

#### 2.7.4 Programar les còpies incrementals

Al mateix fitxer `crontab` afegim la línia següent:

```cron
0 23 * * 1-6 /home/usuari/incrementalbackup.sh
```

Aquesta entrada executa l’script de dilluns a dissabte a les **23:00**, assegurant que cada dia es desin només els canvis des de l’última còpia. D’aquesta manera complim la política: còpia completa un cop per setmana i còpies incrementals els altres dies.

---

- [**Tornar al README**](README.md)
- [**Tornar el projecte**](../README.md)
