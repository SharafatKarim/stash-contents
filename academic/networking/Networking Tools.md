
## CMD 
Some command line based networking tools include,
- ping
- traceroute
- nslookup (`bind` package in archlinux)
- telnet ([inetutils](https://archlinux.org/packages/?name=inetutils)package in archlinux)

## GUI
- wireshark
- cisco packet tracer 

# App specific

## Wireshark

### Archlinux

1. To install in Archlinux,
```shell
yay wireshark
```
for GUI, install the `wireshark-qt` one.

2. Add your user to the `wireshark` usergroup.
```shell
sudo usermod -a -G wireshark $(whoami)
```

3. And re-login and reboot.

## Cisco packet tracer

### Switch mac-address-table 
In the CLI, hit enter, followed by `EN` (enter) and tthen type,
```
show mac-address-table
```