# Cisco Router Configuration Lab

## Overview
This lab demonstrates basic Cisco router configuration including device setup, password security, and serial interface configuration to establish connectivity between two routers.

## Lab Objectives
- Configure basic router settings (hostname, passwords)
- Set up serial interface connections
- Establish connectivity between two routers
- Verify configuration using show commands

## Technologies Used
- Cisco Packet Tracer (Network Simulation)
- Cisco IOS Commands
- Router Configuration
- Network Troubleshooting

## Project Structure

/
├── Lab_3_Router_Config.pkt
├── screenshots/
│   ├── ping_manassas_to_fairfax.png
│   ├── ping_fairfax_to_manassas.png
│   ├── show_run_manassas.png
│   └── show_run_fairfax.png
└── README.md

## Network Topology

Manassas Router (192.168.1.1/30) -- Serial Connection -- Fairfax Router (192.168.1.2/30)
        DCE (Clock Rate: 64000)                              DTE


## Router Configurations

### Manassas Router
- **Hostname**: Manassas
- **Console Password**: cisco
- **Enable Secret**: cisco
- **VTY Password**: class
- **Serial Interface**: 192.168.1.1/30
- **Clock Rate**: 64000 (DCE)

### Fairfax Router
- **Hostname**: Fairfax
- **Console Password**: cisco
- **Enable Secret**: cisco
- **VTY Password**: class
- **Serial Interface**: 192.168.1.2/30

## Key Configuration Commands

### Basic Setup
bash
Router> enable
Router# configure terminal
Router(config)# hostname Manassas
Router(config)# enable secret cisco

### Password Configuration
bash
# Console Password
line console 0
password cisco
login

# VTY Lines (Telnet)
line vty 0 4
password class
login


### Interface Configuration
bash
interface serial 0/0/0
ip address 192.168.1.1 255.255.255.252
clock rate 64000  # Manassas only (DCE)
no shutdown


## Verification

### Testing Connectivity
bash
# From Manassas to Fairfax
Manassas# ping 192.168.1.2

# From Fairfax to Manassas
Fairfax# ping 192.168.1.1


### Show Commands
```bash
show running-config
show ip interface brief
show interfaces serial 0/0/0
show clock
show version
```

## Results
- ✅ Successful ping connectivity between routers
- ✅ All interfaces show "up/up" status
- ✅ Passwords properly configured and encrypted
- ✅ Serial link established with correct clock rate
- ✅ Configuration persists after saving

## Usage
1. Open `Lab_3_Router_Config.pkt` in Cisco Packet Tracer
2. Access router CLIs to view configurations
3. Test connectivity using ping commands
4. Verify settings with show commands

## Notes
- Uses /30 subnet for serial link (2 usable IPs)
- Manassas router serves as DCE end providing clocking
- All passwords follow lab specifications
- Configuration includes both running and startup config saves

---
**Lab Status**: Completed Successfully ✅
```

You can now copy and paste this entire text directly into your `README.md` file on GitHub. The formatting uses standard GitHub Markdown syntax and will display properly on your repository.
