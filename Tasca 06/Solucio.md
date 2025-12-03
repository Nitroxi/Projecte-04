# Guia d’escriptori remot entre Zorin OS i Windows

Aquesta guia explica com configurar una connexió d’escriptori remot entre Zorin OS i Windows dins d’un entorn de màquines virtuals utilitzant el protocol RDP. El procés està basat en una pràctica real i les captures de pantalla incloses al repositori mostren els passos concrets.

---

## Xarxa

Perquè les dues màquines virtuals es puguin veure i tinguin connexió a internet, he configurat la xarxa en mode NAT.

En el meu cas utilitzo **xarxa NAT** perquè les màquines tinguin connexió i es puguin comunicar entre elles sense configurar res complex. Aquesta configuració permet que tant Windows com Zorin tinguin internet i al mateix temps es detectin dins la mateixa xarxa virtual.

---

## Configuració a Windows

A Windows cal activar l’opció d’escriptori remot perquè un altre dispositiu s’hi pugui connectar. Aquesta opció es troba a la configuració del sistema dins l’apartat d’escriptori remot.

Un cop activat, també s’ha d’afegir l’usuari que tindrà permís per accedir remotament.

En el meu cas he afegit un usuari concret, però cada persona haurà d’utilitzar el seu propi usuari segons la configuració del seu sistema.

Perquè la connexió des de Zorin funcionés correctament, en el meu cas he hagut de desactivar el firewall de Windows. Amb el tallafocs activat, la connexió no es completava.

Això només s’ha fet per a la pràctica amb màquines virtuals i no és recomanable fer-ho en un ordinador real connectat a internet perquè suposa un risc de seguretat.

---

## Configuració a Zorin OS

A Zorin he activat la compartició d’escriptori des de la configuració del sistema. També he habilitat el control remot perquè l’altre dispositiu pugui interactuar amb l’escriptori.

El sistema mostra el nom de l’equip, el port i l’usuari amb el qual es permet l’accés remot. A les captures del repositori es poden veure aquests valors tal com els tinc configurats.

---

## Connexió des de Zorin a Windows

Des de Zorin utilitzo el programa Remmina per establir la connexió remota.

En el meu cas escric el nom del dispositiu Windows a la barra de connexió i inicio la sessió. A continuació introdueixo les credencials de Windows.

Després de validar les dades, apareix l’escriptori de Windows dins de Zorin.

---

## Connexió des de Windows a Zorin

També és possible connectar-se en sentit contrari.

Des de Windows s’obre el client d’escriptori remot i s’introdueix el nom del dispositiu Zorin. En el meu cas utilitzo el nom de l’equip tal com apareix a la configuració de Zorin.

Després s’introdueix l’usuari i la contrasenya de Zorin i la connexió s’estableix.

---

## Problemes més comuns

Si la connexió no funciona, el primer que cal comprovar és la configuració de la xarxa. També cal revisar que el tallafocs de Windows estigui desactivat durant la pràctica.

Si Remmina no connecta o la pantalla es queda negra, normalment reiniciar el programa o revisar la configuració del sistema sol solucionar-ho.

---

[Tornar al README](README.md)
[Tornar al projecte](...\README.md)

