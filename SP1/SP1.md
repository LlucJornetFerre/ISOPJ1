---
layout: default
title: "Sprint 1: Instal·lació i configuració inicial"
---

# Virtualització i instal·lació del SO Ubuntu
Documentat - Crear una màquina virtual Ubuntu amb els requisits mínims i fer captura per a mostrar-los (emmagatzematge 80GB, 40GB destinats a Ubuntu, la resta lliure). Particionar els 40GB en arrel, opcionalment, boot i home i swap. Fer recerca per a determinar, basant-me en les característiques de la màquina, si és necessari crear la partició swap, i documentar. Clonar màquina una vegada estigui tot fet. Triar i justificar un adapatador de xarxa per a la màquina virtual.

## Creació de la màquina virtual

Primer, obrim VirtualBox, i creem una nova màquina virtual.
<img width="135" height="104" alt="image" src="https://github.com/user-attachments/assets/c085511f-302c-47a2-8f55-b4cc9630e0e0" />

A la primera pantalla, triem un nom per a la màquina virtual, i busquem la ISO d'Ubuntu a l'ordinador.
<img width="712" height="385" alt="image" src="https://github.com/user-attachments/assets/367dc753-d4ff-4206-a3c2-85e28749f63f" />

A continuació, podem crear el nostre usuari i el nom de la màquina.
<img width="712" height="293" alt="image" src="https://github.com/user-attachments/assets/9cf80447-7127-45d2-8a62-865c4932dd80" />

Tot seguit, toca assignar una quantitat de RAM a la màquina virtual. Per a determinar la quantitat adequada, podem consultar els requisits mínims per al nostre sistema operatiu a la pàgina principal d'aquest. https://ubuntu.com/download/desktop

<img width="528" height="331" alt="image" src="https://github.com/user-attachments/assets/13c46994-79e8-499a-9495-262a12fd34d6" />

Posarem 4GB, ja que és el mínim recomanat, i 4 cores per a la CPU.

<img width="714" height="213" alt="image" src="https://github.com/user-attachments/assets/68428e0f-a9b3-48e0-a3c9-34265087d52a" />

Ara, hem de crear el disc. Aquest serà de 80GB.
<img width="714" height="315" alt="image" src="https://github.com/user-attachments/assets/f4e3e869-080a-415e-aa61-e713b65bcd9b" />

Finalment, revisem que totes les dades del resum de la màquina son correctes, i la creem.
<img width="706" height="383" alt="image" src="https://github.com/user-attachments/assets/57fc8161-7131-46e1-a365-19e2b3e34c52" />

Abans d'acabar la configuració de la màquina, cal seleccionar un adaptador de xarxa per a aquesta. Ho farem seleccionant la màquina virtual, i clicant sobre la rodeta de configuració. Després, anirem a la secció de Xarxa/Network.
<img width="796" height="458" alt="image" src="https://github.com/user-attachments/assets/336fde30-5ff4-41d1-b326-f61a1eb320ae" />

En el meu cas, he decidit triar adaptador pont. Amb aquest adaptador, simulem que la màquina virtual és un altre ordinador de l'aula, i rep una adreça IP privada del mateix rang que la màquina real, per a poder passar fitxers entre les dues, i també dona accés a internet.
<img width="625" height="205" alt="image" src="https://github.com/user-attachments/assets/6ffcc0eb-179c-40bd-a4d0-c875ce75d74e" />


## Configuració del sistema operatiu Ubuntu

Amb la màquina creada, toca 

## Llicenciament
Crear una llicència per al github.

Expicar la llicència del sistema operatiu Ubuntu que fem servir (GNU, robusta).

## Gestors d'arrencada per a instal·lacions DUALS


## Punts de restauració 


## Comandes generals i instal·lació
