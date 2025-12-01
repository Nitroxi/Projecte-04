# T01 — DRP: còpies de seguretat  
## Estudi cas client (Treball cooperatiu)

---

## Introducció
La primera hora el vostre responsable de seguretat us presenta el tema de les còpies de seguretat a partir d’un material didàctic.  
A continuació, caldrà que treballeu els aspectes del tema i ho fareu mitjançant una dinàmica cooperativa.

---

## Presentació del cas client
**"Muntatges i Serveis Tècnics SL"** és una petita empresa dedicada a la instal·lació i manteniment d’equips industrials.

---

## Infraestructura Tècnica

### Servidor de Fitxers (Ubuntu Server)
Conté tota la documentació crítica:

- **Documents de Projectes:** Plànols i especificacions tècniques (300 GB, creixement moderat).
- **Bases de Dades (Comptabilitat i Clients):** Crítiques i d'ús diari (20 GB, canvi constant).
- **Carpetes Personals dels Usuaris:** Per a la feina diària (100 GB).

### Equips clients
- **10 Equips Clients (Windows 10/11)**  
Els usuaris treballen majoritàriament amb fitxers del servidor, però alguns tècnics guarden de forma temporal informes i altres arxius importants a la carpeta Documents.

### Connexió a Internet
- Fibra òptica de **600 Mbps (simètrica)**

---

## Requisits de Recuperació

- **Temps de Recuperació (RTO):**  
Les dades de Comptabilitat/Clients han d'estar disponibles en menys de 4 hores.

- **Pèrdua de Dades Admesa (RPO):**  
Es pot admetre una pèrdua màxima de 24 hores per a la majoria de dades, però les dades de Comptabilitat/Clients no poden perdre més de 4 hores de treball.

- **Retenció:**  
Cal guardar les dades amb un historial d'almenys un mes.

---

# Fase 1 — Treball individual

De forma individual, heu de donar resposta a les següents preguntes basant-se en el cas pràctic:

---

## 1. Què copiar? (Priorització)

El que s’hauria de copiar seria principalment les dades crítiques del servidor que són:

- Bases de Dades  
- Documents de Projectes  
- Carpetes Personals dels Usuaris  

Cal fer les còpies de totes les dades però parcialment, perquè hi ha treballadors que guarden informes temporals en documents que poden ser importants.

---

## 2. Periodicitat i tipus de còpia

Cada dada s’ha de fer còpia segons si és completa, diferencial o incremental.

### Base de dades (crític)
- Còpia completa setmanal  
- Còpia incremental cada 4 hores  

### Documents de projecte
- Còpia completa setmanal  
- Còpia diferencial diària  

### Carpetes personals dels usuaris
- Còpia completa setmanal  
- Còpia incremental diària a la nit  

---

## 3. Mitjans i ubicació

El tipus de mitjà de còpia que utilitzaré serà NAS i Cloud, perquè:

- El NAS és ideal per recuperacions ràpides o snapshots freqüents.  
- El Cloud aporta seguretat davant incendis, robatoris o desastres i redundància geogràfica.

Les còpies més recents, com les incrementals, s’haurien de guardar al NAS per tenir un RTO ràpid, i una còpia diària o setmanal al núvol.

---

# Fase 2 — Treball per parelles

## 1. Discussió i consens
Comparen les seves respostes individuals (Fase 1).

## 2. Elaboració d'una proposta unificada
Heu de consensuar i dissenyar el vostre propi **Esquema 3-2-1 de còpies** (3 còpies, 2 mitjans, 1 fora de lloc) basat en els requisits del cas.

---

### Taula de consens

| Element | Proposta de la parella | Justificació |
|--------|------------------------|--------------|
| **Dades crítiques** | Bases de dades / Documents de projectes | La base de dades és informació única i sensible, en canvi constant. Els documents són essencials per al treball tècnic |
| **Periodicitat (BD)** | Setmanals i cada 4 hores | Alta freqüència de canvi |
| **Tipus de còpia (BD)** | Incrementals (BD) / Diferencials (Documents) | Eficiència i facilitat de recuperació |
| **Mitjà 1 (Local)** | NAS | Equilibri entre seguretat i cost |
| **Mitjà 2 (Extern)** | Cloud | Flexibilitat i protecció externa |

---

# Fase 3 — Treball en grup

## 1. Debat i selecció
Cada parella presenta el seu esquema.  
El grup debat els pros i contres (cost, temps de recuperació, seguretat, simplicitat).

## 2. Disseny de la política final
El grup redacta la política definitiva de còpies de seguretat per a l’empresa.

---

# Document final

## 1) Dades objecte de còpia
Les dades més importants del servidor són les bases de dades de clients, els documents de projectes i les carpetes personals.

No cal copiar completament els equips clients, ja que el treball es guarda quasi tot en un NAS.

Les bases de dades es copien cada 4 hores amb incrementals i una còpia completa setmanal.  
Els documents de projectes tenen còpia diferencial diària i completa setmanal.  
Les carpetes personals es copien cada nit amb incrementals i una completa setmanal.

---

## 2) Cronograma setmanal

| Dia | Dades | Tipus de còpia | Mitjà |
|-----|--------|----------------|------|
| Dilluns | Base de dades | Incremental | NAS |
| Dimarts | Base de dades | Incremental | NAS |
| Dimecres | Base de dades | Incremental | NAS |
| Dijous | Base de dades | Incremental | NAS |
| Divendres | Base de dades | Incremental | NAS |
| Dissabte | Documents projecte | Diferencial | NAS |
| Diumenge | Tot el servidor | Completa | NAS + Cloud |

---

## 3) Elecció de mitjans i ubicació (Regla 3-2-1)

### Mitjà 1 (Local)
El mitjà de còpia local serà un NAS instal·lat a l’empresa.

### Mitjà 2 (Extern)
Còpia al núvol amb proveïdor de confiança (Google Cloud o Microsoft Azure).

### Ubicació fora de lloc
La còpia externa es guarda al núvol, fora de l’empresa.

---

## 4) Estratègia de recuperació (RTO/RPO)

Per garantir que no es perden més de 4 hores d’informació:
- Còpies cada 4 hores  
- NAS com a primer punt de restauració  
- Cloud com a seguretat extra

