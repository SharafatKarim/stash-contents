---
Owner: Sharafat Karim
Last edited time: 2023-02-25T09:30
---
---

pulse - traditional

pipe - newer

---

This will show you if either PulseAudio or PipeWire is currently running on your system.

```Plain
ps -ef | grep -e pulse -e pipewire
```

To check whether your system is using PulseAudio or PipeWire, you can run the following command in the terminal:

---

- Expended
    
    To check if PulseAudio or PipeWire is currently running on your Linux system, you can use the following commands:  
    To check if PulseAudio is running:  
      
    `systemctl --user status pulseaudio.service`  
    If PulseAudio is running, the command output will show its status as "active".  
    To check if PipeWire is running:  
      
    `systemctl --user status pipewire.service`  
    If PipeWire is running, the command output will show its status as "active".  
    
      
    You can also use the ps command to check if the PulseAudio or PipeWire processes are running:  
    To check if PulseAudio processes are running:  
      
    `ps aux | grep pulseaudio`  
    If PulseAudio is running, you will see output similar to the following:  
      
    `user 1234 0.0 0.0 123456 7890 ? S<l Feb24 0:00 /usr/bin/pulseaudio --start --log-target=syslog`
    
      
    To check if PipeWire processes are running:  
      
    `ps aux | grep pipewire`  
    If PipeWire is running, you will see output similar to the following:  
      
    `user 1234 0.0 0.0 123456 7890 ? Ssl Feb24 0:00 /usr/bin/pipewire`  
    By using these commands, you can check if either PulseAudio or PipeWire is running on your Linux system.