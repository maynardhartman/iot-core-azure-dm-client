# Managing Windows IoT Devices through Azure IoT Hub

## Overview

Device Management allows operators to remotely configure and monitor up to hundreds of thousands of devices simultaneously. 

The operators may do the configuration at a time when the target devices are not even online. They would also want to know the status of each device, and whether the configuration has been applied succeessfully or not.

For that work, there needs to be a central reliable mechanism to store the configuration, and to deliver it to the target devices when they come online. Further more, that mechanism needs to be able to listen to the devices and capture the state they report. Not only that, but such mechanism has to be able to handle hunderds of thousands of devices - and robustly.

A complete solution will have the following components:

- **A Robust/Scalable Cloud Service** to store the desired and reported states of the various devices.
  - [Azure IoT Hub](https://azure.microsoft.com/en-us/services/iot-hub/) and [Azure Device Management](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-device-management-overview) offer a very scalable and efficient cloud service for managing millions of devices.

- **A Client** that runs on the device and knows how to apply the desired states and how to report the state of the device.
  - Windows IoT team offers ***Windows IoT Azure DM Client*** (an open source SDK + runtime) that can apply/report a large set of common/critical Windows, and talk to Azure IoT Hub.

- **A Portal or an Application** that will be used by the operator to configure and query the devices remotely.
  - The OEM will have to build that part.
  - Windows IoT team offers an open source data model that eases the interaction with the data consumed/generated by the the Windows IoT client.

This repo holds the ***Windows IoT Azure DM Client*** open source SDK + runtime.

## Windows IoT Azure DM Client

### Release Notes

### [October 2017 - Full Feature List](docs/release-notes-2017-10.md)

### Overview

The *Windows IoT Azure DM Client* integrates tightly with the user's application on the device. This integration allows some interaction scenarios between the remote configuration and the application business logic.

The DM client consists of:

- A UWP library (*Windows IoT Azure DM Client Library*) that is to be linked to the user's application. The application can be a foreground application or a background application.
- An NT service (*SystemConfigurator*) that is running with System privilege and can listen to Azure IoT Hub notifications relayed by the UWP library and carry out the necessary device management actions.

## Getting Started...

- [IoT Core Azure Device Management Overview](https://blogs.windows.com/buildingapps/2017/04/07/managing-windows-iot-core-devices-azure-iot-hub/)
- Azure IoT Hub
  - [Device Management Overview](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-device-management-overview)
  - [Creating IoT Hub](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-csharp-csharp-getstarted)
- [Sample Applications](docs/samples.md)
- [DM Application Creation Walk-through](docs/dm-hello-world-overview.md)

### System Requirements

#### Developer's Box

- Visual Studio 2017 ([download](https://www.visualstudio.com/downloads)).

#### Device

- Windows IoT Core build 15063 (March 2017) or later.

## Reference

- [Architecture](docs/dm-client-architecture.md)
- [Building the Device Management Binaries](docs/building-the-dm-binaries.md)
- [OEM Device Setup](docs/oem-device-setup.md)
- [Library Reference](docs/library-reference.md)
- [Device Provisioning Service(DPS) Client](<https://github.com/ms-iot/iot-azure-dps-client>)
