# Komponen- Komponen Kubernetes

1. Komonen master
Komponen master menyediakan control plane bagi klaster. Komponen ini berperan dalam proses pengambilan secara global pada klaster (contohnya, mekanisme schedule), serta berperan dalam proses deteksi serta pemberian respons terhadap events yang berlangsung di dalam klaster (contohnya, penjadwalan pod baru apabila jumlah replika yang ada pada replication controller tidak terpenuhi).

Komponen master dapat dijalankan di mesin manapun yang ada di klaster. Meski begitu, untuk memudahkan proses yang ada, script inisiasi awal yang dijalankan biasanya memulai komponen master pada mesin yang sama, serta tidak menjalankan kontainer bagi pengguna di mesin ini. Contoh konfigurasi multi-master VM dapat dilihat di modul Membangun Klaster HA.

2. Komponen Node
Komponen ini ada pada setiap node, fungsinya adalah melakukan pemeliharaan terhadap pod serta menyediakan environment runtime bagi Kubernetes.

3. Addons
Addons merupakan pod dan service yang mengimplementasikan fitur-fitur yang diperlukan klaster.

# Membuat Deployment
Kubernetes Pod adalah sekelompok satu atau lebih kontainer, yang diikat bersama-sama untuk keperluan administrasi dan jaringan. Kubernetes memeriksa kesehatan Pod dan restart kontainer jika Pod berakhir atau mati. Pengerahan adalah cara yang disarankan untuk mengelola pembuatan dan penskalaan Pod. Deployment adalah cara yang disarankan mengelola pembuatan Pod.

1. Menggunakan kubectl untuk membuat Deployment yang mengelola Pod. Pod menjalankan Container berdasarkan gambar Docker yang disediakan. Pada praktik ini saya menggunakan gambar yang ada di praktik 8 yaitu Python+Flask

![](image/1.png)

2. Melihat yang sudah di deploy dengan perintah kubectl get deployments dan akan muncul yang sudah di deploy, dan sudah muncul python+Flask

![](image/2.png)

3. Melihat Pod dengan perintah kubectl get pods, dan sudah muncul Podnya

![](image/3.png)

4. Melihat Cluster Event dengan perintah kubectl get events, dan akan muncul seperti gambar di bawah Instalasi

![](image/4.png)

5. Melihat config yang sudah dijalankan dengan perintah kubectl config view

![](image/5.png)

# Membuat Service

Secara default, Pod hanya dapat diakses oleh alamat IP internalnya di kluster Kubernetes. Agar Python Flask dapat diakses dari luar jaringan virtual Kubernetes, saya harus mengekspos Pod sebagai layanan Kubernetes.

1. Mengexpose pod pada internet public menggunakan perintah di bawah ini, setelah perintah dijalankan maka outputnya adalah service/pyton-flask exposed

![](image/6.png)

2. Melihat service yang sudah saya buat dengan perintah kubectl get Service

![](image/7.png)

3. Melihat hasil yang sudah kita buat dengan cara, klik tanda + kemudian masukkan port 30157, dan akan mengenerate, kemudian diarahkan ke hasil yang sudah kita buat.

![](image/8.png)
