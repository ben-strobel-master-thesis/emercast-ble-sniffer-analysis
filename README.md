# Readme

## Prerequisites
- nRF52840 MDK USB Dongle (check the "where to buy" section on https://github.com/makerdiary/nrf52840-mdk-usb-dongle, we got ours from makerdiary/amazon)
- A windows/linux/macos machine

## Setup
- Have a look at this guide OR follow the following steps: https://wiki.makerdiary.com/nrf52840-mdk-usb-dongle/guides/ble-sniffer/installation/#installing-the-nrf-sniffer-capture-tool
- Clone this repository
- Take the nRF52840 dongle and hold the reset button
- Plug the dongle into your machine
- Release the reset button
- Copy the /nrf52840-mdk-usb-dongle/firmware/ble_sniffer/nrf_sniffer_for_bluetooth_le_v4.1.1.uf2 to the drive "UF2BOOT" that should show up now
- Replug the dongle
- Install wireshark
- Head to /nrf52840-mdk-usb-dongle/ble_sniffer/extcap
- Install the python requirements ``python3 -m pip install -r requirements.txt``
- Open wireshark and go to Help > About Wireshark > Folders and copy the "Personal Extcap path"
- Copy the content of /nrf52840-mdk-usb-dongle/ble_sniffer/extcap to this path
- Click Capture > Refresh Interfaces in wireshark
- Enable View > Interface Toolbars > nRF Sniffer for Bluetooth LE
