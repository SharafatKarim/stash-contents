
# Router

## Basic router setup

```sh
Router>en

Router#conf term

Router(config)#hostname R1

R1(config)#no ip domain-lookup

R1(config)#enable secret class

R1(config)#line console 0

R1(config-line)#password cisco

R1(config-line)#login

R1(config-line)#exit

R1(config)#line vty 0 4

R1(config-line)#password cisco

R1(config-line)#login

R1(config-line)#exit

R1(config)#banner motd # Unauthorized Access Is Prohibited #

R1#configure terminal

R1(config)#interface g

R1(config)#interface gigabitEthernet 0/0/1

R1(config-if)#ip address 192.168.1.1 255.255.255.0

R1(config-if)#no shutdown

R1(config-if)#exit

R1(config)#end

R1#copy running-config startup-config
```

## Router Security
```sh
R1(config)#service password-encryption

R1(config)#security passwords min-length 12

R1(config)#enable secret class

% Password too short - must be at least 12 characters. Password not configured.

R1(config)#enable secret $cisco!PRIV*

R1(config)#line console 0

R1(config-line)#password $cisco!!CON*

R1(config-line)#exit

R1(config)#line vty 0 4

R1(config-line)#password $cisco!!VTY*

R1(config-line)#exit

R1(config)#username SSHadmin secret 55HAdm!n2020

R1(config)#ip domain-name ccna-lab.com

R1(config)#crypto key generate rsa general-keys modulus 1024

The name for the keys will be: R1.ccna-lab.com

R1(config)#line vty 0 4

R1(config-line)#transport input ssh

R1(config-line)#login local

R1(config-line)#exit

R1(config)#line console 0

R1(config-line)#exec-timeout 5 0

R1(config-line)#exit

R1(config)#line vty 0 4

R1(config-line)#exec-timeout 5 0

R1(config-line)#exit

R1(config)#login block-for 120 attempts 3 within 60

R1(config)#
```

## Erase Router config

Router> enable
Router# erase startup-config

## SSH
```sh


```

# Switch
## Basic switch setup

```sh
Switch>en

Switch#conf term

Switch(config)#hostname S1

S1(config)#no ip domain lookup

S1(config)#enable secret class

S1(config)#line console 0

S1(config-line)#password cisco

S1(config-line)#login

S1(config-line)#exit

S1(config)#line vty 0 4

S1(config-line)#password cisco

S1(config-line)#login

S1(config-line)#exit

S1(config)#interface vlan 1

S1(config-if)#ip address 192.168.1.11 255.255.255.0

S1(config-if)#no shutdown

S1(config-if)#exit

S1(config)#ip default-gateway 192.168.1.1

S1(config)#end

S1#copy running-config startup-config
```

## Switch Security

### Same as router

- **a.** `S1(config)# service password-encryption`
    
- **b.** `S1(config)# security passwords min-length 12`
    
- **c.**
    
    - `S1(config)# enable secret $cisco!PRIV*`
        
    - `S1(config)# line console 0`
        
    - `S1(config-line)# password $cisco!!CON*`
        
    - `S1(config-line)# exit`
        
    - `S1(config)# line vty 0 4`
        
    - `S1(config-line)# password $cisco!!VTY*`
        
    - `S1(config-line)# exit`
        
- **d.**
    
    - `S1(config)# username SSHadmin secret 55HAdm!n2020`
        
    - `S1(config)# ip domain-name ccna-lab.com`
        
    - `S1(config)# crypto key generate rsa general-keys modulus 1024`
        
    - `S1(config)# line vty 0 4`
        
    - `S1(config-line)# transport input ssh`
        
    - `S1(config-line)# login local`
        
    - `S1(config-line)# exit`
        
- **e.**
    
    - `S1(config)# line console 0`
        
    - `S1(config-line)# exec-timeout 5 0`
        
    - `S1(config-line)# exit`
        
    - `S1(config)# line vty 0 4`
        
    - `S1(config-line)# exec-timeout 5 0`
        
    - `S1(config-line)# exit`
        
    - `S1(config)# login block-for 120 attempts 3 within 60`

### Disabling unused ports

**a. Verify switch port status.**

bash

S1# show ip interface brief

- You will see many interfaces like Fa0/1, Fa0/2, etc., that are "down/down" (not connected). You need to shut them down.
    
- **b. Shut down multiple interfaces.**
    
    bash
    

S1(config)# interface range f0/1-4 , f0/7-24 , g0/1-2
S1(config-if-range)# shutdown
S1(config-if-range)# exit

- *This command shuts down all ports except Fa0/5 and Fa0/6, which are connected to R1 and PC-A.*
    
- **c. Verify that inactive interfaces are shut down.**
    
    bash
    

S1# show ip interface brief

Now, the interfaces you shut down should show "administratively down/down".

## Switch Erase

Switch> enable
Switch# show flash
Switch# delete vlan.dat
Switch# erase startup-config
Switch# reload

