# Fase 1 - Instal·lació del sistema operatiu
## Pas 1 - Crear màquina virtual amb VirtualBox

<img width="779" height="231" alt="image" src="https://github.com/user-attachments/assets/67b0b6ea-d3e2-4413-a398-12f68a264823" />

## Pas 2 - Assignar recursos (RAM mínima 4 GB, disc mínim 40 GB)

<img width="779" height="456" alt="image" src="https://github.com/user-attachments/assets/d2864c7c-2c80-4d37-b5b4-1581570bc8e2" />

<img width="779" height="228" alt="image" src="https://github.com/user-attachments/assets/59780f32-e0ed-4788-a164-8d825e8f0e2c" />

<img width="779" height="342" alt="image" src="https://github.com/user-attachments/assets/5b2b0d1b-0c5a-404e-9fc2-b72bd212b832" />

## Pas 3 - Carregar la ISO de Windows 11

<img width="779" height="265" alt="image" src="https://github.com/user-attachments/assets/fb079977-46a0-4ae5-847f-fc641f198582" />

## Pas 4 - Instal·lar el sistema (idioma, usuari, contrasenya)

<img width="609" height="458" alt="image" src="https://github.com/user-attachments/assets/18172cb8-6892-467e-9fcc-0f4b1cbb71eb" />

## Pas 5 - Comprovar que arrenca correctament

<img width="1115" height="976" alt="image" src="https://github.com/user-attachments/assets/eb287ebd-7821-4bcc-87cd-af7371039f76" />

# Fase 2 - Punts de restauració
## Pas 6 – Cercar “Crear un punt de restauració”

<img width="768" height="297" alt="image" src="https://github.com/user-attachments/assets/7f4fff4f-30c7-453e-9b91-7224615634a6" />

## Pas 7 - Activar la protecció del sistema al disc C:

<img width="407" height="486" alt="image" src="https://github.com/user-attachments/assets/b25b58b5-cdc2-46a1-8878-1e307d3b83ae" /><img width="453" height="516" alt="image" src="https://github.com/user-attachments/assets/9701f393-afdb-41b5-bdc6-df738e54281f" />

## Pas 8 - Crear un punt manual

<img width="405" height="486" alt="image" src="https://github.com/user-attachments/assets/5a139142-6d00-4362-8bdb-0f5b743564bc" />

<img width="405" height="486" alt="image" src="https://github.com/user-attachments/assets/59861a95-e9c8-40ef-81f8-dcd6d7c3df21" />

<img width="271" height="83" alt="image" src="https://github.com/user-attachments/assets/468c8ccc-b21b-4b0c-a92e-361bded74c6a" />

<img width="349" height="118" alt="image" src="https://github.com/user-attachments/assets/e12ce32a-8a8e-4e58-aa53-914fc67e75ec" />

## Pas 9 - Fer un canvi (instal·lar app o configuració)

<img width="1024" height="767" alt="image" src="https://github.com/user-attachments/assets/3c32c45a-b340-45b4-a612-3f5153312f69" />

## Pas 10 - Restaurar i comprovar

<img width="408" height="484" alt="image" src="https://github.com/user-attachments/assets/d4fa536d-4568-467c-baad-f3f6e6537590" />

<img width="559" height="464" alt="image" src="https://github.com/user-attachments/assets/11cc35b4-d0ff-41ea-88cc-5f1839d45c1a" />

<img width="559" height="464" alt="image" src="https://github.com/user-attachments/assets/805a3bb4-4a7c-4aae-be0d-03d4e98e05d2" />

<img width="559" height="464" alt="image" src="https://github.com/user-attachments/assets/54c39d16-5d95-4539-8f77-420b250a80e7" />

<img width="732" height="465" alt="image" src="https://github.com/user-attachments/assets/8258cac2-d83f-4cd2-be0a-e174d86112b4" />

# Fase 3 - Llicències de Windows
## Pas 11 - Obrir Configuració → Sistema → Activació

<img width="316" height="694" alt="image" src="https://github.com/user-attachments/assets/55231260-d5fb-4164-8cb1-c2ab27e3a713" />

## Pas 12 - Veure si Windows està activat

<img width="812" height="680" alt="image" src="https://github.com/user-attachments/assets/71006d16-e1d8-4533-ada8-1355009acd81" />

## Pas 13 - Executar al cmd: slmgr /xpr

<img width="658" height="472" alt="image" src="https://github.com/user-attachments/assets/99b263c7-5b8b-47b8-a80f-5a1a7a03f101" />

## Pas 14 - Esbrinar llicenciament Windows i explicar breument

**Retail (FPP)**	Llicència comercial que es compra a part. És de l'usuari i no de l'ordinador.
**OEM**	Instal·lada per defecte en equips nous. Es vincula de manera permanent a la placa base d'aquell PC.
**Volum**	Dissenyada per a empreses i institucions. Permet activar múltiples dispositius a la vegada.
**Digital**	Llicència enllaçada al maquinari **i** al correu de Microsoft, és el substitut de la clau tradicional.
**Subscripció**: Pagament indefinit (mensual, o anual, com ara Windows 365), utilitzada principalment al núvol.

## Pas 15 - Concultar preu aproximat d'una llicència Windows (web oficial o botigues)

**Windows 11 Home**	145 €
**Windows 11 Pro**	259 €

# Fase 4 - Gestor d'arrencada
## Pas 16 - Obrir Command Prompt com administrador

<img width="812" height="733" alt="image" src="https://github.com/user-attachments/assets/ca455935-a19e-4419-b54d-8911cd69b699" />

## Pas 17 - Executar bcdedit

<img width="529" height="591" alt="image" src="https://github.com/user-attachments/assets/824badbe-5d4e-4e80-a715-2c7aec3a4837" />

## Pas 18 - Identificar els blocs
### Administrador de arranque de Windows (Boot Manager)

<img width="503" height="232" alt="image" src="https://github.com/user-attachments/assets/f2e83f28-5582-4b4c-808c-962201f37728" />

### Cargador de arranque de Windows (Boot Loader)

<img width="504" height="274" alt="image" src="https://github.com/user-attachments/assets/ef84e714-38d6-4c08-88a3-a5e1a7a9d349" />

## Pas 19 - Interpretar dades concretes

Boot Manager
default: {current} -> El sistema que es tria per defecte per a arrencar.
timeout: 30 -> Els segons que tarda abans d'arrencar automàticament.

Boot Loader
device: partition=C: -> partició del disc on està instal·lat el sistema operatiu (Windows).
path: \WINDOWS\system32\winload.efi -> Fitxer que carrega el sistema.
description: Windows 11 -> Nom del sistema operatiu.

## Pas 20 - Respostes a les preguntes curtes
Quin sistema s'està arrencant? S'arrenca Windows 10 (es veu al paràmetre description del Cargador de arranque).

A quin disc o partició està instal·lat? Es troba a la partició C: (es veu al paràmetre device del Cargador de arranque).

Quant temps espera abans d'arrencar? S'espera 30 segons (es veu al paràmetre timeout de l'Administrador de arranque).

Quin fitxer inicia Windows? L'inicia el fitxer \WINDOWS\system32\winload.efi (es veu al paràmetre path del Cargador de arranque).

## Pas 21 - Interpretació final
Qui decideix l'arrencada (Boot Manager): És el gestor principal que llegeix la configuració inicial i decideix quin sistema operatiu s'ha d'executar, basant-se en l'opció per defecte i el temps d'espera.

Qui carrega el sistema (Boot Loader): És el programa específic (com winload.efi) que rep l'ordre del Boot Manager i s'encarrega de carregar físicament el nucli de Windows des del disc dur a la memòria RAM per iniciar-lo.

# Fase 5 - Xarxa bàsica
## Pas 22 - Obrir configuració de xarxa

<img width="1019" height="728" alt="image" src="https://github.com/user-attachments/assets/8b0fd242-708f-4243-954e-eb0a8fc61046" />

## Pas 23 - Consultar IP amb: ipconfig

<img width="978" height="512" alt="image" src="https://github.com/user-attachments/assets/76930112-c545-4954-8cc4-5eed60af3505" />

## Pas 24 - Configurar IP dinàmica (DHCP automàtic)

<img width="1013" height="715" alt="image" src="https://github.com/user-attachments/assets/3741875c-d817-4da6-a7ed-0de90807ce66" />

<img width="375" height="111" alt="image" src="https://github.com/user-attachments/assets/1b22ccd5-d875-4b07-843e-97a390b56730" />

## Pas 25 - Configurar IP fixa (manual: IP, màscara, gateway, DNS)

<img width="391" height="185" alt="image" src="https://github.com/user-attachments/assets/e15b6307-1c52-454f-a83e-98fbe25147af" />

<img width="385" height="718" alt="image" src="https://github.com/user-attachments/assets/405090be-4cdb-4084-998c-bbc6292d4a89" />

<img width="348" height="216" alt="image" src="https://github.com/user-attachments/assets/abbc2e35-21d5-4836-b923-5de14244e99d" />

# Pas 26 - Comprovar connexió amb: ping google.com
# Pas 27 - Obrir PowerShell

<img width="761" height="676" alt="image" src="https://github.com/user-attachments/assets/75e9ea0b-96c6-49b0-902a-7fbaf9d4fc37" />

## Pas 28 - Diferenciar cmd i PowerShell
### Detalls de l'arrencada
**BCD (Boot Configuration Data):** És l'arxiu d'on el Boot Manager llegeix la configuració d'arrencada.
**Kernel:** El Boot Loader (winload.efi) és qui agafa el nucli de Windows (ntoskrnl.exe) i els controladors bàsics i els carrega a la memòria RAM.

### Diferències clau: cmd vs. PowerShell
| Característica | cmd (Símbol del sistema) | Windows PowerShell |
|----------------|--------------------------|--------------------|
| Dades | Treballa amb text pla. | Treballa amb objectes (.NET). |
| Comandes | Bàsiques i heretades de DOS (dir, ping). | Utilitza Cmdlets amb format Verb-Nom (Get-Process). |
| Ús principal | Comprovacions ràpides de xarxa o sistema. | Automatització de tasques i scripts per a administradors. |









