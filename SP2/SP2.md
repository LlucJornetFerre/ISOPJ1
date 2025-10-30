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

**sudo nano /etc/passwd** Aquest fitxer conté informació de tots els usuaris del sistema, aquells que inicien sessió gràficament, i els del sistema. També podem veure si un usuari té contrassenya (tot i que aquesta no es guarda en aquest fitxer), el seu grup principal i el seu directori **home**.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/95b63605-f328-4f87-871e-c28c3ad8d381" />

**sudo nano /etc/shadow** Dintre d'aquest fitxer podem veure tots els usuaris del sistema, amb la seva contrasenya encriptada, si en tenen. Els altres camps mostren la caducitat de la contrasenya de cada usuari, i quan es va canviar per última vegada. Podem resumir aquest fitxer com el fitxer que recull tota l'informació sobre les contrasenyes dels usuaris.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/27b4eff1-1c27-4e10-9d24-feffdbc5b129" />

**sudo nano /etc/group** Aquest fitxer conté tots els grups del sistema, i també mostra quins usuaris formen part dels grups declarats.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/6f1eaf79-c72e-4296-84d3-6511f574b1ca" />

**sudo nano /etc/gshadow** Aquest fitxer conté la mateixa informació que l'anterior, però a diferència de l'anterior, dintre d'aquest fitxer podem veure l'usuari administrador de cada grup.

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/4908fc18-7428-4b30-868d-7ab5752ddff2" />


# Fitxers importants

# Comandes bàsiques

# Directoris i fitxers importants

# Gestió avançada

# PAM








## Còpies de segurett i automatització de tasques
## Quotes d'usuaris
