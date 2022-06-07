### Membuat EC2 Instance di AWS Academy: 
**Dengan ketentuan sebagai berikut :**
- Name and tags: Tugas Akhir
- OS Images: Ubuntu Server 22.04 LTS 64 bit
- Instance type: t2.medium
- Key pair: vockey
- Edit Network settings: allow SSH, allow HTTP, allow HTTPS, allow TCP port 8080, allow TCP port 8081
- Configure storage: 30 GiB, gp3

![1](https://user-images.githubusercontent.com/64295717/172334427-949d466a-a0d4-4bdb-9a4f-13bdd027ae74.PNG)

tampilan membuat instance baru dengan nama Tugas Akhir

![2](https://user-images.githubusercontent.com/64295717/172335493-f51092a3-1b7e-4739-9302-3a893969c298.PNG)
Dalam dilihat pada rincian tentang mesin server yang kita buat yakni menggunakan Ubuntu Server 22.04 LTS 64 bit

![3](https://user-images.githubusercontent.com/64295717/172335804-07329b28-2f06-4f5f-a74c-7f1a80f1d8de.PNG)
Untuk keamanan server yang dibuat bisa dilihat dalam menu keamanan, allow SSH, allow HTTP, allow HTTPS, allow TCP port 8080, allow TCP port 8081.

![4](https://user-images.githubusercontent.com/64295717/172337204-73e78adf-7170-41ca-b13f-0780875bc403.PNG)
terlihat penyimpnan yang dibuat sebesar 30Gib bertype gp3.

![5](https://user-images.githubusercontent.com/64295717/172337410-18041120-097b-4aa9-be9d-5d30748cb7c6.PNG)
```
$ssh -i .ssh/labuser.pem ubuntu@ec2-54-234-133-143.computer-1.amazonaws.com
```
Progam di atas digunakan untuk menjalan mesin aws pada consol

![6](https://user-images.githubusercontent.com/64295717/172340249-4b29e7d7-4778-4652-975c-66025eb4e3d5.PNG)

Selanjutnya proses instalasi
Sebelumnya instalasi melakukan update dahulu dengan cara sebagai berikut
```
sudo apt -yy update && sudo apt -yy upgrade
```
![7](https://user-images.githubusercontent.com/64295717/172340453-bb83b53d-6af4-4ecc-9a18-1851e71ff8ae.PNG)

instalasi mininet dan open flow
```
git clone git://github.com/mininet/mininet
cd mininet
git checkout -b mininet-2.3.0 2.3.0 # or whatever version you wish to install
cd
```

install mininet
```
mininet/util/install.sh -nfv
```
![8](https://user-images.githubusercontent.com/64295717/172340728-2cc420e2-f14d-4aa6-8893-b4f41d22fcc7.PNG)

Instalasi Ryu Unduh repository Ryu dan instal
```
git clone git://github.com/osrg/ryu.git
cd ryu; pip install .
cd
```
![9](https://user-images.githubusercontent.com/64295717/172340802-0c2bc087-065e-473c-b472-9629d7cd0513.PNG)

Instalasi Flowmanager Unduh repository Flowmanager
```
git clone https://github.com/martimy/flowmanager
cd
```
![10](https://user-images.githubusercontent.com/64295717/172341345-3dc0307e-e2d6-4bd6-b9a7-22219d0ffe32.PNG)

Setelah semua kebutuhan telah terinstall bisa dilihat dengan mengetikan 
`$ls` digunakan untuk melihat paket yang sudah di install

![11](https://user-images.githubusercontent.com/64295717/172341468-704b1836-5f89-41d0-8afa-3393debb4573.PNG)

`sudo mn` untuk Interaksi Host dan Switch
![12](https://user-images.githubusercontent.com/64295717/172341728-8c96a9cf-a109-4510-8c15-e11088608721.PNG)

`help` untuk melihat opsi yang disediakan
![13](https://user-images.githubusercontent.com/64295717/172342189-8abe37cd-cc0b-4537-858a-b0af57180f79.PNG)

`node` Melihat node yang tersedia
![14](https://user-images.githubusercontent.com/64295717/172342649-4b6a4f48-78e9-4ef3-a28d-091eef39f842.PNG)

`net` Melihat jalur ethernet yang dapat dihubungkan

![15](https://user-images.githubusercontent.com/64295717/172345163-53f0b6a5-4eb5-4e6d-ac7d-b97fbdf12e4b.PNG)

![16](https://user-images.githubusercontent.com/64295717/172345223-a7616009-9455-4ab8-a543-5093513b9ff9.PNG)

`pingall` Untuk uji koneksi antar host
