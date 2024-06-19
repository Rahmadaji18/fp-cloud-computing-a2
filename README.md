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
| No. | Nama | Spesifikasi | Fungsi | Harga/Bulan |
| --- | --- | --- | --- | --- |
| 1. | KelompokTKA2A-VM1 | 2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64 | App Worker 1 | 18$ |
| 2. | KelompokTKA2A-VM2 | 2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64 | App Worker 2 | 18$ |
| 3. | KelompokTKA2A-VM3 | 2 Intel vCPU / 2GB Memory / 60GB Disk SSD / SGP1 - Ubuntu 24.04 (LTS) x64 | Mongo Database | 18$ |
| 4. | KelompokTKA2A-VM4 | 1 Intel vCPU / 1GB Memory / 10GB Disk SSD / Asia-Southeast2(Jakarta) - Ubuntu 24.04 (LTS) x64 | Load Balancer 1 (Round-Robin) | 6$ |
| 5. | KelompokTKA2A-VM5 | 1 Intel vCPU / 512MB Memory / 10GB Disk SSD / Asia-Southeast2(Jakarta) - Ubuntu 24.04 (LTS) x64 | Load Balancer 2 (Least-Connection) | 4$ |

## Implementasi

## Hasil Pengujian Endpoint

## Hasil Pengujian Locust

## Kesimpulan dan Saran
