# Bluetooth Low Energy Analysis Instructions

This repository contains instructions that help with analyzing the BLE communications of the Emercast prototype (and other BLE or GATT applications).
This approach was used to obtain the average durations of the phases of the synchronization process used by the Emercast prototype.
These durations were used in the simulator to approximate the behavior of the Emercast prototype as close as possible.

## Prerequisites
- nRF52840 MDK USB Dongle (check the "where to buy" section on [this website](https://github.com/makerdiary/nrf52840-mdk-usb-dongle), we got ours from makerdiary/amazon)
- A windows/linux/macos machine

## Setup
Follow the steps laid out in this setup section or follow the steps on this [website](https://wiki.makerdiary.com/nrf52840-mdk-usb-dongle/guides/ble-sniffer/installation/#installing-the-nrf-sniffer-capture-tool)
- Clone this repository
- Take the nRF52840 dongle and hold the reset button
- Plug the dongle into your machine
- Release the reset button
- Copy the /nrf52840-mdk-usb-dongle/firmware/ble_sniffer/nrf_sniffer_for_bluetooth_le_v4.1.1.uf2 to the drive "UF2BOOT" that should show up now
- Replug the dongle
- Install wireshark
- Head to /nrf52840-mdk-usb-dongle/tools/ble_sniffer/extcap
- Install the python requirements ``python3 -m pip install -r requirements.txt``
- Open wireshark and go to Help > About Wireshark > Folders and copy the "Personal Extcap path"
- Copy the content of /nrf52840-mdk-usb-dongle/tools/ble_sniffer/extcap to this path
- Click Capture > Refresh Interfaces in wireshark
- Enable View > Interface Toolbars > nRF Sniffer for Bluetooth LE

## Packet filters

Use the following filter strings to filter for specific packets related to the Emercast Prototype:
- To filter for the Emercast advertisement packets: ```btcommon.eir_ad.entry.uuid_16 == 0xb571```
- To filter for BLE connect requests: ```btle.advertising_header.pdu_type == 0x5```
- To filter for BLE read requests: ```btatt.opcode.method == 0x08```
- To filter for BLE write requests: ```btatt.opcode.method == 0x12```
- To filter for GATT requests regarding a specific characeristic: ```btatt.uuid128 == SEE BELOW FOR SELECTION OF VALUES```

These are the static GATT characeristics used by the Emercast prototype:
- GET_BROADCAST_MESSAGE_SYSTEM_CHAIN_HASH ```7323fe0e-5691-4090-0000-48b1782de633```
- GET_BROADCAST_MESSAGE_NON_SYSTEM_CHAIN_HASH ```7323fe0e-5691-4090-0001-48b1782de633```
- GET_BROADCAST_MESSAGE_SYSTEM_INFO_LIST ```7323fe0e-5691-4090-0002-48b1782de633```
- GET_BROADCAST_MESSAGE_NON_SYSTEM_INFO_LIST ```7323fe0e-5691-4090-0003-48b1782de633```
- POST_MESSAGE_CHARACTERISTIC ```7323fe0e-5691-4090-0004-48b1782de633```
