# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor
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

## Rotació de logs

Els logs poden créixer molt amb el temps.
Per evitar que ocupin massa espai, Linux utilitza logrotate, que permet:

- Comprimir logs antics

- Eliminar logs vells

- Crear nous fitxers de log

Els fitxers de configuració de rotació es troben a **/etc/logrotate.d/**.

Per veure els fitxers disponibles: **ls /etc/logrotate.d/**.

Cada fitxer defineix com es gestionen els logs d’un servei concret.

## Exemple de configuració de rotació


