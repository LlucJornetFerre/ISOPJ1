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
