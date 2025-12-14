# T09: Servidor de Fitxers Linux – NFS (Tasca individual)

## 1. Introducció

En aquesta tasca es realitza la implementació d’un **servidor de fitxers centralitzat mitjançant NFS (Network File System)** en un entorn Linux, simulant un cas real d’empresa.  
L’objectiu és demostrar com NFS permet centralitzar dades, controlar l’accés mitjançant permisos de sistema de fitxers i opcions d’exportació, **sense utilitzar autenticació centralitzada** (LDAP, AD, etc.).

La versió utilitzada serà **NFSv3**, tal com requereix el client.

---

## 2. Cas del Client: DevOptimize Solutions

**DevOptimize Solutions** és una startup de desenvolupament de programari amb les següents característiques:

- Tot l’entorn de treball és Linux
- No disposen d’autenticació centralitzada
- Cada desenvolupador treballa amb còpies locals del codi
- Problemes constants de versions i pèrdua d’eficiència

### Solució proposada
Implementar un **servidor NFS** que centralitzi:
- Codi font
- Documents de disseny
- Scripts i recursos compartits

---

## 3. Arquitectura de la Solució

### Equips
- **Servidor NFS**: Ubuntu Server
- **Client NFS**: Ubuntu Desktop / Server

### Components clau
- NFS Server (`nfs-kernel-server`)
- NFS Client (`nfs-common`)
- Usuaris i grups locals
- Permisos UNIX (chmod, chown)
- Fitxer `/etc/exports`

---

