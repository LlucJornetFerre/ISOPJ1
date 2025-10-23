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



## Gestió de processos
## Gestió d'usuaris i grups i permisos
## Còpies de segurett i automatització de tasques
## Quotes d'usuaris
