# Ez PPPwn PlayStation 4 PPPoE RCE bin loader

![image](https://github.com/DjPopol/Ez-PPPwn/assets/168917709/de9ed0fe-4bf9-4160-ae04-d093540cd141)


PPPwn is a kernel remote code execution exploit for PlayStation 4 up to FW 11.00. This is a proof-of-concept exploit for CVE-2006-4304 that was reported responsibly to PlayStation.

Supported versions are:

    FW 800/ 8.01 / 8.03
    FW 8.50 / 8.52
    FW 9.00
    FW 9.03 / 9.04
    FW 9.50 / 9.51 / 9.60
    FW 10.00 / 10.01
    FW 10.50 / 10.70 / 10.71
    FW 11.00
    more can be added (PRs are welcome)

The exploit only prints PPPwned on your PS4 as a proof-of-concept. In order to launch Mira or similar homebrew enablers, the stage2.bin payload needs to be adapted.
# Requirements

    - A computer with an Ethernet port  USB adapter also works.
    - Ethernet cable.
    - Python3.

# Usage
    Main :
    [ Script ]
    - button "Browse pppwn"    : Browse pppwn.py
    - button "Browse offsets"  : Browse offsets.py
    - button "Save Pythons"    : Save Python's scripts (pppwn.py, offsets.py) to Directory as
                                 pppwn.py and offsets.py must be on the same directory.

    [ Network PC ]             : Select your NetworkInterface (connected to Playstation 4)
    
    [ Firmware Playstation ]   : Choose Firmware version
    
    [ Stage1 ]
    - button "Browse"          : Browse stage1.bin
    
    [ Stage2 ]
    - button "Browse"          : Browse stage2.bin

    [ Command ]
    - button "Save Batch"      : Save Execute Batch script (.sh) as
    - button "Save All To"     : Save Python's script and stage's to Directory as
    - button "Execute"         : Execute POC in new window "Console"
    - button "Save Config"     : Save Config and it load at start up.
    
    Console :
    - button "Save Log"        : Save log as

On your PS4:

- Go to `Settings` and then `Network`
- Select `Set Up Internet connection` and choose `Use a LAN Cable`
- Choose `Custom` setup and choose `PPPoE` for `IP Address Settings`
- Enter anything for `PPPoE User ID` and `PPPoE Password`
- Choose `Automatic` for `DNS Settings` and `MTU Settings`
- Choose `Do Not Use` for `Proxy Server`
- Click `Test Internet Connection` to communicate with your computer

If the exploit fails or the PS4 crashes, you can skip the internet setup and simply click on `Test Internet Connection`. If the `pppwn.py` script is stuck waiting for a request/response, abort it and run it again on your computer, and then click on `Test Internet Connection` on your PS4.

If the exploit works, you should see an output similar to below, and you should see `Cannot connect to network.` followed by `PPPwned` printed on your PS4.

### Example run

```sh
[+] PPPwn - PlayStation 4 PPPoE RCE by theflow
[+] args: interface=enp0s3 fw=1100 stage1=stage1/stage1.bin stage2=stage2/stage2.bin

[+] STAGE 0: Initialization
[*] Waiting for PADI...
[+] pppoe_softc: 0xffffabd634beba00
[+] Target MAC: xx:xx:xx:xx:xx:xx
[+] Source MAC: 07:ba:be:34:d6:ab
[+] AC cookie length: 0x4e0
[*] Sending PADO...
[*] Waiting for PADR...
[*] Sending PADS...
[*] Waiting for LCP configure request...
[*] Sending LCP configure ACK...
[*] Sending LCP configure request...
[*] Waiting for LCP configure ACK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure NAK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure ACK...
[*] Sending IPCP configure request...
[*] Waiting for IPCP configure ACK...
[*] Waiting for interface to be ready...
[+] Target IPv6: fe80::2d9:d1ff:febc:83e4
[+] Heap grooming...done

[+] STAGE 1: Memory corruption
[+] Pinning to CPU 0...done
[*] Sending malicious LCP configure request...
[*] Waiting for LCP configure request...
[*] Sending LCP configure ACK...
[*] Sending LCP configure request...
[*] Waiting for LCP configure ACK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure NAK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure ACK...
[*] Sending IPCP configure request...
[*] Waiting for IPCP configure ACK...
[+] Scanning for corrupted object...found fe80::0fdf:4141:4141:4141

[+] STAGE 2: KASLR defeat
[*] Defeating KASLR...
[+] pppoe_softc_list: 0xffffffff884de578
[+] kaslr_offset: 0x3ffc000

[+] STAGE 3: Remote code execution
[*] Sending LCP terminate request...
[*] Waiting for PADI...
[+] pppoe_softc: 0xffffabd634beba00
[+] Target MAC: xx:xx:xx:xx:xx:xx
[+] Source MAC: 97:df:ea:86:ff:ff
[+] AC cookie length: 0x511
[*] Sending PADO...
[*] Waiting for PADR...
[*] Sending PADS...
[*] Triggering code execution...
[*] Waiting for stage1 to resume...
[*] Sending PADT...
[*] Waiting for PADI...
[+] pppoe_softc: 0xffffabd634be9200
[+] Target MAC: xx:xx:xx:xx:xx:xx
[+] AC cookie length: 0x0
[*] Sending PADO...
[*] Waiting for PADR...
[*] Sending PADS...
[*] Waiting for LCP configure request...
[*] Sending LCP configure ACK...
[*] Sending LCP configure request...
[*] Waiting for LCP configure ACK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure NAK...
[*] Waiting for IPCP configure request...
[*] Sending IPCP configure ACK...
[*] Sending IPCP configure request...
[*] Waiting for IPCP configure ACK...

[+] STAGE 4: Arbitrary payload execution
[*] Sending stage2 payload...
[+] Done!
