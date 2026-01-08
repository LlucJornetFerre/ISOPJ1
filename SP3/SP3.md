### Configuració del servidor

Primer, obrim un terminal dintre de la màquina servidor, executem la comanda **ip a**, ens apuntem l'adreça IP que rebem per dhcp, i la posarem de manera estàtica amb interfície gràfica. Quan configurem un servidor **sempre hem de posar l'adreça IP estàtica**, ja que una adreça dinàmica complicaría l'accés al serveis que ofereix, degut a que cada dia en tindría una de diferent.

<img width="572" height="338" alt="image" src="https://github.com/user-attachments/assets/521a9731-e140-4016-86c8-3b054a9f72f0" />

Tot seguit, accedim a **/etc/hostname** amb la comanda **nano**, on **modificarem el nom del dispositiu**.

<img width="724" height="97" alt="image" src="https://github.com/user-attachments/assets/547787b5-7690-4d71-bc4c-7b9fbce95c0f" />

Fem el mateix amb **/etc/hosts**, i posarem el nou hostname a l'adreça de loopback del dispositiu. També posarem el domini que crearem pròximament lligat a l'adreça IP que ens hem configurat estàticament.

<img width="724" height="255" alt="image" src="https://github.com/user-attachments/assets/8598dff0-b34b-4340-86b3-d86b40e1d1aa" />

A continuació, instal·lem els serveis per a instal·lar i gestionar ldap.

<img width="724" height="110" alt="image" src="https://github.com/user-attachments/assets/55cd9732-601b-44a1-b57e-646cef08a0c9" />

Durant la instal·lació, ens demanarà una contrasenya per a l'usuari administrador de ldap, que haurem de recordar.

<img width="724" height="352" alt="image" src="https://github.com/user-attachments/assets/dd182aff-2e50-45e3-8e60-0a50b3eca39f" />

Podem fer servir la comanda **slapcat** per a veure tots els elements del domini.

<img width="724" height="352" alt="image" src="https://github.com/user-attachments/assets/12a7207c-b576-4ad1-a41f-cae5528ef1ab" />

Ara, anem a baixades, i descomprimim el fitxer **arxius.zip**.

<img width="473" height="151" alt="image" src="https://github.com/user-attachments/assets/9fd1abf3-db8d-4e0b-a13e-896bc2b601da" />

Amb **dpkg-reconfigure slapd**, podem configurar i afegir elements al domini més fàcilment. Alternativament, podem fer servir els fitxers de configuració **.ldif** que hem descomprimit, però aquests no són tan pràctics.

<img width="541" height="29" alt="image" src="https://github.com/user-attachments/assets/976b835c-0c62-4893-8dbf-b43f2e1bca5b" />

Posem el domini que hem indicat prèviament a **/etc/hosts**

<img width="688" height="212" alt="image" src="https://github.com/user-attachments/assets/e6c5aa5f-941f-439d-ba81-fc8ef4963eaf" />

Nom de l'organització.

<img width="688" height="212" alt="image" src="https://github.com/user-attachments/assets/cad885d2-62a8-472a-bcbd-c516cfdae6e2" />

La contrasenya (pot ser la mateixa que hem posat abans).

<img width="688" height="212" alt="image" src="https://github.com/user-attachments/assets/5962d906-417d-4f06-983b-7f678d51aace" />

Eliminem la base de dades en purgar.

<img width="688" height="212" alt="image" src="https://github.com/user-attachments/assets/13ecf4c8-ab6d-4cc3-bf7f-ef3427174d7d" />

Finalment, movem la base de dades antiga, i excutem la comanda **slapcat** per a comprovar que tots els canvis que acabem de configurar s'han aplict correctament

<img width="688" height="212" alt="image" src="https://github.com/user-attachments/assets/fdbf11b7-33ea-4029-805a-661de6abb3d4" />

De moment, no tenim elements (usuaris, grups unitats organitzatives) però el domini ja apareix configurat correctament.

<img width="462" height="295" alt="image" src="https://github.com/user-attachments/assets/d72c3190-b959-4489-9102-423b2ed80a13" />

## Creació dels elements de ldap

Ara, crearem una unitat organitzativa. Farem servir **uo.ldif**, que es un dels fitxers que hem descomprimit, com a plantilla.

<img width="722" height="161" alt="image" src="https://github.com/user-attachments/assets/84039b40-5136-4b49-b75f-846b966a2bf1" />

Per a carregar el fitxer, executem **ldapadd -c -x -D "cn=admin,dc=lluc,dc=cat" -W -f uo.ldif**

<img width="722" height="161" alt="image" src="https://github.com/user-attachments/assets/c61b3bcd-5074-40dd-9d6b-eee107d2bb26" />

Ara, afegirem un usuari. Modificarem **usu.ldif**

<img width="751" height="423" alt="image" src="https://github.com/user-attachments/assets/3dc10784-c3a9-4940-9fd1-3456de7dceeb" />

I executem la mateixa comanda que abans, però amb el fitxer **usu.ldif**.

<img width="843" height="94" alt="image" src="https://github.com/user-attachments/assets/cb8e9cb5-90e0-410a-908c-978e70db06dc" />

Repetim el procés amb **grup.ldif**.

<img width="754" height="197" alt="image" src="https://github.com/user-attachments/assets/6f984d68-9677-46f8-9e5b-51ebe932a795" />

Carreguem el fitxer.

<img width="851" height="90" alt="image" src="https://github.com/user-attachments/assets/4e028ba7-d09a-4802-a1ec-15a3964969d5" />

Finalment, podem executar slapcat una altra vegada, per a veure tots els nous elements que hem carregat.

<img width="461" height="726" alt="image" src="https://github.com/user-attachments/assets/249a5d2c-51a5-4179-8f9d-4a8d823e7242" />
<img width="461" height="561" alt="image" src="https://github.com/user-attachments/assets/e3063563-ef94-48bc-9e7f-845d5eec9873" />


### Configuració del client

Obrim el client, i intentem fer un ping al servidor.

<img width="720" height="247" alt="image" src="https://github.com/user-attachments/assets/a1e9db2d-82b7-4b39-9da4-f0ac79ec3d42" />

Tot seguit, ens descarregarem els següents paquets: **libnss-ldap libpam-ldap nscd**.

<img width="635" height="28" alt="image" src="https://github.com/user-attachments/assets/b5938fd7-d853-4287-9c93-f779dd7615f0" />

Durant la instal·lació, apareixerà un assitent, que ens demana l'adreça IP del domini.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/b5b8e922-a57c-4c70-b895-5a63996d08ac" />

Posem també el nom.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/d663111e-ce78-4456-a6be-3882fabcf33c" />

Versió 3

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/32317eed-e5a4-4b91-8468-d161bef8bccd" />

Si.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/b0180923-c5f4-4517-b1da-47b14d2434b9" />

Si.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/d735222c-1cbb-4fa1-bac2-0917c312796c" />

Usuari administrador.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/9e1561c5-7f5a-4b9e-8947-7ccbf55110f9" />

Contrasenya.

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/e0ec4b67-bcf4-4c80-bde5-c1a999581abc" />

Usuari sense privilegis.

Modifiquem **/etc/nsswitch.conf**

<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/061eb75c-a32f-48f5-81ac-58b3f0b4752e" />

Modifiquem **/etc/pam.d/common-session**

<img width="736" height="639" alt="image" src="https://github.com/user-attachments/assets/1ed44cfc-ceab-4a53-8f3d-6e45cd155dae" />

Modifiquem **/etc/pam.d/common-password**

<img width="938" height="708" alt="image" src="https://github.com/user-attachments/assets/5d8e7e8b-75fc-4672-88d2-369c10473c4f" />




Ara, modificarem **/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf**.

<img width="854" height="131" alt="image" src="https://github.com/user-attachments/assets/e52906a6-b9b2-4cab-b095-af99d5b68d67" />
