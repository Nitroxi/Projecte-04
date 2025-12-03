# T06: Accés remot. Escriptori remot (RDP) (tasca individual)

---

## Xarxa

Perquè les dues màquines virtuals es puguin veure i tinguin connexió a internet, he configurat la xarxa en mode NAT.

En el meu cas utilitzo **xarxa NAT** perquè les màquines tinguin connexió i es puguin comunicar entre elles sense configurar res complex. Aquesta configuració permet que tant Windows com Zorin tinguin internet i al mateix temps es detectin dins la mateixa xarxa virtual.

![img](img/img1.png)

---

## Configuració a Windows

A Windows cal activar l’opció d’escriptori remot perquè un altre dispositiu s’hi pugui connectar. Aquesta opció es troba a la configuració del sistema dins l’apartat d’escriptori remot.

![img](img/img7.png)

Un cop activat, també s’ha d’afegir l’usuari que tindrà permís per accedir remotament.

![img](img/img9.png)

En el meu cas he afegit un usuari concret, però cada persona haurà d’utilitzar el seu propi usuari segons la configuració del seu sistema.

![img](img/img10.png)

Perquè la connexió des de Zorin funcionés correctament, en el meu cas he hagut de desactivar el firewall de Windows. 

---

## Configuració a Zorin OS

A Zorin he activat la compartició d’escriptori des de la configuració del sistema. També he habilitat el control remot perquè l’altre dispositiu pugui interactuar amb l’escriptori.

![img](img/img11.png)

El sistema mostra el nom de l’equip, el port i l’usuari amb el qual es permet l’accés remot. A les captures del repositori es poden veure aquests valors tal com els tinc configurats.

---

## Connexió des de Zorin a Windows

Des de Zorin utilitzo el programa Remmina per establir la connexió remota.

![img](img/img2.png)

Escribim el nom del dispositiu Windows a la barra de connexió i iniciem la sessió. A continuació introdueixo les credencials de Windows.

![img](img/img3.png)

![img](img/img4.png)

Després de validar les dades, apareix l’escriptori de Windows dins de Zorin.

![img](img/img5.png)

---

## Connexió des de Windows a Zorin

També és possible connectar-se en sentit contrari.

Des de Windows s’obre el client d’escriptori remot i s’introdueix el nom del dispositiu Zorin. En el meu cas utilitzo el nom de l’equip tal com apareix a la configuració de Zorin.

![img](img/img12.png)

Després s’introdueix l’usuari i la contrasenya de Zorin i la connexió s’estableix.

![img](img/img13.png)

![img](img/img14.png)

I ja estaria 👍

---

## Problemes més comuns

Si la connexió no funciona, el primer que cal comprovar és la configuració de la xarxa. També cal revisar que el tallafocs de Windows estigui desactivat durant la pràctica.

Si Remmina no connecta o la pantalla es queda negra, normalment reiniciar el programa o revisar la configuració del sistema sol solucionar-ho.

---

[Tornar al README](README.md)

[Tornar al projecte](...\README.md)

