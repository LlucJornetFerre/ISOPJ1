# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor

Lluc i Ivan

## Directoris importants

En sistemes Linux hi ha diversos directoris que contenen informació essencial sobre el funcionament del sistema.
Un dels més importants és /var/log, on es guarden els registres (logs) del sistema i dels serveis.

Aquests registres permeten:

- Diagnosticar errors.

- Monitoritzar serveis.

- Auditar l’activitat del sistema.

Per consultar aquest directori podem executar **ls /var/log**.

<img width="772" height="839" alt="image" src="https://github.com/user-attachments/assets/c034e282-2b89-42c5-932c-68f11fea3367" />

Aquesta comanda mostra els fitxers de log disponibles.

## Logs

Els logs del sistema són fitxers que registren esdeveniments del sistema operatiu i dels serveis.

Normalment es troben al directori: **/var/log**.

Per veure el contingut d’aquest directori: **cd /var/log** i **ls**.

Cada servei pot tenir el seu propi fitxer de registre.

## Consultar el fitxer syslog

El fitxer syslog conté informació general del sistema, com:

- Errors

- Missatges del kernel

- Activitat de serveis

Per veure el contingut del syslog podem executar **cat /var/log/syslog**

<img width="1920" height="863" alt="image" src="https://github.com/user-attachments/assets/c0b7975c-b44b-45bd-833e-011c309c4072" />

## Rotació de logs

Els logs poden créixer molt amb el temps.
Per evitar que ocupin massa espai, Linux utilitza logrotate, que permet:

- Comprimir logs antics

- Eliminar logs vells

- Crear nous fitxers de log

Els fitxers de configuració de rotació es troben a **/etc/logrotate.d/**.

Per veure els fitxers disponibles: **ls /etc/logrotate.d/**.

<img width="1617" height="71" alt="image" src="https://github.com/user-attachments/assets/037a504f-4341-4c9b-8344-456dbb3d6549" />

Cada fitxer defineix com es gestionen els logs d’un servei concret.

## Exemple de configuració de rotació

Podem veure la configuració d’un servei amb **cat /etc/logrotate.d/rsyslog**.

<img width="546" height="421" alt="image" src="https://github.com/user-attachments/assets/f9a90c12-413a-4280-9753-4532324b3c63" />

Aquest fitxer defineix:

- cada quant es roten els logs

- quants fitxers es conserven

- si es comprimeixen o no

## Modificar la configuració de logrotate

Per editar un fitxer de configuració **sudo nano /etc/logrotate.d/rsyslog**.

foto

Aquí podem modificar opcions com:

rotate 7
daily
compress
missingok

<img width="474" height="404" alt="image" src="https://github.com/user-attachments/assets/264f44f7-7497-4112-af41-81a9e4a4340b" />

Per a aplicar els canvis fets, executem la comanda: **systemctl restartsyslog**.

<img width="557" height="55" alt="image" src="https://github.com/user-attachments/assets/1869a991-228e-4b42-8dcc-f8e423a68708" />

## Enviament de logs a un altre servidor

Un exercici habitual és configurar **dues màquines Ubuntu** perquè:

- una màquina **envii els logs**

- l’altra **els rebi**

### Configurar el servidor de logs

Editar el fitxer de configuració: **sudo nano /etc/rsyslog.conf**.

I afegim:

**module(load="imudp")
input(type="imudp" port="514")**

<img width="1092" height="480" alt="image" src="https://github.com/user-attachments/assets/c8b25677-f91b-41a3-b45c-dffc9af847e8" />

Finalment, reiniciem el servei i comprovem l'estat.

**sudo systemctl restart rsyslog**

<img width="1435" height="529" alt="image" src="https://github.com/user-attachments/assets/bc40960a-9fff-4f3f-8b44-41bd707c91ee" />

Editar: **sudo nano /etc/rsyslog.conf**

I afegim ***.* @IP_SERVIDOR:514**

<img width="760" height="154" alt="image" src="https://github.com/user-attachments/assets/671dd98c-700c-43e3-b748-ca291cef0590" />

I reiniciem el sistema amb **systemctl restart syslog**.

<img width="1126" height="385" alt="image" src="https://github.com/user-attachments/assets/0bcc2b83-2fa9-425e-9ee4-c0f778b77ab5" />

## Comprovació de funcionament.

Creem un log manualment al client amb **logger "Missatge de prova"**.

<img width="426" height="34" alt="image" src="https://github.com/user-attachments/assets/646745d2-c839-4989-ada3-8f01130d6fe1" />

Ara, comprovem el contingut del fitxer **/var/log/syslog**.

**cat /var/log/syslog | grep Missatge**.

<img width="639" height="67" alt="image" src="https://github.com/user-attachments/assets/452c17d3-4ea8-4df4-96a1-a0f047b98af4" />



# Servidor d'actualitzacions

## Configuració del servidor

Un servidor d'actualitzacions és un servidor que es descarrega un repositori d'internet per a després servir-lo a clients de la xarxa, de manera que, en lloc de descarregar-lo d'internet, es connectin al servidor i el descarreguin d'allà. Es pot fer amb repositoris molt pesats.

(Captura) apt install apache2

(Captura) apt install apt-mirror

nano /etc/apt/mirror.list

Comentem tots els repositoris per defecte, i afegim el repositori que nosaltres volem.

<img width="1096" height="556" alt="image" src="https://github.com/user-attachments/assets/1bf00a88-5624-4c6e-86c4-b4928aede247" />

(captura) apt-mirror

<img width="1098" height="960" alt="image" src="https://github.com/user-attachments/assets/97cf0cba-c26b-4ff8-ae78-4163d9c9a3f4" />

Creem un enllaç simbòlic.

<img width="925" height="140" alt="image" src="https://github.com/user-attachments/assets/e1ec64a1-3985-40c0-b3c4-b7c9fa0cc536" />

## Configuració del client

(captura) ping IP del server

(captura) nano /etc/apt/sources.list

deb [arch=amd64] http://IP.DEL.SERVER/dl.google.com/linux/chrome/deb/ stable main

(captura) wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -

(captura) apt install google-chrome-stable

(captura de google chrome instal·lat al sistema) 


### Repetri l'activitat amb un altre paquet
