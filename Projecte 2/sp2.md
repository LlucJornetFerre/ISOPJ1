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

### Pas 8. Afegir-los a un grup nou anomenat Limitats

### Pas 9. Provar la còpia de fitxers dins Dades per veure com actuen les quotes (superar límit)
