# Heise Desinfec't 2016 -- Docker Edition

## Was ist Desinfec't?

> Das beliebte Sicherheits-Tool der c't hat nun neben den Viren-Scannern von Avira, ClamAV und Kaspersky erstmals Eset NOD32 mit an Bord. Zudem kann man jetzt unter gewissen Voraussetzungen einen Desinfec't-Stick ohne DVD-Laufwerk bauen. 

http://www.heise.de/security/meldung/Komfortabel-Viren-jagen-Desinfec-t-2016-ist-da-3220381.html

## Docker

Diese Skriptsammlung extrahiert die Virenscanner aus dem ISO und erzeugt daraus einzelne Docker-Images.

Zunächst gilt es, die Virenscanner zu extrahieren. Starte als *root*:

`./desinfect-extract ct_desinfect_2016.iso`

### Kaspersky

Build the image:
::
	cd docker-av-kaspersky
	docker build -t av-kaspersky .

Get help:
::
	docker run -i -t av-kaspersky /kav HELP SCAN

Update the signatures:
::
	docker run --name av-kaspersky-update -i -t av-kaspersky /kav update
	docker commit av-kaspersky-update av-kaspersky
	docker rm av-kaspersky-update

Scan a directory:
::
	docker run -v /directory/to/scan:/data:ro -t av-kaspersky /kav scan /data -i0

### Avira

Build the image:
::
	cd docker-av-avira
	docker build -t av-avira .

Get help:
::
	docker run -i -t av-avira /AntiVir/scancl --help

Update the signatures:
::
	docker run --name av-avira-update -i -t av-avira /avupdate
	docker commit av-avira-update av-avira
	docker rm av-avira-update

Scan a directory:
	docker run -v /directory/to/scan:/data:ro -t av-avira /AntiVir/scancl --defaultaction=ignore --suspiciousaction=ignore /data
