Optimasi-Gudang-GA
Proyek ini bertujuan untuk mengoptimalkan penempatan barang di dalam gudang retail guna meminimalkan total jarak tempuh pengambilan barang (travel distance). Dengan menggunakan Algoritma Genetika (GA), sistem ini secara otomatis memetakan barang-barang dengan tingkat permintaan tinggi ke lokasi rak yang paling dekat dengan pintu keluar.

Penulis dari tugas ini adalah:
1. Rafi Dewantara Rachmat - 101032300130
2. Fauzan Ramdhani - 101032300110
3. Muhammad Afif Anwar - 101032300148

Fitur utama dari program ini adalah berikut:
Data Preprocessing: Pembersihan data otomatis dan agregasi nilai demand (permintaan) dari dataset transaksi penjualan.
Genetic Algorithm Optimization: Menggunakan representasi kromosom permutasi untuk menentukan urutan rak terbaik.
Fitness Function: Perhitungan efisiensi berdasarkan Manhattan Distance antara koordinat rak (grid 2D) dengan titik depot.
Advanced GA Operators: Implementasi Roulette Wheel Selection, Order Crossover (OX), dan Swap Mutation.
Visualisasi: Grafik konvergensi biaya (cost) dan pemetaan tata letak gudang dalam bentuk grid 2D.

Dataset yang digunakan adalah data transaksi Retail and Warehouse Sales yang mencakup:
ITEM CODE: Kode unik barang.
ITEM DESCRIPTION: Deskripsi nama barang.
WAREHOUSE SALES: Volume barang yang keluar dari gudang (sebagai penentu demand).

Bahasa: Python 3.x
Library Utama:
NumPy: Komputasi matriks koordinat.
Pandas: Manipulasi dan analisis dataset.
Matplotlib: Visualisasi layout dan grafik konvergensi.

Program ini bekerja dengan mengintegrasikan pengolahan data besar (Big Data) dan strategi evolusi biologi yang diterapkan melalui Algoritma Genetika. Secara garis besar, alur kerja sistem dibagi menjadi empat tahap utama:
1. Tahap Pra-pemrosesan Data (Preprocessing)
Sistem memulai dengan membaca dataset transaksi retail. Pada tahap ini, dilakukan pembersihan data (data cleaning) untuk memastikan tidak ada nilai kosong atau format yang salah pada kolom penjualan.
  Agregasi Demand: Program mengelompokkan data berdasarkan kode barang (ITEM CODE) dan menjumlahkan seluruh nilai WAREHOUSE SALES.
  Prioritas Barang: Hasil akhirnya adalah daftar barang yang diurutkan dari permintaan tertinggi (fast-moving) ke terendah (slow-moving). Barang dengan permintaan tinggi inilah yang menjadi prioritas utama untuk diletakkan di posisi paling strategis.

2. Representasi Ruang dan Pemetaan Jarak
Gudang direpresentasikan sebagai sebuah Grid 2D (matriks 10x10) yang memiliki 100 slot rak.
  Titik Depot: Pintu keluar gudang (Depot) ditetapkan pada koordinat (0,0).
  Perhitungan Jarak: Program menghitung jarak dari setiap slot rak ke Depot menggunakan rumus Manhattan Distance ($|x1 - x2| + |y1 - y2|$). Jarak ini mewakili seberapa jauh petugas harus berjalan untuk mengambil barang. Slot diurutkan dari yang terdekat hingga terjauh untuk memudahkan proses pemetaan oleh algoritma.

3. Proses Optimasi dengan Algoritma Genetika
Setelah persiapan data selesai, Algoritma Genetika mulai bekerja mencari susunan rak terbaik melalui siklus evolusi:
  Inisialisasi: Program membuat 80 kandidat solusi (populasi awal) yang berisi susunan tata letak barang secara acak.
  Evaluasi (Fitness Function): Setiap kandidat dinilai kualitasnya. Kualitas (fitness) dihitung berdasarkan total biaya perjalanan: $\sum (\text{Demand Barang} \times \text{Jarak Rak ke Depot})$. Semakin kecil biayanya, semakin tinggi nilai fitness-nya.
  Seleksi (Roulette Wheel): Solusi-solusi terbaik dipilih secara probablistik. Layout yang lebih efisien memiliki peluang lebih besar untuk menjadi "orang tua" bagi generasi berikutnya.
  Crossover & Mutasi: Pasangan layout terbaik disilangkan menggunakan Order Crossover (OX) untuk menghasilkan variasi baru tanpa merusak urutan unik barang. Swap Mutation juga dilakukan untuk menukar posisi dua barang secara acak guna mencegah algoritma terjebak pada solusi yang itu-itu saja.

4. Visualisasi dan Hasil Akhir
Proses evolusi dilakukan sebanyak 200 generasi. Di setiap generasi, sistem selalu menyimpan dua layout terbaik melalui mekanisme Elitism.
  Output Grafik: Program menampilkan grafik konvergensi yang menunjukkan penurunan total biaya perjalanan dari generasi ke-1 hingga ke-200.
  Output Layout: Hasil akhir ditampilkan dalam peta Grid 2D. Secara visual, akan terlihat bahwa barang-barang dengan volume penjualan besar telah berpindah secara otomatis ke area di dekat titik Depot (0,0), sehingga operasional gudang menjadi lebih efektif.




