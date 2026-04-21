# Sprint 2 - Windows: Discs, Quotes, Scripts, Processos i ACLs
## Fase 1 – Preparació del sistema
### Pas 1. Afegir un nou disc virtual a la màquina virtual
Creem el disc i l'inserim a la màquina virtual.
<img width="1012" height="609" alt="image" src="https://github.com/user-attachments/assets/70127568-3bc7-42e6-988f-31e835a3193c" />

### Pas 2. Iniciar Windows i obrir Gestió de discs
Podem veure i administrar el disc des de **Gestió de discs**, de Windows. Confirmem que el sistema reconeix el disc, i el marca com a **espai sense assignar**.
<img width="1028" height="771" alt="image" src="https://github.com/user-attachments/assets/add9b3a4-db30-4dc6-aa9a-bba9812077de" />

### Pas 3. Inicialitzar el disc, crear dues particions: una anomenada Dades i una en FAT32 anomenada Portable

**Creació de la partició NTFS**
Creem un nou volum simple al disc.
<img width="1011" height="307" alt="image" src="https://github.com/user-attachments/assets/74302bc5-56a7-47d7-a826-98dbcca67c12" />

Especifiquem la mida.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/c2a830e3-b3a3-4351-a3c1-99e688e5ad82" />

Assignem una lletra a la unitat.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/6069b45e-d1c7-4edc-a069-5adecd7a6128" />

Anomenem la partició.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/a93b502e-fc34-4731-83ae-6e5ed0c71a92" />

Finalment, podem veure el resum de l'operació.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/0a846dcc-7513-4b4a-a129-f6e4906a6343" />

**Creació de la partició FAT32**
Creem el segon volum simple al disc.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/caef9849-6f5f-4d77-8901-df398b223425" />

Especifiquem la mida.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/8a01fe1b-5b63-4cd5-8e85-62ea48f75666" />

Assignem una lletra a la unitat.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/71307d5d-7686-4db9-a33f-a26847676028" />

Anomenem la partició.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/56f12821-6002-42e3-a6d8-a75f787b512e" />

Finalment, podem veure el resum de l'operació.
<img width="495" height="397" alt="image" src="https://github.com/user-attachments/assets/034bd323-6f16-4833-93a8-9b109102fe73" />

### Pas 4. Assignar lletres i comprovar amb diskpart la configuració
Verificarem la configuració amb una consola CMD **amd privilegis d'administrador** i la comanda **diskpart**.

La comanda ens mostra:

 - El disc original (40GB) i la lletra C:
 - El disc sobre el que estem treballant, amb la partició **Dades** (3MB, format NTFS) i la partició **Portable** (2102 MB, format FAT32)

<img width="648" height="629" alt="image" src="https://github.com/user-attachments/assets/42464277-fccb-468e-a0e3-ebe75831ae2d" />

## Fase 2 – Quotes i usuaris
### Pas 5. Activar quotes de disc a la partició Dades (NTFS)
Farem servir les quotes d'usuari per a limitar l'espaiq ue cada usuari pot usar dins d'una partició NTFS.
<img width="548" height="414" alt="image" src="https://github.com/user-attachments/assets/0bb6a257-65e5-46c8-83b2-a031148ebd3d" />

<img width="583" height="550" alt="image" src="https://github.com/user-attachments/assets/291c94b0-ffa7-4ee8-8215-add1e5cc52c9" />

### Pas 6. Establir límit de 300 MB per usuari, amb notificació d’advertència
<img width="610" height="556" alt="image" src="https://github.com/user-attachments/assets/6c54d7fa-12c4-4404-807e-12b4c355baf4" />

### Pas 7. Crear dos usuaris locals: alumne1 i alumne2
Obrim un terminal **amd privilegis d'administrador**, i executarem la comanda **net user username password /add** per a crear els usuaris alumne1 i alumne2 respectivament.

<img width="473" height="251" alt="image" src="https://github.com/user-attachments/assets/77513caa-1ab5-43cd-a158-fc0736bb6e8b" />

### Pas 8. Afegir-los a un grup nou anomenat Limitats
Ara, amb el mateix terminal, crearem el grup **Limitats**, i tot seguit, afegirem els usuaris creats al punt anterior dintre d'aquest.
<img width="416" height="51" alt="image" src="https://github.com/user-attachments/assets/ea47f164-b4a0-45f8-9892-9f4311d07fb6" />

<img width="462" height="117" alt="image" src="https://github.com/user-attachments/assets/803970f4-9c11-4e25-9c5f-e92228451b81" />

### Pas 9. Provar la còpia de fitxers dins Dades per veure com actuen les quotes (superar límit)
Finalment, accedirem a l'usuari **alumne1**, i provarem de crear fitxers més grans que el límit que li hem establert.
<img width="566" height="393" alt="image" src="https://github.com/user-attachments/assets/d0579377-0aa4-41d1-b82d-28480a3bdcb0" />

## Fase 3 – Script de còpia i automatització
### Pas 10 – Afegir tercer disc virtual, formatar-lo en NTFS com a Backups
Afegirem un 3r disc, i el canviarem a format NTFS per a backups.
<img width="1011" height="608" alt="image" src="https://github.com/user-attachments/assets/b39bd72e-0348-467d-8430-e958cb89a06b" />

**Creen un nou volum simple dintre del 3r disc**.
<img width="854" height="188" alt="image" src="https://github.com/user-attachments/assets/22c79680-90c5-45f4-b8d8-fc830fcb3ab0" />

Format NTFS, amb el nom **Backups**.
<img width="495" height="390" alt="image" src="https://github.com/user-attachments/assets/d7447d22-8534-453d-8457-b4914835611f" />

### Pas 11 – Crear carpeta CòpiesUsuaris dins Backups
Creem la carpeta dintre de **Backups**.
<img width="786" height="593" alt="image" src="https://github.com/user-attachments/assets/fddf978f-0a40-46c9-86e1-391167a95250" />

### Pas 12 – Crear un script .bat que copiï C:\Users%USERNAME% a B:\CòpiesUsuaris%USERNAME%

**Explicació de l'script**.
**@echo off**:	Silencia la sortida de les comandes a la consola
**xcopy**:	Copia fitxers i directoris (inclou subdirectoris)
**%USERNAME%**:	Variable d'entorn que s'expandeix automàticament amb el nom de l'usuari actiu
**/E**:	Copia tots els subdirectoris, fins i tot els buits
**/I**:	Si la destinació no existeix, la crea com a directori
**/Y**:	Sobreescriu fitxers existents sense demanar confirmació

<img width="751" height="132" alt="image" src="https://github.com/user-attachments/assets/18f92808-56b7-41d9-abb4-68da25eaf03f" />

### Pas 13 – Obrir gpedit.msc → Configuració d'usuari → Scripts → Inici de sessió
Ara, farem que el sistema executi l'script automàticament quan s'inicia sessió.
<img width="397" height="207" alt="image" src="https://github.com/user-attachments/assets/c6b449cf-8ac7-42ae-9a26-5cb90b5b9820" />

<img width="636" height="311" alt="image" src="https://github.com/user-attachments/assets/1dc26de5-29f1-45e2-9636-5f114e06c17f" />

### Pas 14 – Assignar l'script perquè s'executi automàticament en iniciar sessió
Afegim la ruta de l'script a la pestanya **Iniciar Sessió**.
<img width="639" height="321" alt="image" src="https://github.com/user-attachments/assets/9e3f3e89-338f-4047-b933-22e6fd5f6a90" />

## Fase 4 – Verificació i documentació
### Pas 15 – Comprovació: l'script fa la còpia a Backups
Iniciem sessió amb **alumne1** per a que s'executi l'script, i comprovem que les carpetes s'han copiat correctament a **Backups**.
<img width="785" height="412" alt="image" src="https://github.com/user-attachments/assets/26ca07c4-f98a-4ab0-8585-08720e370f7f" />

## Fase 5 – Gestió de processos i serveis
### Pas 19 – Llistar processos actius
Podem veure tots els processos actius amb la comanda **tasklist**, executada al **CMD**.
<img width="631" height="714" alt="image" src="https://github.com/user-attachments/assets/1291cfe7-4ea3-40ee-84b1-fb2f0cd3a713" />

Podem redirigim la sortida de la comanda a un fitxer de text amb la comanda tasklist > C:\Users\alumne1\processos_inici.txt

<img width="519" height="62" alt="image" src="https://github.com/user-attachments/assets/21fd6779-7149-4295-bd95-eee238e323ac" />

<img width="1013" height="703" alt="image" src="https://github.com/user-attachments/assets/5615a767-e159-45ce-8407-783263eefa9a" />

Filtre els processos que volem usant **findstr** per filtrar del fitxer guardat:
<img width="627" height="166" alt="image" src="https://github.com/user-attachments/assets/291d5848-7ef3-4e74-a3b7-151704d947c7" />

### Pas 20 – Identificar processos prescindibles
Filtrarem tasklist per a trobar els processos no essencials per a l'usuari en un entorn "educatiu".
<img width="617" height="75" alt="image" src="https://github.com/user-attachments/assets/82df2252-f834-4c37-b870-619208df42f7" />

### Pas 21 – Eliminar processos manualment
Farem servir **taskkill** per a eliminar el procés OneDrive.
<img width="489" height="75" alt="image" src="https://github.com/user-attachments/assets/ece40f27-8648-42e9-a481-bbd5e844fc48" />

### Pas 22 – Automatitzar-ho a l'inici de sessió
Ara, modificarem l'script que hem creat a la fase anterior, afegint les comandes del pas anterior per a que, de manera automàtica cada vegada que es faci un inici de sessió, es mati el procés de **OneDrive** i **Teams**.
<img width="740" height="154" alt="image" src="https://github.com/user-attachments/assets/c34ca5e2-dd5b-4b4a-9fd6-a8bfc20990ef" />

Comprovem que el procés ha sigut matat quan iniciem sessió amb **alumne1**.
<img width="1031" height="251" alt="image" src="https://github.com/user-attachments/assets/177fa6c2-9516-4298-9130-a61b4b8696c7" />

### Pas 23 – Documentació: tasklist, anàlisi de processos crítics i rendiment

**Què passa si mates un procés crític com explorer.exe?**
 - L'escriptori desapareix (la barra de tasques, les icones i fins i tot el fons).
 - No es poden obrir finestres noves, ni accedir als fitxers.
 - El sistema es manté funcional, no tenim kernel panick, tot i que fallin coses.
 - Per recuperar-lo: Ctrl + Alt + Supr → Administrador de tasques → Arxiu → Executar nova tasca → explorer.exe

## Fase 6 – Gestió de permisos (ACLs)
**Què són les ACLs i com funcionen a Windows**

A Windows, cada fitxer i carpeta disposa d’una ACL (Access Control List), que és la llista encarregada d’establir quins usuaris o grups poden interactuar amb aquell recurs i de quina manera.

Cada element dins d’una ACL s’anomena ACE (Access Control Entry), i especifica:
 - Quina identitat (usuari o grup) rep l’aplicació del permís
 - Quins permisos té assignats (lectura, escriptura, execució, control total, etc.)
 - Si el permís està configurat com a Permetre o Denegar

| Permís                  | Descripció                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Control total (F)      | Permet totes les accions: llegir, escriure, modificar, eliminar i gestionar permisos |
| Modificar (M)          | Autoritza llegir, escriure i eliminar fitxers, però no modificar permisos   |
| Lectura i execució (RX)| Permet obrir fitxers i executar aplicacions                                |
| Mostrar contingut      | Permet visualitzar els elements dins d’una carpeta                         |
| Lectura (R)            | Permet accedir als fitxers només en mode lectura                           |
| Escriptura (W)         | Permet crear nous fitxers i subcarpetes                                    |
