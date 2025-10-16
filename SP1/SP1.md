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

## Llicenciament

Ubuntu és un sistema operatiu lliure de codi obert que es basa en Linux. Té una llicència de programari lliure, anomenada GNU (GPL, en anglès). Aquesta llicència permet:
 - Fer servir el programa lliurement.
 - Copiar-lo, i redistribuir-lo.
 - Modificar-lo, i distribuir aquestes copies, sempre que també siguin lliures.

 <img width="720" height="358" alt="image" src="https://github.com/user-attachments/assets/f18c5ad3-a386-4644-8522-53d434d687e8" />


## Gestors d'arrencada per a instal·lacions DUALS
### Instal·lar Windows al mateix disc.

Primer, anem a la VM d'Ubuntu, i li afegim la ISO de Windows 10 enterpise.

<img width="246" height="140" alt="image" src="https://github.com/user-attachments/assets/40994469-1364-46c8-8087-fa6d7a06fe5a" />

Ara, anem a l'apartat de Sistema de la màquina virtual, i activem l'opció: "Enable EFI"

<img width="242" height="34" alt="image" src="https://github.com/user-attachments/assets/cbe29fd0-bce6-4675-bf05-c72945f815dd" />

Ara, ja podem obrir la màquina virtual. Quan ho fem, haurem de prémer la tecla "ESC", cosa que ens portarà al boot menú. Allà, triem CD-ROM, i ja podem començar la instal·lació de Windows.

<img width="226" height="100" alt="image" src="https://github.com/user-attachments/assets/a2399b8b-0084-4aed-857d-0575bd62db99" /><img width="314" height="103" alt="image" src="https://github.com/user-attachments/assets/de58f704-7768-4ddd-9e68-6f44935ce706" />

Seguim la instal·lació fins al punt de les particions, on seleccionem l'espai lliure, i el formatem com a partició, on instal·larem el sistema.

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/1d2cdb89-8ad2-445c-8d85-a2744e2c9f03" />

#### Recuperar el menú grub.

Windows ha esborrat el menú que ens permet seleccionar quin sistema operatiu volem bootar, per tant, ara el recuperarem.

Primer, entrem a Ubuntu, i executem grub-install /dev/sda.

<img width="561" height="74" alt="image" src="https://github.com/user-attachments/assets/141e1773-6e41-473b-99cd-1864d7ed90a9" />

Tot seguit, executem grub-update.

<img width="690" height="274" alt="image" src="https://github.com/user-attachments/assets/9cd74e79-7aae-4972-98ec-91cd588ef169" />

Grub no està configurat per a detectar altres sistemes operatius. Per tant, accedirem a /etc/default/grub amb un nano.

<img width="625" height="26" alt="image" src="https://github.com/user-attachments/assets/bbb2211b-4c31-4f2b-81df-2c1ecde76bec" />

Dintre del fitxer, busquem la línia "GRUB_DISABLE_OS_PROBER=false", i la descomentem/escrivim, si no la tenim.

<img width="800" height="287" alt="image" src="https://github.com/user-attachments/assets/2a13d9a3-5496-4802-a875-8d6016f61b99" />

Guardem i sortim, i tornem a executar "sudo update-grub". Podem veure que, aquesta vegada, ha detectat Windows, i li ha afegit una entrada al menú.

<img width="724" height="96" alt="image" src="https://github.com/user-attachments/assets/4a8d2970-fb6d-423b-a035-e8b2951ed62c" />

Finalment, reiniciem la màquina, i el grub ja torna a funcionar.

<img width="299" height="82" alt="image" src="https://github.com/user-attachments/assets/6dfaa842-5089-489b-86b8-ffe0e69d5982" />

---

### Instal·lar Windows i Ubuntu en discs diferents.

El primer pas és crear un nou disc, on instal·larem Windows, treiem el disc on Ubuntu està instal·lat, posem la ISO de Windows, i iniciem la màquina.

<img width="248" height="163" alt="image" src="https://github.com/user-attachments/assets/dbe097b9-5229-4af2-b42b-2bec3b52228c" />

Ara, fem la instal·lació de Window.

<img width="582" height="410" alt="image" src="https://github.com/user-attachments/assets/f8020dce-a859-4062-aac5-457be852d3d7" />

Amb Windows instal·lat, tornem a posar el disc d'Ubuntu, i entrarem des del boot menu.

<img width="244" height="113" alt="image" src="https://github.com/user-attachments/assets/29ddb4c4-f55d-4ef3-bb8c-80099d866038" />

Ara, repetim els passos per a recuperar el grub.

Tot seguit, modificarem l'arranc EFI per a indcar que, per defecte, s'obri Ubuntu primer.

Podem veure que Windows és 0004, i Ubuntu 0006.

<img width="512" height="268" alt="image" src="https://github.com/user-attachments/assets/eecd3406-dafa-441d-b577-6fc60635d3b8" />

Amb aquesta informació, podem modificar l'ordre d'arranc executant: "efibootmgr -o 0006, 0004".

<img width="635" height="267" alt="image" src="https://github.com/user-attachments/assets/ac1e1178-d157-49b6-81e9-f5eeef740080" />

Finalment, podem comprovar que els canvis s'han aplicat correctament obrint la màquina virtual, i no seleccionant cap opció al menú grub, per a confirmar que aquest triarà Ubuntu.

## Punts de restauració 

Primer, ens posem en mode superusuari, i descarreguem timeshift.

<img width="720" height="436" alt="Screenshot from 2025-10-07 12-50-47" src="https://github.com/user-attachments/assets/3d5190e1-37f7-4c7c-b9cf-e0ee0fa1a509" />A

Ara, entrem a fdisk seleccionant el disc que hem afegit a la màquina virtual (podem llistar els discs del sistema amb lsblk).

<img width="497" height="39" alt="Screenshot from 2025-10-07 12-53-31" src="https://github.com/user-attachments/assets/d0f46892-4868-44af-a941-476cdeea5040" />

Creem una nova partició.
<img width="723" height="235" alt="Screenshot from 2025-10-07 12-53-49" src="https://github.com/user-attachments/assets/08979076-3fad-4743-821a-0bfb60694730" />

I confirmem que s'ha creat correctament amb lsblk.

<img width="358" height="57" alt="Screenshot from 2025-10-07 12-54-23" src="https://github.com/user-attachments/assets/584030dd-1e4b-4119-b456-12fae3f3d21d" />

Formatem la partició a .ext4

<img width="719" height="256" alt="Screenshot from 2025-10-07 12-56-00" src="https://github.com/user-attachments/assets/4e88c51c-daf2-41fa-9f80-ef56ddaeda0f" />

A continuació, creem un directori i document de text.

<img width="492" height="121" alt="Screenshot from 2025-10-07 12-56-43" src="https://github.com/user-attachments/assets/d25bb6e7-c229-4191-a59a-1c2281d43bd4" />

Obrim timeshift, i configurem una instantànea.

<img width="238" height="138" alt="Screenshot from 2025-10-07 12-57-29" src="https://github.com/user-attachments/assets/71a1c25b-b719-430b-8a36-58b954274eb6" />

Seleccionem la partició que hem configurat.

<img width="587" height="234" alt="Screenshot from 2025-10-07 12-57-59" src="https://github.com/user-attachments/assets/9f53e866-8613-48ee-a6a8-0b3c2e6a510f" />

Especifiquem quan volem que es facin les instantànies, i quantes en volem conservar abans que es sobreescriguin.

<img width="587" height="304" alt="Screenshot from 2025-10-07 12-59-02" src="https://github.com/user-attachments/assets/5586de25-6338-45fe-acc4-61f5748fdb0c" />

Indiquem quins directoris volem guardar.

<img width="659" height="146" alt="Screenshot from 2025-10-07 12-59-39" src="https://github.com/user-attachments/assets/0f97b62b-4770-4b48-accd-eb2f0e5349cf" />

I ja hem acabat.

<img width="1166" height="286" alt="Screenshot from 2025-10-07 12-59-54" src="https://github.com/user-attachments/assets/19821895-fe32-4422-b10f-4fc0af83936f" />

Per a comprovar que les instantànies funcionen correctament, en fem una manualment.

<img width="270" height="166" alt="Screenshot from 2025-10-07 13-02-37" src="https://github.com/user-attachments/assets/d9c5c42d-5b07-4dfb-a876-ccd5df2b7f6f" />

Amb la instantània feta, esborrem la carpeta i document de text que hem creat abans.

<img width="454" height="97" alt="Screenshot from 2025-10-07 13-09-21" src="https://github.com/user-attachments/assets/df16f13e-9eec-4bd7-9194-f50df14cb6f0" />

Obrim timeshift, i restaurem la instantània.

<img width="481" height="287" alt="Screenshot from 2025-10-07 13-09-55" src="https://github.com/user-attachments/assets/674281bb-0773-4f03-9d21-b8ee535b666b" />

Finalment, esperem a que s'acabi de restaurar, obrim un terminal, i comprovem que els elements que haviem esborrat han tornat a apareixer.

<img width="501" height="77" alt="Screenshot from 2025-10-07 13-11-50" src="https://github.com/user-attachments/assets/0cf83c27-3522-4868-b64a-0747d7eba1cd" />

## Configuració de netplan
Amb netplan, podem configurar manualment certs paràmetres de xarxa del nostre dispositiu mitjançant la terminal de comandes, com ara el mètode d'obtenció de l'adreça (estàtic, DHCP), l'adreça i màscara concreta (si hem triat estàtica al pas anterior, amb format CIDR), la porta d'enllaç (IP del router) i nameservers (servidors DNS).

Netplan està instal·lat per defecte a tots els dispositius Ubuntu, i podem trobar i modificar el seu fitxer a **/etc/netplan/**. Per a fer una prova, el modificarem amb **nano**.

<img width="617" height="23" alt="image" src="https://github.com/user-attachments/assets/54b6d16d-1345-4653-8ab4-e04ed057ba6a" />

Dintre del fitxer, trobem la configuració per defecte. El primer pas és indicar quin adaptador de xarxa volem configurar (podem veure els adaptadors de xarxa amb ip a).

<img width="574" height="197" alt="image" src="https://github.com/user-attachments/assets/5499e5fb-8f54-4c91-9eed-10bacd25753b" />

Tornem al netplan, i escrivim el nom de l'adaptador que hem trobat. Dintre d'aquest, amb un format similar a html, indicarem que no volem dhcp4 o dhcp6, l'adreça IP i la màscara de xarxa, l'adreça IP del router com a via de sortida, i 8.8.8.8 com a nameserver.

<img width="507" height="240" alt="Screenshot from 2025-10-07 13-49-21" src="https://github.com/user-attachments/assets/b3be8619-56fc-46bb-aa99-d420d36bef58" />

Per a guardar aquests canvis, executem la comanda **netplan apply**, i si no rebem cap missatge d'error, vol dir que tot ha funcionat correctament. Finalment, comprovem que podem sortir a internet, i que la resolució de noms funciona correctament executant la comanda **ping**, primer a l'adreça IP de google, i després al domini.

<img width="798" height="416" alt="Screenshot from 2025-10-07 13-53-28" src="https://github.com/user-attachments/assets/23f27074-d69a-472d-a89d-a6e6ccce6894" />

## Comandes generals i instal·lació
Comprovar i documentar quina versió del paquet de la nostra elecció s'instal·larà al sistema per defecte amb apt-policy. Modificar el fitxer on es guarda la versió a descarregar del paquet, i canviar a una versió diferent. Instal·lar el programa, i comprovar que s'ha instal·lat la versió que hem posat al document.

Primer, revisem quina versió descarrega el sistema per defecte de python3 amb **apt-cache policy python3**.

<img width="720" height="220" alt="image" src="https://github.com/user-attachments/assets/e9281055-e7d3-499d-82d7-b14741457e5a" />

Ara, per a canviar la versió que el sistema instal·la, accedirem a **/etc/apt/preferences.d/** i crearem el fitxer **python3.pref**, on indicarem el nom, la versió i la prioritat.

<img width="572" height="129" alt="image" src="https://github.com/user-attachments/assets/f9741e5a-419a-417d-83e7-4a4d7029aec0" />

Tot seguit, tornem a executar **apt-cache policy python3**, i veiem que la versió que el sistema descarregarà ha canviat a la que nosaltres hem indicat.

<img width="800" height="285" alt="image" src="https://github.com/user-attachments/assets/28b62a76-b0de-414e-bfb7-e8f82bf3003e" />

Finalment, instal·lem python3.

