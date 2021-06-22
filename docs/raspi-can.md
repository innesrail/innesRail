# Adding CAN to a Raspberry Pi

The MCP2515 CAN controller chip uses SPI to communicate with the Raspberry Pi.

To use:

1. Ensure SPI is enabled in the Raspi-config interfaces utility
2. `sudo apt install can-utils -y`
3. Add the following to the bottom of /boot/config.txt file with command `sudo nano /boot/config.txt`

    ```shell
    dtoverlay=mcp2515-can0,oscillator=16000000,interrupt=25
    dtoverlay=spi1-1cs
    ```

4. Create the can0 interface by editing /etc/network/interfaces file `sudo nano /etc/network/interfaces` and add the following content

    ```text
    auto can0
    iface can0 inet manual
    pre-up /sbin/ip link set can0 type can bitrate 125000
    up /sbin/ifconfig can0 up
    down /sbin/ifconfig can0 down
    ```

5. reboot the pi

To see the state of the CAN interface use commands

- `ifconfig` - should see the can0 interface as active
- `ip -details -statistics link show can0` - shows statistics of interface
- `candump can0` - shows raw data flowing on the bus

If needed you can manually control the interface:

- start - `ip link set can0 up type can bitrate 125000`
- stop - `sudo ip link set can0 down`
