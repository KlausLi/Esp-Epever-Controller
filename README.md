<img src="Tracer10420an.png" alt="Soyosource Controller by BavarianSuperGuy"/>

# EspEpeverController mit Webseite
Der Esp8266 ist über ein Rs485 Modul mit dem Epever Solar Laderegler verbunden und kann diesen die verfügbaren Daten auslesen bzw. auch das LoadReails des Tracer ein und ausschalten. 

Kurzum die Firmware die es hier zum Download gibt stellt ein Montitoring über Web bereit.

Die Firmware(firmware_vX.X.X.X.bin") ist im Verzeichnis espflasher.
Diese kann unkompliziert auf einen 4Mbyte Esp mit dem im Verzeichnis enhaltenen
Tool "FlashESP8266.exe" geflasht werden. 
Dieses Tool FlashESP8266.exe ist nicht von mir , aber hat schon hevorragende Dienste geleistet.

<img src="WebSeite-Epever Controller.png" alt="Soyosource Controller by BavarianSuperGuy"/>

Was kann der ESP8266 Epever Controller :



- Die blinkende Überschrift in der Webseite ist ein Alive zeichen , solange die Überschrift "ESP Herzschlag" blinkt , ist alles gut
- Es kann das Relais im Tracer für Load aus und eingeschalten werden.
- Anzeige aller verfügbaren Daten des Tracer in der Webseite
- Übermittlung per Mqtt aller verfügbaren Tracer Daten als Json Array  (Topic steht in der Webseite)
- Übermittlung per Webinterface  aller verfügbaren Tracer Daten als Json Array (Url steht in der Webseite)
- Doppelreset implementierung um wieder ins Configportal im eigenen Esp AP zu kommen
- ElegantOta Implementierung für FirmwareUpdates
- ...



<img src="Tracer_Rj45_Rs485.png" alt="Soyosource Controller by BavarianSuperGuy"/>

RS485 ttl Adapter (2 verschiedene getestet)
- rs485 adapter A an A von Epever Rj45(Pin5) anschliessen und Rs485 B an  Epever Rj45 B (Pin4)

<img src="rs485.png" alt="Soyosource Controller by BavarianSuperGuy"/>
- Beim "DI DE RE RO" Rs485 Modul
werden die mittleren Rs485 Pins "DE RE" auf einen Pin gebrückt an Esp GPIO0 angeschlossen.
Dann Rs485 "DI" auf Esp TX  und Rs485 "RO" auf Esp RX 

<img src="rs485_2 .png" alt="Soyosource Controller by BavarianSuperGuy"/>
- Beim RX TX Rs485 Modul
wird der Rs485 TX mit Esp TX verbunden und Rs485 RX mit Esp RX verbunden , also nicht kreuzen!

!Vcc ist bei beiden Modulen 3.3volt!

Keinen USB/TTL Adapter als 3,3v Poduktiv Stromquelle verwenden, für erstflashen is es OK!


ESP:

EINRICHTUNG##############################################################################################
- 0.Bei Nutzung von Mqtt: Mqtt.fx Client öffnen mit Broker verbinden und Topic : 'Soyosource/#' abonnieren
- 0.1 Es kommt nach Schritt 8. ein Info Publish vom Esp mit der IP adresse.
- 0.2 Man kann die Ip Adresse nat. auch auf dem herkömmlichen Weg herausfinden
- 1.Firmware auf den gelöschten Esp8266 flashen
- 2.Esp Neustart
- 3.Im Wlan nach EPEVER_... suchen
- 4.Wlan mit Pwd 12345678 verbinden
- 5.Es öffnet sich automatisch Browser Fenster mit 192.168.4.1
- 6.Unter Configuration
- 6.1 Wifi auswählen oder eingeben und Passwort eingeben
- 6.2 Mqtt kann derzeit nur ohne ssl und ohne Benutzer/Passwort benutzt werden
- 7.Speichern mit dem Button ganz unten
- 8.Esp Neustart
- 9.Ipadresse in Mqtt Client oder Router ausfindig machen
EINRICHTUNG#############################################################################################

INBETRIEBNAHME##########################################################################################
- 1.Ipaddresse im browser aufrufen

INBETRIEBNAHME##########################################################################################

Tip:
- Die Webschnittstelle für die Tracer Daten nur max alle 1-2 sekunden aufrufen

Falls Ihr mich unterstützen wollt, Spenden sind herzlich willkommen und würde mich sehr freuen :-)
Hier bitte - https://paypal.me/armerprogrammer
