Microclimates Device Module Template
====================================

This repository contains the minimum requirements for installing your device
into a secure [Microclimates](https://www.microclimates.com) network.

It's designed to be used as a template for your own device module.

While there is no requirement for this to install a device, it will allow
the device be installed without the security warning.

We recommend all devices running within the secure network have this minimum installation, 
consting of the package.json file acknowledging your understanding and
acceptance of the [security agreement](https://www.microclimates.com/device-security-agreement)
and [privacy policy](https://www.microclimates.com/device-privacy-policy).

Device Requirements
-------------------

Any device following the [Homie convention](https://github.com/marvinroger/homie)
can be added to the secure Microclimates network. It has been tested using the [ESP8266](https://github.com/marvinroger/homie-esp8266) homie
library.

In order to find your device module it must be published to npm, and the following must be in the device settings section of the [JSON configuration file](https://homie-esp8266.readme.io/docs/json-configuration-file) on the device:

```
{
  ...
  "settings": {
    "npm-module": "this-repo@^2.12.0"
  }
}
```

If the `npm-module` value contains a semver range as in the above example, automatic updates of your module are restrained to this range.

Installing
----------

The device must be in configuration mode as a WiFi hotspot, broadcasting an SSID. If the SSID begins with `homie-` or `microclimates-`, the Microclimates hub will find it without asking the user to view all available SSIDs.

Once the user confirms their intent to install the device, the `microclimates` section of the `package.json` for your module will be downloaded, validated, and presented to the user. 

Upon installation, your device will be configured to connect to the secure Microclimates network, the shared MQTT message bus, and be controlled by [node-red](http://nodered.org/) flows and the external [Climate Control API](https://microclimates.com/api/v1/).

License
-------

Copyright 2017  Microclimates, Inc.
May be freely distributed under the [MIT license](https://opensource.org/licenses/MIT)

