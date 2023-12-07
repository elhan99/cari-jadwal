<template>
    <div>
    <h1>Cari Jadwal</h1>
      <input v-model="searchQuery" placeholder="Cari Nama Peneliti..." />
    <br><br>
      <div v-for="item in filteredItems" :key="item.id">
        Hari/ Tanggal : {{ item.hariTanggal }}<br>
        Bidang Fokus : {{ item.bidangFokus }}<br>
        Room : {{ item.room }}<br>
        Sesi : {{ item.sesi }}<br><br>



        
        <table id="customers">
  <tr>
    <th>No</th>
    <th>Nama</th>
    <th>Judul</th>
    <th>Skema</th>
    <th>Institusi</th>
    <th>Bidang Fokus</th>
    <th>Waktu</th>
  </tr>
  <tr>
    <td>{{ item.no1 }}</td>
    <td>{{ item.nama1 }}</td>
    <td>{{ item.judul1 }}</td>
    <td>{{ item.skema1 }}</td>
    <td>{{ item.institusi1 }}</td>
    <td>{{ item.bidangFokus1 }}</td>
    <td>{{ item.waktu1 }}</td>
  </tr>
  <tr>
    <td>{{ item.no2 }}</td>
    <td>{{ item.nama2 }}</td>
    <td>{{ item.judul2 }}</td>
    <td>{{ item.skema2 }}</td>
    <td>{{ item.institusi2 }}</td>
    <td>{{ item.bidangFokus2 }}</td>
    <td>{{ item.waktu2 }}</td>
  </tr>
  <tr>
    <td>{{ item.no3 }}</td>
    <td>{{ item.nama3 }}</td>
    <td>{{ item.judul3 }}</td>
    <td>{{ item.skema3 }}</td>
    <td>{{ item.institusi3 }}</td>
    <td>{{ item.bidangFokus3 }}</td>
    <td>{{ item.waktu3 }}</td>
  </tr>
  <tr>
    <td>{{ item.no4 }}</td>
    <td>{{ item.nama4 }}</td>
    <td>{{ item.judul4 }}</td>
    <td>{{ item.skema4 }}</td>
    <td>{{ item.institusi4 }}</td>
    <td>{{ item.bidangFokus4 }}</td>
    <td>{{ item.waktu4 }}</td>
  </tr>
  <tr>
    <td colspan="4">Diskusi</td>
    <td colspan="3">{{ item.diskusi }}</td>
  </tr>
  
</table>

            <br><br>
        </div>
    </div>
  </template>

  <style>
#customers {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#customers td, #customers th {
  border: 1px solid #ddd;
  padding: 8px;
}

#customers tr:nth-child(even){background-color: #f2f2f2;}

#customers tr:hover {background-color: #ddd;}

#customers th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}
</style>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  // Sample data
  const items = ref([
  { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '1',




no1: '1', nama1: 'Muhamad Syukur', judul1: 'Kajian Genetik dan Studi Pewarisan Karakter Kualitatif dan Kuantitatif Melon untuk Perbaikan Kualitas Buah ', skema1: 'PPS-PDD', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Muhamad Syukur', judul2: 'STUDI GENETIK SENYAWA FUNGSIONAL PADA OKRA (Abelmoschus esculentus L. Moench)', skema2: 'PPS-PDD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Netti Tinaprilla', judul3: 'Peran Smart Fertigasi dalam Usahatani Cabai di Indonesia ', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Dewi Sukma', judul4: 'Karakterisasi Profil Pigmen dan Ekspresi Gen Terkait Flavonoid/Antosianin pada Marigold Sudamala Barak (Tagetes patula)', skema4: 'PPS-PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '2',




no1: '5', nama1: 'Satriyas Ilyas', judul1: 'Efektifitas Nano Seed Coating Diperkaya Fungi Mikoriza Arbukula dalam Peningkatan Toleransi Jagung pada Cekaman Kekeringan', skema1: 'PPS-PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Satriyas Ilyas', judul2: 'Priming Nanopartikel Perak (AgNPs) untuk Peningkatan Produksi dan Mutu Benih Kedelai pada Cekaman Biotik dan Abiotik', skema2: 'PPS-PDD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Zakiah Wulandari', judul3: 'Produksi dan Karakterisasi Peptida Bioaktif dari Daging dan Telur Ayam Lokal IPB D1 untuk Meningkatkan Kesehatan dan Mendukung Tujuan Pembangunan Berkelanjutan', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Zakiah Wulandari', judul4: 'Optimasi Proses Pembuatan Tepung Kuning Telur Ayam IPB-D1 dengan Berbagai Metode Pengeringan', skema4: 'PPS-PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '3',




no1: '9', nama1: 'Sari Nurulita', judul1: 'Pemantauan Penyakit dan Pengembangan Metode Diagnostik Molekuler Untuk Meningkatkan Industri Jeruk di Indonesia', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Yulin Lestari', judul2: 'Rekayasa Rizosfer Tanaman Padi dan Bawang Merah Menggunakan Aktinobakteri Pemacu Pertumbuhan Tanaman', skema2: 'PT-JH', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Yanti Nuraeni Muflikh', judul3: 'MODEL SYSTEM DYNAMICS INTEGRASI SAPI POTONG - TANAMAN BERBASIS AGROFORESTRY UNTUK MENDUKUNG KEBERLANJUTAN DAN SWASEMBADA DAGING SAPI DI INDONESIA', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Zakiah Wulandari ', judul4: 'Kualitas Tepung Kuning Telur Ayam IPB-D1 dengan Berbagai Metode Pengeringan dan Aplikasinya pada Mayones', skema4: 'PTM', institusi4: 'IPB University ', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan dan Kesehatan',
room: '1',
sesi: '4',




no1: '13', nama1: 'Dewi Sukma', judul1: 'Karakterisasi Mekanisme Biokimia dan Molekuler untuk Pengembangan Strategi Pemuliaan dan Pengendalian Penyakit Busuk Lunak pada Anggrek Phalaenopsis ', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Elisabeth Sri Hendrastuti', judul2: 'Teknologi HTS dalam upaya pencegahan masuknya penyakit baru melalui impor benih bawang putih', skema2: 'PDUPT', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Elisabeth Sri Hendrastuti', judul3: 'Aplikasi NGS dan qPCR dalam metode penapisan ketahanan cabai terhadap penyakit daun keriting kuning cabai sebagai upaya peningkatan produksi cabai', skema3: 'PPS-PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Yusuf Ryadi', judul4: 'Stress Psikologis dan Kesehatan Ibu Hamil Keluarga Petani: Kaitannya dengan Pertumbuhan dan Perkembangan Bayi Baru Lahir', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '1',




no1: '1', nama1: 'IRMA ISNAFIA ARIEF', judul1: 'Karakterisasi Enzim Fitasi yang diproduksi oleh Lactobacillus plantarum IIA-1A5 serta Aplikasinya untuk Menurunkan Asam Fitat Kacang Koro pada Pembuatan Sosis', skema1: 'PPS-PDD', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'IRMA ISNAFIA ARIEF', judul2: 'Identifikasi Senyawa Antikanker dari Probiotik Lokal dan Aplikasinya pada Pembuatan Pangan Sehat Susu Fermentasi', skema2: 'PT-JH', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'ANAS DINURROHMAN SUSILA', judul3: 'PENETAPAN REKOMENDASI PEMUPUKAN PADA FERTIGASI TANAMAN CABAI MELALUI IRIGASI TETES MENGGUNAKAN FERADS (DECISION SUPPORT SYSTEM) DALAM PERTANIAN PRESISI ', skema3: 'PTUPT', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Anas D Susila', judul4: 'Penetapan Dosis Rekomendasi Pemupukan Fosfor Berdasarkan Analisis Tanah Menggunakan PUTK pada Fertigasi Tanaman Tomat ', skema4: 'PPS-PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '2',




no1: '5', nama1: 'Christina Eviutami Mediastika', judul1: 'Reviving immersive heritage tourims experiences using audiovisual technologi for open -air museums. Case Study: Kotagede Yogyakarta', skema1: 'UKICIS', institusi1: 'Universitas Ciputra', bidangFokus1: 'Pariwisata', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'DINAMELLA WAHJUNINGRUM', judul2: 'Potensi Bakteriofage Untuk Pengendalian Penyakit Akibat Infeksi Vibrio parahaemolyticus pada Udang Vaname', skema2: 'PPS-PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Eny Palupi', judul3: 'Sintesis Effect Size Respon Dosis Ultra-Processed Food terhadap Penyakit Tidak Menular', skema3: 'PPS-PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Eny Palupi', judul4: 'High-Fiber Extruded Purple Sweet Potato (Ipomoea batatas) and Kidney Bean (Phaseolus vulgaris) Extends The Feeling of Fullness', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '3',




no1: '9', nama1: 'Dinar Tri Soelistyowati', judul1: 'Domestikasi Dan Teknologi Reproduksi Untuk Pengembangan Budidaya Ikan Gabus Hias C. gachua', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Uswatun Hasanah', judul2: 'Seleksi Mikroba Asal Pangan Fermentasi dengan Kemampuan Deglikosilasi untuk Peningkatan Bioaktivitas Komponen Aktif', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Munif Ghulamahdi', judul3: 'Rotasi Tanam Bawang Merah-Kedelai Melalui Pemberian Amelioran Dan Aktinobakteri Pada Budidaya Jenuh Air Di Lahan Pasang Surut', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Munif Ghulamahdi', judul4: 'Penurunan Kadar Fe Pada Tanaman Padi Melalui Pemberian Asam Humat Pada Budidaya Jenuh Air Di lahan Sawah Pasang Surut', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '4',




no1: '13', nama1: 'Ridi Arif', judul1: 'Digital Twin Model untuk Diagnostik, Terapi, dan Pengendalian Helminthiasis pada Domba ', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Rika Zahera', judul2: 'Deteksi Proteksi Lemak Coconut Fatty Acid Distillate secara presisi menggunakan Near Infrared Reflectance Spectroscopy dan Pemanfaatannya dalam Ransum Sapi Perah', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Idat Galih Permana', judul3: 'Pengembangan Suplemen Protein Hijau Berbasis Leguminosa dalam Meningkatkan Produktivitas Kambing Perah', skema3: 'PPS-PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Idat Galih Permana', judul4: 'Suplemen Protein Terproteksi sebagai Suplai Rumen Undegradable Protein untuk Kambing Perah Laktasi Produksi Tinggi', skema4: 'PPS-PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '1',




no1: '1', nama1: 'Willy Bayuardi Suwarno', judul1: 'Pengembangan Varietas Melon Eksklusif untuk Budidaya dalam Greenhouse', skema1: 'PT-JH', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Muhammad Ridla', judul2: 'Kandungan karbohidrat struktural dan nonstruktural pada beberapa hijauan tropis hubungannya dengan fermentasi rumen dan produksi metana: studi in vitro', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Darda Efendi', judul3: 'Konservasi Terap (Artocarpus elasticus Reinw. ex Blume): Penyimpanan Benih, Penyimpanan Pertumbuhan Lambat, dan Kriopreservasi', skema3: 'PPS-PDD', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Darda Efendi', judul4: 'Identifikasi dan Karakterisasi Karotenoid dan Ekspresi Gen terkait Karotenoid pada Marigold untuk Mendukung Pemuliaan Tanaman Marigold', skema4: 'PPS-PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '2',




no1: '5', nama1: 'Anang Kurnia', judul1: 'Modified Generalized Lasso for Variable Selection in Lag Distributed Modeling of Fresh Fruit Bunch Production from Oil Palm Plantations in Riau-Indonesia', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Awang Maharijaya', judul2: 'Pengembangan Varietas Baru Bawang Merah Tahan Layu Fusarium', skema2: 'PTJH', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Arya Widura Ritonga', judul3: 'Perakitan Varietas Cabai Rawit Toleran Naungan Berdaya Hasil Tinggi dan Pengembangannya pada Sistem Budidaya Tumpang Sari dan Agroforestri', skema3: 'RIIM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Arya Widura Ritonga', judul4: 'Perakitan Varietas Unggul Jagung Manis Hibrida Beta Karoten dan Antosianin Tinggi untuk Mendukung Biofortifikasi Pangan', skema4: 'PTUPT', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '3',




no1: '9', nama1: 'Okti Syah Isyani Permatasari', judul1: 'Penyimpanan Umbi Talas dengan Perlakuan Coating dan Kondisi Ruang Simpan dalam Rangka Menyediakan Bahan Tanam Bermutu', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Jakaria', judul2: 'Penentuan Keragaman Genetik Kerbau Jambi Menggunakan Marka D- Loop Mitokondria', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Made Astawan', judul3: 'Potensi Tempe Koro Benguk untuk Memperbaiki Profil Biokimia Serum dan Fungsi Kognitif Tikus Percobaan', skema3: 'PDKN', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Made Astawan', judul4: 'Pengaruh Jenis Snack Bar terhadap Tingkat Rasa Kenyang dan Penerimaan Sensori pada Kelompok Usia Dewasa Awal', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '4',




no1: '13', nama1: 'Dase Hunaefi', judul1: 'Karakterisasi Profil Sensori dan Senyawa Volatil Pada Oncom Merah di Kecamatan Dramaga', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Tri Atmowidi', judul2: 'Kekayaan Spesies dan Karakteristik Pintu Masuk Sarang Lebah tak Bersengat (Hymenoptera: Apidae) di Taman Nasional Ujung Kulon', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Nadzirum Mubin', judul3: 'Pengaruh Insektisida Abamektin dan Profenofos terahadap Lebah Tanpa Sengat Tetragonula laeviceps Smith (Hymenoptera: Apidae: Meliponini)', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Hajrial Aswidinnoor', judul4: 'POLA AKUMULASI ZINC PADA ORGAN TANAMAN PADI, KANDUNGAN ASAM FITAT, GGE BIPLOT GALUR-GALUR PADI BIOFORTIFIKASI', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '1',




no1: '1', nama1: 'Arief Boediono', judul1: 'Analisis Viabilitas dan Sitokin Conditioned Medium Sel Punca Mesenkimal Wharton`s jelly Sapi Pasca Suplementasi dengan Serum Penyakit Respirasi', skema1: 'PPS-PDD', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Agus Setiyono', judul2: 'Isolasi Coxiella burnetii Asal Indonesia Melalui Teknik Propagasi In Vivo Sebagai Dasar Pengembangan Alat Diagnostik Cepat Q Fever', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Eti Rohaeti', judul3: 'AUTENTIKASI TEMPUYUNG (Sonchus arvensus) DALAM CAMPURAN TAPAK LIMAN (Elephantopus scaber L.) MENGGUNAKAN KOMBINASI FTIR-ATR DENGAN KEMOMETRIK ', skema3: 'PPS-PDD', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Eti Rohaeti', judul4: 'Pengembangan Metode Identifikasi dan Autentikasi Keji Beling dan Sidaguri Menggunakan Pendekatan Metabolomik Berbasis Kromatografi Cair (TLC, LC-MS/MS) dan Spektroskopi Inframerah', skema4: 'PFR', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '2',




no1: '5', nama1: 'Eti Rohaeti', judul1: 'Sensor Elektrokimia berbasis grafena oksida tereduksi didekorasi nanizyme untuk deteksi asam urat', skema1: 'PPS-PTM', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Rika Indri Astuti', judul2: 'Metabolit Bakteri Endofit dan Flavonoid asal Daun Cengkeh (Syzygium aromaticum) sebagai       Agen Anti -Genotoksik: untuk Pengembangannya Sebagai Agen Terapi Genetic Disorders', skema2: 'PD', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Kustiariyah', judul3: 'Imunostimulan Berbasis Fungi Laut dan Mekanisme Aksinya pada Lobster', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Annisa Utami Seminar', judul4: 'Peran Komunikasi Kesehatan dalam Meningkatkan Niat Konsumsi Tablet Tambah Darah pada Siswi', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '3',




no1: '9', nama1: 'Huda Shalahudin Darusman', judul1: 'Antibodi Monoklonal Amiloid Untuk Kit Penapisan Penyakit Saraf Degeneratif Alzheimer', skema1: 'LPDP ', institusi1: 'Pusat Studi Satwa Primata IPB', bidangFokus1: 'Kesehatan', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Huda Shalahudin Darusman', judul2: 'Eksosom Asal Sel Punca Mesenkimal Monyet Ekor Panjang Sebagai In Vitro Model Dalam Pengobatan Regeneratif dan Agen Terapeutik Kanker', skema2: 'PFR', institusi2: 'Pusat Studi Satwa Primata IPB', bidangFokus2: 'Kesehatan', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Hadri Latif', judul3: 'Analisis Whole Genome Sequencing pada Escherichia coli Resistan Antibiotik dari Peternakan Babi di Provinsi Banten', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Septian Rahardiantoro', judul4: 'Spatio-temporal Clustering using Generalized Lasso to Identify the Spread of Covid-19 in Indonesia according to Provincial Flight Route-based Connections', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '4',




no1: '13', nama1: 'Ani Kurniawati', judul1: 'Kajian Kriteria Panen dan Pola Pemanenan Bunga Kenanga (cananga odorata) untuk Menghasilkan Minyak Atsiri Bunga Berkualitas ', skema1: 'PPS-PTM', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Syaefudin', judul2: 'Optimasi Fermentasi Gandarusa oleh Aspergillus tamarii untuk Peningkatan Kapasitas Antioksidan dan Produksi Senyawa Fenolik serta Flavonoid', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Dwi Budiono', judul3: 'PEMANFAATAN SERUM DOMBA DARI LIMBAH PEMOTONGAN HEWAN SEBAGAI PENGENCER SEMEN DOMBA', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Dyah Iswantini', judul4: 'Biosensor Antioksidan Berbasis Multi-enzim dan Multivariat untuk Mendukung Kesehatan Pasca Pandemi COVID-19', skema4: 'PFR', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '5',
sesi: '1',




no1: '1', nama1: 'Puji Rianti', judul1: 'Keanekaragaman Komposisi Mikrobioma Usus Monyet  Ekor Panjang (Macaca Fascicularis) Berdasarkan Pakan  Berbeda Di Pusat Studi Satwa Primata (PSSP) IPB', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Etty Riani', judul2: 'Konsentrasi total timbal (Pb) di Desa Cinangka, Kecamatan Ciampea, Kabupaten Bogor, pasca ditinggalkannya kegiatan peleburan aki bekas tradisional', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Tutik Wresdiyati', judul3: 'Uji Toksisitas Subkronis Ekstrak Daun Undis (Cajanus Cajan) dan Jahe (Zingiber Officinale)                     pada Tikus Percobaan ', skema3: 'RIIM', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Syarifah Iis Aisyah', judul4: 'Polyphenol contents and antioxidant activity of Portulaca oleracea aereal parts extracts', skema4: 'PDUPT', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '5',
sesi: '2',




no1: '5', nama1: 'Tatacipta Dirgantara', judul1: 'DEVELOPMENT OF JAW SURGERY AND RECONSTRUCTION TOOLS MADE OF LOCAL MATERIALS', skema1: 'UKICIS', institusi1: 'Institut Teknologi Bandung', bidangFokus1: 'Kesehatan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Irzaman', judul2: 'Kemandirian Bangsa dalam Teknologi Proses Pembuatan Alat Deteksi Dini Pengukuran Kadar Hb Darah Non Invasif', skema2: 'LPDP', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Theresia Indah Budhy ', judul3: 'DETEKSI DINI KARSINOMA SEL SKUAMOSA DENGAN PROTEIN KHUSUS', skema3: '-', institusi3: 'Universitas Airlangga Surabaya – Indonesia', bidangFokus3: 'Kesehatan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Ekowati Handharyani', judul4: 'Perancangan Imunoglobulin Y (IgY) sebagai Agen Prophylaxis Potensial dalam Pengembangan Alat Diagnostik African Swine Fever Virus (ASFV) Asal Babi Hutan', skema4: 'PFR', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '5',
sesi: '3',




no1: '9', nama1: 'Tutik Wresdiyati', judul1: 'Extracts Daun Undis (Cajanus cajan) dan Jahe (Zingiber officinale) mengatasi hiperglikemia              pada Tikus Model Diabetes ', skema1: 'PTUPT', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Dyah Iswantini Pradono', judul2: 'Konsorsium Mikrob Saccharomyces cerevisiae dan Bacillus megaterium  sebagai Biosensor Etanol', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Didah Nur Faridah', judul3: 'Pengembangan Bubur Instan Rendah Indeks Glikemiks (IG) Berbahan Baku Talas Sutra, Jagung Manis dan Kacang Merah', skema3: 'PDUPT', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Hasim', judul4: 'Profil Komponen Bioaktif, Kemampuan Antioksidan, dan Potensi Penghambatan Lipase berbagai Fraksi Ekstrak Daun Kelor (Moringa oleifera)', skema4: 'PDUPT', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '5',
sesi: '4',




no1: '13', nama1: 'Jepri Agung Priyanto', judul1: 'Bioprospeksi Bacillus spp. Endofit asal Jengkol (Archidendron pauciflorum): Potensi Antimycobacterium dan Karakterisasi Genom lengkapnya', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Safika', judul2: 'ISOLASI BAKTERI ASAM LAKTAT PADA ORANGUTAN SUMATERA (Pongo abelii) LIAR SEBAGAI PROBIOTIK PENCEGAH INFEKSI SALURAN PENCERNAAN PRIMATA DI KEBUN BINATANG', skema2: 'PDUPT', institusi2: 'IPB University ', bidangFokus2: 'Kesehatan', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Mala Nurilmala', judul3: 'PENGEMBANGAN PRODUK BERBASIS KOLAGEN IKAN UNTUK KESEHATAN KULIT', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Kesehatan', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Aulia Andi Mustika', judul4: 'Potensi Ekstrak Kombinasi Biji Bengkuang dan Daun Sirih Merah Sebagai Bioinsektisida Miasis', skema4: 'Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '1',




no1: '1', nama1: 'Obie Farobie', judul1: 'A novel mesoporous catalyst derived from algae for biodiesel production using conventional, microwave, and subcritical methanol', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Elias Elias', judul2: 'Pemanfaatan dan Peningkatan Produktivitas Hutan Alam Terdegradasi Melalui Penerapan Teknologi Tanam Rumpang Dengan Jenis Unggulan Intoleran Setempat', skema2: 'RISPRO LPDP', institusi2: 'IPB University', bidangFokus2: 'Energi & SDAL', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Yuli Anggun Lestari ', judul3: 'Pengaruh konsentrasi perekat lateks pada kualitas briket cangkang buah karet (Havea Brasiliensis)', skema3: '-', institusi3: 'Universitas Jambi ', bidangFokus3: 'Energi & SDAL', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Iskandar Z. Siregar', judul4: 'Sekuensing Genom Kloroplas Calophyllum inophyllum dengan Teknologi Oxford Nanopore dan Penerapannya untuk Kajian Analisis Filogenetik ', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Energi & SDAL', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '2',




no1: '5', nama1: 'Obie Farobie ', judul1: 'High Value Chemicals And Syngas Production From Indonesian Marine Macro-Algae Under Sub- And Supercritical Conditions', skema1: 'RISPRO Kolaborasi Internasional', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Asmadi Saad', judul2: 'KARAKTERISTIK BEBERAPA SIFAT FISIK TANAH GAMBUT PADA BERBAGAI UMUR TANAMAN KELAPA SAWIT', skema2: '-', institusi2: 'Universitas Jambi', bidangFokus2: 'Energi & SDAL', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Hamim', judul3: 'Pemanfaatan Brassica juncea dan Amaranthus spinosus serta Cendawan Endofit untuk Fitomining Emas pada Media Tailing Tambang Emas', skema3: 'PTM', institusi3: 'IPB University ', bidangFokus3: 'Energi & SDAL', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'BAYU WINATA', judul4: 'POTENSI SIMPANAN KARBON PADA EKOSISTEM HUTAN HUJAN TROPIS DI TNGHS DENGAN CITRA SENTINEL-2A', skema4: 'Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Energi & SDAL', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '3',




no1: '9', nama1: 'Rika Indri Astuti', judul1: 'Karakterisasi Klaster Gen Adh Pengkode Enzim Alkohol Dehidrogenase dari Isolat -Isolat Khamir Indigenos Pichia spp. untuk Pengembangan Galur Khamir Etanologenik', skema1: 'PPS-PTM', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'R. R. Dyah Perwitasari', judul2: 'RE-EVALUASI SISTEMATIKA TAKSA KATAK MARUN MUTIARA (Nyctixalus margaritifer Boulenger 1882)', skema2: 'PPS-PDD', institusi2: 'IPB University', bidangFokus2: 'Energi & SDAL', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Udjiana Sekteria', judul3: 'Pemodelan Geostatistika Semivariogram Isotropik menggunakan Penaksiran Maksimum Likelihood (Studi Kasus: Lahan Gambut di Kalimantan)', skema3: 'UKICIS', institusi3: 'IPB University ', bidangFokus3: 'Energi & SDAL', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Lina Karlinasari', judul4: 'Biomekanika Pohon Hutan untuk Mendukung Kesehatan Ekosistem', skema4: 'PDUPT', institusi4: 'IPB University ', bidangFokus4: 'Energi & SDAL', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '4',




no1: '13', nama1: 'Budi Indra Setiawan', judul1: 'A new Method to identify patterns of wet and dry seasons  ', skema1: 'RKD', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Sachnaz Desta Oktarina', judul2: 'Modeling Retrospective Climate Effects with Quantile Regression Lasso in Estimating Oil Palm Productivity in Indonesia', skema2: 'Dosen Muda', institusi2: 'IPB University ', bidangFokus2: 'Energi & SDAL', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Lina Karlinasari', judul3: 'Pengembangan Produk Komposit Struktural CLT Hybrid Kayu Bambu (CLTB) Ramah Lingkungan dan Ramah Energi dengan Perekat Berbasis Melamin', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Energi & SDAL', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'LINA KARLINASARI', judul4: 'Pengembangan Teknologi Pemindaian Kondisi Internal Pohon Berbasis Tomografi Listrik', skema4: 'PDD', institusi4: 'IPB University ', bidangFokus4: 'Energi & SDAL', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '1',




no1: '1', nama1: 'Karlisa Priandana', judul1: 'Modifikasi Algoritma Ant Colony Optimization (ACO) sebagai Solusi Masalah Multi-Agent Task Allocation untuk Swarm Drone dalam Aplikasi Pertanian', skema1: 'PDUPT', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Hilya Mudrika Arini', judul2: 'ACCELERATING ADOPTION OF PHOTOVOLTAIC (PV) THROUGH BEHAVIOURAL INTERVENTIONS IN INDONESIA: Preliminary Key Policy Recommendations', skema2: 'UKICIS', institusi2: 'UGM', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Imas Sukaesih Sitanggang', judul3: 'Pembangunan Sistem Penilaian Agroekologi Kesesuaian Lahan untuk Bawang Putih (INA Agro-GARLIC)', skema3: 'PT-JH', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Imas Sukaesih Sitanggang', judul4: 'Analisis Sentimen Kebakaran Hutan dan Lahan menggunakan Salp Swarm Algorithm-Transfer Function (SSA-TF) sebagai Teknik Seleksi Fitur', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '2',




no1: '5', nama1: 'Istie Sekartining Rahayu', judul1: 'APLIKASI PARTIKEL NANO TiO2 PADA KAYU CEPAT TUMBUH DALAM RANGKA MENINGKATKAN KETAHANANNYA TERHADAP WEATHERING MELALUI TEKNOLOGI NANO COATING', skema1: 'PDKN', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Istie Sekartining Rahayu', judul2: 'Karakteristik Sifat Magnetik Kayu Sengon Terimpregnasi Nanopartikel Magnetit (Fe3O4) Yang Disintesis Dengan Metode Kopresipitasi', skema2: 'PPS-PTM', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Sam Herodian', judul3: 'RANCANG BANGUN WORK PLATFORM PEMANEN TBS KELAPA SAWIT', skema3: 'BPDPKS', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Sitti Yani', judul4: 'Simulasi Monte Carlo Muografi Pendeteksi Bagasi Penumpang di Bandara', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '3',




no1: '9', nama1: 'Arief Sabdo Yuwono ', judul1: 'Rancang bangun alat ukur dan peraga ISPU statis dan bergerak ', skema1: 'PT-JH', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Yuni Cahya Endrawati', judul2: 'Optimasi Produk Serat Sutra Unggul (Samia cynthia ricini) Menggunakan Response Surface Methodology Pada Proses Degumming', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Yeni Herdiyeni', judul3: 'PENGEMBANGAN MODEL DEEP LEARNING UNTUK IDENTIFIKASI KESEHATAN TANAMAN SINGKONG (MANIHOT ESCULENTA CRANTZ) MENGGUNAKAN CITRA UAV (UNMANED AREAL VEHICLE)', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Yeni Herdiyeni', judul4: 'Pengembangan Model Smart Count Stomata Untuk Penciri Karakter Ideal Varietas Unggul Nilam Berbasis Yolov5 (You Only Look Once)', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '4',




no1: '13', nama1: 'Chusnul Arif', judul1: 'Pengembangan Model Identifikasi Emisi Gas Rumah Kaca dari Padi Sawah dengan Berbagai Sistem Pengairan Berbasis Jaringan Saraf Tiruan', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '14.00 - 14.10',
no2: '14', nama2: 'Irzaman', judul2: 'Pembuatan Sensor Cahaya Berbasis Film Tipis Berstruktur Al/BST/Si (Metal Oksida Semikonduktor/MOS) serta Pengembangan Sensor Cahaya yang Berkelanjutan', skema2: 'RKI PTN BH', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '14.10 - 14.20',
no3: '15', nama3: 'Setia Natalia Br Brahmana ', judul3: 'Korelasi Antara Lama Fermentasi Serta Pengeringan Terhadap Mutu Bubuk Teh Hitam Di PTPN IV Unit Bah Butong Sumatera Utara ', skema3: '-', institusi3: 'Universitas Jambi', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '14.20 - 14.30',
no4: '16', nama4: 'Dearni Christina Saragih', judul4: 'Korelasi Karekteristik Kimia pada Beberapa Pangan Fungsional Berbasis Tepung Uwi terhadap Profil Gula Darah Konsumen', skema4: '-', institusi4: 'Universitas Jambi', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '1',




no1: '1', nama1: 'Sobir', judul1: 'Whole Genome Sequencing dan Analisis Transkriptomik pada Varietas Unggul Pinang Emas (Genjah) dan Pinang Betara (Dalam) Sebagai Strategi Efektif dalam Pelestarian Plasma Nutfah', skema1: 'PPS-PDD', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Wasrin syafii/Nur Adi Saputra', judul2: 'Kajian Struktur dan Pemanfaatan Karbon Aktif sebagai Material Elektroda Superkapasitor untuk Pengembangan Sistem Microgrid', skema2: 'PDD', institusi2: 'Pusat Riset Biomassa dan Bioproduk-BRIN', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Ronny Rachman Noor', judul3: 'Keragaman Gen MSTN pada Sapi Peranakan Ongole dan Asosiasinya dengan Bobot Badan', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Dede Hermawan', judul4: 'Ketahanan Glued Laminated Timber Polistirena terhadap Serangan Rayap Tanah ', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '8',
sesi: '3',




no1: '5', nama1: 'Asty Khairi Inayah Syahwani', judul1: 'Mapping potensi Lokasi Lembaga Keuangan Mikro', skema1: 'Dosen Muda', institusi1: 'IPB University ', bidangFokus1: 'Sosial Humaniora', waktu1: '13.00 - 13.10',
no2: '6', nama2: 'Bagus Sartono', judul2: 'The Implementation of Filter Feature Selection Method to Identify the Best Subset of Variables in Modeling of Food Insecurity in West Java', skema2: 'PDKN', institusi2: 'IPB University ', bidangFokus2: 'Sosial Humaniora', waktu2: '13.10 - 13.20',
no3: '7', nama3: 'Ernan Rustiadi', judul3: 'Evaluasi Keberlanjutan Kawasan DAS (Daerah Aliran Sungai) Ditinjau dari Perspektif Penataan Ruang di DAS Bengawan Solo Hulu, Kab. Wonogiri, Prop Jawa Tengah', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '13.20 - 13.30',
no4: '8', nama4: 'Herawati', judul4: 'MODEL PENERAPAN CONTROL ATMOSPHERIC STORAGE (CAS) PADA KOMODITAS BAWANG MERAH SEBAGAI SOLUSI CERDAS BAGI KESEJAHTERAAN PETANI DI ERA 4.0', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '4',




no1: '9', nama1: 'Ernan Rustiadi', judul1: 'Pengembangan Teknologi Pemetaan Presisi Populasi Spasial Kebun Kelapa Sawit Rakyat', skema1: 'LPDP', institusi1: 'IPB University ', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '14.00 - 14.10',
no2: '10', nama2: 'Ari Widyanti', judul2: 'ANALISIS INTENSI PENGGUNAAN AUTONOMOUS VEHICLE DI INDONESIA', skema2: 'UKICIS', institusi2: 'ITB', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '14.10 - 14.20',
no3: '11', nama3: 'Sesar Husen Santosa', judul3: 'STOCK CONTROL AND PRODUCTION SCHEDULE APPLICATION (SCAPSA) UNTUK PENENTUAN STOCK POSITION DAN JADWAL PRODUKSI OPTIMAL AIR MINUM DALAM KEMASAN GELAS DI PT NIRWANA TIRTA', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '14.20 - 14.30',
no4: '12', nama4: 'Heriansyah Putra', judul4: 'Soybean Crude Urease-Calcite Precipitation (SCU-CP) for Problematic Soils Improvement ', skema4: 'PDKN', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '9',
sesi: '1',




no1: '1', nama1: 'R. R. Dyah Perwitasari', judul1: 'Sistematika dan Filogeograf Macrobrachium yang Berhabitat Pada Air Asam Asal Sumatra dan Kalimanta', skema1: 'PPS-PDD', institusi1: 'IPB University', bidangFokus1: 'Kemaritiman', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Luky Adrianto', judul2: 'KAJIAN KEBIJAKAN DAN STRATEGI PENURUNAN EMISI KARBON PADA BLUE CARBON ECOSYTEMS : PERSPEKTIF    SISTEM SOSIAL-EKOLOGI', skema2: 'UKICIS', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Sukenda', judul3: 'Distribusi Vibrio parahaemolyticus pada Udang Vaname Litopenaeus vannamei Melalui Perendaman sebagai Model Infeksi Alami', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Kemaritiman', waktu3: '10.20 - 10.30',
no4: '4', nama4: 'Beata Ratnawati', judul4: 'Pengolahan Sampah Plastik Menggunakan Wadah Sampah Press Otomatis (WSPO)', skema4: 'Penelitian Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '9',
sesi: '2',




no1: '5', nama1: 'TRIDOYO KUSUMASTANTO', judul1: 'APLIKASI BLUE CARBON TRADING SEBAGAI UPAYA KONSERVASI MANGROVE DI PULAU BANGKA MELALUI PENDEKATAN SOCIAL-ECOLOGICAL SYSTEMS (SES) BERBASIS MODEL SPASIAL DINAMIK', skema1: 'PKDN', institusi1: 'IPB University ', bidangFokus1: 'Kemaritiman', waktu1: '11.20 - 11.30',
no2: '6', nama2: 'Hefni Effendi', judul2: 'Aplikasi eDNA untuk Biomonitoring Keanekaragaman Hayati Sungai', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'BISMAN NABABAN', judul3: 'Peningkatan Kualitas Data Tinggi Muka Laut di Indonesia dengan Retracking Waveform Satelit Altimeter menggunakan Kecerdasan Buatan', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Kemaritiman', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Nurjanah', judul4: 'Optimalisasi Pemanfaatan Rumput Laut Tropika Sebagai Bahan Baku Garam Diet dan Pupuk Organik Ramah Lingkungan', skema4: 'PTJH', institusi4: 'IPB University ', bidangFokus4: 'Kemaritiman', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '9',
sesi: '3',




no1: '9', nama1: 'Sugeng Heri Suseno', judul1: 'Evaluasi Efektivitas Metode Kristalisasi Suhu Rendah dan Kristalisasi Urea dalam Pembuatan Konsentrat Omega-3 Ikan Tuna (Thunnus sp.) ', skema1: 'RIIM', institusi1: 'IPB University', bidangFokus1: 'Kemaritiman', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Sugeng Heri Suseno', judul2: 'Pengembangan Produk Inovatif Virgin Deep Sea Fish Oil (VFO) sebagai Sediaan Suplemen Kesehatan untuk Peningkatan Imunitas dan Vitalitas Tubuh pada Masa Pandemi COVID-19', skema2: 'PTKN', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Kustiariyah ', judul3: 'Immunostimulant dari Fungi Laut', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Kemaritiman', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Etty Riani', judul4: 'Bioakumulasi Mikroplastik Dan Dampaknya Pada Sumberdaya Ikan Di Teluk Banten', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Kemaritiman', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '10',
sesi: '1',




no1: '1', nama1: 'Heru Purwandari', judul1: 'Perubahan Daya Dukung Lingkungan Desa di Kawasan Krisis Ekologi di Jawa Barat', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Defina', judul2: 'Kajian peran gender, komunikasi, interaksi, dan pengasuhan orang tua serta hubungannya dengan kesejahteraan keluarga nelayan  di pesisir Jawa Barat dalam menghadapi dinamika perubahan iklim', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Andrea Emma Pravitasari', judul3: 'Spatial Quantitative Zoning dan Model Pengembangan Wilayah Berbasis Daya Dukung Lingkungan untuk Mewujudkan Tata Ruang Pulau Jawa-Bali Berkelanjutan', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Arif Imam Suroso', judul4: 'Dampak Internet Terhadap Sektor Riil dan Perdagangan Global', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '10',
sesi: '2',




no1: '5', nama1: 'Tursina Andita Putri', judul1: 'Perbandingan Alternatif Model Peremajaan Kakao dengan Tanaman Sela di Kabupaten Pesawaran Provinsi Lampung', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'EKS Harini ', judul2: 'Tata kelola bahaya ekowisata di kawasan rawan bencana ', skema2: 'LPDP', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'Manuntun Parulian Hutagaol', judul3: 'Resolusi Konflik Dalam Penggunaan Sumberdaya Alam Danau Toba Menuju Pengembangan Perikanan Dan Pariwisata Internasional', skema3: 'LPDP', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '11.10 - 11.20',
diskusi: '',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '10',
sesi: '3',




no1: '9', nama1: 'Herry Suhardiyanto ', judul1: 'Pengembangan Sistem Kontrol Cerdas Berbasis Internet of Things untuk Budidaya Purwoceng sebagai Bahan Baku Industri Jamu', skema1: 'LPDP', institusi1: 'IPB University ', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Khairin Anisa', judul2: 'Studi Kombinasi Media tanam dan Debit Air Irigasi Tetes pada Budidaya Tanaman Seledri', skema2: '-', institusi2: 'Universitas Jambi', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Rima Fitria Adiati', judul3: 'Alkali Selulosa Tandan Sawit Sebagai Material Rotary Sensor Dalam Mendukung Otomatisasi Industri Pertanian', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Medhanita Dewi Renanti', judul4: 'Pemodelan Deep Learning dalam Pendeteksian Tangis Bayi', skema4: 'Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '11',
sesi: '1',




no1: '1', nama1: 'Ali Khomsan', judul1: 'Status gizi dan komposisi tubuh berhubungan dengan glukosa darah puasa pada kelompk dewasa perempuan', skema1: 'PDD', institusi1: 'IPB University ', bidangFokus1: 'Sosial Humaniora', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Dodik Ridho Nurrochmat', judul2: 'OPTIMASI MODEL PEMANFAATAN HUTAN UNTUK KESEJAHTERAAN MASYARAKAT', skema2: 'WCR', institusi2: 'IPB University ', bidangFokus2: 'Sosial Humaniora', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Dodik Ridho Nurrochmat', judul3: 'KAJIAN KOMPARASI ASPEK EKOLOGI, SOSIAL-EKONOMI, DAN PEMASARAN KOMODITAS MINYAK NABATI: STUDI KASUS MINYAK KANOLA, KEDELAI, BIJI BUNGA MATAHARI DAN KELAPA SAWIT DI ASIA, AFRIKA, EROPA DAN AMERIKA', skema3: 'BPDPKS', institusi3: 'IPB University ', bidangFokus3: 'Sosial Humaniora', waktu3: '10.10 - 10.20',
diskusi: '',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '11',
sesi: '2',




no1: '4', nama1: 'Rici Tri Harpin Pranata ', judul1: 'Strategi Komunikasi dalam Upaya Mitigasi Perubahan Iklim Berbasis Karbon Biru (Blue Carbon)', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '10.50 - 11.00',
no2: '5', nama2: 'Ratih Pratiwi', judul2: 'Rancangan Sistem Akuntansi Eduwisata pada One Home Farm Kota Bogor', skema2: 'Dosen Muda', institusi2: 'IPB University ', bidangFokus2: 'Sosial Humaniora', waktu2: '11.00 - 11.10',
no3: '6', nama3: 'Anna Fatchiya', judul3: 'Penguatan Tatakelola Sumberdaya Manusia dalam Ekosistem Merdeka Belajar Kampus Merdeka dari Kekerasan Berbasis Gender', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '11.10 - 11.20',
no4: '7', nama4: 'Irma Isnafia Arief', judul4: 'Pengembangan Produk Lokal Olahan Susu Dadih dan Dangke dengan Menggunakan Probiotik Indigenous Lactobacillus Plantarum IIA-1a5 yang Mempunyai Sifat Fungsional Antimikroba, Antioksidan dan Antihipertensi', skema4: 'RKI PTNBH', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '11',
sesi: '3',




no1: '7', nama1: 'Y. Aris Purwanto', judul1: 'Metode Praproses Spektrum NIR Berbasis CNN untuk Pendugaan Kualitas Beras', skema1: 'PDD', institusi1: 'IPB University ', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '13.00 - 13.10',
no2: '8', nama2: 'Y. Aris Purwanto', judul2: 'Pengembangan Model Multi Layer Classifier Menggunakan Metode Ensemble Learning Untuk Grading Brokoli', skema2: 'PDD', institusi2: 'IPB University ', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '13.10 - 13.20',
no3: '9', nama3: 'Y Aris Purwanto', judul3: 'Sistem Perangkat Cerdas Prediksi Perubahan Kualitas Buah Klimaterik Tropika untuk Mendukung Logistik 4.0 dalam Rangka Meningkatkan Ekspor', skema3: 'LPDP', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '13.20 - 13.30',
no4: '10', nama4: 'Siti Nikmatin', judul4: 'Pengembangan Untuk hilirisasi Rompi Anti peluru Berbahan Biomass Tandan Sawit', skema4: 'PTKN', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Kesehatan',
room: '11',
sesi: '4',




no1: '11', nama1: 'Anisa Rahma', judul1: 'Pengembangan Potensi Feces Kelelawar sebagai Alergen dan Fertilizer', skema1: 'Dosen Muda', institusi1: 'IPB University ', bidangFokus1: 'Kesehatan', waktu1: '14.00 - 14.10',
no2: '12', nama2: 'I Made Artika', judul2: 'Sonication-Maceration Solvent Extraction of Total Phenolic and Antibacterial Activity from Acanthus ilicifolius Leaves using D-Optimal Mixture Design', skema2: 'PDKN', institusi2: 'IPB University ', bidangFokus2: 'Kesehatan', waktu2: '14.10 - 14.20',
no3: '13', nama3: 'Siti Nurjanah', judul3: 'Prevalensi Cemaran Salmonella spp. dan Analisis Titik Kritis Cemaran pada Rantai Pasok Daging Ayam', skema3: 'PDUPT', institusi3: 'IPB University ', bidangFokus3: 'Kesehatan', waktu3: '14.20 - 14.30',
no4: '14', nama4: 'Dipo Aldila', judul4: 'Analisis Ekonomi Berbagai Alternatif Respon Awal Terhadap  Wabah Penyakit Mulut dan Kuku di Kabupaten Malang', skema4: 'UKICIS', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan',
room: '12',
sesi: '1',




no1: '1', nama1: 'Asep Gunawan', judul1: 'Investigasi Keragaman Gen CYP2A6 dan Gen FABP4 sebagai Marker Seleksi Kualitas Karkas dan Nilai Gizi Domba Sehat', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Asep Gunawan', judul2: 'Perbaikan Genetik Sifat Kolesterol, Mineral, Flavor dan Odor Berbasis Penanda Genetik OLFML3 dan ADH1C sebagai Penentu Kualitas Daging Domba Premium', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'I Komang Gede Wiryawan', judul3: 'Optimalisasi Pakan Babi Berbasis Hasil Samping Agroindustri Sebagai Subsitusi Pakan Komersial', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '4', nama4: 'Endang Warsiki', judul4: 'Rekayasa Kemasan Aktif dan Halokromik Cerdas Berbasis Nano Seng Oksida (nZnO) - Polianilin', skema4: 'PTM', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Senin, 11 Desember 2023',
bidangFokus: 'Pangan & Teknologi dan Rekayasa',
room: '12',
sesi: '2',




no1: '5', nama1: 'Slamet Susanto', judul1: 'Pencegahan Kejadian Pengkerutan dan Peningkatan Kualitas Buah Sbou Melalui Degreening pada Beberapa Suhu Penyimpanan', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'MUHAMAD ACHMAD CHOZIN', judul2: 'OPTIMASI UKURAN DAN BENTUK BUTIRAN BIOHERBISIDA BERBAHAN BAKU TEKI (Cyperus rotundus)  UNTUK PENGENDALIAN GULMA BERDAUN LEBAR', skema2: 'PT-JH', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '7', nama3: 'CHAERUL BASRI', judul3: 'Analisis Ekonomi Berbagai Alternatif Respon Awal Terhadap  Wabah Penyakit Mulut dan Kuku di Kabupaten Malang', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Imas Sukaesih Sitanggang', judul4: 'Model Optimasi Algoritma Machine Learning untuk Prediksi PM2.5 dari Kabut Asap hasil Kebakaran Hutan dan Lahan di Provinsi Riau', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Teknologi&Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',
},

// SELASA

{hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '1',




no1: 'No', nama1: 'Nama', judul1: 'Judul', skema1: 'Skema', institusi1: 'Institusi', bidangFokus1: 'Bidang Fokus', waktu1: 'Waktu',
no2: '1', nama2: 'Nisa Rachmania', judul2: 'Karakterisasi Biosurfaktan Asal Bakteri Penghambat Cendawan Patogen Tanaman Pangan ', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '08.50 - 09.00',
no3: '2', nama3: 'TRI ASMIRA DAMAYANTI', judul3: 'Aktivitas Antiviral Nanopartikel Kitosan dan Ekstrak Daun Bougainvillea spp. untuk Mengendalikan Virus Tumbuhan', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '09.00 - 09.10',
no4: '3', nama4: 'Edi Santosa', judul4: 'Adaptasi 17 Genotipe Tanaman Talas (Colacasia esculenta) Terhadap Perubahan Ketersediaan Air Tanah', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '09.10 - 09.20',
diskusi: '09.20 - 09.30',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '2',




no1: '5', nama1: 'Bramada Winiar Putra', judul1: 'ANALISIS EKOSISTEM HOLISTIK USAHA PEMBIAKAN SAPI POTONG SEBAGAI KONSTRUKSI DESAIN LIVESTOCK ESTATE', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Aris Tri Wahyudi', judul2: 'Aktinomiset Rizosfer Penghasil Enzim Glukanase dan Potensinya sebagai Pengendali Fungi Fitopatogen', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Henny Purwaningsih', judul3: 'Pengembangan Material Smart Food Packaging Berbasis Paduan Biopolimer untuk Monitoring Kualitas dan Keamanan Produk Pangan', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
diskusi: '10.20 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '3',




no1: '9', nama1: 'Bambang Sapta Purwoko', judul1: 'Pengembangan Varietas dan Teknologi Budidaya Padi Green Super Rice', skema1: 'RIIM I', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Bambang Sapta Purwoko ', judul2: 'Perakitan Varietas Padi Unggul Berdayahasil Tinggi, Tahan Hama Penyakit Penting dan Toleran Kekeringan ', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Sandra Arifin Aziz', judul3: 'Produksi flavonoid daun beluntas (Pluchea indica) dengan dosis pupuk kandang ayam ', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Aris Tri Wahyudi', judul4: 'Aktivitas Biopigmen Berwarna Merah dari Bakteri asal Tanah Rizosfer sebagai Agens Antimikrob dan Antioksidan', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '4',




no1: '13', nama1: 'Ratih Dewanti', judul1: 'Pemetaan Senyawa Antimikroba Bumbu Rendang terhadap Bakteri Patogen Pembentuk Spora dengan Pendekatan Metabolomik', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Desta Wirnas', judul2: 'Analisis Genetik dan Molekuler Sifat Waxy pada Sorgum Populasi Single Cross dan Populasi MAGIC', skema2: 'PDUPT', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Desta Wirnas', judul3: 'Studi Pewarisan dan Molekuler Sifat Waxy Pada Sorgum (Sorghum bicolor (L.) Moench)', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Ratih Dewanti', judul4: 'Phenotypic and Genotypic Screening of Bacillus cereus Local Isolates for Their Animicrobial Resistance Properties', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '5',




no1: '17', nama1: 'Sudarsono', judul1: 'Pengembangan Referensi Pan-Genom dan Penerapan Association Studies Pada Kelapa Sawit (Elaeis Guineensis Jacq.) Sebagai Percepatan Riset Bioteknologi Dan Pemuliaan Kelapa Sawit di Indonesia', skema1: 'BPDPKS', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Slamet Widodo ', judul2: 'Sistem Pendugaan Kandungan Gula Berbasis Portable NIR Spectroscopy Terintegrasi GIS untuk Mendukung Penerapan Pertanian Presisi pada Perkebunan Tebu Modern', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Dias Indrasti', judul3: 'Profil Volatilomik Produk Olahan Daging untuk Autentikasi Kehalalan', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
diskusi: '14.30 - 14.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '1',




no1: '1', nama1: 'Asadatun Abdullah', judul1: 'Pengembangan Metode Presisi untuk Screening dan Surveillance Mikroba Patogen Persisten pada Industri Pengolahan Ikan melalui Pendekatan Short-Read dan Long- Read Metagenomik', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Asadatun Abdullah', judul2: 'Kombinasi teknik Loop-Mediated Isothermal Amplification (LAMP) kolorimetri, marka gen mitokondria, dan probe fluoresensi untuk identifikasi onsite spesies ikan Alopias spp. sebagai pendukung perikanan berkelanjutan Indonesia', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Debora Kristin Panjaitna', judul3: 'Pengaruh konsentrasi natrium hidroksida (NaOH) dan natrium monokloroasetat (NaMCA) terhadap karakteristik carboxymethyl cellulose dari serat pinang ', skema3: '-', institusi3: 'Universitas Jambi', bidangFokus3: 'Pangan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Nur Rochmah Kumalasari', judul4: 'Studi Budidaya Gynura procumbens sebagai Green Concentrate dan Functional Plant untuk Peningkatan Imunitas dan Methane Reductor dalam Tubuh Ternak', skema4: 'PFR', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '2',




no1: '5', nama1: 'Widanarni', judul1: 'Penerapan Sistem Bioflok sebagai Anti Quorum Sensing untuk Pengendalian Penyakit Vibriosis pada Budidaya Udang Vaname', skema1: 'PT-JH', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'R. TONY IBNU SUMARDAYA WIJAYA PUSPITA', judul2: 'Deteksi air dan kontaminan bahan pangan berskala nano menggunakan molecular dynamics dan optika nonlinie', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Sri Murtini', judul3: 'PARAMETER GENETIK IGY (IMUNOGLOBULIN YOLK) DAN TITER ND (NEW DISEASE CASTLE) PADA AYAM IPB-D2 DAN IPB-D3', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Asep Sudarman', judul4: 'Evaluasi Suplementasi Sabun Kalsium Asal Minyak Maggot Serangga Hermetia Illucens Pada Pakan Untuk Meningkatkan Produksi Domba', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '3',




no1: '9', nama1: 'C Hanny WIjaya', judul1: 'Presisi Pengemulsi Guna Memperoleh Cloudifier Minyak Buah Merah Untuk Meningkatkan Kualitas Sensori dan Kapasitas Antioksidan Minuman Fungsional Berbasis Kumis Kucing', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'C Hanny WIjaya', judul2: 'Pengembangan Oncom dengan Kualitas Sensori, Gizi, dan Bioaktivitas Unggul : Penilaian Sensori dan Karakteristik Fisikokimia Oncom Merah dan Oncom Hitam Bogor', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 -11.10',
no3: '11', nama3: 'C Hanny Wijaya', judul3: 'Peningkatan Produksi dan Kualitas Eksosom-like (PDEN) dari Tiga Varietas Jahe dan Aplikasinya pada Pangan Fungsional', skema3: 'RKI PTNBH', institusi3: 'IPB University ', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Asep Sudarman', judul4: 'Pengembangan Ransum yang Efektif Untuk Mengatasi Penyakit Mulut dan Kuku Dengan Penambahan Herbal, Zink dan Selenium Guna Meningkatkan Daya Tahan Tubuh Sapi', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '4',




no1: '13', nama1: 'Krisantini', judul1: 'Studi Morfologi, Pertumbuhan dan DNA Barcoding untuk Identifikasi Genus Scindapsus', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Desi Nadalia', judul2: 'Mineralogi Tanah dan Hubungannya dengan Variasi Kalium Tanah pada Lahan Sentra Bawang Merah di Kabupaten Brebes, Jawa Tengah ', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Maya Utami', judul3: 'Pengaruh Penambahan Tepung Wortel Terhadap Sifat Fisik, Kimia, dan Organoleptik Cookies Modifikasi ', skema3: '-', institusi3: 'Universitas Jambi', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '5', nama4: 'Supriyono', judul4: 'Atractive Toxic Blood Sugar Bait (ATBSB) Sebagai Alternatif Pengendalian Nyamuk Vektor Demam Berdarah Dengue (Aedes Aegypti)', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '5',




no1: '16', nama1: 'Ikeu Tanziha', judul1: 'Determinan pemilihan konsumsi pangan', skema1: 'RKI PTNBH', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '17', nama2: 'Nabilla Rahma Aulia', judul2: 'Pengaruh Lama Perebusan Terhadap Aktivitas Antioksidan dan Karakteristik Fitokimia Minuman Herbal Akar Kancil (Smilax Zeylanica L.)', skema2: '-', institusi2: 'Universitas Jambi ', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '18', nama3: 'Ahmad Fauzan ', judul3: 'Kajian metode pengeringan daun kayu manis (cinnamomum Burmannii) terhadap sifat fitokimia antioksidan dan sensori teh herbal yang dihasilkan ', skema3: '-', institusi3: 'Universitas Jambi ', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
no4: '19', nama4: 'Indah Anggreini ', judul4: 'Kajian Penambahan Gula Stevia Pada Minuman Serbuk Akar Pasak Bumi Terhadap Karakteristik Fitokimia dan Aktivitas Antioksidan ', skema4: '-', institusi4: 'Universitas Jambi', bidangFokus4: 'Pangan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '1',




no1: '1', nama1: 'Rima Shidqiyya Hidayati Martin', judul1: 'Studi Potensi Gynura procumbens sebagai Sumber Hijauan Pakan Fungsional Peningkat Produktivitas dan Methane Reductor pada Ruminansia', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Sobir', judul2: 'Penyediaan dan Komersialisasi Benih Bermutu Varietas Unggul (200% Rata-Rata Produktivitas Nasional) yang didukung Teknologi Produksi Ramah Lingkungan dan Berkelanjutan untuk Meningkatkan Daya Saing Bawang Merah', skema2: 'RIIM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Agus Purwito', judul3: 'Pengembangan Varietas Kentang Unggul Tipe Industri Berdaya Hasil Tinggi', skema3: 'PTKN', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Sri Nuryati', judul4: 'Aplikasi Ekstrak Batang Pisang Ambon (EBPA) untuk Penanggulangan Penyakit Utama pada Budidaya Udang Vaname', skema4: 'PTJH', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '2',




no1: '5', nama1: 'Jakaria', judul1: 'Peningkatan  nilai tambah sapi Bali melalui cross-breeding dengan sapi Wagyu untuk menghasilkan bibit sapi potong  penghasil daging premium', skema1: 'RIIM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Jakaria', judul2: 'Eksplorasi gen MC1R, KIT, ASIP dan TYR sebagai marker genetik warna bulu pada sapi Bali', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Miftahudin', judul3: 'RESPON MORFOLOGI, FISIOLOGI, DAN METABOLIT TIGA GENOTIPE MELON ASAL INDONESIA PADA KONDISI CEKAMAN SALINITAS', skema3: 'RKI PTNBH', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'MIFTAHUDIN', judul4: 'Kombinasi Pemetaan Pautan dan Asosiasi, Pengembangan Marka, dan Introgresi Gen Arsitektur Tajuk dalam Upaya Perakitan Varietas Padi dengan Produktivitas Tinggi', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '3',




no1: '9', nama1: 'Hanifah N. Lioe', judul1: 'Proximate Composition of Dried Gracilaria sp. from Five Different Location', skema1: 'PDD', institusi1: 'IPB University ', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Hanifah Nuryani Lioe', judul2: 'Peptida Umami Asal Tauco: Isolasi Peptida Umami dan Sintesis Peptida Umami untuk Penentuan Umami Threshold beserta Aplikasi Peptida Umami untuk Produk Pangan', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Hanifah Nuryani Lioe', judul3: 'Eksplorasi Senyawa Umami pada Produk Fermentasi Ikan: Studi Peptida Umami pada Rusip', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Drajat Martianto', judul4: 'Efektifitas Perlakuan Model Edukasi Kombinasi Informasi dan Nudge dalam Menurunkan Prakek Menyisakan Makanan di Piring', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '4',




no1: '13', nama1: 'LILIS KHOTIJAH', judul1: 'Kualitas Sperma Domba yang Diberi Ransum Mengandung Minyak Maggot Terproteksi', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Awang Maharijaya', judul2: 'Seleksi Klonal Biji Tunggal untuk Menghasilkan Split Umbi Bawang Merah Berbasis Marka Molekuler', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Awang Maharijaya', judul3: 'Decision Support System towards Precision and Smart Farming for Vegetable Production ', skema3: 'LPDP', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Awang Maharijaya', judul4: 'Peningkatan Ketersediaan Dan Komersialisasi 10 Varietas Unggul Dan Benih Bermutu Cabai Dengan Produktivitas 150% Rata-Rata Nasional', skema4: 'RIIM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '3',
sesi: '5',




no1: '17', nama1: 'Mersi Kurniati', judul1: 'Optimasi Formulasi Pelepasan Pupuk Terkendali pada Hidrogel Berbahan Karagenan-AAm sebagai Agen Pembawa Pupuk', skema1: 'PDUPT', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Dian Eka Ramadhani', judul2: 'The Intestinal Microbial Diversity and Probiotics Selection in Pasific Whiteleg Shrimp Litopenaeus vannamei Fed with Cinnamaldehyde-Containing Feed', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Cece Sumantri', judul3: 'Pelepasan Calon Galur Betina IPB-D2 (G5) Tahan Penyakit dan Produksi Telur Tinggi serta Calon Galur Pejantan IPB-D3 (G4) Tumbuh Cepat dan Penghasil Daging Fungsional', skema3: 'Riset Aksi', institusi3: '', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
no4: '20', nama4: 'Windi Al Zahra', judul4: 'Pengaruh intervensi pakan yang berbeda terhadap emisi metana dari feses sapi dara', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '1',




no1: '1', nama1: 'Mohamad Rafi', judul1: 'PROFIL METABOLIT TIGA VARIETAS JERUK INDONESIA MENGGUNAKAN LC-MS/MS SERTA EVALUASI AKTIVITAS ANTIOKSIDANNYA', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Mohamad Rafi', judul2: 'Standardisasi Bahan Baku dan Ekstrak Pegagan (Centella asiatica) Menggunakan Metabolomik Berbasis Spektroskopi FTIR Dan LC-MS/MS serta Evaluasi Aktivitas Biologisnya', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Mohamad Rafi', judul3: 'IDENTIFIKASI SENYAWA ANTIOKSIDAN DAUN SAMBUNG NYAWA (Gynura procumbens [Lour]. Merr) MENGGUNAKAN PENDEKATAN METABOLOMIK BERBASIS LC-MS/MS', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Nurlela', judul4: 'Potensi Adenostemma lavenia, A. madurense, dan  A. platyphyllum sebagai Antibakteri: Pendekatan metabolomik, In Silico, dan In Vitro, serta Optimasi Ekstraksi', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '2',




no1: '5', nama1: 'Anom Bowolaksono', judul1: 'Incretin-based therapy, GLP-1 receptor agonist, for gestational diabetes traetment', skema1: 'UKICIS', institusi1: 'Universitas Indonesia', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Trivadila', judul2: 'Ekstrak Biji Asam Jawa sebagai Antidepresan: Optimisasi Ekstraksi, Evaluasi Profil Metabolit, dan Studi Mekanisme Inhibisi terhadap Monoamina Oksidase A secara in Vitro', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Dwi Utari Rahmiati', judul3: 'Stimulasi Nervus Vagus dengan Terapi Ultrasound untuk Penanganan Syok Hemoragi pada Hewan Model Kelinci New Zealand White', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Inge Permatasari', judul4: 'PENGARUH PARTIKEL NANOPLASTIK TERHADAP HISTOPATOLOGI HEPAR TIKUS (Rattus norvegicus)/THE EFFECT OF NANOPLASTIC PARTICLES ON THE LIVER  HISTOPATHOLOGY OF RATS (Rattus norvegicus)', skema4: '-', institusi4: 'Universitas Airlangga', bidangFokus4: 'Kesehatan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan',
room: '4',
sesi: '3',




no1: '9', nama1: 'Purwantiningsih', judul1: 'Prediksi Mekanisme Aktivitas Antikanker Melalui Penambatan Molekul serta Pemodelan Pembelajaran Mesin (ML) dan Jaringan Syaraf Konvolusional (CNN) Biflavonoid dari Genus Araucaria disertai Sintesis Turunan dan Uji In vitro-nya', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Yessie Widya Sari', judul2: 'Pasta Gigi Terfortifikasi Nanohidroksiapatit dan Senyawa Aktif Rimpang Temu Hitam: Upaya Minimalisasi Insidensi Karies Gigi di Indonesia', skema2: 'RISPRO LPDP', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Wini Trilaksani', judul3: 'Sediaan Kandidat Serum Antiaging Kolagen Gelembung Renang Ikan Manyung Melalui Teknologi Nano Formulasi', skema3: 'PDKN', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Rini Madyastuti Purwono', judul4: 'Formulasi ekstrak daun alpukat dan alang-alang dalam menghambat urolithiasis kalsium oksalat ', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '4',
sesi: '4',




no1: '13', nama1: 'Wisnu Ananta Kusuma', judul1: 'Prediksi Efek Samping Obat Tuberkulosis Menggunakan Klasifikasi Multilabel dengan Random Forest', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Wisnu Ananta Kusuma', judul2: 'Identifikasi Potensi Senyawa Bioaktif Teripang Keling sebagai Bahan Anti Kanker Menggunakan Machine Learning', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Neneng Rachmalia Izzatul Mukhlishah', judul3: 'AKTIVITAS ANTIBAKTERI FRAKSI KLOROFORM HERBA PEGAGAN (Centella asiatica) METODE SOKHLETASI TERHADAP ISOLAT KLINIS Pseudomonas aeruginosa', skema3: '-', institusi3: 'Universitas Mataram', bidangFokus3: 'Kesehatan', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Dian Herawati', judul4: 'Seleksi Kopi Unggul Indonesia sebagai Ingredien Minuman Fungsional Kaya Antioksidan', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '4',
sesi: '5',




no1: '17', nama1: 'Nugraha Edhi Suyatma', judul1: 'Controlled Release Ethanol Emitter dan Cinnamon Oil sebagai Kemasan Aktif Produk Roti', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Dian Herawati', judul2: 'Komponen bioaktif, zat gizi, sifat fungsional dan sensori kopi siap saji populer di Indonesia serta evaluasi manfaatnya untuk kesehatan', skema2: 'PKDN', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Evy Damayanthi', judul3: 'Uji Efikasi Puding Dan Suplemen Okra Ungu (Abelmoschus Esculentus L.) terhadap Perbaikan Biomarker Klinis dan Nutrigenomik Pada Penderita Diabetes', skema3: 'PT-JH', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '14.20 - 14.30',
no4: '20', nama4: 'Evy Damayanthi', judul4: 'PENGARUH SUPLEMENTASI VITAMIN D TERHADAP BIOAVAILABILITAS KALSIUM, PROFIL LIPID, EKSPRESI GEN (SNPS FOK1) DAN STATUS SISTEM IMUN PADA WANITA DEWASA', skema4: 'PDD', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '5',
sesi: '1',




no1: '1', nama1: 'Alimuddin', judul1: 'Evaluasi Pewarisan Marka SNP2- LYS-C, Ekspresi Gen Dan Daya Tahan Ikan Lele Generasi Kedua Terhadap Infeksi Aeromonas Hydrophila', skema1: 'PTM', institusi1: 'IPB University ', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Waras Nurcholis', judul2: 'Response surface modeling to optimize sonication extraction with the maceration method for the phenolic content and antioxidant activity of Justicia gendarussa Burm f.', skema2: 'PDKN', institusi2: 'IPB University ', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Mega Safithri', judul3: 'FORMULASI DAN PENGUJIAN AKTIVITAS ANTI AGING KULIT SEDIAAN SERUM BERBAHAN AKTIF NANO SIRIH MERAH DAN NANO PROPOLIS', skema3: 'PTKN', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Waras Nurcholis', judul4: 'Changes in volatiles compound profile and bioactivities of Curcuma xanthuria essential oils upon various shading ', skema4: 'PTM', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '5',
sesi: '2',




no1: '5', nama1: 'Wisnu Ananta Kusuma', judul1: 'Sintesis Dan Pengembangan Peptida Dari Venom Ular Tanah (Calloselasma Rhodostoma) Sebagai Agen Antikanker', skema1: 'RKI PTNBH', institusi1: 'IPB University ', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Nahrowi', judul2: 'Optimasi Protein Terlarut Bulu Ayam Menggunakan Larutan NaOH pada Pembuatan Kecap Manis', skema2: 'PDD', institusi2: 'IPB University ', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Nurheni Sri Palupi', judul3: 'Mewujudkan Ketersediaan Produk Pangan Intermediat dan Siap Santap Hipoalergenik Berbasis Komoditas Ikan Melalui Penerapan Teknologi Proses Pangan', skema3: 'PFR', institusi3: 'IPB University ', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Nurheni Sri Palupi', judul4: 'Aplikasi Teknologi Proses Iradiasi serta Proses Termal dalam Upaya Mengurangi Alergenisitas Udang Vaname (Littopenaeus vannamei) dan Udang Windu (Penaeus monodon) [Application of Irradiation and Thermal Process Technology to Reduce Allergenicity of White Shrimp (Littopenaeus vannamei) and Tiger Shrimp (Penaeus monodon)]', skema4: 'PTM', institusi4: 'IPB University ', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '5',
sesi: '3',




no1: '9', nama1: 'Sri Murtini', judul1: 'ANCAMAN INFEKSI Lagovirus PENYEBAB RABBIT HAEMMORHAGIC DISEASE (RHD) PADA TERNAK KELINCI SEBAGAI SUMBER PROTEIN ALTERNATIF', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'HERA MAHESHWARI', judul2: 'Efektivitas Antioksidan Nanopartikel Kuersetin Intranasal sebagai Terapi Awal pada Tikus Model Stroke Iskemik', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Wisnu Ananta Kusuma', judul3: 'Eksplorasi dan Analisis Potensi Senyawa Bioaktif pada Kemuning (Murraya paniculata) sebagai Antiobesitas dengan Menggunakan Pendekatan Network Pharmacology, Molecular Docking, dan Metabolomika', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Mokhamad Fakhrul Ulum', judul4: 'Teknik pencitraan ultrasonografi dan tomografi impedansi listrik pada potongan komersial daging sapi', skema4: 'RIIM', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '5',
sesi: '4',




no1: '13', nama1: 'Liwaul Muniroh', judul1: 'Pengaruh Ekstrak Rumput Laut Merah (Dichotomaria Obtusata) Sebagai Agen Antioksidan Terhadap Kerusakan Histologi Hepar Tikus (Rattus Norvegicus) Yang Terpapar Nanoplastik', skema1: '-', institusi1: 'Universitas Airlangga', bidangFokus1: 'Kesehatan', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Dyah Iswantini', judul2: 'Obat Herbal Terstandar Pelangsing Berbasis Ekstrak Asam Gelugur Yang Mempunyai Nilai Keekonomian Tinggi', skema2: 'LPDP', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Anna Rozaliyani', judul3: 'Improving the Diagnosis and Management of Chronic Fungal Lung Diseases Complicating Tuberculosis in Multiple Areas in Indonesia', skema3: 'UKICIS', institusi3: 'Universitas Indonesia', bidangFokus3: 'Kesehatan', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Srihadi Agungpriyono', judul4: 'Potensi ekstrak duri landak dalam persembuhan luka', skema4: 'PDUPT', institusi4: 'IPB University ', bidangFokus4: 'Kesehatan', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan dan Pangan',
room: '5',
sesi: '5',




no1: '17', nama1: 'Adillya Saputri', judul1: 'PENGARUH SUBSTITUSI TEPUNG TERIGU DENGAN TEPUNG PEPAYA (Carica papaya L.) PADA PEMBUATAN COOKIES TERHADAP SIFAT FISIK, KIMIA DAN ORGANOLEPTIK ', skema1: '-', institusi1: 'Universitas Jambi', bidangFokus1: 'Pangan', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Alfira Kinanti', judul2: 'Pengaruh Daya Lampu Neon terhadap Pertumbuhan dan Hasil Berbagai Varietas Tanaman Selada (Lactuca sativa L.) dengan Sistem Hidroponik NFT (Nutrient Film Technique)', skema2: '-', institusi2: 'Universitas Garut', bidangFokus2: 'Pangan', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Baba Barus', judul3: 'Early detection of rice damage due to drought and flood using spectral values', skema3: 'PFR', institusi3: 'IPB University ', bidangFokus3: 'Pangan', waktu3: '14.20 - 14.30',
diskusi: '14.30 - 14.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '1',




no1: '1', nama1: 'Hendradi Hardhienata ', judul1: 'Investigation of Perovskite Surfaces Using Nonlinear Bond Model', skema1: 'PDKN', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Hendradi Hardhienata', judul2: 'Investigation of Perovskite Surfaces Using Nonlinear Bond Model', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Energi & SDAL', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Sri Wilarso Budi R', judul3: 'Sinergi antara Fungi Mikoriza Arbuskula dengan Pot Organik dalam Meningkatkan Pertumbuhan Bibit Samanea saman pada Media Tanah Pasca Tambang', skema3: 'PDUPT', institusi3: 'IPB University', bidangFokus3: 'Energi & SDAL', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'ASMADI SAAD', judul4: 'KARAKTERISTIK SPASIAL DAN TEMPORAL KEJADIAN KEBAKARAN LAHAN GAMBUT ', skema4: '-', institusi4: 'UNIVERSITAS JAMBI', bidangFokus4: 'Energi & SDAL', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '2',




no1: '5', nama1: 'Hamim', judul1: 'Eksplorasi dan analisis tumbuhan hiperakumulator pada lahan pasca tambang nikel di Sulawesi Tenggara', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Hamim', judul2: 'Pemanfaatan Brassica juncea dan Amaranthus spinosus serta cendawan endofit untuk fitomining emas pada media tailing tambang emas', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Energi & SDAL', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Purwantiningsih', judul3: 'Hidrodeoksigenasi Palm Fatty Acid Distillate (PFAD) menjadi Green Diesel menggunakan Katalis Nikel Fosfida Berpenyangga Zeolit Alam Hierarki', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Energi & SDAL', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Imam Wahyudi', judul4: 'Mekanisme Pembentukan Kayu pada Pohon Cepat dan Lambat Tumbuh Berdasarkan Pinning Method (II): Laju pertumbuhan pohon jati dan waktu untuk pemulihan', skema4: 'PDD', institusi4: 'IPB University ', bidangFokus4: 'Energi & SDAL', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '3',




no1: '9', nama1: 'Ivan Permana Putra', judul1: 'Mengungkap Keragaman Jamur Liar Indonesia Sebagai Upaya Penguatan Pangkalan Data Hayati dan Ketahanan Pangan Masyarakat', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Muhammad Alam Firmansyah', judul2: 'POTENSI MINYAK ATSIRI SEBAGAI FUNGISIDA NABATI UNTUK PENGENDALIAN PATOGEN DI PERSEMAIAN YANG RAMAH LINGKUNGAN', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Energi & SDAL', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Gilang Ayuningtyas', judul3: 'Integrasi Puyuh-Maggot “Pumagg” Pada Peternakan Puyuh Arkan Quail Farm: Implementasi Model Ekonomi Sirkular', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Energi & SDAL', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Faozan', judul4: 'Hidrogenasi CO2 menjadi Asam Format pada Permukaan Katalis N3Cu-Graphene', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Energi & SDAL', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Energi & SDAL',
room: '6',
sesi: '4',




no1: '13', nama1: 'Adisti Permatasari Putri Hartoyo', judul1: 'APLIKASI MICROFERTILIZERS DAN SEED BOMB UNTUK PERTUMBUHAN JELUTUNG RAWA (Dyera polyphylla (Miq.) Steenis) DAN PADI (Oryza sativa L.) PADA TANAH GAMBUT', skema1: 'PDUPT', institusi1: 'IPB University', bidangFokus1: 'Energi & SDAL', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Kaswanto', judul2: 'Pemanfaatan Jasa Lanskap Kebun Campuran untuk Pembangunan Desa Berbasis Data Desa Presisi', skema2: 'PTM', institusi2: 'IPB University ', bidangFokus2: 'Energi & SDAL', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Kaswanto', judul3: 'Manajemen Jasa Lanskap Agroforestri pada Ruang Terbuka Hijau dan Biru sebagai Perwujudan Kota dan Komunitas yang Berkelanjutan', skema3: 'PTJH', institusi3: 'IPB University ', bidangFokus3: 'Energi & SDAL', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Prijanto Pamoengkas', judul4: 'Kajian Teknik Silvikultur Intensif (Silin) dalam Pengelolaan Hutan Alam Produksi', skema4: 'PDD', institusi4: 'IPB University ', bidangFokus4: 'Energi & SDAL', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '1',





no1: 'No', nama1: 'Nama', judul1: 'Judul', skema1: 'Skema', institusi1: 'Institusi', bidangFokus1: 'Bidang Fokus', waktu1: 'Waktu',
no2: '1', nama2: 'Muhammad Asyhar Agmalaro', judul2: 'Dashboard Interaktif Simulasi lintasan dan Emisi Polutan Kabut Asap Dampak Kebakaran Hutan dan Lahan (Karhutla)', skema2: 'Dosen Muda', institusi2: 'IPB University ', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '08.50 - 09.00',
no3: '2', nama3: 'Agus Buono', judul3: 'OPTIMASI MODEL HYBRID CONVOLUTIONAL NEURAL NETWORK (CNN) UNTUK DEFECT DETECTION PADA EXTRUSION-BASED 3D FOOD PRINTING', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '09.00 - 09.10',
no4: '3', nama4: 'Agus Buono', judul4: 'Optimasi Algoritma Convolutional Neural Network (CNN) Untuk Defect Detection pada Extrusion-Based 3D Food Printing	', skema4: 'PDD', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '09.10 - 09.20',
diskusi: '09.20 - 09.30',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '2',




no1: '5', nama1: 'Toni Bakhtiar', judul1: 'Strategi Pengendalian Penyebaran Penyakit Menular Multivarian dengan Kapasitas Vaksinasi Terbatas', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Faldiena Marcelita', judul2: 'Pengembangan Alat Pencacah Daun Bambu Kering untuk Media Tanam Skala Rumah Tangga dengan Inovasi Sensor dan Fuzzy Logic', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'KUDANG BORO SEMINAR', judul3: 'Pengembangan Sistem Cerdas dan Presisi Pemilihan dan Rekomendasi Makanan Komersial Berbasis Status Gizi Konsumen Spesifik', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Medhanita Dewi Renanti', judul4: 'Pemodelan Bispektrum dan Recurrent Neural Network untuk Mengatasi Noise pada Sistem Pengenalan Tangis Bayi', skema4: 'Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '3',




no1: '9', nama1: 'Eti Rohaeti', judul1: 'Evaluasi mutu bahan baku tempuyung (Sonchus arvensis) menggunakan profil metabolit serta aktivitas antioksidan dan inhibisi xantin oksidase', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Arinana', judul2: 'Bioaktivitas Ekstrak n-heksana Akar Anakan Kayu Putih sebagai Pemikat Rayap Tanah Coptotermes curvignathus Holmgrenn (Isoptera{ Rhinotermitidae)', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Arinana', judul3: 'Dekomposer Kayu pada Enam Jenis Kayu Rakyat di Dua Lokasi Berbeda', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Lailan Syaufina', judul4: 'SIPAKAR (Sistem Penilaian Tingkat Keparahan Area Pasca Kebakaran Hutan dan Lahan)', skema4: 'PKDN', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '4',




no1: '13', nama1: 'Harsi Dewantari Kusumaningrum', judul1: 'Potensi Bakteriosin dari Bakteri Asam Laktat asal Pado sebagai Biopreservatif Pangan', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Yessie Widya Sari', judul2: 'Biomimetik Mineralisasi Tulang dan Gigi Menggunakan Nanokomposit Hidroksiapatit/Asam Amino Terkonjugasi Partikel Emas', skema2: 'WCR', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Yessie Widya Sari', judul3: 'Scaffold Nanofiber Polianilin/Hidroksiapatit/Asam Amino untuk Rekayasa Jaringan Tulang', skema3: 'RKI PTNBH', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Irmanida Batubara', judul4: 'Membran Optode Untuk Deteksi Logam Berat Pencemar Lingkungan: Fabrikasi, Uji Kinerja, Dan Evaluasi', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '7',
sesi: '5',




no1: '17', nama1: 'Harsi Dewantari Kusumaningrum', judul1: 'Potensi buah sagu Metroxylon Rottb. bubuk sebagai sumber prebiotik pangan', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Despal', judul2: 'Komparasi Akurasi Kalibrasi Database Basah dan Kering Hijauan Pakan Sapi Perah Menggunakan Near-Infrared Reflectance Spectroscopy ', skema2: 'PTM', institusi2: 'IPB University ', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Despal', judul3: 'Optimalisasi Pemanfaatan Lemak Sawit Terproteksi Ca-Soap pada Sapi Perah di Daerah Tropis', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '14.20 - 14.30',
no4: '20', nama4: 'Despal', judul4: 'Pengembangan Suplemen Mineral Berbasis Dietary Cation Anion Difference untuk Sapi Perah Menggunakan Pendeteksi Presisi Near Infrared Reflectance Spectroscopy ', skema4: 'PFR', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '1',




no1: '1', nama1: 'Purwantiningsih', judul1: 'Rekayasa Material Peredam Getaran Jenis Viskoelastik dari Komposit Partikulat-Kompon Karet Alam', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Trisna Priadi', judul2: 'Sifat Mekanis, Ketahanan Api dan Biodeteriorasi dari Kayu Manii Termodifikasi Senyawa Boron dan Minyak Nabati', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Andik Pribadi', judul3: 'Variasi Spasiotemporal Polutan PM2.5 di Jalan Raya Kota Bogor Berdasarkan Instrumen Pemantauan Bergerak', skema3: 'Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Hermin Indah Wahyuni', judul4: 'Pemanfaatan Platform Digital “Symbolic” sebagai Upaya Menata Ekologi Informasi Guna Mencapai Well-Informed Society', skema4: 'UKICIS', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '2',




no1: '5', nama1: 'Walidatush Sholihah', judul1: 'Deteksi Kualitas Air pada Budidaya Ikan Arwana Menggunakan Simonair (Sistem Monitoring Kualitas Air) Berbasis IoT dengan Machine Learning', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Cindy Rianti Priadi', judul2: 'Optimasi Anaerobik Digester untuk Limbah Ikan: Pengaruh Rasio Limbah Ikan, Sisa Makanan, Kotoran Sapi, dan Serbuk Gergaji Terhadap Produksi Biogas dan Reduksi Padatan', skema2: 'UKICIS', institusi2: 'Universitas Indonesia', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Pingkan Nuryanti', judul3: 'Percancangan Roof Garden Berbasis Landscape Engineerinh pada gedung pendidikan kampus IPB', skema3: 'Dosen Muda', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Erliza Hambali', judul4: 'Teknologi Produksi Oleokimia Sukrosa Ester dan Aplikasinya Pada Produk Skin Cream Skala Industri Kecil dan Menengah', skema4: 'BPDPKS', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '3',

descZoom: '',

no1: '9', nama1: 'Wayan Darmawan', judul1: 'Wood quality improvement by non biocide method based on thermal and chemical midification', skema1: 'WCR', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Zaenal Abidin', judul2: 'Adsorpsi Ion Cr(VI) pada Layered Double Hydroxide MgAl dan MgAlFe serta Mekanisme Reduksinya secara In Situ dengan Ion Fe(II)', skema2: 'PTM', institusi2: 'IPB University ', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '11.00 -11.10',
no3: '11', nama3: 'Zaenal Abidin', judul3: 'Desain dan Optimasi Filter Nanokamposit Zeolit Oksida serta Uji Multilokasinya', skema3: 'RIIM', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Zaenal Abidin', judul4: 'Sintesis dan Karakterisasi Nanopartikel ZnO serta Enkapsulasinya', skema4: 'PTUPT', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '4',




no1: '13', nama1: 'I Wayan Budiastra', judul1: 'Rekayasa Sistem Deteksi Mutu Buah Sawit Secara Non Destruktif Berbasis Electrical Impedance Spectroscopy', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '13.00 - 13.10',
no2: '14', nama2: 'Wayan Darmawan', judul2: 'Quality improvement of short rotation teak by non biocide methods based on thermal and chemical modifikation.', skema2: 'WCR', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '13.10 - 13.20',
no3: '15', nama3: 'Wayan Darmawan', judul3: 'Physical Properties of Short Rotation Teak Through Chemical Modification with Lactic Acid, Citric Acid, and Glycerol', skema3: 'PDD', institusi3: 'IPB University ', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '13.20 - 13.30',
no4: '16', nama4: 'Imam Wahyudi', judul4: 'Evaluasi Karakteristik Kayu Mangium (Acacia mangium Willd.) Hasil Kegiatan Pemuliaan', skema4: 'PTM', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '8',
sesi: '5',




no1: '17', nama1: 'I Wayan Budiastra', judul1: 'Pengembangan Model Jaringan Syaraf Tiruan dan Near-Infrared Spectroscopy untuk Prediksi Kandungan Kimia Buah Sawit Secara Non-Destruktif', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '14.00 - 14.10',
no2: '18', nama2: 'Sesar Husen Santosa', judul2: 'STOCK CONTROL AND PRODUCTION SCHEDULE APPLICATION (SCAPSA) UNTUK PENENTUAN STOCK POSITION DAN JADWAL PRODUKSI OPTIMAL AIR MINUM DALAM KEMASAN GELAS DI PT NIRWANA TIRTA', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '14.10 - 14.20',
no3: '19', nama3: 'Irzaman', judul3: 'Implementasi Sensor Ba0.5Sr0.5TiO3 (BST) Yang Didadah RuO2 Sebagai Pendeteksi Dini Diabetes Militus Dengan Metode Non-Invasive Berbasis Hembusan Bau Mulut', skema3: 'PTKN', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '14.20 - 14.30',
no4: '20', nama4: 'Mahdi Mubarok', judul4: 'Adhesion Performance of Furfurylated Wood Veneers in Plywood Bonded with Polyurethane and Epoxy Adhesives', skema4: 'Dosen Muda', institusi4: 'IPB University ', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '14.30 - 14.40',
diskusi: '14.40 - 15.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '9',
sesi: '1',




no1: '1', nama1: 'Kastana Sapanli', judul1: 'Identifikasi Nilai Ekonomi Stok Karbon Mangrove di TWA Jering Menduyung, Provinsi Kepulauan Bangka Belitung', skema1: 'PKDN', institusi1: 'IPB University ', bidangFokus1: 'Kemaritiman', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Yudi Setiawan', judul2: 'Model Spasial-Adaptif dan Desain Restorasi dan Rehabilitasi Blue Carbon Mangrove Berbasis Kerentanan Pesisir', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Achmad Farajallah', judul3: 'Survei Mitogenomik Kepiting Pasir di Bagian Barat Indonesia dan Garis Wallacea: kepiting pasir (hippoid crab) di Pulau Enggano, Bengkulu', skema3: 'PDUPT', institusi3: 'IPB University', bidangFokus3: 'Kemaritiman', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Supriyanto', judul4: 'Data Analitik dan Inovasi Perangkat Lunak Berbasis Drone dan Machine Learning untuk Tanaman Hortikultura Guna Mendukung Pengembangan Agromaritim 4.0 di Indonesia', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kemaritiman', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Kesehatan, Pangan dan Sosial Humaniora',
room: '9',
sesi: '2',




no1: '5', nama1: 'Rudi Heryanto', judul1: 'Integrating UPLC-Q-Orbitrap base Metabolite Profiling and Network Pharmacology Strategy for Multicomponent-multitarget Prediction of Annona muricata as Anticancer', skema1: 'PFR', institusi1: 'IPB University ', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Laksmi Ambarsari', judul2: 'Extraction of phenolic antioxidant compounds from Orthosiphon stamineus leaves by Saccharomyces cerevisiae ATCC-9763 fermentation', skema2: 'PDKN', institusi2: 'IPB University ', bidangFokus2: 'Kesehatan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Puspo Edi Giriwono', judul3: 'Strengthening sustainable fish food systems in Indonesia and Cambodia with innovative high- quality and affordable Ready-to-Use Fish Foods (RUFF) to Address Intergenerational malnutrition: a South-East Asian – European partnership.', skema3: 'RKD', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Tatik Chikmawati', judul4: 'Etnoekologi Tanaman Pangan Belitung dalam Upaya Diversifikasi Pangan Lokal', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '10',
sesi: '1',

no1: '1', nama1: 'Sumardjo', judul1: 'Transformasi menuju Pangan Sehat berbasis Bio-cylo Farming pada Pemberdayaan Masyarakat Peri-Urban', skema1: 'PDUPT', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Sumardjo', judul2: 'SINKRONISITAS  MEDIA PERSPEKTIF KOMUNIKASI LINGKUNGAN MEREHABILITASI SUNGAI DARI LIMBAH DOMESTIK', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Djuara Lubis', judul3: 'PROGRAM KOMUNIKASI DALAM PENANGANAN TUBERKULOSIS DI KOTA BANDUNG', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Djuara Pangihutan Lubis', judul4: 'MEMBANGUN RESILENSI MELALUI PROSES KOMUNIKATIF PADA WARGA TERDAMPAK PROYEK PEMBANGUNAN ', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '10',
sesi: '3',




no1: '5', nama1: 'Dede Aulia Rahman', judul1: 'Metode Operasional Berbasis Fotogrametri Drone untuk Menentukan Umur dan Ukuran Populasi Gajah Sumatera', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'Rahman Setiawan', judul2: 'Pengembangan Teknologi Sistem Penggerask Listrik Untuk Bus Listrik Sedang', skema2: 'UKICIS', institusi2: 'ITB', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '11.00 -11.10',
no3: '7', nama3: 'Sony Hartono Wijaya', judul3: 'Sistem Perangkat Cerdas Monitoring dan Klasifikasi Kesehatan Kuda Berbasis AIoT Untuk Mendukung Indonesia 4.0 dalam Pembuatan Antisera', skema3: 'LPDP', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '11.10 - 11.20',
no4: '8', nama4: 'Suhono Harso Supangkat', judul4: 'DIGITAL TWIN JALAN DAN JEMBATAN', skema4: 'UKICIS', institusi4: 'UGM', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Sosial Humaniora dan Kemaritiman',
room: '10',
sesi: '4',




no1: '9', nama1: 'Amiruddin Saleh', judul1: 'Penerapan teknologi & kelembagaan usahatani padi kawasan berkelanjutan untuk meningkatkan produktivitas, kesejahteraan petani berbasis Agromaritim Cerdas Industri 4.0', skema1: 'PT-JH', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '13.00 - 13.10',
no2: '10', nama2: 'Illah Sailah', judul2: 'Strategi Pengembangan Sumber Daya Manusia Unggul Pada Agroindustri Gula Tebu di Era Industri 4.0', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '13.10 - 13.20',
no3: '11', nama3: 'Amiruddin Saleh', judul3: 'Model Komunikasi Keluarga dalam Praktek Nilai Budaya 4S di kelembagaan Zeinial Kecamatan Tamansari.', skema3: 'PDD', institusi3: 'IPB Universitt', bidangFokus3: 'Sosial Humaniora', waktu3: '13.20 - 13.30',
no4: '12', nama4: 'Sri Pujiyati', judul4: 'Pemetaan Spasial Habitat Bentik Perairan Dangkal Menggunakan Remote Sensing dan Machine Learning: Komparasi dan Integrasi Data Hidroakustik dan Inderaja Optik', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Kemaritiman', waktu4: '13.30 - 13.40',
diskusi: '13.40 - 14.00',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '11',
sesi: '2',




no1: '1', nama1: 'Risma Yuliana', judul1: 'Pengaruh Konsentrasi Maltodekstrin sebagai Bahan Penyalut terhadap Karakteristik Enkapsulasi Cabai Merah Bubuk', skema1: '-', institusi1: 'Universitas Jambi', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Bambang Purwantara', judul2: 'Identifikasi Marker-Assisted Fertility and Freezability (MAFF) berbasis Multi-Omics dalam Mendukung Seleksi dan Pengafkiran Sapi Pejantan Unggul', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '3', nama3: 'Bambang Purwantara', judul3: 'Kajian Berbasis Omics (Transcriptomic dan Proteomic) pada Tingkat Kemampuan Fertilisasi Spermatozoa dan Perkembangan Embrio In Vitro sebagai Biomarker Penentu Fertilitas Sapi Bali (Bos sondaicus)', skema3: 'RKI PTNBH', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
diskusi: '10.20 - 10.50',

}, {hariTanggal: 'Selasa, 12 Desember 2023',
bidangFokus: 'Pangan',
room: '11',
sesi: '3',




no1: '5', nama1: 'Nancy Dewi Yuliana', judul1: 'Metabolomics Approach Using Lc-Ms/Ms Combined With Chemometrics And Real-Time Pcr For Halal Authentication Of Food And Pharmaceutical Products', skema1: 'RKI PTNBH', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '6', nama2: 'PURWIYATNO HARIYADI', judul2: 'KAJIAN PRODUKSI DAN STABILISASI MINYAK IKAN PETEK (Leiognathus equulus) SERBUK MENGGUNAKAN METODE PENDINGINAN SEMPROT', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 -11.10',
no3: '7', nama3: 'Nancy Dewi Yuliana', judul3: 'Metabolomics approach to reveal the potential of Indonesian local edible mushrooms as sources of bioactive compound', skema3: 'PKDN', institusi3: 'IPB University ', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
diskusi: '11.20 - 11.40',

},

// RABU


{ hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '1',




no1: '1', nama1: 'Wahyu Ramadhan', judul1: 'SINTESIS COMPLEX HYBRID GEL DARI HASIL SAMPING INDUSTRI PERIKANAN DAN APLIKASINYA SEBAGAI BUTTER SUBSTITUTE DALAM PRODUK KONFEKSIONERI', skema1: 'Penelitian Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Roedhy Poerwanto', judul2: 'Teknik Percepatan Transisi Juvenil Tanaman Buah Lokal dengan Cahaya Buatan melalui Pendekatan Multiomics', skema2: 'PDUPT', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Noviyan Darmawan', judul3: 'Uji Kinerja Metode ddPCR untuk Autentikasi Gelatin dan Produk Makanan Olahan', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Panca Dewi Manu Hara Karti', judul4: 'Keanekaragaman Vegetasi Alami di Lahan Reklamasi Pascatambang Kapur dan Evaluasi Ketersediaan Nutriennya untuk Ternak', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '2',




no1: '5', nama1: 'Rika Raffiudin', judul1: 'Evolusi Lebah Apis cerana di Indonesia: Pendekatan Morfologi dan Molekuler', skema1: 'PD', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Deden Derajat Matra', judul2: 'Karakterisasi Marka Spesifik Berbasis Pendekatan Genomik dan Transkriptomik untuk Mempercepat Program Pemuliaan dan Peningkatan Kualitas Buah Lokal', skema2: 'PDKN', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Luki Abdullah', judul3: 'Produksi Biomassa Nutrien Sorgum Samurai  Pola Ratun', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Luki Abdullah', judul4: 'Kajian Agronomis dan Nutrisi Kacang Koro (Canavalia ensiformis) Sebagai Sumber Pakan', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '1',
sesi: '3',




no1: '9', nama1: 'Deden Derajat Matra', judul1: 'Prospek Pengembangan Climate-Resilient Crop melalui Paparan Sinar Ultraviolet-B untuk Induksi Gen Ketahanan Tanaman Bawang Merah terhadap Cekaman Lingkungan.', skema1: 'RKI', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Baba Barus', judul2: 'Deteksi dini kerusakan padi berbasis teknologi penginderaan jauh dan geospasial untuk mendukung ketahanan pangan', skema2: 'PD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'Candra Budiman', judul3: 'Pengembangan metode uji cepat vigor benih kedelai dan kacang panjang melalui pemunculan radikula menggunakan pengolahan citra digital', skema3: 'Penelitian Dosen Muda', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Didah Nur Faridah', judul4: 'Pengembangan Bubur Instan Rendah indeks Glikemik Berbahan Baku Talas Sutra, Jagung Manis dan Kacang Merah', skema4: 'PDUPT', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '1',




no1: '1', nama1: 'Wulan Tri Wahyuni', judul1: 'Sensor Elektrokimia Berbasis Polimer Konduktif untuk Deteksi Residu Pestisida Organofosfat pada Buah dan Sayur secara in-situ', skema1: 'PKDN', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Wulan Tri Wahyuni', judul2: 'Elektrode Berbasis Grafena Oksida/PEDOT:PSS Termodifkasi Nanozyme untuk Sensor Pencemar Hidrazina di Lingkungan Perairan', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Deden Derajat Matra', judul3: 'Respons Fisiologi dan Pertumbuhan Bibit Tanaman Jambu Air (Syzygium Aqueum) Terhadap Perbedaan Intensitas dan Spektrum Cahaya Buatan Light Emitting Diode', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Azis Boing Sitanggang', judul4: 'Karakterisasi dan Stabilitas dari Sistem Multifase yang Terdiri Atas Minyak Sawit Merah dan Air dengan Partikel Nano Seng Oksida sebagai Penstabil', skema4: 'PFR', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '2',




no1: '5', nama1: 'Roedhy Poerwanto', judul1: 'Respons Fisiologi dan Produksi Tomat Mikrotom terhadap Cahaya Buatan Light Emmitting Diode dengan Pendekatan Transkriptomik dan Metabolomik', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Wulan Tri Wahyuni', judul2: 'Sensor Elektrokimia Berbasis Elektrode Termodifikasi Nanopartikel Logam untuk Deteksi Residu Pestisida Karbaril dalam Produk Pertanian', skema2: 'RKI', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Azis Boing Sitanggang', judul3: 'Peptida Bioaktif Bersifat Antioksidan dari Tempe Koro Benguk: Desain Reaktor Sintesis, Produksi Kontinu dan Karakterisasi Aktivitas Biologisnya', skema3: 'RIIM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Hasim', judul4: 'Profil Komponen Bioaktif, Kemampuan Antioksidan, dan Potensi Penghambatan Lipase berbagai Fraksi Ekstrak Daun Kelor (Moringa oleifera)', skema4: 'PDUPT', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '2',
sesi: '3',




no1: '9', nama1: 'Wahyu Ramadhan', judul1: 'Sistem Model Emulsion-Templated (HIPE) Marine Oil sebagai Penstabil Omega-3 dan Structuring Gel: Bifungsionalitas Protein Oleogel Complexes', skema1: 'PFR', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Ridwan Diaguna', judul2: 'Imbibisi, Viabilitas dan Vigor Benih Sorgum setelah Penyimpanan', skema2: 'Penelitian Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'MIFTAHUDIN', judul3: 'Pemetaan Genetik, Pengembangan Marka Molekuler, dan Introgresi Gen Arsitektur Malai dalam Upaya Perakitan Varietas Padi Tipe Baru dengan Produktivitas Tinggi', skema3: 'RIIM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Azis Boing Sitanggang', judul4: 'Peptida Bioaktif dari Susu Kambing: Analisis Antioksidan, Inhibitor Angiotensin Converting Enzyme (ACE), dan Inhibitor α-amilase', skema4: 'PDKN', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kesehatan',
room: '3',
sesi: '1',




no1: '1', nama1: 'Iriani Setyaningsih', judul1: 'Bioaktivitas dari mikroalga Spirulina platensis yang dikultivasi dalam media pupuk', skema1: 'RIIM', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Deny Setyo Wibowo', judul2: 'Metode Diagnosa Cepat Mastitis Subklinis Berbasis Teknologi Pencitraan Kamera Pendeteksi Panas pada Sapi Perah', skema2: 'Penelitian Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'CAHYO BUDIMAN', judul3: 'Sialil Oligosakarida asal Kolostrum Kambing Perah Lokal Sebagai Kandidat Antivirus SARS Cov-2 Penyebab Covid-19', skema3: 'PDKN', institusi3: 'IPB University', bidangFokus3: 'Kesehatan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Popi Asri Kurniatin', judul4: 'Eksplorasi Plant Antimicrobial Peptida (PAMP) dari tanaman asli Indonesia dengan pendekatan insilico dan invitro untuk bahan baku obat dan kosmetika', skema4: 'PFR', institusi4: 'Institut Pertanian Bogor', bidangFokus4: 'Kesehatan', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kesehatan',
room: '3',
sesi: '2',




no1: '5', nama1: 'Aep Setiawan', judul1: 'IMPLEMENTASI AUTOMATISASI "INTARA" SEBAGAI FASILITAS KESEHATAN HEWAN DI POLIKLINIK HEWAN SEKOLAH VOKASI IPB UNIVERSITY', skema1: 'Penelitian Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'YULIANA MARIA DIAH RATNA DEWI', judul2: 'Peningkatan metabolit sekunder tanaman kitolod (H. longiflora) dengan teknik kultur jaringan untuk mendapatkan senyawa bioaktif antikanker', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Kesehatan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Marianti A. Manggau', judul3: 'UJI AKTIVITAS FUKOIDAN SEBAGAI ANTIKOAGULAN MELALUI SISTEM PENGHANTARAN TRANSDERMAL DISSOLVING MICRONEEDLES', skema3: 'UKICIS', institusi3: 'Universitas Hasanuddin ', bidangFokus3: 'Kesehatan', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Sri Anna Marliyati', judul4: 'Efektivitas  pemberian bubur kanji rumbi instan  dan stimulasi psikososial terhadap pertumbuhan dan perkembangan motorik anak baduta gizi kurang', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kesehatan',
room: '3',
sesi: '3',




no1: '9', nama1: 'agustin Indrawati', judul1: 'Karakterisasi dan Analisis Probiotik ARG untuk Pemenuhan Pangan Asal Hewan yang Sehat dan Aman Mewujudkan One Health', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Kesehatan', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Maya Safitri', judul2: 'Potential of Macang (Mangifera foetida Lour.) extract to restore enzymatic levels induced by polysterene nanoplastics in rat (Rattus norvegicus L.)', skema2: 'Universitas Airlangga', institusi2: 'Universitas Airlangga', bidangFokus2: 'Kesehatan', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'ROSALIA NURIL QOLBI', judul3: 'Potensi Rumput Laut Merah (Dichotomaria obtusata) Sebagai Agen Antioksidan Terhadap Kerusakan Ginjal Tikus (Rattus norvegicus) Yang Terpapar Nanoplastik', skema3: 'Universitas Airlangga', institusi3: 'Universitas Airlangga', bidangFokus3: 'Kesehatan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Anisa Rahma', judul4: 'Analisis Proksimat serta Kandungan Makro dan Mikro Guano di Gua Gundawang Bogor untuk Menilai Potensinya sebagai Pupuk', skema4: 'Penelitian Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kesehatan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '4',
sesi: '1',




no1: '1', nama1: 'Heriyanto Syafutra', judul1: 'Perancangan Alat Ekstraktor Crude Palm Oil Model Screw Press', skema1: 'Penelitian Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Auzi Asfarian', judul2: 'Survey dan Evaluasi Digital Nudge di Layanan Digital Populer di Indonesia untuk Meningkatkan Pola Konsumsi Bertanggung Jawab di Generasi Muda', skema2: 'PKDN', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Sri Nurdiati', judul3: 'Model Pembobotan Pada Sistem Pendukung Keputusan Kelompok Berdasarkan Pakar Untuk Prediksi Kualitas Mutu Gaharu Budidaya', skema3: 'PDD', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Mohammad Khotib', judul4: 'Produksi Skala Pilot Lithium Grease Multifungsi Berbahan Baku Minyak Kotor (MIKO) Menggunakan Mikrogelombang Dalam Rangka Mewujudkan Ekonomi Sirkular', skema4: 'BPDPKS', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '4',
sesi: '2',




no1: '1', nama1: 'Muh Taufik', judul1: 'Postfire effect on hydrophysical properties of Indonesian peatland', skema1: 'PDUPT', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '09.50 - 10.00',
no2: '2', nama2: 'Tineke Mandang', judul2: 'Rekayasa ALSINTAN Penyemprot Pestisida Pada Padi Berbasis Teknologi Sensor Ba0.5Sr0.5TiO3 (BST), Mikrokontroller dan Energi', skema2: 'PDD', institusi2: 'IPB University ', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '10.10 - 10.20',
no3: '3', nama3: 'Tri Prartono', judul3: 'Karakteristik Material Aerosol Laut sebagai Sumber Transpor Logam Berat di Laut ', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Kemaritiman', waktu3: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Teknologi & Rekayasa',
room: '4',
sesi: '3',




no1: '9', nama1: 'Auliya Ilmiawati', judul1: 'Identifikasi Senyawa Termitisida pada Tumbuhan Bintaro (Cerbera odollam) dan Kecubung (Brugmansia candida)', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Teknologi & Rekayasa', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Farah Fahma', judul2: 'Pemanfaatan Lignoselulosa Tandan Kosong Kelapa Sawit Untuk Aplikasi Pupuk Laju Lepas Lambat (Slow Release Fertilizer)', skema2: 'PFR', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'Rita Kartika Sari', judul3: 'KARAKTERISTIK PEREKAT HYBRID FENOL FORMALDEHIDA-METILEN DIFENIL DIISOSIANAT DAN PAPAN UNTAI BERARAH KAYU SENGON', skema3: 'RIIM', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Anne Carolina', judul4: 'EFEKTIVITAS EKSTRAKSI DAN ANALISIS BIOAKTIVITAS BALSAM RASAMALA TERINDUKSI METIL JASMONAT', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '5',
sesi: '1',




no1: '1', nama1: 'Novindra', judul1: 'Strategi Pengelolaan Wisata Bahari Berkelanjutan di Kabupaten Pesisir Barat, Lampung (Studi Kasus: Pulau Pisang dan Pantai Labuhan Jukung)', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Kemaritiman', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Ani Nuraeni', judul2: 'Peningkatan Umur Simpan Premiks Berbasis Mocaf Tinggi Protein Melalui Reformulasi Dan Pemilihan Kemasan', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Teknologi & Rekayasa', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Meika Syahbana Rusli', judul3: 'Pengaruh Bioaditif dari Minyak Atsiri terhadap Kinerja Biosolar B35', skema3: 'LPDP', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Meutia Samira Ismet ', judul4: 'Karakterisasi Aktivitas dan Identifikasi Molekular Bakteri Simbion Spons Laut Pendegradasi Mikroplastik ', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Kemaritiman', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '5',
sesi: '2',




no1: '5', nama1: 'Meutia Samira Ismet', judul1: 'Karakteristik komunitas bakteri rizosfer secara molekuler sebagai penciri kesehatan vegetasi mangrove di ekosistem alami dan rehabilitasi', skema1: 'PTM', institusi1: 'IPB University', bidangFokus1: 'Kemaritiman', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Mala Nurilmala', judul2: 'Optimasi Proses Produksi Skala Pilot Gelatin Halal dan Aplikasinya untuk Kapsul Cangkang Keras pada Produk Farmasi dan Kesehatan', skema2: 'LPDP', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Erliza Noor', judul3: 'Uji Aplikasi Produksi Kopi Luwak Enzimatis Pada Industri Skala Menengah', skema3: 'PTKN', institusi3: 'IPB University', bidangFokus3: 'Teknologi & Rekayasa', waktu3: '10.10 - 10.20',
no4: '8', nama4: 'Erliza Noor', judul4: 'OPTIMALISASI PEMANFAATAN BATANG SAGU MELALUI PROSES KERING UNTUK BIOFUEL DAN ANTIOKSIDAN', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Teknologi & Rekayasa', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Kemaritiman',
room: '5',
sesi: '3',




no1: '9', nama1: 'Domu Simbolon', judul1: 'DEGRADASI DAERAH PENANGKAPAN IKAN DI PERAIRAN UTARA PROVINSI BANTEN', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Kemaritiman', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Wini Trilaksani', judul2: 'Efektivitas Masking Green Tea terhadap Kualitas Minyak Mata Tuna dan Formulasinya pada Sediaan Tablet Berbasis Mikrokapsul dan Spirulina platensis', skema2: 'PTM', institusi2: 'IPB University', bidangFokus2: 'Kemaritiman', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'Arifin Budiman Nugraha', judul3: 'The pattern of biological character, morphometry, and genetic information of Trypanosoma evansi isolated from District Bogor', skema3: 'Dosen Muda', institusi3: 'IPB University ', bidangFokus3: 'Kemaritiman', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Tri Prartono', judul4: 'Variasi Fluks Gas Rumah Kaca (CO2, CH4, N2O) dari Sedimen Mangrove dalam Upaya Perhitungan Serapan Karbon Bersih Ekosistem Mangrove di Taman Hutan Raya Ngurah Rai, Bali', skema4: 'PTM', institusi4: 'IPB University', bidangFokus4: 'Kemaritiman', waktu4: '10.20 - 10.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '6',
sesi: '2',




no1: '5', nama1: 'MIFTAHUDIN', judul1: 'PARIWISATA BERKELANJUTAN DAN TERINTEGRASI BERDASARKAN SUMBERDAYA HAYATI DI KEPULAUAN BELITUNG, INDONESIA', skema1: 'UKICIS', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Khairil Anwar Notodiputro', judul2: 'Model Beta-Binomial dalam Pendugaan Area Kecil dengan Pendekatan Adjusted Profile Hierarchical Likelihood untuk Prediksi Angka Buta Huruf di Jawa Timur', skema2: 'PDD', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Muhammad Rahmad Suhartanto', judul3: 'Induksi Toleransi terhadap Cekaman Kekeringan dengan Perlakuan Priming dan Coating pada Benih Jagung', skema3: 'PTM', institusi3: 'IPB University', bidangFokus3: 'Sosial Humaniora', waktu3: '10.10 - 10.20',
no4: '6', nama4: 'Ahmad Sulaeman', judul4: 'PENGEMBANGAN MINUMAN FUNGSIONAL SARIPATI AYAM HERBAL SERTA PONTESINYA UNTUK MENINGKATKAN KEBUGARAN', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Sosial Humaniora',
room: '6',
sesi: '3',




no1: '9', nama1: 'Machfud', judul1: 'Strategi proses inovasi agroindustri di masa perubahan', skema1: 'PDD', institusi1: 'IPB University', bidangFokus1: 'Sosial Humaniora', waktu1: '10.50 - 11.00',
no2: '10', nama2: 'Veralianta Br Sebayang', judul2: 'Penerapan Sistem Pemasaran Melalui Digital Marketing pada  Koperasi Okiagaru Indonesia Agricoop', skema2: 'Dosen Muda', institusi2: 'IPB University', bidangFokus2: 'Sosial Humaniora', waktu2: '11.00 - 11.10',
no3: '11', nama3: 'Anuraga Jayanegara', judul3: 'Pengaruh kandungan metabolit sekunder tanaman sebagai additive silase terhadap fermentabilitas rumen', skema3: 'PMDSU', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '12', nama4: 'Anuraga Jayanegara', judul4: 'Kajian Nilai Nutrisi, Metabolomik dan Metagenomik Tumbuhan Lokal Terfermentasi Mengandung Komponen Bioaktif Sebagai Pakan Ternak Ruminansia', skema4: 'PDD', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '7',
sesi: '1',




no1: '1', nama1: 'Anuraga Jayanegara', judul1: 'Modifikasi Rumen Undegradable Starch Asal Bahan Pakan Lokal Berbasis Pengolahan Fisik-Kimia', skema1: 'PMDSU', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '08.50 - 09.00',
no2: '2', nama2: 'Anuraga Jayanegara', judul2: 'Investigation of Tropical Fermented Legumes for Mitigating Enteric Methane Emissions, Enhancing Productivity and Improving Product Quality of Ruminant Livestock', skema2: 'RKD', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '09.00 - 09.10',
no3: '3', nama3: 'Anuraga Jayanegara', judul3: 'Rekayasa Garam Nitrat Sebagai Pakan Aditif Inhibitor Metanogenesis dan Evaluasinya Melalui Pendekatan Metagenomik dan Metabolomik', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '09.10 - 09.20',
no4: '4', nama4: 'Sazli Tutur Risyahadi ', judul4: 'MODEL LEAN SUPPLY HAIN MANAGEMENT PADA INDUSTRI PAKAN SKALA KECIL DAN MENENGAH UNTUK PENGUATAN INDUSTRI SAPI NASIONAL', skema4: 'Dosen Muda', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '09.20 - 09.30',
diskusi: '09.30 - 09.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '7',
sesi: '2',




no1: '5', nama1: 'Aliati Iswantari', judul1: 'Optimasi Perbanyakan Mikroalga Berfilamen Skala Massal Sebagai Sumber Serat Alternatif', skema1: 'Dosen Muda', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '09.50 - 10.00',
no2: '6', nama2: 'Alfira Kinanti', judul2: 'Pengaruh Daya Lampu Neon terhadap Pertumbuhan dan Hasil Berbagai Varietas Tanaman Selada (Lactuca sativa L.) dengan Sistem Hidroponik NFT (Nutrient Film Technique)', skema2: 'Universitas Garut', institusi2: 'Universitas Garut', bidangFokus2: 'Pangan', waktu2: '10.00 - 10.10',
no3: '7', nama3: 'Muhamad Baihaqi', judul3: 'PENINGKATAN KESEJAHTERAAN TERNAK DOMBA YANG DITRANSPORTASIKAN MELALUI REKAYASA DESAIN KENDARAAN', skema3: 'PFR', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '10.10 - 10.20',
no4: '9', nama4: 'Anuraga Jayanegara', judul4: 'Uji Kombinasi Ekstrak Tea Polyphenol Dan Kurkumin Sebagai Pakan Aditif Dan Antelmintik Pada Bibit Domba Lokal Yang Diinfeksi Nematoda Strongylus Sp.', skema4: 'RKI - PTNBH', institusi4: 'IPB University', bidangFokus4: 'Pangan', waktu4: '10.20 - 10.30',
diskusi: '10.30 - 10.50',

}, { hariTanggal: 'Rabu, 13 Desember 2023',
bidangFokus: 'Pangan',
room: '7',
sesi: '3',




no1: '10', nama1: 'DIMAS ANDRIANTO', judul1: 'Pertanian Terpadu Bermodal Limbah Ladang, Dapur, dan Kandang dengan Memanfaatkan Maggot Black Soldier Fly untuk Mewujudkan Desa Nir Limbah di Desa Tegal Waru, Ciampea, Bogor', skema1: 'PKM', institusi1: 'IPB University', bidangFokus1: 'Pangan', waktu1: '10.50 - 11.00',
no2: '11', nama2: 'IVAN PERMANA PUTRA', judul2: 'Pengenalan dan Pengembangan Produk dari Jamur Liar Edible di Sukabumi, Jawa Barat', skema2: 'PKM', institusi2: 'IPB University', bidangFokus2: 'Pangan', waktu2: '11.00 - 11.10',
no3: '12', nama3: 'IYEP KOMALA', judul3: 'Peningkatan Kesejahteraan Peternak Mandiri Sapi Perah dengan Penerapan Good Dairy Farming Practices (GDFP) dan Good Milking Practices (GMiP) ((Hak Cipta: 000388970)', skema3: 'PKM', institusi3: 'IPB University', bidangFokus3: 'Pangan', waktu3: '11.10 - 11.20',
no4: '13', nama4: 'SARWITITI SARWOPRASODJO', judul4: 'Pemberdayaan Community Based Tourism Desa Wisata di Kecamatan Tamansari, Kabupaten Bogor, Jawa Barat', skema4: 'PKM', institusi4: 'IPB University', bidangFokus4: 'Sosial Humaniora', waktu4: '11.20 - 11.30',
diskusi: '11.30 - 11.50',
}
    // Add more items as needed
  ]);
  
  // Search query state
  const searchQuery = ref('');
  
  // Computed property to filter items based on searchQuery
  const filteredItems = computed(() => {
  return items.value.filter(item =>
    Object.values(item).some(val =>
      typeof val === 'string' &&
      val.toLowerCase().includes(searchQuery.value.toLowerCase())
    )
  );
});
  </script>