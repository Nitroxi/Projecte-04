# T07: Accés remot. Serveis d’assistència remota (tasca en parelles)

## Fase 1: Anàlisi comparativa i selecció de la solució

El primer pas és decidir quina eina utilitzarà EverPia. Pel que hem fet una anàlisi de mercat i un breu informe comparatiu entre les diferents eines d’assistència remota que hi ha al mercat. Un cop feta aquesta anàlisi, hem seleccionat l’eina que millor s’adapta a les necessitats de l’empresa i hem justificat la nostra elecció.

## Taula Comparativa d’Eines d’Assistència Remota

| Criteri | TeamViewer | AnyDesk | Google (Chrome) Remote Desktop | LogMeIn |
|-------|------------|---------|--------------------------------|---------|
| Facilitat d’ús (client) | Requereix descarregar l’aplicació o mòdul QuickSupport. L’usuari ha de facilitar un ID i una contrasenya. | Instal·lació ràpida i lleugera. ID visible i fàcil de comunicar. | Molt senzill si l’usuari té compte Google. Connexió via navegador i PIN. | Accés mitjançant aplicació o enllaç. Pensat per a entorns empresarials. |
| Instal·lació / Portable | Mòdul QuickSupport sense instal·lació completa | Instal·lació lleugera | No requereix instal·lació d’escriptori | Requereix instal·lació de l’agent |
| Windows | ✅ | ✅ | ✅ | ✅ |
| macOS | ✅ | ✅ | ✅ | ✅ |
| Linux | ✅ | ✅ | ✅ | No |
| Dispositius mòbils | ✅ | ✅ | ✅ | ✅ |
| Ús comercial permès en versió gratuïta | No | No | ✅ | No |
| Model de preu | Subscripció per tècnic | Subscripció (més econòmica) | Gratuït | Subscripció (cost elevat) |
| Limitacions de la versió gratuïta | Tall de sessions i detecció d’ús comercial | Funcions avançades limitades | Funcionalitats bàsiques | No disposa de versió gratuïta |

## Justificació de l’Eina Seleccionada

Després d’analitzar les diferents opcions disponibles, es recomana `TeamViewer` com a eina oficial d’assistència remota per a EverPia. Aquesta solució destaca per la seva gran fiabilitat, estabilitat i reconeixement al mercat professional, sent àmpliament utilitzada en entorns empresarials.

---

## Fase 2: Guia per als Tècnics d'Assistència Remota amb TeamViewer

Aquesta guia està destinada als tècnics d'assistència remota d'EverPia per utilitzar `TeamViewer` de manera eficient i segura. 

## 1. Instal·lació de TeamViewer

Per a poder fer assistència remota, hem de tenir instal·lat `TeamViewer` a l'ordinador des del qual es realitzarà l'assistència. Ens dirigim a la pàgina oficial de TeamViewer i descarreguem la versió per a donar suport, es a dir, la versió completa de TeamViewer.

<img src="img/1.png">

Una vegada descarregat, procedim a la instal·lació seguint els passos de l'assistent d'instal·lació.

<img src="img/2.png">

En finalitzar la instal·lació, obrim l'aplicació i ens demana que acceptem la llicència d'ús de TeamViewer.

<img src="img/3.png">

I acceptem les noves funcions que ens ofereix TeamViewer.

<img src="img/4.png">

Ens apareix el panell principal de TeamViewer, on podem veure el nostre ID i contrasenya en cas de que necessitéssim rebre assistència, pero l'opció que ens interessa és la de donar assistència remota a un altre usuari, així que iniciem sessió amb les credencials del nostre compte de TeamViewer.

<img src="img/5.png">

I escollim iniciar sessió amb el nostre compte Google per a més comoditat.

<img src="img/6.png">

Una vegada dins de l'aplicació, ja podem començar a donar assistència remota als usuaris finals.

<img src="img/7.png">

---

## 2. Procés d'Assistència Remota

Per a poder donar assistència remota a un usuari final, primer hem de demanar-li que descarregui i executi el mòdul `TeamViewer QuickSupport` des de la pàgina oficial de TeamViewer. 

<img src="img/8.png">

---

## 2.1 Connexió Remota a través del ID i Contrasenya

Una vegada l'usuari final ha executat el mòdul, li demanem que ens faciliti l'ID i la contrasenya que apareixen a la finestra del QuickSupport. I els introduïm a la nostra aplicació de TeamViewer a la secció de `Soporte remoto`.

<img src="img/9.png">

Un cop introduïts, fem clic a `Conectar` i s'establirà la connexió remota amb l'usuari , podent veure i controlar el seu escriptori per ajudar-lo.

<img src="img/10.png">

Aqui ens demana la contrasenya que l'usuari ens ha facilitat.

<img src="img/11.png">

I finalment podem veure que ja estem connectats al seu ordinador.

<img src="img/12.png">

---

## 2.2 Connexió Remota a través de la sessió

També podem connectar-nos a l'ordinador de l'usuari a través d'una sessió que haurem de crear desde la pestanya de `Sessions` a l'aplicació de TeamViewer donat-li al botó de `Nueva sesión`.

<img src="img/15.png">

Una vegada amb la sessió creada, l'usuari es pot connectar per un enllaç que li proporcionem o bé introduint el codi de la sessió a la seva aplicació de TeamViewer QuickSupport.

<img src="img/16.png">

Un cop l'usuari s'ha connectat a la sessió, nosaltres rebem una notificació a la pestanya de `Sessions` i haurem de clicar a `Iniciar sesión` per a iniciar la sessió.

<img src="img/17.png">

Haurem d'esperar que l'usuari accepti la connexió.

<img src="img/18.png">

I finalment ja estem connectats a l'ordinador de l'usuari.

<img src="img/19.png">

---

## 3. Funcions Addicionals

Una vegada connectats, podem utilitzar diverses funcions addicionals com transferència de fitxers, xat amb l'usuari, reinici remot, entre altres.

<img src="img/icons.png">

## 3.1 Veure informació sobre el sistema de l'usuari (Panel)

Una de les funcions és poder veure la informació de sobre el sistema de l'usuari, per a això anem a la barra superior i a la primera icona, anomenada `Panel`.  

Aquí podem veure tota la informació del sistema de l'usuari, com el sistema operatiu, processador, memòria RAM, etc. El que és molt útil per diagnosticar problemes del sistema.

<img src="img/13.png">

---

## 3.2 Enviar la seqüència de tecles Ctrl+Alt+Supr

La segona icona és la de enviar la seqüència de tecles `Ctrl+Alt+Supr` a l'ordinador de l'usuari, que ens obrirà el gestor de tasques o la pantalla de bloqueig segons el sistema operatiu.

---

## 3.3 Transferència de Fitxers

Desrpés tenim la funció de transferència de fitxers, que ens permet enviar o rebre fitxers entre el nostre ordinador i l'ordinador de l'usuari. Per a això anem a la tercera icona, anomenada `Transferencia de archivos`.

<img src="img/14.png">

---

## 3.4 Reinici Remot de l'Ordindor

Amb la cuarta icona, anomenada `Reiniciar`, podem reiniciar l'ordinador de l'usuari de manera remota.

<img src="img/icons.png">

---

## 3.5 Funció de Pissarra

També tenim la funció de `Pizarra` que ens permet dibuixar sobre la pantalla de l'usuari per indicar-li on ha de fer clic o quina opció ha de seleccionar.

<img src="img/20.png">

---

## 4. Bones Pràctiques de Seguretat

Per garantir la seguretat durant les sessions d'assistència remota, és important seguir aquestes bones pràctiques:

- Assegurar-se que l'usuari està informat i ha donat el seu consentiment abans d'iniciar la sessió remota.
- No compartir les credencials d'accés amb persones no autoritzades.
- Finalitzar la sessió remota immediatament després de completar l'assistència.
- Mantenir el programari de TeamViewer actualitzat per beneficiar-se de les últimes mesures de seguretat.

[Tornar a enunciat](README.md)
