###  aplikasi Ryu  Shortest Path Routing
**Tugas 4 - SPF Routing**

![image](https://user-images.githubusercontent.com/64295717/172839270-f9bb6d43-bd96-4347-ac80-e602844421b4.png)
1.	dijkstra_Ryu_controller.py 
Dalam source code yang ada dalam dijkstra yaitu  dari source code hampir mirip dengan simple  switch yang load balance yang dimodifikasi  berupa beberapa pendeskripsian yang digunakan untuk routing memilih jalur terpendek berdasarkan algoritma djikstra
syaratnya mengetahui jumlah seluruh switch 
dalam line 38 get_path untuk mendapatkan path untuk melakukan literasi dalam penerapanya dari kiri kenan yaitu dari source ke destination, dari destination ke source sampai mendapatkan nilai dari route 
Ketika  paket masuk ke controler kemudian  mengidentifikasi masuk ke port berapa, src,dst,pid (switch) untuk mencari jalur 
terdapat fungsi mymacs untuk mendeskripsikan destination address jika sudah tau akan mencari path nya jika belom tahu dengan teknik flood  
2.	topo-spf_lab.py 
dalam progam terdapat 6 host dan 6 switch 
dalam praktiknya tidak menggunakan ipv6 jadi harus di matikan , kemudian mac address dibuat true 

![image](https://user-images.githubusercontent.com/64295717/172839585-16334c20-1fb6-4241-80c5-06684815392f.png)

Saat awal progam python dijalankan 

![image](https://user-images.githubusercontent.com/64295717/172839658-71105e1e-92be-4419-bdff-b855226e2702.png)

Disini switch sudah terhubung ke kontroler otomatis kontroler dapat mengirim paket ke switch berupa lntp untuk mengidentifikasi switch terhubung ke mana saja 

![image](https://user-images.githubusercontent.com/64295717/172839706-67c9dbb8-3531-4362-9b27-6a338b1e5507.png)

Berisikan ada paket apapun dikirimkan ke controler 

![image](https://user-images.githubusercontent.com/64295717/172839762-97e8857c-27ba-43a4-8216-8d6dc73c057f.png)

![image](https://user-images.githubusercontent.com/64295717/172839798-eeee604d-72b6-4282-b3c9-2ab62c4c4a9f.png)

Yang berbeda dari s4 yaitu ada 2 flow yang dibuat jika ada paket dari h1 alamat tujuan h4 dikeluarkan port1 sebaliknya jika ada src 4 tujuan h1 diarahkan output ke port2 
Jalur yang terpilih yaitu s1 s2 ke s4

![image](https://user-images.githubusercontent.com/64295717/172839875-0d8a18f4-97c6-4a5c-9a67-cf8160cd219c.png)

![image](https://user-images.githubusercontent.com/64295717/172839900-53f9684c-e03c-470a-866a-5ccbf9339175.png)

Jika flow sudah tertulis maka tidak akan tampil pada saat melakukan ping

![image](https://user-images.githubusercontent.com/64295717/172840000-a61e2b6e-0f24-4fc6-a077-ea669000083a.png)

Ping dari h5 ke –c4 h6

![image](https://user-images.githubusercontent.com/64295717/172840138-44c785f9-b179-4a4a-b22e-5f42bd4bda3f.png)

![image](https://user-images.githubusercontent.com/64295717/172840213-b4b37b68-f17a-4ecb-a9a5-6abef6e99214.png)

Melewati jalur s1,s2,s4,S5,dan S6





