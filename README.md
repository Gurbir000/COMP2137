                                                                          
Hostname:$(whoami)

OS:$(source /etc/os-release && echo "$NAME $VERSION")

Uptime:$(uptime -p)


Hardware Information

--------------------


cpu:$(lshw | grep "product" | head -n 1)

speed:$(sudo lshw | grep "capacity" | tail -n 3)

ram:$(free -h | grep "$totalmem" | head -n 2 | awk '{print $2}')

Disk:$(lshw -class disk -short)

video:$(lshw -class display | grep -E "description|product" )


Network Information

-------------------


FQDN=$(hostname -f)

Host Address:$(ip a | grep inet | head -n 1 | awk '{print $2}')

Gteway IP:$(ip r | grep default | awk '{print $3}')

DNS Server: $(grep nameserver /etc/resolv.conf | awk '{print $2}')

InterfaceName:$(grep nameserver /etc/resolv.conf | awk '{print $1}')

IPAddress:$(ip a | grep inet6 |tail -n 1)



System Status

-------------

User Logged In:$(who)

Disk Space=$(df -h | awd '{print $6 $4}' | head -n 1)

Proccess Count=$(ps)


Memory Allocation:$(free -h) 

Listening Network ports:$(ss | grep UNCON)

UFW Rules:$(sudo ufw status)



