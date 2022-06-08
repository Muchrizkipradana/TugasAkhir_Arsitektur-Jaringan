###  Custom Topology Mininet
![a](https://user-images.githubusercontent.com/64295717/172503174-e595fa11-1526-47ea-b60c-ca7cc727eb0d.PNG)
- 2 program mininet yang mendeskripsikan topology mininet 2 host dan 2 switch dan topology mininet 3 switch (loop) dengan 6 host
- percobaan pada topology mininet 3 switch (loop) dengan 6 host dengan penerapan STP (spanning tree protocol) dengan secara manual menulis flow pada masing-masing switch

![1](https://user-images.githubusercontent.com/64295717/172504193-c448602e-e757-4983-ab95-23dc16797569.PNG)
Yang pertama yaitu membuat file python di direktori mininet dengan cara `cd mininet/custome/`
Dan ketik an coding untuk topologi

![2](https://user-images.githubusercontent.com/64295717/172504314-6e29fec7-9ba3-4798-9086-66f01a3e2037.PNG)
perintah `cat` untuk membuka file .py yang telah kita buat

![3](https://user-images.githubusercontent.com/64295717/172504420-ed3f09ec-445b-43ad-815b-3951f4e5a1fa.PNG)
Menjalankan mininet tanpa controller menggunakan custom topo yang telah dibuat 
dengan perintah ``` $ sudo mn --controller=none --custom custom_topo_2sw2h.py --topo mytopo --mac --arp ```

![4](https://user-images.githubusercontent.com/64295717/172504609-5ecddfa9-8a5e-473d-90b7-d9254202bd8c.PNG)

