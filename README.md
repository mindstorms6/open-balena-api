# Open Balena API

## What is this?

This project is the open sourced Balena API - from the folks at balena.io

This version has minor modifications to run on AWS and use AWS Primitives over local docker containers.

Balena.io builds a platform to manage deployments to IoT devices, using containers as deployment mechanism.
The end devices run BalenaOS, which polls an upstream API for updates.

This repo is that API they poll. It manages deployments / applications / devices and their state.

## Setting it up

First up, you need to set up a Device Type repoistory.
Device Types are synomous to an architecture, eg, a raspberry pi (arm) vs a raspberry pi 3 (armv7)
Balena uses either a S3 bucket, or a S3 like interface to store device types. A simple setup is to create a bucket. The layout is 

`$BUCKET/$PREFIX/$DEVICE_TYPE/$BUILD_VERSION/device-type.json`

Where `device-type.json` is similar to:

```
{
    "slug": "raspberrypi",
    "name": "Raspberry Pi",
    "arch": "armv6",
    "yocto": {
        "deployArtifact": ""
    },
    "buildId": "0.0.1"
}
```

The source of device-type.json can be found in `typings/devices-types.d.ts`