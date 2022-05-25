```shell
Docker image for openvpn updated. 

PREREQUISITES
 - Docker installed

INSTALLATION
 - Docker compose example: 

# OpenVpn -> Add to init script TUN.sh (Synology)
  openvpn:
    container_name: openvpn
    image: baroka/openvpn:latest
    restart: unless-stopped
    cap_add:
      - net_admin
    devices:
      - /dev/net/tun
    networks:
      - t2_proxy
    security_opt:
      - no-new-privileges:true
    ports:
      - 8085:8085
    # - 6080:6080
    # - 9091:9091
    # - 51413:51413
    # - 51413:51413/udp
    volumes:
      - $DOCKERDIR/openvpn/config:/vpn
    environment:
      DNS: 1.1.1.1
      FIREWALL: ""
      TZ: $TZ
      PGID: $PGID
      PUID: $PUID

 - $DOCKERDIR points to your local path for script files
```
