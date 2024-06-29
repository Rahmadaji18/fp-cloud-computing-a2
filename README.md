# Final Project Teknologi Komputasi Awan
---
## Kelompok 2/Kelas A

| Nama | NRP |
| --- | --- |
| Rahmad Aji Wicaksono | 5027221034 |
| Zulfa Hafizh Kusuma | 5027221038 |
| M. Rifqi Oktaviansyah | 5027221067 |
| Romandhika Rijal Ibrahim | 5311840000048 |

## Permasalahan Utama
Anda adalah seorang lulusan Teknologi Informasi, sebagai ahli IT, salah satu kemampuan yang harus dimiliki adalah Keampuan merancang, membangun, mengelola aplikasi berbasis komputer menggunakan layanan awan untuk memenuhi kebutuhan organisasi.

Pada suatu saat anda mendapatkan project untuk mendeploy sebuah aplikasi Sentiment Analysis dengan komponen Backend menggunakan python: sentiment-analysis.py dengan spesifikasi sebagai berikut

### Endpoints:
1. **Analyze Text**
   - **Endpoint:** ```POST /analyze```
   - **Description:** Endpoint ini menerima input teks dan mengembalikan skor sentimen dari teks tersebut.
   - **Request:**
     ```http
     {
     "text": "Your text here"
     }
     ```
   - **Response:**
     ```http
     {
     "sentiment": <sentiment_score>
     }
     ```
2. **Retrieve History**
   - **Endpoint:** ```GET /history```
   - **Description:** Endpoint ini mengambil riwayat teks yang dianalisis sebelumnya beserta skor sentimennya.
   - **Response:**
     ```http
     {
       {
       "text": "Your previous text here",
       "sentiment": <sentiment_score>
       },
     ...
     }
     ```
---
Kemudian juga disediakan sebuah Frontend sederhana menggunakan index.html dan styles.css dengan tampilan antarmuka sebagai berikut  
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/1b5ece65-857a-4b47-8056-089122ce20ee)  
Kemudian anda diminta untuk mendesain arsitektur cloud yang sesuai dengan kebutuhan aplikasi tersebut. Apabila dana maksimal yang diberikan adalah 1 juta rupiah per bulan (65 US$) konfigurasi cloud terbaik seperti apa yang bisa dibuat?  

## Rancangan Arsitektur Awan
Disini kami menggunakan 2 provider yaitu DigitalOcean dan Google Cloud Platform. Karena setelah beberapa pertimbangan dari kami, provider DigitalOcean hanya memperbolehkan membuat maksimal 3 droplet. Sehingga kami membuat lagi 2 droplet pada Google Cloud Platform. Pertimbangan tersebut menurut kami yang paling masuk akal dengan rancangan yang kami buat dikarenakan keterbatasan device dan resource yang kami gunakan.  

### Rancangan:
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/50f48ca5-8de3-4003-b642-a839efbb34dd)

### Tabel Harga:
<table>
  <tr>
    <th>No.</th>
    <th>Nama</th>
    <th>Spesifikasi</th>
    <th>Fungsi</th>
    <th>Harga/Bulan</th>
  </tr>
  <tr>
    <td>1.</td>
    <td>KelompokTKA2A-VM1</td>
    <td>2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>App Worker 1</td>
    <td>18$</td>
  </tr>
  <tr>
    <td>2.</td>
    <td>KelompokTKA2A-VM2</td>
    <td>2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>App Worker 2</td>
    <td>18$</td>
  </tr>
  <tr>
    <td>3.</td>
    <td>KelompokTKA2A-VM3</td>
    <td>2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>Mongo Database</td>
    <td>18$</td>
  </tr>
  <tr>
    <td>4.</td>
    <td>KelompokTKA2A-VM4</td>
    <td>1 Intel vCPU / 1GB Memory / 10GB Disk SSD / Asia-Southeast2(Jakarta) - Ubuntu 24.04 (LTS) x64</td>
    <td>Load Balancer 1 (Round-Robin)</td>
    <td>6$</td>
  </tr>
  <tr>
    <td>5.</td>
    <td>KelompokTKA2A-VM5</td>
    <td>1 Intel vCPU / 512MB Memory / 10GB Disk SSD / Asia-Southeast2(Jakarta) - Ubuntu 24.04 (LTS) x64</td>
    <td>Load Balancer 2 (Least-Connection)</td>
    <td>4$</td>
  </tr>
  <tr>
    <td colspan="4" align="right"><strong>Total</strong></td>
    <td><strong>64$</strong></td>
  </tr>
</table>

---
### Revisi Rancangan & Tabel Harga
![rancanganfptka2 drawio (1)](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/0389324b-a9e4-4a77-8227-f1a4f00dc32d)

![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/22558a1b-ac7d-462e-a09f-990de1750e9d)
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/0742df76-eba5-436d-bca5-10a46f8d6f92)
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/0468d06e-a644-4e21-b878-d2c3ed7c2a05)


<table>
  <tr>
    <th>No.</th>
    <th>Nama</th>
    <th>Spesifikasi</th>
    <th>Fungsi</th>
    <th>Harga/Bulan</th>
  </tr>
  <tr>
    <td>1.</td>
    <td>KelompokTKA2A-VM1</td>
    <td>2 Premium Intel vCPU / 2GB Memory / 90GB NVMe Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>App Worker 1</td>
    <td>24$</td>
  </tr>
  <tr>
    <td>2.</td>
    <td>KelompokTKA2A-VM2</td>
    <td>2 Premium Intel vCPU / 2GB Memory / 90GB NVMe Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>App Worker 2</td>
    <td>24$</td>
  </tr>
  <tr>
    <td>3.</td>
    <td>KelompokTKA2A-VM3</td>
    <td>1 Premium Intel vCPU / 2GB Memory / 70GB NVMe Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64</td>
    <td>Load Balancer & Mongo Database</td>
    <td>16$</td>
  </tr>
  <tr>
    <td colspan="4" align="right"><strong>Total</strong></td>
    <td><strong>64$</strong></td>
  </tr>
</table>

## Implementasi
### Konfigurasi VM-3 (Database)
1. Sambungkan terminal windows ke terminal vm.  
   ```ssh root@146.190.102.47```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f84cebf9-b7a4-400d-a95b-201cf0890b0c)  
   Masukkan password vm.
2. Jalankan beberapa command berikut untuk install MongoDB.
   ```bash
   sudo apt update
   sudo apt upgrade
   
   # Install dependency
   sudo apt install gnupg wget apt-transport-https ca-certificates software-properties-common
   echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list
   sudo apt-get update
   sudo apt-get install libssl1.1

   # Install mongodb
   curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
   sudo apt update
   sudo apt install mongodb-org -y
   ```
3. Enable MongoDB.
   ```bash
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```
4. Konfigurasi MongoDB  
   ```sudo nano /etc/mongod.conf```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/76e9f0cd-fe02-4a2a-99f6-2532385bc876)  
6. Restart service MongoDB  
   ```sudo systemctl restart mongod```  
8. Buka port pada firewall  
   ```sudo ufw allow 27017```  
9. Buka shell MongoDB  
   ```mongo```
10. Masuk sebagai user Admin  
    ```use admin```
11. Buat user Admin
    ```js
    db.createUser({
    user: "KelompokTKA2A",
    pwd: "KelompokTKA2A",
    roles: [{ role: "userAdminAnyDatabase", db: "admin" }]
    })
    ```
12. Cek user yang baru dibuat  
    ```db.getUser("KelompokTKA2A")```
13. Sambungkan ke MongoDBCompass  
    ```mongodb://146.190.102.47:27017```  
14. Jika sudah bisa terhubung dengan Compass maka konfigurasi database berhasil.  

### Konfigurasi VM-1 (Worker 1)
1. Sambungkan terminal windows ke terminal vm.
   ```ssh root@152.42.226.87```
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/e69e9a9a-f83f-4bb0-b0ec-3c10f3a26cc0)  
   Masukkan password vm.  
2. Download semua resource keperluan dari github
   ```bash
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/index.html
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/styles.css
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/BE/sentiment-analysis.py
   ```
3. Lakukan beberapa command berikut untuk install nginx
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
4. Install dependency python
   ```bash
   sudo apt update
   sudo apt install python3 -y
   sudo apt install python3-pip -y
   sudo apt install python3.12-venv

   python3 -m venv myenv
   source myenv/bin/activate
   
   pip install flask
   pip install flask_cors
   pip install gunicorn
   pip install flask_pymongo
   pip install textblob
   pip install pymongo
   pip install gevent
   ```
5. Pindahkan index.html kedalam /var/www/html  
   ```mv index.html /var/www/html/index.html```  
6. Ubah cara fetch pada index.html agar mengarah ke ip worker  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5d53aa94-fa1a-4b62-8269-7d3dedc2e3a9)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/40c67a85-058d-466d-b3f8-6c71543099a5)  
7. Konfigurasikan /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f31e9a09-73e0-4abd-8f52-8b5503cc394b)  
   Tambahkan routing ke endpoint /analyze dan /history  
8. Konfigurasikan ip database pada file sentiment-analysis.py agar tersambung  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/eedac14a-3ad1-4bba-a7f2-45659bb832ca)  
9. Jika sudah restart nginx  
    ```sudo service nginx restart```  
10. Jalankan sentiment-analysis.py  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/26157122-dbcd-4e67-bbd6-599b732d07b1)  
11. Coba lakukan query untuk mengetes apakah berjalan dengan lancar  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/8cd4a7cf-e81a-4ec3-876e-5a9c16543163)  
    Jika muncul seperti gambar maka konfigurasi benar.  

### Konfigurasi VM-2 (Worker 2)  
1. Sambungkan terminal windows ke terminal vm.  
   ```ssh root@152.42.229.121```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/2024e70a-a1e0-4839-be45-6801a28178a4)  
   Masukkan password vm.  
2. Download semua resource keperluan dari github  
   ```bash
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/index.html
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/styles.css
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/BE/sentiment-analysis.py
   ```
3. Lakukan beberapa command berikut untuk install nginx
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
4. Install dependency python
   ```bash
   sudo apt update
   sudo apt install python3 -y
   sudo apt install python3-pip -y
   sudo apt install python3.12-venv

   python3 -m venv myenv
   source myenv/bin/activate
   
   pip install flask
   pip install flask_cors
   pip install gunicorn
   pip install flask_pymongo
   pip install textblob
   pip install pymongo
   pip install gevent
   ```
5. Pindahkan index.html kedalam /var/www/html  
   ```mv index.html /var/www/html/index.html```  
6. Ubah cara fetch pada index.html agar mengarah ke ip worker  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/de4a5033-16d6-459c-a2d3-cb597d6414bb)
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/955c5726-d483-4750-b1a7-22d4a295c22e)
7. Konfigurasikan /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/ae12a6c7-8f6a-4b3a-98c9-37460636f646)  
   Tambahkan routing ke endpoint /analyze dan /history  
8. Konfigurasikan ip database pada file sentiment-analysis.py agar tersambung  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/eedac14a-3ad1-4bba-a7f2-45659bb832ca)  
9. Jika sudah restart nginx  
    ```bash sudo service nginx restart```  
10. Jalankan sentiment-analysis.py  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/70c103c0-199d-4306-b310-b72545057335)  
11. Coba lakukan query untuk mengetes apakah berjalan dengan lancar  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/c73b8b6e-2d74-4b4c-aed0-8f6b32b79596)  
    Jika muncul seperti gambar maka konfigurasi benar.

### Konfigurasi VM-4 (Load-Balancer 1 Round-Robin)
1. Sambungkan terminal VM.  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/46ee167c-b5de-496e-a6c3-35cf2124f9f5)  
2. Lakukan beberapa command berikut untuk install nginx  
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
3. Konfigurasikan file default pada /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/62cce576-d1f0-4037-85e1-fb5388311ad8)  
4. Restart service nginx  
   ```sudo service nginx restart```  
5. Jika sudah test load-balancer dengan refresh page berkali-kali  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f950b386-6958-40f6-b514-0fc35efcb06e)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/9f2e40f4-3f01-47e0-b9c5-a91e37c947e9)  

### Konfigurasi VM-5 (Load-Balancer 2 Least-Connection) 
1. Sambungkan terminal VM.  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/b7e7d1d4-cfc8-4133-929d-3e373f8f10ce)  
2. Lakukan beberapa command berikut untuk install nginx  
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
3. Konfigurasikan file default pada /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/7b8362b6-a5cd-4d9d-8df8-01b8f10b01cd)  
4. Restart service nginx  
   ```bash sudo service nginx restart```  
5. Jika sudah test load-balancer dengan refresh page berkali-kali  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f566b9b1-59a5-4e92-b16d-78d78d9a08bc)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/1a361196-0730-49c8-a1e3-0d40fc5022cd)

---
### Revisi Implementasi
### Konfigurasi VM-3 (Load Balancer & Database)
#### Database:
1. Sambungkan terminal windows ke terminal vm.  
   ```ssh root@146.190.102.47```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f84cebf9-b7a4-400d-a95b-201cf0890b0c)  
   Masukkan password vm.
2. Jalankan beberapa command berikut untuk install MongoDB.
   ```bash
   sudo apt update
   sudo apt upgrade
   
   # Install dependency
   sudo apt install gnupg wget apt-transport-https ca-certificates software-properties-common
   echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list
   sudo apt-get update
   sudo apt-get install libssl1.1

   # Install mongodb
   curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
   sudo apt update
   sudo apt install mongodb-org -y
   ```
3. Enable MongoDB.
   ```bash
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```
4. Konfigurasi MongoDB  
   ```sudo nano /etc/mongod.conf```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/76e9f0cd-fe02-4a2a-99f6-2532385bc876)  
6. Restart service MongoDB  
   ```sudo systemctl restart mongod```  
8. Buka port pada firewall  
   ```sudo ufw allow 27017```  
9. Buka shell MongoDB  
   ```mongo```
10. Masuk sebagai user Admin  
    ```use admin```
11. Buat user Admin
    ```js
    db.createUser({
    user: "KelompokTKA2A",
    pwd: "KelompokTKA2A",
    roles: [{ role: "userAdminAnyDatabase", db: "admin" }]
    })
    ```
12. Cek user yang baru dibuat  
    ```db.getUser("KelompokTKA2A")```
13. Sambungkan ke MongoDBCompass  
    ```mongodb://146.190.102.47:27017```  
14. Jika sudah bisa terhubung dengan Compass maka konfigurasi database berhasil.  
#### Load Balancer:
1. Lakukan beberapa command berikut untuk install nginx  
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```  
2. Konfigurasikan file default pada /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/fbdcbd6e-3076-44ad-bd81-8fd49e086519)  

3. Restart service nginx  
   ```sudo service nginx restart```
4. Lakukan tuning pada konfigurasi nginx.conf
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/18f30bc0-09ba-45cc-a7a1-b9e5bab9ad49)
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5cc36f3a-3ae1-46e8-a3d8-7e379b3bc2ee)  
5. Restart kembali service nginx  
   ```sudo service nginx restart```

### Konfigurasi VM-1 (Worker 1)
1. Sambungkan terminal windows ke terminal vm.
   ```ssh root@152.42.226.87```
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/e69e9a9a-f83f-4bb0-b0ec-3c10f3a26cc0)  
   Masukkan password vm.  
2. Download semua resource keperluan dari github
   ```bash
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/index.html
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/styles.css
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/BE/sentiment-analysis.py
   ```
3. Lakukan beberapa command berikut untuk install nginx
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
4. Install dependency python
   ```bash
   sudo apt update
   sudo apt install python3 -y
   sudo apt install python3-pip -y
   sudo apt install python3.12-venv -y

   python3 -m venv myenv
   source myenv/bin/activate
   
   pip install flask
   pip install flask_cors
   pip install gunicorn
   pip install flask_pymongo
   pip install textblob
   pip install pymongo
   pip install gevent
   ```
5. Pindahkan index.html kedalam /var/www/html  
   ```mv index.html /var/www/html/index.html```  
6. Ubah cara fetch pada index.html agar mengarah ke ip worker  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5d53aa94-fa1a-4b62-8269-7d3dedc2e3a9)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/40c67a85-058d-466d-b3f8-6c71543099a5)  
7. Konfigurasikan /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f31e9a09-73e0-4abd-8f52-8b5503cc394b)  
   Tambahkan routing ke endpoint /analyze dan /history
8. Tuning konfigurasi pada nginx.conf
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/18f30bc0-09ba-45cc-a7a1-b9e5bab9ad49)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5cc36f3a-3ae1-46e8-a3d8-7e379b3bc2ee)  
9. Konfigurasikan ip database pada file sentiment-analysis.py agar tersambung  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/eedac14a-3ad1-4bba-a7f2-45659bb832ca)  
10. Jika sudah restart nginx  
    ```sudo service nginx restart```  
11. Jalankan sentiment-analysis.py  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/26157122-dbcd-4e67-bbd6-599b732d07b1)  
12. Coba lakukan query untuk mengetes apakah berjalan dengan lancar  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/8cd4a7cf-e81a-4ec3-876e-5a9c16543163)  
    Jika muncul seperti gambar maka konfigurasi benar.  

### Konfigurasi VM-2 (Worker 2)
1. Sambungkan terminal windows ke terminal vm.  
   ```ssh root@152.42.229.121```  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/2024e70a-a1e0-4839-be45-6801a28178a4)  
   Masukkan password vm.  
2. Download semua resource keperluan dari github  
   ```bash
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/index.html
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/FE/styles.css
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/BE/sentiment-analysis.py
   ```
3. Lakukan beberapa command berikut untuk install nginx
   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install nginx -y
   ```
4. Install dependency python
   ```bash
   sudo apt update
   sudo apt install python3 -y
   sudo apt install python3-pip -y
   sudo apt install python3.12-venv -y

   python3 -m venv myenv
   source myenv/bin/activate
   
   pip install flask
   pip install flask_cors
   pip install gunicorn
   pip install flask_pymongo
   pip install textblob
   pip install pymongo
   pip install gevent
   ```
5. Pindahkan index.html kedalam /var/www/html  
   ```mv index.html /var/www/html/index.html```  
6. Ubah cara fetch pada index.html agar mengarah ke ip worker  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/de4a5033-16d6-459c-a2d3-cb597d6414bb)
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/955c5726-d483-4750-b1a7-22d4a295c22e)
7. Konfigurasikan /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/ae12a6c7-8f6a-4b3a-98c9-37460636f646)  
   Tambahkan routing ke endpoint /analyze dan /history
8. Tuning konfigurasi pada nginx.conf
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/18f30bc0-09ba-45cc-a7a1-b9e5bab9ad49)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5cc36f3a-3ae1-46e8-a3d8-7e379b3bc2ee)  
9. Konfigurasikan ip database pada file sentiment-analysis.py agar tersambung  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/eedac14a-3ad1-4bba-a7f2-45659bb832ca)  
10. Jika sudah restart nginx  
    ```bash sudo service nginx restart```  
11. Jalankan sentiment-analysis.py  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/70c103c0-199d-4306-b310-b72545057335)  
12. Coba lakukan query untuk mengetes apakah berjalan dengan lancar  
    ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/c73b8b6e-2d74-4b4c-aed0-8f6b32b79596)  
    Jika muncul seperti gambar maka konfigurasi benar.
## Hasil Pengujian Endpoint  
### Uji Endpoint /analyze  
#### 152.42.229.121/analyze  
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/6306661d-3768-4473-ab89-05f90e191962)
#### 152.42.226.87/analyze
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/a47c71fe-46e2-4cf7-9feb-50b38ada1536)

### Uji Endpoint /history  
#### 152.42.226.87/history:  
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f7021abc-d066-4a56-927a-e34d3e101f3a)  
#### 152.42.229.121/history:  
![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/4c6a2489-9821-4ed8-9b82-3c73d6371fa6)  

## Hasil Pengujian Locust  
### Uji RPS Dalam 60 Detik
- **34.101.97.188**  
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f0e64cbe-1719-49c6-985e-bd42717e32b7)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/844062a3-4fae-4811-9fc4-0c085d016e3e)
  - Garis hijau menunjukkan RPS dari waktu ke waktu.
  - Grafik RPS menunjukkan nilai yang berfluktuasi, tetapi kita perlu mengidentifikasi RPS puncak sambil memastikan bahwa tingkat kegagalan tetap 0%.
  - Nilai RPS puncak diamati sekitar 25 permintaan per detik.

- **34.101.124.205**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5b18a892-112d-4267-9862-67258265f66c)  
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/e051af22-1b7b-4cff-8db2-3eb2b447c0b8)
  - Garis hijau menunjukkan RPS dari waktu ke waktu.
  - Grafik RPS menunjukkan nilai yang berfluktuasi, tetapi kita perlu mengidentifikasi RPS puncak sambil memastikan bahwa tingkat kegagalan tetap 0%.
  - Nilai RPS puncak diamati sekitar 20 permintaan per detik.

### Uji Peak Concurrency Dengan Spawn Rate 50/s
- **34.101.97.188**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/3caeb3a2-74c1-4616-a2f0-16b46ca1d970)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/8a33ef35-99db-4d25-a788-f2e06c4f6026)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 50 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

- **34.101.124.205**  
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5d1ad87d-8100-42d9-9de7-d5f4904b6ea4)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/115540b9-a23c-45d2-9480-465114f807c3)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 50 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

### Uji Peak Concurrency Dengan Spawn Rate 100/s
- **34.101.97.188**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/76f02003-1848-4d91-8988-26ebebac6e4d)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/e5dbb6e5-a6b9-4335-ae75-c10cb96e5d5b)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 100 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

- **34.101.124.205**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/814bba0f-4418-46a6-943b-cefee27e0830)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/3cec739c-8cfc-4519-9924-0aef474b99a3)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 100 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

### Uji Peak Concurrency Dengan Spawn Rate 200/s
- **34.101.97.188**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/c128c522-46c6-4b51-a1e2-f5014045e162)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/47cc6749-3bbd-45ab-81c5-b0febf05af35)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 200 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

- **34.101.124.205**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5f8af281-037a-489f-80fa-6356e610e053)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/7a324e0b-33fc-43ca-810a-ba7c060a4451)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 200 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 300 pengguna.

### Uji Peak Concurrency Dengan Spawn Rate 500/s
- **34.101.97.188**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/9a2fcd28-46ed-4523-9655-56d082469982)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/6c0d1982-a3f8-4aed-b772-69475cb87bda)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 500 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 500 pengguna.

- **34.101.124.205**
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/e17fd601-485f-4697-bbb8-329fece5ad18)
  ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/c0deeef2-eb37-4074-8117-3fdab01259d1)
  - Jumlah peak concurrency maksimum yang dapat ditangani server dengan tingkat pemunculan 500 pengguna per detik selama durasi 60 detik, dengan tingkat kegagalan 0%, adalah 500 pengguna.

## Kesimpulan dan Saran

1. Dari analisis hasil berdasarkan RPS :
   - Algoritme Round Robin mampu mencapai RPS maksimum yang lebih tinggi (25) dibandingkan dengan algoritme Least Connection (20).
   - Hal ini menunjukkan bahwa, untuk pengaturan dan skenario pengujian khusus ini, algoritma Round Robin memberikan kinerja yang lebih baik dalam hal menangani jumlah permintaan yang lebih tinggi per detik.

   - **Round Robin**:
     Lebih cocok untuk skenario di mana server memiliki kapasitas dan karakteristik kinerja yang sama, dan tujuannya adalah untuk memaksimalkan throughput.
   - **Least Connection**:
     Mungkin lebih efektif di lingkungan dengan server heterogen atau di mana tujuan utamanya adalah memastikan penyeimbangan beban berdasarkan beban server saat ini.

2. Dari analisis hasil berdasarkan spawn rate:

   a. Konsistensi di Kedua Algoritma:

      - Baik algoritme Round Robin maupun Least Connection mencapai peak concurrency maksimum yang sama pada semua skenario yang diuji. Hal ini menunjukkan bahwa dalam pengujian khusus 
      ini, tidak ada perbedaan kinerja yang signifikan antara kedua algoritme load balancing dalam hal menangani peak concurrency.

   b. Skalabilitas:

      - Kedua algoritme berhasil diskalakan untuk menangani peak concurrency maksimum yang diuji (hingga 500 pengguna) tanpa penurunan kinerja. Hal ini menunjukkan bahwa kedua 
      algoritme mampu menskalakan secara efektif dalam kondisi tertentu.

   c. Implikasi untuk Load Balancing:

      - Karena kedua algoritma berkinerja sama baiknya dalam hal mencapai konkurensi puncak maksimum, pilihan antara Round Robin dan Least Connection dapat didasarkan pada faktor-faktor 
      lain seperti:
        - Round Robin: Kesederhanaan dan pemerataan beban di seluruh server.
        - Least Connection: Penanganan ketidakseimbangan beban yang lebih baik dengan mengarahkan permintaan baru ke server yang tidak terlalu sibuk.
       
3. Saran

   Meskipun hasilnya menunjukkan tidak ada perbedaan dalam peak concurrency, metrik kinerja lain seperti respons time, failure, dan pemanfaatan sumber daya dapat memberikan wawasan tambahan. Sebagai contoh, pada tingkat pengujian dengan 500 tingkat pemijahan, server mulai menunjukkan tanda-tanda ketegangan, termasuk peningkatan respons time dan beberapa kegagalan. Hal ini menunjukkan bahwa meskipun 500 pengguna adalah batas atas, kinerja optimal mungkin berada pada tingkat concurrency yang sedikit lebih rendah untuk menghindari kegagalan dan mempertahankan waktu respons yang wajar, pengujian lebih lanjut dengan kondisi yang berbeda dan metrik yang lebih rinci mungkin diperlukan untuk membuat keputusan yang lebih tepat.
