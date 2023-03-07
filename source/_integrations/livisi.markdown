---
title: LIVISI Smart Home
description: Access and control your LIVISI Smart Home Controller (SHC) and its connected RWE/innogy devices.
ha_category:
  - Climate
  - Switch
ha_iot_class: Local Polling
ha_release: 2022.12
ha_config_flow: true
ha_codeowners:
  - '@StefanIacobLivisi'
ha_domain: livisi
ha_platforms:
  - climate
  - switch
ha_integration_type: integration
---

The LIVISI Smart Home integration allows you to connect your LIVISI Smart Home Controller (SHC) to Home Assistant. The SHC can control compatible devices from RWE/innogy connected to it.
 
The following devices are currently supported by this integration:
 
- Indoor Smart Plug (PSS)
- Room Heating Control (VRCC) that includes support for physical heating devices such as RSTx, WRT, FSC8
- Remote (BRC8) and Wall Buttons (WSC2)
 
## Prequisites
 
This integration communicates with the local version of LIVISI SmartHome only. 
 
To activate the local SmartHome functionality, please use the LIVISI App and go to **Settings** >> **General Settings** >> **Local SmartHome** and click **Activate**.
 
Please visit [LIVISI Community](https://community.livisi.de) for more information.
 
{% include integrations/config_flow.md %}
 
### Extra Configuration
 
The current integration will not find your SHC automatically and needs to be configured manually. You will need to provide the IP address and the local password for the controller.
 
## Device Discovery

All devices are automatically discovered and included by the integration. If you include a new device in LIVISI SmartHome, the device will automatically appear in Home Assistant after a few minutes.

## Remotes and wall switches

Livisi remotes such as the 8 Button remote (BRC8) and wall buttons (WSC2) are stateless devices, meaning that they do not have a on/off state like regular entities in Home Assistant. Instead, such devices emit the event `livisi_event` when a button is pressed. You can test what events come in using the event {% my developer_events title="developer tools in Home Assistant" %} and subscribe to the `livisi_event`. Once you know what the event data looks like, you can use this to create automations.
