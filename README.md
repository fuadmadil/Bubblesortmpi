# Panduan Instalasi MPI di Ubuntu Server
## Skema
![image](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/f8d0a758-04d8-4092-b9a8-b7510e6e417a)

## 1. Proses Awal
1. Persiapkan beberapa komputer dan tentukan satu sebagai master serta lainnya sebagai slave.
2. Pastikan semua komputer terhubung dalam satu jaringan.
3. Lakukan pembaruan dan peningkatan paket: **sudo apt update && sudo apt upgrade**

## 2. Pembuatan Pengguna Baru
Lakukan di Master dan Slave
1. Buat Pengguna <br> **sudo adduser <nama user>**
2. Berikan Hak Root <br> **sudo usermod -aG mpiuser**
3. Login ke Pengguna yang Dibuat <br> **su - mpiuser**

## 3. Instalasi MPICH
Lakukan di Master dan Slave
1. Pasang MPICH dan Paket Dokumentasi MPICH di Sistem <br> **sudo apt-get install -y mpich-doc mpich**
2. Periksa Versi MPI <br> **mpirun --version**
3. Uji Instalasi <br> **mpiexec -n <jumlah core> pyhton3 -m mpi4py.bench helloworld**
4. Pasang paket python mpi4py menggunakan pip untuk menjalankan python pada MPI <br> **pip install mpi4py -U**

## 4. Konfigurasi Berkas /etc/hosts
**sudo nano /etc/hosts**
1. Untuk Master <br>
   ![image1](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/4eebb045-9e2d-4c10-abc1-8cf37bb57704)
2. Untuk Slave <br>
   ![Image2](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/1b49e18a-57ec-4284-8dac-daf4ef5a97d6)

## 5. Instalasi SSH
Lakukan di Master dan Slave <br>
**sudo apt install openssh-server**
1. Buat Kunci <br> Lakukan pada master **ssh-keygen -t rsa**
2. Salin kunci publik ke klien <br> **ssh-copy-id <nama user>@<host>** <br>
   Ganti <nama user> dengan pengguna yang dibuat dan <host> dengan slave, lakukan pada semua slave.

## 6. Eksekusi MPI
Lakukan pada master <br> **mpiexec -n <jumlah core> python -m mpi4py.bench helloworld**<br>
<img width="404" alt="percobaan" src="https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/8e1d12c1-2d12-4016-afd9-341b1eea56e7">

# Tutorial Menjalankan Program Buble Sort Python dengan MPI
## 1. Pengaturan SSH untuk Semua Slave 
**ssh-copy-id user@hostname_or_ip**

## 2. Sisipkan Kode Program Buble Sort Python 
Berikut adalah potongan kode yang digunakan oleh kelompok kami <br>
![G2](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/06f0602c-f77c-4e96-a9cc-2bcae83c3c68)

## 3. Salin Berkas Python ke Semua Slave
**~path$ scp /path/to/locate/bin * user@hostname_or_ip:path/to** <br>
![image](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/d6455bd1-4c86-41e2-9116-f5648166b92c)

## 4. Hasil Uji Coba
![image](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/assets/145323449/72d92ade-9125-4b55-b043-add4c0e6ee1f)
