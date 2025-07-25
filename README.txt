Install PdaNet+.
Before you start the app, you must turn on Wifi, Mobile Data, and Location

Install ByeDPI, or any app that allows you to expose a SOCKS server

On the Linux machine:
sudo ip tuntap add mode tun dev tun0 #Pick a tun interface
sudo ip addr add 198.18.0.1/15 dev tun0 #Pick an IP address
sudo ip route add default dev tun0 metric 1
sudo ip route add 198.18.0.1 via 192.168.64.1 dev enp1s0f3 #{ip address} via {default gateway} dev {default interface}. You can learn of your default with (ip route|grep default)
./tun2socks-linux-arm64 -device tun://tun0 -proxy socks5://192.168.49.1:1080 -interface enp1s0f3 -tcp-auto-tuning
(Taken from https://medium.com/@SaeedDev94/use-socks-proxy-as-vpn-in-linux-d31b1cce44e0)
You can undo the routes by using "del" instead of "add"