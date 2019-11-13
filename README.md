# IoT Playground – EclipseCon Europe 2019

## Things Network gateway

First register the gateway and set credentials:

    hat device create ttn-gateway
    hat cred set-password ttn-gateway gateway <password>

## Thing Network integration

<dl>

<dt>Type</dt><dd>HTTP</dd>

<dt>URL</dt>

<dd>

    https://iot-lorawan-adapter-enmasse-infra.apps.<my.cluster>/ttn

</dd>

<dt>Authentication header:</dt>

<dd>

    echo "Basic $(echo -n "gateway@<k8s-ns>.iot:<password>" | base64 -w0)"

</dd>

</dl>

## Provision a new device

    hat device create <device-eui> '{"via":["ttn-gateway"]}'

e.g.:

    hat device create 0123456789ABCDEF '{"via":["ttn-gateway"]}'
