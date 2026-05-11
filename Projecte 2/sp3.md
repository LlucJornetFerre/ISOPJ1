# Active Directory: Instal·lació del DC i unió d'un client Windows

Configurem una direcció IP estàstica al servidor.
<img width="813" height="483" alt="image" src="https://github.com/user-attachments/assets/3baad714-962f-4268-a235-2763fcb81bf5" />

Afegim el rol "**Active Directory Domain Services**".
<img width="417" height="175" alt="image" src="https://github.com/user-attachments/assets/31d4590e-0c15-43d9-b70b-2d6776f0d9b6" />

Deixem tot per defecte fins que arribem a **Roles de servidor**. Allà, seleccionem **Servicios de dominio de Active Directory**.
<img width="985" height="586" alt="image" src="https://github.com/user-attachments/assets/77b4b05c-600d-41d1-8736-0fdd96793266" />

Continuem deixant tot per defecte, i iniciem la instal·lació.
<img width="985" height="586" alt="image" src="https://github.com/user-attachments/assets/0e07c659-697b-4567-afce-8f1d41ec8ea6" />

Quan s'ha acabat la instal·lació, promovem el servidor a "**Controlador de dominio**.
<img width="349" height="321" alt="image" src="https://github.com/user-attachments/assets/3eb68966-05e3-4d34-bf87-ffd09d7f6987" />

Això l'assitent de configuració, i ens oferirà de crear un nou bosc. Acceptem, i el creem.
<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/f4bc9f23-14f2-4e72-9b93-1fa4cd88faea" />

Indiquem una contrasenya.
<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/55029b86-c17e-4f50-adbd-08b71f036bb6" />

Deixem el nom proposat per defecte per a NetBios.
<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/c14df4ca-590c-4cc0-a644-d84472716541" />

Farem servir les rutes proposades per defecte per l'instal·lador.
<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/ab2e6e6b-f8dd-49e4-90f3-2eb07c1fe96f" />

<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/079338dd-3102-405b-92a2-5b5fc1a37527" />

<img width="760" height="554" alt="image" src="https://github.com/user-attachments/assets/42103ce3-bc9c-4f6b-b214-42e76683a1cb" />

Quan hem acabat la instal·lació, reiniciem l'equip, i iniciarem sessió amb JORNET/Administrador
<img width="904" height="514" alt="image" src="https://github.com/user-attachments/assets/0249f8d3-3231-4b56-a084-16d690acf1e9" />

A continuació, accedirem a la gestió d'usuaris i equips d'active directory, i crearem un nou usuari.
<img width="783" height="680" alt="image" src="https://github.com/user-attachments/assets/5beb8193-2bc1-46ac-bc3f-1a886fb87f22" />

<img width="763" height="561" alt="image" src="https://github.com/user-attachments/assets/bf40683f-9a58-4bbe-a675-03123730279b" />

<img width="746" height="533" alt="image" src="https://github.com/user-attachments/assets/56d26397-3f44-4152-a09f-c1a990e86c7b" />

<img width="746" height="533" alt="image" src="https://github.com/user-attachments/assets/6a813c8f-5d8e-4bfc-8d12-30d45df3a420" />

<img width="746" height="533" alt="image" src="https://github.com/user-attachments/assets/26ddf1ab-2132-40bf-a613-fa69483d2b85" />

<img width="746" height="533" alt="image" src="https://github.com/user-attachments/assets/04dec180-4a75-43ee-a8ac-e581b448dabb" />

Ara, amb una nova màquina Windows, ens connectarem a l'active directory a través de l'usuari que hem creat.

Primer, obrirem la configuració de xarxa del client, i posarem la direcció IP del servidor com a DNS.
<img width="400" height="453" alt="image" src="https://github.com/user-attachments/assets/24adcdec-033b-4a2c-be8a-c2d1a6a25590" />

Després, accedim a **Cuenta**, i **Unir este dispositivo a un dominio local de Active Directory**.
<img width="1021" height="731" alt="image" src="https://github.com/user-attachments/assets/cf08c48f-ad1b-41ef-be5d-c6157f1bb435" />

<img width="1021" height="731" alt="image" src="https://github.com/user-attachments/assets/d23ebdc5-14b8-403c-a9a3-0de7eb532347" />

Posem les credencials de l'usuari administrador del servidor.
<img width="1021" height="731" alt="image" src="https://github.com/user-attachments/assets/ce76eb04-b022-4bb7-9122-33cacd7b7a90" />

L'usuari que hem creat abans.
<img width="1021" height="731" alt="image" src="https://github.com/user-attachments/assets/d94da680-eac8-4aee-af49-56d713705b11" />

