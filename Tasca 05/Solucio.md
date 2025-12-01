# 🖥️ Guia Completa de Configuració SSH

## 1. Instal·lació de SSH a Ubuntu

Pots instal·lar SSH durant la instal·lació inicial d’Ubuntu o manualment amb:

```bash
sudo apt update && sudo apt install openssh-server
```
![img](img/img1.png)
![img](img/img2.png)

Comprovem l’estat del servei:

```bash
sudo systemctl status ssh
```

![img](img/img3.png)

## 2. Instal·lació de SSH a Windows

A Windows, podem instal·lar SSH des de:

Configuració → Sistema → Característiques opcionals → Afegeix una característica

![img](img/img4.png)

També amb PowerShell:

```powershell
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

![img](img/img5.png)
![img](img/img6.png)

## 3. Connexió des de Windows a Ubuntu

També podem connectem des de PowerShell:

```powershell
ssh usuari@IP-del-servidor
```
![img](img/img7.png)

Verifiquem el hostname:

```bash
hostname
```

![img](img/img8.png)

## 4. Creació d’un túnel SSH (Proxy SOCKS)

Creem un túnel amb:

```bash
ssh -D 9876 usuari@IP-del-servidor
```

![img](img/img9.png)

## 5. Configuració del Proxy a Windows

Panell de control → Xarxa i Internet → Opcions d’Internet → Connexions → Configuració LAN

![img](img/img10.png)

Habilitem Servidor Proxy amb IP local i port 9876.

![img](img/img11.png)
![img](img/img12e.png)

## 6. Validació del túnel amb Wireshark

![img](img/img13.png)

## 7. Control d’usuaris amb SSH

Habilitar root:

```bash
sudo passwd root
```
![img](img/img14.png)

Crear nou usuari:

```bash
sudo adduser usuari2
```

![img](img/img15.png)

Editar configuració:

```bash
sudo nano /etc/ssh/sshd_config
```
![img](img/img16.png)

Afegir:

```
PermitRootLogin no
AllowUsers usuari usuari2
```

Reiniciar servei:

```bash
sudo systemctl restart ssh
```

I comprobem:
![img](img/img17.png)
![img](img/img18.png)

En canvi amb el que hem permès:
![img](img/img19.png)

## 8. Autenticació amb claus SSH

Generar clau:

```powershell
ssh-keygen
```

![img](img/img20.png)

Copiem la clau al servidor Ubuntu:

```powershell
scp id_rsa.pub usuari@IP:/home/usuari/
```

![img](img/img21.png)

Posem la clau a la carpeta:

```bash
mkdir -p ~/.ssh
cat id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

![img](img/img22.png)

Comprovem si es connecta sense contrasenya:

![img](img/img23.png)

## 9. Connexió d’Ubuntu cap a Windows

Activar SSH a Windows:

```powershell
Start-Service sshd
Set-Service -Name sshd -StartupType Automatic
```

![img](img/img24.png)

Connectem:

```bash
ssh usuari@IP-windows
```

![img](img/img25.png)
![img](img/img26.png)

## I JA ESTARIA 👍

