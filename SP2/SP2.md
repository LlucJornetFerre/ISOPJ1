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

### Accedir al terminal real d'Ubuntu

Amb la combinació de tecles **Ctrl dret + F5** accedim al sistema operatiu sense interfície gràfica. Aquest és el terminal real del sistema, a diferència dels **pseudo-terminals** que obrim amb la interfície gràfica. **Per a tornar a la interfície gràfica, hem de fer Ctrl+F2**

<img width="299" height="74" alt="image" src="https://github.com/user-attachments/assets/a001d78b-8836-4edc-a5ad-42ad10c4604c" />

Exercici: "Quina comanda o comandes he de fer servir quan vull canviar un nom d'usuari correctament"

Exercici2: "Especificar tots els paràmetres d'un usuari que creem amb useradd".

# Fitxers importants

# Comandes bàsiques

# Directoris i fitxers importants

# Gestió avançada

# PAM








## Còpies de segurett i automatització de tasques
## Quotes d'usuaris
