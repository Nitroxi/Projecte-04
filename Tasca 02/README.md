# T02: DPR – Còpies de seguretat  

## Breu descripció

### Introducció al cas
A la tasca anterior heu dissenyat una política de còpies de seguretat pel nostre nou client **"Muntatges i Serveis Tècnics SL"**.  
Ara toca passar a l’acció i portar a la pràctica l’estudi anterior.

El client demana que s’elaborin unes **guies tècniques amb proves de concepte** per tal que el seu personal estigui qualificat per implantar el pla de còpies de seguretat.

---

## Part 1: Còpia de seguretat dels equips clients Windows

Encara que en principi el DPR no contemplaria fer còpia dels arxius locals dels equips clients, se’ns demana fer una excepció amb l’equip Windows del director de l’empresa.

En aquest equip es guarda informació important que no es vol tenir accessible al servidor de fitxers de l’empresa.  
Per aquest motiu és necessari definir una política de còpies de seguretat seguint l’esquema **3-2-1**:

- Una còpia de seguretat a un **disc secundari local**
- Una segona còpia al **cloud**, en aquest cas **Google Drive**, usant l’eina **Duplicati**

### Prova de concepte
- Crear una **màquina virtual Windows 11** amb:
  - Un disc per al sistema operatiu
  - Un disc secundari de **10 GB** per a les còpies de seguretat
- Per simular Google Drive:
  - Usar un **compte que no sigui el de l’escola** (es pot crear un compte específic per l’activitat)
- Configuració de còpies:
  - Còpia del **perfil d’usuari cada hora** al disc secundari
  - Còpia a **Google Drive a les 18:00**

### Tasques a documentar
- Procediment d’instal·lació de **Duplicati**
- Configuració dels plans de còpia
- Observació del funcionament:
  - Afegir arxius a les carpetes de l’usuari (especialment **Documents**)
- Esborrar el contingut de **Documents**
- Restaurar des de:
  - Disc secundari
  - Còpia emmagatzemada al cloud

---

## Part 2: Còpia de seguretat servidor Linux

Per fer les còpies del servidor Linux la solució proposada és **Duplicity**, que permet fer còpies tant a un mitjà local com a un servidor remot.

Combinat amb el programador de tasques (**cron**) es poden implementar les polítiques de còpia desitjades.

### Prova de concepte
- Crear una **màquina virtual amb Ubuntu Server**
- Afegir un segon disc de **10 GB** que simularà una unitat auxiliar

### Tasques

1. Inicialitzar i formatar el disc en format **xfs**  
   - Muntar-lo manualment a `/media/backup` (crear abans la carpeta)
2. Instal·lar **duplicity**
3. Crear un parell d’usuaris més amb carpeta personal  
   - Crear **4 arxius de 10 MB** a la carpeta `home` del teu usuari
4. Fer una còpia de seguretat de la carpeta `/home`
5. Esborrar els arxius i fer un **restore** per comprovar la recuperació
6. Afegir un nou arxiu de **4 MB**  
   - Fer una nova còpia i observar que és **incremental**
7. Desmuntar la unitat de backup

---

## Automatització amb scripts i cron

La unitat de backup ha d’estar **desmuntada per defecte**.  
El procés ha de:
1. Muntar la unitat
2. Fer la còpia
3. Desmuntar la unitat

### Tasques

8. Crear un script `fullbackup.sh` que:
   - Faci una còpia completa de `/home`
   - Emmagatzemi la còpia al volum muntat
   - Utilitzi la variable d’entorn `PASSPHRASE`
   - Tingui permisos d’execució
9. Programar l’script amb **cron** com a `root`
   - **Diumenges a les 23:00**
10. Crear un script `incrementalbackup.sh` que:
    - Faci còpies incrementals
    - Utilitzi la mateixa `PASSPHRASE`
    - Tingui permisos d’execució
11. Programar l’script amb **cron** com a `root`
    - **De dilluns a dissabte a les 23:00**

---

## Materials i enllaços de suport

- [**Duplicati**](https://duplicati.com/)
- [**WayToIT – Creando archivos con fsutil (Març 2015)**](https://waytoit.wordpress.com/2015/03/15/creando-archivos-con-fsutil/)
- [**WayToIT – Creando archivos de prueba en Linux (Març 2015)**](https://waytoit.wordpress.com/2015/03/21/creando-archivos-de-prueba-en-linux/)
- [**Duplicity man page**](http://manpages.ubuntu.com/manpages/trusty/man1/duplicity.1.html)
- [**Programant tasques amb cron**](https://geekytheory.com/programar-tareas-en-linux-usando-crontab)

---

- [**Solucio**](Solucio.md)
- [**Tornar el projecte**](../README.md)
