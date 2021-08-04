# Debian VM


build
```docker
docker build -t mbwali/debian:10 ./debian/
```

run 
```docker
docker run -it mbwali/debian:10
```

run detached
```docker
docker run -it -d mbwali/debian:10
```

ping ip address

```bash
$ docker inspect -f "{{ .NetworkSettings.IPAddress }}" 7fd8b80ae7e8
172.17.0.2

$ ping -c 3 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.161 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.104 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.116 ms

--- 172.17.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2030ms
rtt min/avg/max/mdev = 0.104/0.127/0.161/0.024 ms
```
