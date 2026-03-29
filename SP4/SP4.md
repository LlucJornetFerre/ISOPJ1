# RAIDS

## Que és un RAID?

### Un RAID (Redundant Array of Independent Disks) és una tecnologia que combina diversos discs durs en un sol sistema per millorar el rendiment, la seguretat de les dades o ambdues coses.

Segons com es configuri, el RAID pot:

Accelerar l’accés a les dades (repartint la informació entre diversos discs).
Protegir les dades (guardant còpies duplicades en diferents discs, de manera que si un falla, no es perd la informació).
Equilibrar rendiment i seguretat segons el tipus de RAID utilitzat (com RAID 0, RAID 1, RAID 5, etc.).

En resum, el RAID s’utilitza per fer que els sistemes d’emmagatzematge siguin més ràpids, més segurs o més fiables.

### RAID 1 (Mirroring o “mirall”)
Com funciona

RAID 1 consisteix a duplicar exactament les dades en dos (o més) discos.
Tot el que s’escriu en un disc, també s’escriu simultàniament en l’altre.

Beneficis
Alta redundància: si un disc falla, les dades continuen disponibles a l’altre.
El sistema pot seguir funcionant de forma transparent.
Bones lectures, ja que es poden llegir dades de més d’un disc.
Desavantatges
Es perd capacitat: només s’aprofita la meitat de l’espai total.
Exemple: 2 discos de 1TB → només 1TB utilitzable.
L’escriptura no és més ràpida que en un disc individual.
Requisit mínim
Es necessiten almenys 2 discos.
Què són els volums?

Per entendre-ho millor, cal diferenciar alguns conceptes:

Disc físic: el maquinari real (HDD o SSD).
Partició: una divisió lògica dins d’un disc físic.
Volum: una unitat d’emmagatzematge que el sistema operatiu reconeix i utilitza (com C:, D: a Windows).

Un volum té un sistema de fitxers propi (com NTFS, ext4, etc.).

Relació entre volums i RAID

Un volum no ha d’estar limitat a un sol disc físic.

Gràcies a la gestió del RAID (hardware o software), es pot crear un volum lògic que utilitza diversos discos físics alhora.

Per exemple:

En un RAID 5 amb 4 discos, el sistema operatiu no veu 4 discs separats.
Veu un únic volum gran, que es pot formatar i utilitzar com si fos un sol disc.

## Implementació d'un RAID. 

Obrim una màquina, amb 2 discs de 2 GB on crearem l'estructura RAID.

Instal·lem el paquet mdadm

<img width="496" height="291" alt="image" src="https://github.com/user-attachments/assets/df592500-7639-4ed7-9b41-f383bd179a1b" />

Identifiquem els discs de 2GB amb **lsblk**, i els particionem.

<img width="639" height="637" alt="image" src="https://github.com/user-attachments/assets/2dca7872-bd0b-4016-b27b-bab372a4623c" />

Disc 1

<img width="747" height="466" alt="image" src="https://github.com/user-attachments/assets/d4afb97e-e3fd-4513-8441-a62d63254e5b" />

Disc 2

<img width="747" height="468" alt="image" src="https://github.com/user-attachments/assets/546f27dc-0bbd-4b27-b128-fe805f9ec348" />

Tornem a executar **lsblk**, i ara veurem les particions creades als discs.

<img width="602" height="141" alt="image" src="https://github.com/user-attachments/assets/fcb437e1-0b81-42bd-8e60-e0e90b221f0b" />

Ara, creem el directori on implementarem el **RAID**.

<img width="485" height="201" alt="image" src="https://github.com/user-attachments/assets/e3335bf6-ed9f-43a8-a904-b8e99698484c" />

I creem el **RAID**.

Amb **--create /dev/md0** creem el raid.

Amb **--level=1** indiquem el nivell del RAID que creem.

Amb **--raid-devices=2 /dev/sdb1 /dev/sdc1** Indiquem quants dispositius conformen el **RAID**, i després posem la ruta d'aquests dintre del sistema.

<img width="967" height="230" alt="image" src="https://github.com/user-attachments/assets/5bff6ad3-fb36-4062-8348-23ee6f0d6ea8" />

Canviem el format del **RAID** a ext4.

<img width="906" height="288" alt="image" src="https://github.com/user-attachments/assets/d76938e5-1806-4359-b5f4-fc89e6c48605" />

Ara, amb la comanda **mdadm --detail /dev/md0**, podem veure l'estat del **RAID**.

<img width="695" height="623" alt="image" src="https://github.com/user-attachments/assets/0ebf553d-b153-473c-bca2-962864aa1457" />

Tot seguit, redirigirem la sortida que ens dona la primera comanda a l'arxiu **mdadm.conf**.

<img width="903" height="92" alt="image" src="https://github.com/user-attachments/assets/cb628e37-231a-4b57-81d3-f4eccd41ecd6" />

El següent pas és assegurar-nos de que el sistema faci el mount del raid automàticament cada vegada que el sistema s'inicia. Ho farem afegint la línia adient a **/etc/fstab**.

<img width="937" height="296" alt="image" src="https://github.com/user-attachments/assets/ca840440-2c70-4923-9b87-c9dc776bfc47" />

Montem el kernel i l'actualitzem.

<img width="636" height="106" alt="image" src="https://github.com/user-attachments/assets/07224dde-08b1-4a53-942d-0ad96ef91dc2" />

Finalment, reiniciem el dispositiu i comprovem que el RAID està funcionant correctament.

<img width="694" height="619" alt="image" src="https://github.com/user-attachments/assets/f9c9e69b-436e-45dd-a53a-b15ec092edd0" />

## Comprovació del funcionament del RAID

Per a fer les comprovacions, crearem fitxers dintre dels discs.

<img width="478" height="173" alt="image" src="https://github.com/user-attachments/assets/41557ce0-72f4-4aff-9b27-e83d619305a1" />

Ara, farem fallar el disc, i el treiem.

<img width="596" height="109" alt="image" src="https://github.com/user-attachments/assets/3cdae192-2e9c-4a77-9d10-22f61169139d" />

Si tornem a executar la comanda de comprovació d'estat del **RAID**, veurem que un dels discs està **removed**, i l'altre apareix com a **active**.

<img width="697" height="618" alt="image" src="https://github.com/user-attachments/assets/3f4f90e8-18b0-4735-b209-8524ed966de1" />


