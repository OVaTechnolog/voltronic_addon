# "voltronic_addon" je addon do HA.

### Zdroj:
    - https://github.com/lavron/docker-voltronic-mqtt
    - Supports protocols PI30 and PI41 devices.

### Poznámka:
    - "config.yaml" a "run.sh" by měly mít oddělovače řádků LF
    - Nastavit cestu k sériovému portu.
    - V "config.yaml" je potřeba nastavit správnou cestu k Docker obrazu. Koncovka označuje architekturu procesoru, na kterém je Docker runtime spuštěn.
	- "config.yaml" / "startup" může nabývat hodnot "services" nebo "application"
	- "config.yaml" / "options" definuje výchozí hodnoty, které může uživatel změnit.
	- "config.yaml" / "schema" určuje typ proměnné.
	- "config.yaml" / "environment" mapuje proměnnou do prostředí Docker kontejneru.
	- Proměnné definované v "config.yaml" se dají měnit přes GUI Home Assistantu → Supervisor → Add-ons → Konfigurace.

### Docker obraz:
#### Tagy
`    docker.io/ondrejva/voltronic-mqtt:0.0.5-x64`  
`    docker.io/ondrejva/voltronic-mqtt:0.0.5-arm32v7`  
`    docker.io/ondrejva/voltronic-mqtt:0.0.5-arm64v8`  

    Vytvořil jsem ještě variantu "-test", kde má sice parametr pro sériovou linku, ale nepoužije ji, nečte data z měniče, ale obsahuje nasnímané vzorky zpráv. Vrací tedy stále dokola stejné, neměnné hodnoty. Mělo by to sloužit k přípravě aplikace v HA, než odjedeš na stavbu.


`   docker.io/ondrejva/voltronic-mqtt-test:0.0.5-x64`  
`   docker.io/ondrejva/voltronic-mqtt-test:0.0.5-arm32v7`  
`   docker.io/ondrejva/voltronic-mqtt-test:0.0.5-arm64v8`  

#### Proměnné prostředí
	SERIAL_PORT         priklad = /dev/ttyUSB0
	REPORT_INTERVAL_S   vychozi = 1 s

	MQTT_SERVER
	MQTT_USER
	MQTT_PASSWORD
	MQTT_PORT           vychozi = 1883
	MQTT_TOPIC_PREFIX   vychozi = homeassistant
	INVERTER_NAME       vychozi = inverter

	Neni ve zdrojaku Python, ale mozna ho bude potrebovat MQTT klient:
	MQTT_CLIENT_ID      priklad = voltronic-mqtt

#### Ruční spuštění
    docker run --rm --name voltronic-mqtt -v /dev:/dev -e SERIAL_PORT=/dev/ttyusb0 -e REPORT_INTERVAL_S=10 -e MQTT_SERVER=localhost -e MQTT_USER=user -e MQTT_PASSWORD=password -e MQTT_PORT=1883 -e MQTT_CLIENT_ID=voltronic-mqtt -e MQTT_TOPIC_PREFIX=homeassistant -e INVERTER_NAME=inverter docker.io/ondrejva/voltronic-mqtt:0.0.5-x64

#### Komunikace po sériové lince
    2400 Bd, timeout= 500 ms

