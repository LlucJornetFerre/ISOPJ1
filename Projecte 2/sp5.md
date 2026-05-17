# Auditories de Seguretat amb Windows Server 2022

## Contextualització: Auditories

En un entorn empresarial, saber **qui ha accedit a quins recursos, quan i des d'on** és fonamental per garantir la seguretat dels sistemes. Les **auditories de seguretat** permeten als administradors de sistemes registrar i monitoritzar totes les activitats rellevants que es produeixen en un servidor o estació de treball: inicis de sessió, accessos a fitxers, canvis de configuració, creació i eliminació de comptes, etc.

Windows Server incorpora un sistema d'auditoria integrat basat en **polítiques de seguretat locals o de domini** que, quan s'activen, generen entrades al **Visor d'esdeveniments** (`eventvwr.msc`) sota el registre de **Seguretat**. Cada esdeveniment té un **Event ID** únic que identifica exactament quina acció s'ha produït.

---

## Teoria: El sistema d'auditoria de Windows

### Tipus d'auditories disponibles

### Per què és important l'auditoria?

- **Detecció d'intrusions:** Identificar intents d'accés no autoritzats (Event 4625 repetits).
- **Compliment normatiu:** Moltes regulacions (ISO 27001, GDPR, PCI-DSS) exigeixen registres d'auditoria.
- **Investigació forense:** En cas d'incident de seguretat, els logs permeten reconstruir els fets.
- **Monitoratge intern:** Controlar l'accés a dades sensibles per part del personal intern.

| Directiva d'auditoria | Descripció | Event IDs principals |
|-----------------------|------------|----------------------|
| **Auditar eventos de inicio de sesión** | Registra tots els intents d'autenticació al sistema | 4624 (èxit), 4625 (fallada) |
| **Auditar el acceso a objetos** | Registra l'accés a fitxers, carpetes, claus de registre i altres objectes | 4663 (accés a objecte) |
| **Auditar el seguimiento de procesos** | Registra la creació i finalització de processos | 4688 (creat), 4689 (finalitzat) |
| **Auditar la administración de cuentas** | Registra operacions sobre comptes d'usuari | 4720 (creat), 4725 (deshabilitat), 4726 (eliminat) |
| **Auditar el cambio de directivas** | Registra canvis a les polítiques de seguretat | 4719 |
| **Auditar el uso de privilegios** | Registra l'ús de privilegis elevats | 4672 |

### Com accedir al Visor d'esdeveniments

Podem accedir al Visor d'esdeveniments amb **Windows + R → eventvwr.msc** → **Registros de Windows** → **Seguridad**

Per filtrar per Event ID específic: clic dret sobre **Seguridad** → **Filtrar registro actual** → introduir el número d'event.

---

## Auditories pas a pas

### 1. Activar les auditories: Directiva de seguretat local

Obrim el diàleg d'execució amb **Windows + R** i escrivim **secpol.msc** per obrir la **Directiva de seguretat local**. Acceptem per executar-ho amb privilegis administratius.

<img width="410" height="228" alt="image" src="https://github.com/user-attachments/assets/81da254a-db4d-4133-ae5b-1efc8eabe14f" />

---

### 2. Activar l'auditoria d'inici de sessió

Dins de secpol.msc, naveguem a:
**Directivas locales → Directiva de auditoría → Auditar eventos de inicio de sesión**

Obrim les propietats i marquem tant **Correcto** com **Erróneo**. Això farà que Windows registri tots els inicis de sessió, tant els exitosos (4624) com els fallits (4625).

- **Correcto** → registra logins amb èxit (Event ID **4624**)
- **Erróneo** → registra intents fallits (Event ID **4625**)

<img width="1167" height="568" alt="image" src="https://github.com/user-attachments/assets/a0d9a3ff-19de-49e5-aa80-e8fbaa1a410b" />

---

### 3. Comprovar l'Event ID 4624: inici de sessió correcte

Obrim el **Visor d'esdeveniments** (eventvwr.msc) i naveguem a **Registros de Windows → Seguridad**. Filtrem per l'Event ID **4624** i veiem totes les entrades d'inici de sessió correctes. Seleccionem-ne una i al panell inferior veiem el detall:

- **"Se inició sesión correctamente en una cuenta"**
- Compte: `WIN-BUTVQ9ER1MK$` del domini `JORNET.CAT`
- Tipus d'inici de sessió: `3` (xarxa)

Això confirma que l'auditoria d'inici de sessió funciona correctament.

<img width="2541" height="1290" alt="image" src="https://github.com/user-attachments/assets/e96ba92c-8bb8-42e1-84d2-fa2f2474309a" />

---

### 4. Activar l'auditoria d'accés a objectes

Tornem a `secpol.msc` i activem **Auditar el acceso a objetos** marcant **Correcto** i **Erróneo**. Aquesta directiva és necessària per registrar accessos a fitxers i carpetes específiques, però **no és suficient per ella sola**: cal configurar l'auditoria també a nivell de cada carpeta o fitxer.

<img width="1166" height="543" alt="image" src="https://github.com/user-attachments/assets/5e3b3f0d-d90f-4382-a253-3313037b4eb2" />

---

### 5. Crear la carpeta d'auditoria

Creem una carpeta nova a l'arrel del disc C: anomenada `Prova`. Serà la carpeta sobre la qual configurarem l'auditoria i sobre la qual farem proves d'accés, lectura i modificació de fitxers.

<img width="1121" height="631" alt="image" src="https://github.com/user-attachments/assets/053631a1-f8c1-416e-b4ed-3b66ace2e8d5" />

---

### 6. Configurar l'auditoria sobre la carpeta

Fem clic dret sobre `Prova` → **Propiedades → Seguridad → Opciones avanzadas → Auditoría → Agregar**.

Afegim l'usuari **Administrador** (`JORNET\Administrador`) amb tipus d'accés **Control total** perquè quedi registrada qualsevol acció que l'Administrador faci sobre la carpeta. La configuració es veu reflectida a la pestanya **Auditoría** de la finestra de seguretat avançada.

<img width="1448" height="743" alt="image" src="https://github.com/user-attachments/assets/7775ea79-614a-4111-953d-0b0f6883c40e" />

---

### 7. Generar accions dins la carpeta

Creem un fitxer de text `exemple.txt` dins de `C:\Prova`. Després l'obrim, el modifiquem i l'eliminem. Cada una d'aquestes accions genera un Event ID 4663 al Visor d'esdeveniments.

<img width="793" height="564" alt="image" src="https://github.com/user-attachments/assets/37408994-7cc7-4a8a-847b-e30e958cb2c0" />

---

### 8. Filtrar per Event ID 4663

Al Visor d'esdeveniments, fem clic dret sobre **Seguridad** → **Filtrar registro actual** i introduïm el codi **4663** per mostrar únicament els events d'accés a objectes.

<img width="1233" height="569" alt="image" src="https://github.com/user-attachments/assets/711cdf21-6a52-468f-b3c6-b8b5db833484" />

---

### 9. Comprovar l'Event ID 4663: accés a objecte

Veiem múltiples entrades amb Event ID **4663** (categoria: File System) generades al moment que vam crear i manipular el fitxer. El detall de l'event mostra:

- **"Se intentó tener acceso a un objeto"**
- Firmant: `JORNET\Administrador`
- Objecte: `C:\Prova` (tipus File)
- Nom del procés: `C:\Windows\explorer.exe`

Això confirma que Windows ha registrat correctament l'accés a la carpeta auditada.

<img width="1372" height="849" alt="image" src="https://github.com/user-attachments/assets/45e06c35-21fc-43ca-9eca-71983a989968" />

---

### 10. Activar l'auditoria de seguiment de processos

Tornem a `secpol.msc` i activem **Auditar el seguimiento de procesos** amb **Correcto** i **Erróneo**. Amb aquesta directiva, Windows registrarà cada vegada que s'iniciï o finalitzi un procés en el sistema.

<img width="1202" height="554" alt="image" src="https://github.com/user-attachments/assets/3e333241-9e40-4763-9d1a-b438ed557646" />

---

### 11. Obrir el Bloc de notes per generar un Event 4688

Per provar l'auditoria de processos, cerquem **bloc de notes** al menú d'inici i l'obrim. Aquesta acció ha de generar l'Event ID **4688** (procés creat) al registre de Seguretat.

<img width="783" height="679" alt="image" src="https://github.com/user-attachments/assets/6d73d7dd-ff60-497e-be65-2a2fd4868132" />

---

### 12. Filtrar per Event ID 4688

Al Visor d'esdeveniments, filtrem per l'Event ID **4688** per veure tots els processos creats des que es va activar l'auditoria.

<img width="546" height="550" alt="image" src="https://github.com/user-attachments/assets/e4a0a9db-72dc-468b-9407-1bf0d63466a2" />

---

### 13. Comprovar l'Event ID 4688: procés creat

L'Event **4688** registrat mostra:

- **"Se creó un nuevo proceso"**
- Firmant creador: `JORNET\Administrador`
- **Nom del nou procés: `C:\Windows\System32\notepad.exe`**
- Tipus d'elevació de token: `TokenElevationTypeDefault (1)`
- Registrat a les `21:02:37`

Queda documentat exactament qui ha iniciat el procés, quan i quin executable s'ha executat.

<img width="596" height="845" alt="image" src="https://github.com/user-attachments/assets/a919554d-fbd8-483d-baa0-723aa4c6c756" />

---

### 14. Filtrar per Event ID 4689

Tanquem el Bloc de notes. Per comprovar que s'ha registrat la finalització, filtrem per l'Event ID **4689** (procés finalitzat).

<img width="542" height="547" alt="image" src="https://github.com/user-attachments/assets/d2fab32e-baac-4fc6-bba9-85b65b8e2eac" />

---

### 15. Comprovar l'Event ID 4689: procés finalitzat

L'Event **4689** confirma:

- **"Se salió de un proceso"**
- Firmant: `JORNET\Administrador`
- **Nom del procés: `C:\Windows\System32\notepad.exe`**
- ID del procés: `0x8e0` (el mateix que quan es va crear)
- **Estat de sortida: `0x0`** (finalització correcta)

Amb els events 4688 i 4689 podem saber exactament quins programes s'han executat al servidor i durant quant de temps.

<img width="594" height="844" alt="image" src="https://github.com/user-attachments/assets/c45a74c9-3739-47de-ab02-505c152c5526" />

---

### 16. Activar l'auditoria d'administració de comptes

Tornem a `secpol.msc` i activem **Auditar la administración de cuentas** amb **Correcto** i **Erróneo**. Aquesta directiva registra totes les operacions sobre comptes d'usuari: creació, activació, deshabilitació i eliminació.

<img width="1199" height="541" alt="image" src="https://github.com/user-attachments/assets/da93dc65-dc90-41c4-81c3-69aa86242ef4" />

---

### 17. Obrir la gestió d'usuaris i equips d'AD

Premem **Windows + R** i escrivim `lusrmgr.msc` per accedir a la consola de gestió de comptes del domini **Usuarios y equipos de Active Directory**.

<img width="409" height="227" alt="image" src="https://github.com/user-attachments/assets/1de515a8-204a-4db2-accc-864734a87a71" />

---

### 18. Crear un nou usuari de prova

A la consola d'AD, fem clic dret sobre el contenidor **Users** i seleccionem **Nuevo → Usuario**. Creem un usuari de prova amb el nom `prova`, que serà el compte que utilitzarem per provar la generació d'events d'administració de comptes.

<img width="755" height="559" alt="image" src="https://github.com/user-attachments/assets/1bc8697b-855a-4685-a847-34bf599b8f72" />

---

### 19. Dades del nou usuari prova

Omplim les dades del nou usuari:

- **Nombre de pila:** `prova`
- **Nombre de inicio de sesión:** `prova@jornet.cat`
- **Nom anterior a Windows 2000:** `JORNET\prova`

Fem clic a **Siguiente** per continuar i finalitzem la creació.

<img width="749" height="526" alt="image" src="https://github.com/user-attachments/assets/61e97719-389c-4269-8e9c-bf3c0ff25830" />

---

### 20. Filtrar per Event ID 4720

Al Visor d'esdeveniments, filtrem per l'Event ID **4720** per verificar que la creació de l'usuari s'ha registrat.

<img width="545" height="548" alt="image" src="https://github.com/user-attachments/assets/699d817d-729d-4087-88fd-cc0751e6f827" />

---

### 21. Comprovar l'Event ID 4720: usuari creat

L'Event **4720** confirma:

- **"Se creó una cuenta de usuario"**
- Firmant (qui l'ha creat): `JORNET\Administrador`
- **Nova compte: `JORNET\prova`**
- Nom de compte SAM: `prova`
- Principal d'usuari: `prova@jornet.cat`
- Categoria de tasca: **User Account Management**

Queda registrat qui va crear el compte, quan i amb quins atributs.

<img width="1327" height="835" alt="image" src="https://github.com/user-attachments/assets/ad88e025-7c3d-450b-ab9a-f74f81c36190" />

---

### 22. Deshabilitar el compte d'usuari

Tornem a la consola d'AD. Fem clic dret sobre l'usuari **prova** i seleccionem **Deshabilitar cuenta** per simular la desactivació temporal d'un compte.

<img width="746" height="445" alt="image" src="https://github.com/user-attachments/assets/392db9f4-cb2d-43e1-a234-3b3e0e21d214" />

---

### 23. Confirmació de deshabilitació

AD mostra el missatge de confirmació: **"El objeto prova ha sido deshabilitado"**. Acceptem.

<img width="286" height="149" alt="image" src="https://github.com/user-attachments/assets/07270fd0-1ad9-4f08-abf0-6c354d6bfbce" />

---

### 24. Filtrar per Event ID 4725

Al Visor d'esdeveniments, filtrem per l'Event ID **4725** per verificar que la deshabilitació s'ha registrat.

<img width="539" height="548" alt="image" src="https://github.com/user-attachments/assets/7574dd9d-a869-4c95-8629-20af253b4e78" />

---

### 25. Comprovar l'Event ID 4725: usuari deshabilitat

L'Event **4725** mostra:

- **"Se deshabilitó una cuenta de usuario"**
- Firmant: `JORNET\Administrador`
- **Compte de destí: `JORNET\prova`**
- Registrat a les `21:27:10`
- Categoria: **User Account Management**

El registre permet saber exactament quan i qui va deshabilitar el compte.

<img width="608" height="844" alt="image" src="https://github.com/user-attachments/assets/4cc9560f-5949-4766-90e4-31c39dd08aa9" />

---

### 26. Eliminar el compte d'usuari

Tornem a la consola d'AD. Fem clic dret sobre l'usuari **prova** i seleccionem **Eliminar** per suprimir definitivament el compte del domini.

<img width="370" height="339" alt="image" src="https://github.com/user-attachments/assets/2a547595-af13-4d59-aa1a-8b50ae3ade66" />

---

### 27. Filtrar per Event ID 4726

Al Visor d'esdeveniments, filtrem per l'Event ID **4726** per verificar que l'eliminació del compte ha quedat registrada.

<img width="547" height="548" alt="image" src="https://github.com/user-attachments/assets/2b8bd9c0-6338-4ced-9f0c-1dbcb012838b" />

---

### 28. Comprovar l'Event ID 4726: usuari eliminat

L'Event **4726** confirma:

- **"Se eliminó una cuenta de usuario"**
- Firmant: `JORNET\Administrador`
- **Compte eliminat: `JORNET\prova`**
- Registrat a les `21:27:58`
- Categoria: **User Account Management**

Amb aquest darrer event, el cicle de vida complet del compte `prova` queda documentat al registre de seguretat: creació (4720) → deshabilitació (4725) → eliminació (4726).

<img width="598" height="833" alt="image" src="https://github.com/user-attachments/assets/e9f452e3-c5f0-4ec5-90d6-e9582fede8cf" />

---

## IDs de procés fets servir durant les proves

| Event ID | Categoria | Descripció | Activat per... |
|----------|-----------|------------|----------------|
| **4689** | Process Termination | Procés finalitzat | Auditar el seguimiento de procesos |
| **4625** | Logon | Inici de sessió fallit | Auditar eventos de inicio de sesión |
| **4726** | User Account Management | Compte d'usuari eliminat | Auditar la administración de cuentas |
| **4722** | User Account Management | Compte d'usuari activat | Auditar la administración de cuentas |
| **4663** | File System | Accés a un objecte (fitxer/carpeta) | Auditar el acceso a objetos + config. carpeta |
| **4688** | Process Creation | Nou procés creat | Auditar el seguimiento de procesos |
| **4624** | Logon | Inici de sessió correcte | Auditar eventos de inicio de sesión |
| **4720** | User Account Management | Compte d'usuari creat | Auditar la administración de cuentas |
| **4725** | User Account Management | Compte d'usuari deshabilitat | Auditar la administración de cuentas |


---

## Reflexió final

### Conclusions generals

- **L'auditoria de Windows és una eina potent i granular:** Permet registrar amb precisió qui fa cada acció, quan i des d'on, sense necessitat de programari de tercers.

- **La doble configuració és necessària per a objectes:** Per registrar accés a fitxers i carpetes (Event 4663), cal activar la política a `secpol.msc` **i** configurar l'auditoria a les propietats de la carpeta concreta. Sense les dues parts, l'auditoria no funciona.

- **El Visor d'esdeveniments és la finestra a la seguretat del sistema:** Centralitza tots els registres i permet filtrar per Event ID, data, usuari o equip per trobar ràpidament la informació rellevant.

- **El seguiment de processos pot generar molt de volum:** Activar l'auditoria de processos en un servidor en producció pot omplir ràpidament el registre de seguretat. Cal calibrar bé quines auditories s'activen i configurar una mida adequada per al registre.

### Observacions tècniques

- **L'Event ID 4624 es genera molt freqüentment:** Inclou autenticacions del sistema operatiu, serveis i comptes de màquina. Per trobar inicis de sessió d'usuaris humans, cal filtrar per tipus d'inici de sessió `2` (interactiu) o `10` (remot).

- **Els logs no duren per sempre:** Per defecte, Windows sobreescriu el registre quan es plena. En entorns professionals s'han d'enviar els logs a un **SIEM** (*Security Information and Event Management*) per emmagatzemar-los i analitzar-los centralment.

- **L'auditoria d'AD és especialment crítica:** Qualsevol creació, modificació o eliminació de comptes al domini queda registrada, la qual cosa permet detectar comportaments anòmals com la creació de comptes no autoritzats.

- **L'auditoria és una capa de visibilitat, no una capa de protecció:** Cal combinar-la amb còpies de seguretat, polítiques d'accés mínims i plans de resposta a incidents per tenir una postura de seguretat completa.

---

# Monitorització del sistema amb Windows Server 2022

## Contextualització: monitorització

La **monitorització del sistema** consisteix a observar en temps real el comportament dels recursos del servidor: CPU, memòria RAM, disc i xarxa. A diferència de les auditories (que registren *qui* ha fet *què*), la monitorització ens diu *com* es troba el sistema en cada moment i permet detectar problemes de rendiment, colls d'ampolla i processos que consumeixen massa recursos.

Windows Server ofereix dues eines principals per a aquesta tasca:

| Eina | Accés | Nivell de detall |
|------|-------|-----------------|
| **Administrador de tasques** | `Ctrl + Shift + Esc` | Visió general ràpida |
| **Monitor de recursos** | `resmon` o des de l'Administrador de tasques | Anàlisi detallada per procés |

---

## Pràctica: Monitorització pas a pas

### Pas 1. Obrir l'Administrador de tasques i revisar els processos

Premem **Ctrl + Shift + Esc** per obrir l'**Administrador de tasques**. A la pestanya **Procesos** podem veure tots els processos actius del sistema agrupats per categoria:

- **Aplicaciones (2):** `Administrador de tareas` (17,3 MB) i `Server Manager` (70,1 MB)
- **Procesos en segundo plano (35):** serveis del sistema operatiu com `AggregatorHost.exe`, `AntiMalware Definition Update`, `Experiencia de entrada de Windows`, etc.

En el moment de la captura, el sistema presenta un **ús de CPU de l'1%** i un **consum de memòria del 48%**. Això indica que el servidor té una càrrega baixa-moderada. El procés `Server Manager` és el que consumeix més memòria entre les aplicacions obertes (70,1 MB).

<img width="551" height="853" alt="image" src="https://github.com/user-attachments/assets/48ac43ad-1d89-407a-8e00-ebb24503380f" />

---

### Pas 2. Monitoritzar la CPU

Anem a la pestanya **Rendimiento → CPU**. El gràfic mostra l'evolució de l'ús del processador en els darrers 60 segons.

Dades observades:
- **Processador:** AMD Ryzen 7 5800X 8-Core Processor
- **Ús actual:** 2%
- **Velocitat:** 3,80 GHz
- **Processos actius:** 108
- **Subprocessos (fils):** 1054
- **Identificadors:** 45928
- **Temps d'activitat:** 0:00:05:38
- **Processadors virtuals:** 4 (màquina virtual: Sí)

La CPU mostra el percentatge d'ús del processador. El gràfic amb pics indica que el sistema ha tingut moments de càrrega alta però en el moment actual es troba en un ús baix (2%). Si un procés utilitza molta CPU durant molt de temps, pot indicar una sobrecàrrega o un problema en el sistema.

<img width="1151" height="649" alt="image" src="https://github.com/user-attachments/assets/f3cb782f-fddf-489d-a825-b1fd2ffb24b2" />

---

### Pas 3. Monitoritzar la memòria RAM

Anem a **Rendimiento → Memoria**. El gràfic mostra l'ús de la memòria en el temps.

Dades observades:
- **Memòria total instal·lada:** 4,0 GB
- **En ús (comprimida):** 1,6 GB (42%)
- **Disponible:** 2,3 GB
- **Confirmada:** 1,7 / 4,7 GB
- **En caché:** 885 MB
- **Bloque paginado:** 87,3 MB
- **Bloque no paginado:** 101 MB

La memòria RAM indica quanta memòria està utilitzant el sistema i quanta queda disponible. En aquest cas, el 42% d'ús (1,7 GB de 4 GB) és un valor acceptable. La memòria en caché (885 MB) indica que Windows reserva una bona part per accelerar l'accés a dades freqüentment usades. Si la memòria disponible fos molt baixa, el sistema hauria de recórrer al fitxer de paginació al disc, cosa que reduiria significativament el rendiment.

<img width="1146" height="625" alt="image" src="https://github.com/user-attachments/assets/2d15f7ad-a639-4394-88cf-20f1aa9489bc" />

---

### Pas 4. Monitoritzar la xarxa

Anem a **Rendimiento → Ethernet**. El gràfic mostra el rendiment de la connexió de xarxa en temps real.

Dades observades:
- **Adaptador:** Intel(R) PRO/1000 MT Desktop Adapter
- **Enviament:** 80,0 Kbps
- **Recepció:** 9,2 Mbps
- **Velocitat màxima:** 11 Mbps
- **Direcció IPv4:** 10.0.2.17
- **Direcció IPv6:** fe80::81c9:f99a:5180:5eea%9
- **Tipus de connexió:** Ethernet

La xarxa mostra les dades enviades i rebudes pel servidor. S'observa que la recepció (9,2 Mbps) és molt superior a l'enviament (80 Kbps), cosa típica en un servidor que descarrega actualitzacions o rep dades de clients. El pic en el gràfic indica un moment de trànsit intens. Amb aquesta informació es pot detectar si alguna aplicació fa un ús excessiu de la connexió.

<img width="752" height="454" alt="image" src="https://github.com/user-attachments/assets/57b8cf40-f1f2-435f-86ed-9ee6cde1e3a7" />

---

### Pas 5. Obrir el Monitor de recursos

Des de l'Administrador de tasques, fem clic a **Abrir el Monitor de recursos** (a la part inferior de la pestanya Rendimiento), o premem **Windows + R** i escrivim `resmon`. El Monitor de recursos ofereix una visió molt més detallada que l'Administrador de tasques, amb informació per procés, PID, serveis associats i activitat de disc i xarxa.

---

### Pas 6. Revisar la CPU al Monitor de recursos

Dins del **Monitor de recursos**, anem a la pestanya **CPU**. Veiem dues seccions:

**Processos** (Ús de CPU: 3%):
- `svchost.exe` — PID 1400, 14 subprocessos, 0.00% CPU
- `perfmon.exe` — PID 1940, monitor de rendiment actiu, **3,48% CPU**
- `SearchApp.exe` — suspès (0% CPU)

El Monitor de recursos permet veure quins serveis concrets estan associats a cada procés `svchost.exe`, cosa que no és possible amb l'Administrador de tasques. En aquest cas, queda clar que **Windows Update** és el responsable del consum elevat de CPU.

<img width="1138" height="548" alt="image" src="https://github.com/user-attachments/assets/6fb3e637-11f6-4f32-b06a-607c6fa30d0b" />

---

### Pas 7. Revisar la memòria al Monitor de recursos

Anem a la pestanya **Memoria** del Monitor de recursos.

**Processos per consum de RAM (Privada):**
- `MsMpEng.exe` (Windows Defender) — 71.324 KB assignats, 55.168 KB privada
- `dns.exe` (servei DNS) — 250.968 KB assignats, **235.168 KB privada**
- `lsass.exe` (autenticació) — 57.564 KB assignats, 34.032 KB privada
- `dwm.exe` (gestor finestres) — 26.848 KB assignats, 22.812 KB privada

**Resum de memòria física:**
- **Total instal·lada:** 4.0 MB
- **En ús:** 1.701 MB
- **Disponible:** 2357 MB
- **En caché:** 1257 MB
- **En espera:** 1220 MB | **Lliure:** 1137 GB

El procés que més memòria privada consumeix és `dns.exe` (servei DNS).

<img width="1138" height="538" alt="image" src="https://github.com/user-attachments/assets/d322324a-b16a-4388-a47d-18df307a84e8" />

---

### Pas 8. Revisar el disc al Monitor de recursos

Anem a la pestanya **Disco** del Monitor de recursos.

**Processos amb activitat de disc:**
- `System` — PID 4, Lectura: 0 B/s, Escriptura: 4865 B/s
- `perfmon.exe` — PID 1940, Lectura: **6554 B/s**, Escriptura: **0 B/s**, Total: 6554 B/s  (monitorització activa)
- `svchost.exe (LocalSystemNet...)` — PID 6700, Lectura: 273 B/s
- `lsass.exe` — PID 702, Lectura 496 B/s

**Activitat de disc global:** 0 B/s | 0% de temps actiu

L'apartat de disc permet veure si algun procés està llegint o escrivint moltes dades. En aquest cas, el procés `perfmon.exe` és el que més escriu (486 KB/s), probablement per operacions del sistema de fitxers i la memòria virtual. El temps de resposta de 4,72 ms és acceptable per a un disc virtual.

<img width="1138" height="402" alt="image" src="https://github.com/user-attachments/assets/2ec5e71f-e602-47a3-8d47-d8b952bf08ce" />

---

### Pas 9. Revisar la xarxa al Monitor de recursos

Anem a la pestanya **Red** del Monitor de recursos. Aquesta és la vista més completa de l'activitat de xarxa.

**Processos amb activitat de xarxa:**
- `svchost.exe (NetworkService...)` — PID 1160, Recepció: **117 B/s**
- `lsass.exe` — PID 704, 24 B/s enviat, 44 B/s rebut (autenticació AD)
- `Microsoft.ActiveDirectory.W...` — PID 2984, trànsit bidireccional
- `dns.exe` — PID 2844, 1 B/s enviat, 2 B/s rebut

**Activitat de xarxa global:** E/S de xarxa: 0 Mbps | 0% de percentatge d'ús

**Connexions TCP actives:**
- `lsass.exe` (PID 704) — múltiples connexions cap a `fe80:b452:4fc4:2e81:` (actualitzacions de Windows)

<img width="1138" height="549" alt="image" src="https://github.com/user-attachments/assets/36631e4a-b4e1-453b-9996-c7f24730d241" />

---

### Pas 10. Ports d'escolta al servidor

A la secció inferior de la pestanya **Red** del Monitor de recursos, veiem els **Puertos de escucha**, que indiquen quins ports té oberts el servidor esperant connexions entrants:

- `dns.exe` (PID 2844) — Port **53** TCP i UDP per IPv4 i IPv6 (servei DNS)
- `lsass.exe` (PID 704) — Port **88** TCP (Kerberos, autenticació del domini)

Aquests ports oberts corresponen als serveis normals d'un controlador de domini Active Directory. El port 53 és el DNS i el port 88 és Kerberos. En un anàlisi de seguretat, aquesta llista permet detectar ports oberts inesperats que podrien indicar programari maliciós o configuració incorrecta.

<img width="914" height="224" alt="image" src="https://github.com/user-attachments/assets/a18519a2-5fcd-4f3f-aa5e-2a6c8f7a49ef" />

---

## Reflexió de la monitorització

Amb aquesta pràctica hem après a utilitzar l'**Administrador de tasques** i el **Monitor de recursos** de Windows per analitzar el consum de CPU, memòria RAM, disc i xarxa. Aquestes eines són imprescindibles per a qualsevol administrador de sistemes.

### Resum de l'estat del sistema observat

| Recurs | Eina | Valor observat | Valoració |
|--------|------|----------------|-----------|
| CPU | Administrador de tasques | 9% (Intel i7-10700) | Baix |
| Memòria RAM | Administrador de tasques | 1,6 / 4,0 GB (40%) | Acceptable |
| Xarxa (Ethernet) | Administrador de tasques | R: 9,2 Mbps / E: 80 Kbps | Descàrrega activa |
| CPU (detall) | Monitor de recursos | 35%, wuauserv 9,63% | Windows Update actiu |
| Memòria (detall) | Monitor de recursos | 37%, MsMpEng 161 MB | Acceptable |
| Disc | Monitor de recursos | System 939 KB/s, 5% actiu | Normal |
| Xarxa (detall) | Monitor de recursos | svchost 1,1 MB/s rebut | Actualitzacions |
| Ports oberts | Monitor de recursos | 53 (DNS), 88 (Kerberos) | Normals per AD |
