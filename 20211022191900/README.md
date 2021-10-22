# Netboot Linux based computer

To boot from network, it needs:

* DHCP Server for IP
* TFTP Server to download boot image
* NFS server to serve filesystem

## PXE boot ROCK/PINE/ROCKPRO64 boards

### Updating bootloader via SPI
Follow [ayufan's instructions](https://github.com/ayufan-rock64/linux-build/blob/master/recipes/flash-spi.md) for enabling PXE boot option. Validate with your DHCP server that your board is receiving an IP address.

