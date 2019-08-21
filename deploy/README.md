# Deployment

All directories can be applied with `oc apply -f`, e.g. `oc apply -f 020-IoT`.

However, some files need to be adapted first, like assigning proper passwords. See
the next sections for specific instructions on each component. Each file which needs
modifications has the suffix `.in`. It is required that you copy/rename the file, and
adapt it **before** applying. This should ensure that you do not, by accident, deploy
weak passwords.

## Telemetry bridge

Edit the file `030-ConfigMap.yaml`, exchange the `amqp.host` with the value from
the current address space.

    oc get addressspace iot -o yaml

Look for the `serverHost` field, where the `name` field is `messaging`, e.g. `messaging-32yssrfm3l.enmasse-infra.svc`.

## InfluxDB

Edit the `030-Secret.yaml` to add proper passwords.
