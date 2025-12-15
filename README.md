# Advanced Linux Administration

Practical, real-world oriented notes for Linux system administration.
Focused on **how things are used in daily production environments**.

---

## 1. Process Management

### What is a Process?

A process is any running program on Linux. Each process has:

* PID (Process ID)
* Owner
* State (Running, Sleeping, Stopped)

### View Running Processes

```bash
ps aux
ps aux | grep nginx
```

### Live Monitoring

```bash
top
htop
```

### Background & Foreground Jobs

```bash
sleep 100 &
jobs
fg %1
```

### Killing Processes

```bash
kill PID
kill -9 PID
pkill nginx
```

### Linux Signals

| Signal  | Number | Description   |
| ------- | ------ | ------------- |
| SIGTERM | 15     | Graceful stop |
| SIGKILL | 9      | Force stop    |
| SIGSTOP | 19     | Pause         |
| SIGCONT | 18     | Resume        |

---

## 2. Memory & CPU Troubleshooting

### Check Memory Usage

```bash
free -h
```

### CPU Load

```bash
uptime
```

### Identify Resource-Hungry Processes

```bash
ps aux --sort=-%mem | head
ps aux --sort=-%cpu | head
```

---

## 3. Disk & Filesystem Management

### Disk Space Usage

```bash
df -h
```

### Find Large Directories

```bash
du -sh /var/*
```

### Inode Usage

```bash
df -i
```

### Mount & Unmount

```bash
mount
mount /dev/sdb1 /data
umount /data
```

---

## 4. Logs & Journald

### Traditional Logs

```bash
tail -f /var/log/syslog
tail -f /var/log/messages
```

### journalctl

```bash
journalctl
journalctl -u nginx
journalctl -u nginx -f
journalctl -b
```

---

## 5. Advanced Networking

### Check Listening Ports

```bash
ss -tulnp
```

### Connectivity Testing

```bash
ping 8.8.8.8
telnet IP PORT
nc -zv IP PORT
```

### Packet Capture

```bash
tcpdump -i eth0 port 8080
```

---

## 6. Advanced Permissions

### ACL (Access Control Lists)

```bash
setfacl -m u:ahmed:r file.txt
getfacl file.txt
```

### SUID

```bash
chmod u+s file
ls -l /usr/bin/passwd
```

### SGID

```bash
chmod g+s directory
```

---

## 7. Real Production Troubleshooting Flow

1. Check service status

```bash
systemctl status service
```

2. Check logs

```bash
journalctl -u service
```

3. Check resources

```bash
top
free -h
df -h
```

4. Check networking

```bash
ss -tulnp
ping
```

5. Check permissions

```bash
ls -l
getfacl
```

---


This document represents the **daily workflow of a Linux System Administrator**,
covering troubleshooting, monitoring, and production issue resolution.
