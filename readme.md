# "voltronic_addon" je Addon do HA.

### Zdroj:
    - https://github.com/lavron/docker-voltronic-mqtt
    - Supports protocols PI30 and PI41 devices.

### Poznámka:
    - "config.yaml" a "run.sh" by měly mít oddělovače řádků LF
    - Nastavit cestu k sériovému portu.
    - V "config.yaml" je potřeba nastavit správnou cestu k Docker obrazu. Koncovka označuje architekturu procesoru, na kterém je Docker runtime spuštěn.

### Docker obraz:
`    docker.io/ondrejva/voltronic-mqtt:0.0.1-x64`  
`    docker.io/ondrejva/voltronic-mqtt:0.0.1-arm32v7`  
`    docker.io/ondrejva/voltronic-mqtt:0.0.1-arm64v8`  

    Vytvořil jsem ještě variantu "-test", kde má sice parametr pro sériovou linku, ale nepoužije ji, nečte data z měniče, ale obsahuje nasnímané vzorky zpráv. Vrací tedy stále dokola stejné, neměnné hodnoty. Mělo by to sloužit k přípravě aplikace v HA, než odjedeš na stavbu.


`   docker.io/ondrejva/voltronic-mqtt-test:0.0.1-x64`  
`   docker.io/ondrejva/voltronic-mqtt-test:0.0.1-arm32v7`  
`   docker.io/ondrejva/voltronic-mqtt-test:0.0.1-arm64v8`  


