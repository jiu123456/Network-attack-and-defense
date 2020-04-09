import nmap

nm=nmap.PortScanner()

nm.scan('192.168.1.9', '22-443') # 扫描主机 192.168.1.9 端口号 

nm.command_line() # 获取用于扫描的命令行：nmap -oX - -p 

for host in nm.all_hosts():

    print('----------------------------------------------------')
    print('Host : %s (%s)' % (host, nm[host].hostname()))
    print('State : %s' % nm[host].state())
    for proto in nm[host].all_protocols():
        print('----------')
        print('Protocol : %s' % proto)
        lport = nm[host][proto].keys()
        #lport.sort()
        for port in lport:
            print ('port : %s\tstate : %s' % (port, nm[host][proto][port]['state']))


![](2.png)

import nmap

host= '192.168.1.9'

nm = nmap.PortScanner()

for port in range(20,25):

    result = nm.scan(host,str(port))
    state = result['scan']['192.168.1.9']['tcp'][int(port)]['state']
    print('[%s] port state: %s' %(port,state))

![](1.png)

import nmap # 导入 nmap.py 模块
 
nm = nmap.PortScanner() # 获取 PortScanner 对象
 
nm.command_line() # 获取用于扫描的命令行：nmap -oX - -p
 
nm.scaninfo() # 获取本次扫描的信息 {'tcp': {'services': '22-443', 'method': 'connect'}}

nm.scan('192.168.1.9', '22-443') # 扫描主机  端口号 22-443
 
nm['192.168.1.9'].state() # 获取主机  的状态 (up|down|unknown|skipped)
 
nm['192.168.1.9']['tcp'].keys() # 获取所有tcp端口
 
nm['192.168.1.9'].all_protocols()
 
nm['192.168.1.9']['tcp'][135]


![](3.png)


![](4.png)


![](5.png)