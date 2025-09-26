---
layout: default
title: "Sprint 1: Instal·lació i configuració inicial"
---

# Virtualització i instal·lació del SO Ubuntu
Documentat - Crear una màquina virtual Ubuntu amb els requisits mínims i fer captura per a mostrar-los (emmagatzematge 80GB, 40GB destinats a Ubuntu, la resta lliure). Particionar els 40GB en arrel, opcionalment, boot i home i swap. Fer recerca per a determinar, basant-me en les característiques de la màquina, si és necessari crear la partició swap, i documentar. Clonar màquina una vegada estigui tot fet. Triar i justificar un adapatador de xarxa per a la màquina virtual.

## Creació de la màquina virtual

Primer, obrim VirtualBox, i creem una nova màquina virtual.
<img width="135" height="104" alt="image" src="https://github.com/user-attachments/assets/c085511f-302c-47a2-8f55-b4cc9630e0e0" />

A la primera pantalla, triem un nom per a la màquina virtual, i busquem la ISO d'Ubuntu a l'ordinador.
<img width="712" height="385" alt="image" src="https://github.com/user-attachments/assets/367dc753-d4ff-4206-a3c2-85e28749f63f" />

A continuació, podem crear el nostre usuari i el nom de la màquina.
<img width="712" height="293" alt="image" src="https://github.com/user-attachments/assets/9cf80447-7127-45d2-8a62-865c4932dd80" />

Tot seguit, toca assignar una quantitat de RAM a la màquina virtual. Per a determinar la quantitat adequada, podem consultar els requisits mínims per al nostre sistema operatiu a la pàgina principal d'aquest. https://ubuntu.com/download/desktop

<img width="528" height="331" alt="image" src="https://github.com/user-attachments/assets/13c46994-79e8-499a-9495-262a12fd34d6" />

Posarem 4GB, ja que és el mínim recomanat, i 4 cores per a la CPU.

<img width="714" height="213" alt="image" src="https://github.com/user-attachments/assets/68428e0f-a9b3-48e0-a3c9-34265087d52a" />

Ara, hem de crear el disc. Aquest serà de 80GB.
<img width="714" height="315" alt="image" src="https://github.com/user-attachments/assets/f4e3e869-080a-415e-aa61-e713b65bcd9b" />

Finalment, revisem que totes les dades del resum de la màquina son correctes, i la creem.
<img width="706" height="383" alt="image" src="https://github.com/user-attachments/assets/57fc8161-7131-46e1-a365-19e2b3e34c52" />

Abans d'acabar la configuració de la màquina, cal seleccionar un adaptador de xarxa per a aquesta. Ho farem seleccionant la màquina virtual, i clicant sobre la rodeta de configuració. Després, anirem a la secció de Xarxa/Network.
<img width="796" height="458" alt="image" src="https://github.com/user-attachments/assets/336fde30-5ff4-41d1-b326-f61a1eb320ae" />

En el meu cas, he decidit triar Xarxa NAT. Amb aquest adaptador, puc combinar els avantatges del NAT (sortida a internet), manté l'equip aillat de la resta de dispositius de la LAN, tot i permetent comunicar-se amb els dispositius de la mateixa xarxa NAT.

<img width="427" height="203" alt="image" src="https://github.com/user-attachments/assets/aab16eff-3ba6-4441-b1b0-82433454e24c" />

Podem crear una nova xarxa NAT a Eines > Xarxa > Xarxa NAT i crear
<img width="498" height="245" alt="image" src="https://github.com/user-attachments/assets/06666d26-8d9e-4d92-bb3f-c029ed090342" />


## Configuració del sistema operatiu Ubuntu

Obrim la màquina virtual, i seleccionem *Try or install Ubuntu* **(Aquesta opció es selecciona automàticament si no triem res)**
<img width="707" height="276" alt="image" src="https://github.com/user-attachments/assets/3a840cb8-bc6e-48e4-975e-b11b01f66f24" />

Ara, seguim el procés d'instal·lació fins que arribem a la secció de les particions. 
<img width="776" height="496" alt="image" src="https://github.com/user-attachments/assets/a4f03ad9-939a-441a-b286-25d6f126e928" />

Aqui, crearem les següents particions al disc:

/home: La mida d'aquesta partició serà de 16GB, ja que només crearé un usuar, i l'espai és una mica limitat.
<img width="776" height="496" alt="image" src="https://github.com/user-attachments/assets/e4801df9-76c9-4763-8967-a94cd4eadec1" />

/boot: Ja que, en un futur, farem un dualboot, posarem 1GB d'espai per a aquesta partició.
<img width="602" height="255" alt="image" src="https://github.com/user-attachments/assets/778d206d-c561-42f8-8ac0-d85772f14970" />

/: 16GB
<img width="602" height="318" alt="image" src="https://github.com/user-attachments/assets/8ff5ac37-f551-42fc-a49e-dbe267616b83" />

/swap: 4GB
<img width="510" height="391" alt="image" src="https://github.com/user-attachments/assets/27ddaa9c-b5bc-4701-97a0-e28487fe5f04" />


- Justificació per ChatGPT: Per què val la pena tenir swap

Suport quan s’omple la RAM: si els 4 GB de RAM es queden curts, el sistema pot descarregar dades menys utilitzades a la swap i evitar que les aplicacions es pengin.

Estabilitat: ajuda a mantenir el sistema estable en moments de càrrega alta.

Hibernació (opcional): permet guardar el contingut de la RAM al disc i reprendre després.

- Per què 4 GB de swap és suficient amb 4 GB de RAM

La swap no substitueix la RAM: només s’usa com a “coixí” quan cal.

Amb 4 GB de RAM, un swap de 4 GB dona prou marge per a usos normals (navegar, ofimàtica, programació lleugera) i fins i tot permet hibernar si cal.

Més de 4–6 GB en aquest cas no aporta gaire, tret que facis coses molt exigents (com màquines virtuals o edició de vídeo).

---

## Instal·lar Windows al mateix disc.

Primer, anem a la VM d'Ubuntu, i li afegim la ISO de Windows 10 enterpise.

<img width="246" height="140" alt="image" src="https://github.com/user-attachments/assets/40994469-1364-46c8-8087-fa6d7a06fe5a" />

Ara, anem a l'apartat de Sistema de la màquina virtual, i activem l'opció: "Enable EFI"

<img width="242" height="34" alt="image" src="https://github.com/user-attachments/assets/cbe29fd0-bce6-4675-bf05-c72945f815dd" />

Ara, ja podem obrir la màquina virtual. Quan ho fem, haurem de prémer la tecla "ESC", cosa que ens portarà al boot menú. Allà, triem CD-ROM, i ja podem començar la instal·lació de Windows.

<img width="226" height="100" alt="image" src="https://github.com/user-attachments/assets/a2399b8b-0084-4aed-857d-0575bd62db99" /><img width="314" height="103" alt="image" src="https://github.com/user-attachments/assets/de58f704-7768-4ddd-9e68-6f44935ce706" />

Seguim la instal·lació fins al punt de les particions, on seleccionem l'espai lliure, i el formatem com a partició, on instal·larem el sistema.

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/1d2cdb89-8ad2-445c-8d85-a2744e2c9f03" />

### Recuperar el menú grub.

Windows ha esborrat el menú que ens permet seleccionar quin sistema operatiu volem bootar, per tant, ara el recuperarem.

Primer, 





## Llicenciament

Ubuntu és un sistema operatiu lliure de codi obert que es basa en Linux. Té una llicència de programari lliure, anomenada GNU (GPL, en anglès). Aquesta llicència permet:
 - Fer servir el programa lliurement.
 - Copiar-lo, i redistribuir-lo.
 - Modificar-lo, i distribuir aquestes copies, sempre que també siguin lliures.

 <img width="720" height="358" alt="image" src="https://github.com/user-attachments/assets/f18c5ad3-a386-4644-8522-53d434d687e8" />


## Gestors d'arrencada per a instal·lacions DUALS


## Punts de restauració 


## Comandes generals i instal·lació

