# Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers

## Sistemes de fitxers i particions
 - Mida sector
 - Mida block
 - Fragmentació interna: Espai desaprofitat degut a que arxius es guarden a un bloc, encara que no l'ocupin, perden espai.
 En aquest exemple, només ocupem 8 bytes dels 4096 disponibles al bloc. Per tant, tenim fragmentació.

 <img width="411" height="115" alt="image" src="https://github.com/user-attachments/assets/e6f61180-a7fc-4a61-afbb-b2d24ed98580" />

 - Fragmentació externa: Fragments d'un mateix arxiu està separat en diferents blocs, cosa que alenteix el sistema a l'hora d'executar-lo.
 - Tipus de formateig
   - Baix nivell: Esborra el sistema de fitxers, arxius i restaura sectors defectuosos.
   - Mig nivell: Esborra el sistema de fitxers, i esborra sectors defectuosos.
   - Alt nivell: Esborra el sistema de fitxers, deixant intactes els arxius.
 - Gestió de particions
   - GPARTED
   - Comandes

<img width="625" height="114" alt="image" src="https://github.com/user-attachments/assets/d797a705-9392-42bd-b013-d6576c65da43" />

Comprovar si una partició està fragmentada amb e4defrag.

<img width="713" height="361" alt="image" src="https://github.com/user-attachments/assets/8138945f-3b2b-4178-a849-09f4259aee26" />

Desfragmentació de la partició amb e4defrag.

<img width="478" height="73" alt="image" src="https://github.com/user-attachments/assets/e977eb1a-170e-4874-8eb3-dc8ca04427da" />

Volums: Afegir una capa d'extracció a sobre de les particions.


En gparted, podem fer el mateix que amb comandes EXCEPTE modificar la mida del block, que és 4096 per defecte.

<img width="775" height="202" alt="image" src="https://github.com/user-attachments/assets/8b6978ee-3c93-4b1d-b8d6-f3fd5762e615" />

(Crear partició, i formatejar-la, i altres proves per a demostrar que podem fer de tot excepete modificar la mida del bloc).

(aprox la mitat).
<img width="905" height="514" alt="image" src="https://github.com/user-attachments/assets/ba4a5f97-361a-4440-81df-86c25840720c" />

Crear el sistema de fitxers amb format ext4 a la partició que hem creat, i especifiquem 2048 com a mida del bloc amb **-b**.

<img width="780" height="312" alt="image" src="https://github.com/user-attachments/assets/ce927315-b68d-42da-b416-c84c96f88495" />

Comprovem amb tune2fs que la partició s'ha creat correctament **amb la mida de bloc que hem especificat anteriorment**. 
<img width="777" height="465" alt="image" src="https://github.com/user-attachments/assets/d0a08a5b-2d22-4c95-a097-22134074815d" />

Creem un sistema de fixters amb ntfs a /dev/sdb2.

<img width="497" height="136" alt="image" src="https://github.com/user-attachments/assets/b79070a5-4fcd-4906-9ddf-9d1d216512f3" />

I comprovem que les particions apareixen a gparted.

<img width="725" height="53" alt="Screenshot from 2025-10-23 14-13-26" src="https://github.com/user-attachments/assets/945d7536-bca4-4fad-b9b0-a0a19a287ddc" />

<img width="459" height="203" alt="Screenshot from 2025-10-23 14-14-40" src="https://github.com/user-attachments/assets/64b79419-82c1-48b2-806f-16230eb508a5" />

<img width="475" height="93" alt="Screenshot from 2025-10-23 14-16-46" src="https://github.com/user-attachments/assets/85e13fc7-9d7b-4071-91f9-ede359451d63" />

Si tornem a muntar, veiem que tornen a apareixer els fitxers.

<img width="726" height="139" alt="image" src="https://github.com/user-attachments/assets/d13b5911-da56-4479-aa79-1f1680365e44" />

Per a fer el mount permanent, editem el fitxer /etc/fstab, on introduirem les mateixes dades que posavem amb la comanda manual, i reiniciem l'equip.

<img width="802" height="314" alt="image" src="https://github.com/user-attachments/assets/60556326-144e-4e92-85f0-69b11bfe4eb9" />

Finalment, veiem que, encara que s'ha reinciat l'equip, la comanda s'executa automàticament al reiniciar l'equip.

<img width="531" height="149" alt="image" src="https://github.com/user-attachments/assets/b3fb0d4c-8f0d-48c4-9756-2d59fbfe4b6b" />

## Gestió de processos

El saltem, de moment.

## Gestió d'usuaris i grups i permisos

### Fitxers importants del sistema.

**sudo nano /etc/passwd** Aquest fitxer conté informació de tots els usuaris del sistema, aquells que inicien sessió gràficament, i els del sistema. També podem veure si un usuari té contrassenya (tot i que aquesta no es guarda en aquest fitxer), el seu grup principal i el seu directori **home**.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/95b63605-f328-4f87-871e-c28c3ad8d381" />

**sudo nano /etc/shadow** Dintre d'aquest fitxer podem veure tots els usuaris del sistema, amb la seva contrasenya encriptada, si en tenen. Els altres camps mostren la caducitat de la contrasenya de cada usuari, i quan es va canviar per última vegada. Podem resumir aquest fitxer com el fitxer que recull tota l'informació sobre les contrasenyes dels usuaris.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/27b4eff1-1c27-4e10-9d24-feffdbc5b129" />

**sudo nano /etc/group** Aquest fitxer conté tots els grups del sistema, i també mostra quins usuaris formen part dels grups declarats.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/6f1eaf79-c72e-4296-84d3-6511f574b1ca" />

**sudo nano /etc/gshadow** Aquest fitxer conté la mateixa informació que l'anterior, però a diferència de l'anterior, dintre d'aquest fitxer podem veure l'usuari administrador de cada grup.

### Gestió d'usuaris

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/4908fc18-7428-4b30-868d-7ab5752ddff2" />

Ara, crearem un nou usuari al sistema amb l'assistent amb la comanda **adduser**.

<img width="713" height="471" alt="image" src="https://github.com/user-attachments/assets/08d594c1-6c31-4e9c-b3be-360ef658a36a" />

Amb l'usuari creat, revisem que han aparegut noves entrades per a l'usuari als fitxers que hem vist abans.

<img width="1004" height="252" alt="image" src="https://github.com/user-attachments/assets/6e8d56ea-a00f-4fc1-8d92-1a46a3b255da" />

Si esborrem l'usuari amb **userdel -r alumnat**, veurem que les entrades i el seu directori local han desaparegut.

<img width="615" height="209" alt="image" src="https://github.com/user-attachments/assets/ab42530f-407f-4943-8b1c-6a4ab4511d2a" />

Tot seguit, creem un nou usuari, aquesta vegada amb la comanda **useradd**. Després, busquem l'entrada del nou usuari a **/etc/passwd**, i podrem veure que se li han assignat uns quants paràmetres per defecte, com ara l'interpret de comandes, i el home directory. Cal mencionar que, tot i que se li ha assignat un directori home, aquest no s'ha creat.

<img width="606" height="138" alt="image" src="https://github.com/user-attachments/assets/b7312f68-7921-41a1-b4a7-b79f25a1f21e" />

No ens agraden els paràmetres per defecte, per tant, executarem la comanda **usermod alumnat2** per a modificar els paràmetres de l'usuari que especifiquem. També crearem la carpeta que se li ha assignat com a home, i **li donarem permisos a l'usuari alumnat2**, ja que si no en te, no podrà fer res al seu directori local.

<img width="592" height="27" alt="image" src="https://github.com/user-attachments/assets/920b2832-9c7e-46e8-8b29-ed2df04195e3" />

<img width="709" height="507" alt="image" src="https://github.com/user-attachments/assets/55b2667d-0678-4da3-a65d-92fdaef98f1d" />

Finalment, li assignarme una contrsenya a l'usuari amb **passwd alumnat2**, i ja podrà iniciar sessió amb interfície gràfica.

<img width="632" height="133" alt="image" src="https://github.com/user-attachments/assets/60db3162-17f0-491f-81b6-d538dc0f4648" />

Per a prohibir l'accés a un usuari al sistema, executarem la comanda **usermod -L alumnat2**. Aquesta comanda bloqueja l'accés a l'usuari especificat, i rebrà un missatge de contrasenya equivocada si intenta entrar. Podem comprovar que l'usuari està bloquejat ja que, a **/etc/passwd**, té una exclamació davant de la contrasenya encriptada.

Per a revertir aquesta comanda, executem **usermod -U alumnat2** i ja podrà accedir al sistema.

<img width="1023" height="201" alt="image" src="https://github.com/user-attachments/assets/4baacad4-807c-41d8-a6ab-085100ab8a93" />

Per a canviar el nom d'un usuari, cal fer-ho amb una comanda específica **I NO MODIFICANT MANUALMENT ELS FITXERS DE CONFIGURACIÓ**, ja que molts fitxers depenen d'aquest paràmetre, i canviar-lo manualment a un fitxer com ara **/etc/passwd** faria que l'usuari deixés de funcionar. La comanda és **usermod -l alumnat2 alumnat3** 

<img width="579" height="54" alt="image" src="https://github.com/user-attachments/assets/81bb47d9-1b35-4484-a368-bc0ea6b9dabb" />

### Gestió de grups

Podem crear un grup amb la comanda **addgroup asix**, i podem modificar els paràmetres d'aquest amb **groupmod.**

<img width="717" height="210" alt="image" src="https://github.com/user-attachments/assets/8f41c4f2-a8d9-4bf1-83ab-f75aa1b3cb5a" />

Podem afegir usuaris a grups de diverses maneres, per exemple:

**adduser**

<img width="517" height="71" alt="image" src="https://github.com/user-attachments/assets/eaa9dab6-b9c1-40c2-9619-bdc1bae11a0a" />

**gpasswd**

<img width="546" height="46" alt="image" src="https://github.com/user-attachments/assets/58f84078-9d5b-44e0-973b-7ba4e5d0021e" />

**usermod**

<img width="573" height="71" alt="image" src="https://github.com/user-attachments/assets/c7b78d1a-45f6-4cea-8166-1e83d618b54c" />

Per a eliminar un usuari d'un grup, executem la comanda **deluser alumnat2 asixA**

<img width="537" height="75" alt="image" src="https://github.com/user-attachments/assets/0c1b2950-88fe-46c8-88f3-90d112fa4fd8" />

### Accedir al terminal real d'Ubuntu/TTY

Amb la combinació de tecles **Ctrl dret + F5** accedim al sistema operatiu sense interfície gràfica. Aquest és el terminal real del sistema, a diferència dels **pseudo-terminals** que obrim amb la interfície gràfica. **Per a tornar a la interfície gràfica, hem de fer Ctrl dret + F2**

<img width="299" height="74" alt="image" src="https://github.com/user-attachments/assets/a001d78b-8836-4edc-a5ad-42ad10c4604c" />

Exercici: "Quina comanda o comandes he de fer servir quan vull canviar un nom d'usuari correctament"

Exercici2: "Especificar tots els paràmetres d'un usuari que creem amb useradd". 

Tot i que és impossible resumir tots els passos de la creació de l'usuari en una sola comanda, podem fer-ne la majoría. Amb la comanda **useradd -s /bin/bash**

### - 1 Permisos "normals" UOG

Dintre del sistema operatiu, tots els arxius i directoris tenen un set de permisos, que determinen quins usuaris, o grups, podem realitzar certes accions sobre aquests. Els permisos es poden desglossar en 3 valors:

 - r: Significa **read**, o llegir, i indica si l'usuari pot visualitzar els continguts d'un fitxer o directori.

 - w: Significa **write**, o escriure, i determina si l'usuari pot fer canvis al directori o fitxer.

 - x: Significa **execute**, o executar, i ens permet saber si l'usuari pot executar l'arxiu.

Els permisos de certs usuaris o grups sobre el directori o fitxer es determinen mitjançant una combinació dels 3 valors anteriors, que s'apliquen a 3 grups o usuaris diferents. 

Com podem comprovar si executem la comanda **ll | grep test**, el sistema ens mostra el següent: drwxr-xr-x. 

<img width="634" height="68" alt="image" src="https://github.com/user-attachments/assets/afa37d64-bfa9-4b62-a2dc-8a7548999226" />

Primer, podem veure una **d**. Aquest valor ens indica que l'objectiu de la comanda és un directori. En el cas d'un arxiu, aquest valor es mostra com un **-**. Com podem veure, els 3 valors anteriors, (r, w, x) es repeteixen 3 vegades sobre el mateix directori. Això és degut a que el sistema otorga 3 combinacions de permisos al mateix arxiu, cadascun per a algú diferent. La primera combinació representa els permisos de **l'usuari propietari**, que sovin té els 3 valors habilitats. El propietari de la carpeta és **root**, per tant, provarem a crear, eliminar i llistar el contingut de la carpeta per a confirmar que els permisos s'apliquen correctament.

<img width="320" height="157" alt="image" src="https://github.com/user-attachments/assets/f7126fd7-0aee-4322-abd5-347249d2ad67" />

Tot seguit, tenim els del grup del propietari. Els usuaris que formin part del grup propietari del fitxer tindran els permisos r i x sobre l'arxiu, es a dir, han de poder llistar el contingut del directori i executar arxius dintre d'aquest, però no tenen permès crear, editar o esborrar el contingut de la carpeta. Ho comprovarem amb l'usuari **lluc2**, que forma part del grup **estudiants**, el grup propietari de la carpeta test.

<img width="737" height="269" alt="image" src="https://github.com/user-attachments/assets/704325aa-749d-46fa-a921-f7d235e53013" />

Finalment, tenim els permisos per a la resta d'usuaris del sistema. Aquests són els mateixos que els del cas anterior, i els comprovarem amb un usuari que no forma part del grup estudiants.

<img width="737" height="269" alt="image" src="https://github.com/user-attachments/assets/9a0ba11f-4de8-46b7-8ecf-c7d6ae81f83b" />

Aquests permisos es representen amb números, 1 per a cada combinació, que surt de la suma dels 3 valors assignats. Representats a la taula següent es veuen les possibles combinacions, entenent que **x** -> 1 **w** -> 2 i **r** -> 4. Per tant, si volem donar permisos totals al propietari, grup del propietari i a la resta d'usuaris del sistema, posarem 777.

| valor numèric | representació en lletres |
| :-----------: | :----------------------: |
|       0       |         ---              |
|       1       |         --x              |                      
|       2       |         -w-              |
|       3       |         -wx              |
|       4       |         r--              |
|       5       |         r-x              |  
|       6       |         rw-              |
|       7       |         rxw              |

### 2 - UMASK

UMASK determina **els permisos per defecte que tindran els fitxers i directoris** quan un usuari els crea. Funciona com una màscara de bits que **“resta”** permisos dels valors per defecte:


Permisos base per defecte:

Fitxers: 666 (rw-rw-rw-)

Directoris: 777 (rwxrwxrwx)

UMASK substrau permisos dels valors base per obtenir els permisos finals.

**Exemple:**

```UMASK = 022

Fitxers creats: 666 – 022 = 644 (rw-r--r--)

Directoris creats: 777 – 022 = 755 (rwxr-xr-x)
```

El sistema ens permet gestionar el valor d'UMASK per a tots els usuaris del sistema, però també podem modificar manualment el valor d'un usuari en concret. Per a modificar el valor per defecte d'UMASK per a tots els usuaris del sistema, accedirem a **/etc/login.defs**. Allà, trobarem el valor UMASK que el sistema assigna per defecte a tots els usuaris, i el podrem modificar lliurement.







### 3 - 













### 4 - ACL

Primer, executem **getacl numeros** per a veure permisos i excepcions d'ACL aplicades al directori **numeros**

<img width="323" height="168" alt="image" src="https://github.com/user-attachments/assets/efc12cdf-7659-409e-9a0d-b8ff094cccee" />

Tot seguit, eliminarem els permisos de l'usuari **segon** sobre la carpeta **numeros**. Aplicarem una excepció a la carpeta **numeros**, que permet **r**, **w** i **x** a **others** (es a dir, tots els usuaris del sistema), per a que no els apliqui a l'usuari segon, i que se li apliquin els permisos que establirem amb la comanda, en aquest cas, res.

<img width="485" height="222" alt="image" src="https://github.com/user-attachments/assets/20405cdd-98c6-4328-a0e3-faaed8112739" />

Ara, entrarem amb l'usuari **primer**, i comprovarem que té permisos sobre la carpeta (recordem, la carpeta numeros permet read, write i execute a tots els usuaris del sistema).

<img width="391" height="148" alt="image" src="https://github.com/user-attachments/assets/353a4563-b6f1-4f64-b2cd-4746e084508a" />

A continuació, comprovem que l'excepció dels permisos de la carpeta numeros de l'usuari segon funciona correctament.

<img width="591" height="145" alt="image" src="https://github.com/user-attachments/assets/a3e1bfec-db00-403e-bc95-75fda8816dbb" />

Finalment, podem esborrar les excepcions aplicades sobre un directori o fitxer, executem la comanda **setfacl -b numeros**.

<img width="355" height="181" alt="image" src="https://github.com/user-attachments/assets/afb059de-cc51-4413-a8f5-70faa6f17ae0" />





## Còpies de seguretat i automatització de tasques
## Quotes d'usuaris
