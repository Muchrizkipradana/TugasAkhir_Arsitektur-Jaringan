###  Custom Topology Mininet
![a](https://user-images.githubusercontent.com/64295717/172503174-e595fa11-1526-47ea-b60c-ca7cc727eb0d.PNG)
- 2 program mininet yang mendeskripsikan topology mininet 2 host dan 2 switch dan topology mininet 3 switch (loop) dengan 6 host
- percobaan pada topology mininet 3 switch (loop) dengan 6 host dengan penerapan STP (spanning tree protocol) dengan secara manual menulis flow pada masing-masing switch

![1](https://user-images.githubusercontent.com/64295717/172504193-c448602e-e757-4983-ab95-23dc16797569.PNG)

Yang pertama yaitu membuat file python di direktori mininet dengan cara `cd mininet/custome/`
Dan ketik an coding untuk topologi

![2](https://user-images.githubusercontent.com/64295717/172504314-6e29fec7-9ba3-4798-9086-66f01a3e2037.PNG)

perintah `cat` untuk membuka file .py yang telah kita buat. 
**Berikut source code**
```
" Custom Topology "
from mininet.topo import Topo
from mininet.log import setLogLevel, info
class MyTopo( Topo ):
def addSwitch(self, name, **opts ):
kwargs = { 'protocols' : 'OpenFlow13'}
kwargs.update( opts )
return super(MyTopo, self).addSwitch( name, **kwargs )
def __init__( self ):
# Inisialisasi Topology
Topo.__init__( self )

# Tambahkan node, switch, dan host
info( '*** Add switches\n')
s1 = self.addSwitch('s1')
s2 = self.addSwitch('s2')
# ....
info( '*** Add hosts\n')
h1 = self.addHost('h1', ip='10.1.0.1/24')
h2 = self.addHost('h2', ip='10.1.0.2/24')
# ...
info( '*** Add links\n’)
self.addLink(s1, h1, port1=1, port2=1)
self.addLink(s1, s2, port1=2, port2=1)
self.addLink(s2, h2, port1=2, port2=1)
# ....
```

![3](https://user-images.githubusercontent.com/64295717/172504420-ed3f09ec-445b-43ad-815b-3951f4e5a1fa.PNG)

Menjalankan mininet tanpa controller menggunakan custom topo yang telah dibuat 
dengan perintah 
``` $ sudo mn --controller=none --custom custom_topo_2sw2h.py --topo mytopo --mac --arp ```

![4](https://user-images.githubusercontent.com/64295717/172504609-5ecddfa9-8a5e-473d-90b7-d9254202bd8c.PNG)

Membuat flow agar h1 dapat terhubung dengan h2
```
mininet> sh ovs-ofctl add-flow s1 -O OpenFlow13 "in_port=1,action=output:2"
mininet> sh ovs-ofctl add-flow s1 -O OpenFlow13 "in_port=2,action=output:1"
mininet> sh ovs-ofctl add-flow s2 -O OpenFlow13 "in_port=1,action=output:2"
mininet> sh ovs-ofctl add-flow s2 -O OpenFlow13 "in_port=2,action=output:1“
```

![5](https://user-images.githubusercontent.com/64295717/172505060-abea284d-a0c4-412d-b834-e4de99f924dd.PNG)

`mininet> h1 ping -c2 h2` digunakan untuk uji koneksi antar host1 dan host2 , jika keterangan TTL atau Time to Live memiliki fungsi dalam program ping untuk membatasi waktu dalam ping dalam jangka waktu tertentu.

<br> </br>
![b](https://user-images.githubusercontent.com/64295717/172505664-47c163e3-b4ca-4ee6-818c-41b062320b36.PNG)

Sesuai topolgi diatas terdapat 6host yang nantinya agar bisa terhubung dengan penerapan STP (spanning tree protocol).

![6](https://user-images.githubusercontent.com/64295717/172506272-7341d009-d1a0-4920-adab-16084e706efc.PNG)

**Berikut source code**
```
from mininet.topo import Topo
from mininet.cli import CLI
from mininet.log import setLogLevel, info
    class MyTopo( Topo ):  
        "Simple topology example."
    def addSwitch(self, name, **opts):
        kwargs ={'protocols':'OpenFlow13'}
        kwargs.update(opts)
    return super(MyTopo, self).addSwitch(name, **kwargs)

    def __init__( self ):
        "Create custom topo."
        # Initialize topology
        Topo.__init__( self )
        # Add hosts and switches
        
        info('***Add Hosts ***\n')
        Host1 = self.addHost( 'h1' , ip='10.1.0.1' )
        Host2 = self.addHost( 'h2' , ip='10.1.0.2' )
        Host3 = self.addHost( 'h3' , ip='10.2.0.3' )
        Host4 = self.addHost( 'h4' , ip='10.2.0.4' )
        Host5 = self.addHost( 'h5' , ip='10.3.0.5' )
        Host6 = self.addHost( 'h6' , ip='10.3.0.6' )

        info('***Add Switches ***\n')
        Switch1 = self.addSwitch('s1')
        Switch2 = self.addSwitch('s2')
        Switch3 = self.addSwitch('s3') 

        # Add links
        info('***Add Links for Hosts***\n')
        self.addLink( Host1, Switch1 )
        self.addLink( Host2, Switch1 )
        self.addLink( Host3, Switch2 )
        self.addLink( Host4, Switch2 )
        self.addLink( Host5, Switch3 )
        self.addLink( Host6, Switch3 )

        info('***Add Links between Switches***\n')
        self.addLink( Switch1, Switch2 ) 
        self.addLink( Switch2, Switch3 )
        self.addLink( Switch1, Switch3 )

topos = { 'mytopo': ( lambda: MyTopo() ) }
```
Selanjutnya uji koneksi antar host

![7](https://user-images.githubusercontent.com/64295717/172507510-f3f22680-81a1-4f9d-9b77-e25dd2e52bd2.PNG)
