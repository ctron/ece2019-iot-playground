# IoT Playground – EclipseCon Europe 2019

## Things Network gateway

    hat device create thing-gateway
    hat cred set-password thing-gateway gateway <password>

## Thing Network integration

Type: HTTP

URL:

    https://iot-lorawan-adapter-enmasse-infra.apps.<my.cluster>/ttn

Authentication header:

    echo "Basic $(echo -n "gateway@ece2019.iot:<password>" | base64 -w0)"

## Provision a new device

    hat device create <device-eui> '{"via":["thing-gateway"]}'
    hat device update <device-eui> '{"via":["thing-gateway"]}' # need to fix bug!
