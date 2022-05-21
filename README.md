# How to setup Wifi when installing Home Assistant OS.
### Tested on Rasp 3 B+ (x64)

## Things you need:

- balenaEtcher software
- SD-card
- USB-drive

## Steps:

1. Flash the SD-card drive using balenaEtcher software according to the official docs 19
2. Format USB-drive as FAT32 and name it CONFIG
3. Create folder network, inside it create a file my-network
4. Write the file with the following content:

-- 
[connection]
id=my-network
uuid=72111c67-4a5d-4d5c-925e-f8ee26efb3c3
type=802-11-wireless

[802-11-wireless]
mode=infrastructure
ssid=**Your SSID**

#Uncomment below if your SSID is not broadcasted
#hidden=true

[802-11-wireless-security]
auth-alg=open
key-mgmt=wpa-psk
psk=**Your Password**

[ipv4]
method=auto

[ipv6]
addr-gen-mode=stable-privacy
method=auto
-- 

5. Plug into Raspberry Pi 3B+ USB-stick and SD-card
6. Plug power supply and wait for around 1 minute (Note: do not plug LAN cable)
7. Check the http://homeassistant.local:8123/
8. DONE!


## Troubleshooting:

If you cannot connect via homeassistant.local, check the following:

- Go to your router (usually via 192.168.1.1 or 192.168.0.1)
- Check Wireless tab and Active clients
- If homeassistant client appears with ip-address, use alternative link: http://ip-address:8123/
