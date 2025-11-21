# T01 — DRP: Còpies de Seguretat  
## Estudi de Cas Client (Treball cooperatiu)

## 📝 Breu descripció

### Introducció
Durant la primera part de la sessió, el vostre responsable de seguretat us presenta el tema de les **còpies de seguretat** mitjançant un material didàctic.  
A continuació, caldrà treballar els conceptes mitjançant una **dinàmica cooperativa**, aplicant-los sobre un cas realista.

---

## 🏢 Presentació del cas client

**Client:** *Muntatges i Serveis Tècnics SL*  
Empresa dedicada a la instal·lació i manteniment d’equips industrials.

### 🔧 Infraestructura tècnica
- **Servidor de Fitxers (Ubuntu Server)**  
  Conté tota la documentació crítica:
  - *Documents de Projectes:* plànols i especificacions tècniques (300 GB, creixement moderat).  
  - *Bases de Dades (Comptabilitat i Clients):* crítiques i d’ús diari (20 GB, canvi constant).  
  - *Carpetes Personals d’Usuaris:* feina diària (100 GB).

- **10 Equips Clients (Windows 10/11)**  
  Els usuaris treballen majoritàriament amb el servidor, però alguns tècnics guarden temporalment informes i arxius importants a la carpeta *Documents*.

- **Connexió a Internet:**  
  Fibra òptica simètrica de 600 Mbps.

---

## 🎯 Requisits de Recuperació

- **RTO (Recovery Time Objective):**  
  Les dades de Comptabilitat/Clients han d’estar disponibles en menys de **4 hores**.

- **RPO (Recovery Point Objective):**  
  - Pèrdua màxima admesa per a la majoria de dades: **24 hores**  
  - Comptabilitat/Clients: **≤ 4 hores**

- **Retenció:**  
  Històric mínim d'**un mes**.

---

# 🔍 Fase 1 — Treball individual

Baseu-vos en el cas pràctic per respondre:

### 1️⃣ Què copiar? (Priorització)
- Quines dades són les més crítiques del servidor?  
- Cal fer còpia dels 10 equips clients? **Justifica-ho.**

### 2️⃣ Periodicitat i Tipus de Còpia
Proposa un calendari setmanal indicant:
- Quins dies es fan còpies  
- Quin **tipus de còpia** s’utilitza:
  - Completa  
  - Diferencial  
  - Incremental  
- En especial per a dades crítiques com bases de dades.

### 3️⃣ Mitjans i Ubicació
Defineix:
- Quin mitjà utilitzaries (Discs externs, NAS, Cloud, Cintes LTO…)
- On es guarda cada còpia segons la **Regla 3-2-1**:
  - 3 còpies  
  - 2 mitjans diferents  
  - 1 còpia fora de les instal·lacions

---

# 🤝 Fase 2 — Treball per parelles

### 1️⃣ Discussió i Consens
Compartiu i compareu les res

