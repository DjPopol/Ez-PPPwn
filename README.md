# Ez PPPwn PlayStation 4 PPPoE RCE bin loader

![image](https://github.com/DjPopol/Ez-PPPwn/assets/168917709/b8b2979e-fb9a-48f4-b979-7dbc0dd22f66)

PPPwn is a kernel remote code execution exploit for PlayStation 4 up to FW 11.00. This is a proof-of-concept exploit for CVE-2006-4304 that was reported responsibly to PlayStation.

Supported versions are:

    FW 8.50
    FW 9.00
    FW 9.03 / 9.04
    FW 9.50 / 9.60
    FW 10.00 / 10.01
    FW 10.50 / 10.70 / 10.71
    FW 11.00
    more can be added (PRs are welcome)

The exploit only prints PPPwned on your PS4 as a proof-of-concept. In order to launch Mira or similar homebrew enablers, the stage2.bin payload needs to be adapted.
# Requirements

    - A computer with an Ethernet port  USB adapter also works.
    - Ethernet cable.
    - Python3 and gcc installed.

# Usage
    Main :
    [ Script ]
    - button "Browse pppwn"    : Browse pppwn.py
    - button "Browse offsets"  : Browse offsets.py
    - button "Save Pythons"    : Save Python's scripts (pppwn.py, offsets.py) to Directory as

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

    Console :
    - button "Save Log"        : Save log to
