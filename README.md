# IoT Playground – EclipseCon Europe 2019

This repository contains the cloud side deployment we for the AMQ Online IoT
setup at EclipseCon Europe 2019.

![Overview](images/overview.svg "Overview")

**Note:** It is not possible to directly deploy the YAML files. Some of the files
          need to be updated with the proper passwords. File which need to be updated
          have the suffix `.in`. If you fill in the information, and rename them to `.yaml`,
          then you can simply do `oc apply -f deploy`.

## Things Network gateway

Register the gateway and set credentials:

    hat device create ttn-gateway
    hat cred set-password ttn-gateway gateway <password>

## Things Network integration

Create a new "integration" for your Things Network account:

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

Each sensor needs to be registered with Hono as well:

    hat device create <device-eui> '{"via":["ttn-gateway"]}'

e.g.:

    hat device create 0123456789ABCDEF '{"via":["ttn-gateway"]}'
