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
   wget -qO- https://pgp.mongodb.com/server-7.0.asc | gpg --dearmor | sudo tee /usr/share/keyrings/mongodb-server-7.0.gpg >/dev/null
   echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/7.0 multiverse" | sudo tee -a /etc/apt/sources.list.d/mongodb-org-7.0.list
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
    ```mongodb://KelompokTKA2A:KelompokTKA2A@146.190.102.47:27017```  
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
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/Test/locustfile.py
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
   ```bash mv index.html /var/www/html/index.html```  
6. Ubah cara fetch pada index.html agar mengarah ke ip worker  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/5d53aa94-fa1a-4b62-8269-7d3dedc2e3a9)  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/40c67a85-058d-466d-b3f8-6c71543099a5)
7. Konfigurasikan /etc/nginx/sites-enabled/default  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/f31e9a09-73e0-4abd-8f52-8b5503cc394b)  
   Tambahkan routing ke endpoint /analyze dan /history  
8. Konfigurasikan ip database pada file sentiment-analysis.py agar tersambung  
   ![image](https://github.com/Rahmadaji18/fp-cloud-computing-a2/assets/62441217/eedac14a-3ad1-4bba-a7f2-45659bb832ca)
9. Jika sudah restart nginx
    ```bash sudo service nginx restart```
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
   wget https://raw.githubusercontent.com/fuaddary/fp-tka/main/Resources/Test/locustfile.py
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
   ```bash mv index.html /var/www/html/index.html```  
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

## Hasil Pengujian Endpoint

## Hasil Pengujian Locust

## Kesimpulan dan Saran
