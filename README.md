# Cara Mengunakan

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

# Detail Tugas

## Goals :

Saya sebagai perawat ingin menginputkan data TRIASE pasien, setelah tersimpan data
TRIASE, kemudian data pasien tersebut akan masuk ke dashboard Klinik IGD, selain itu saya juga ingin mengubah detail sesuai kebutuhan, dan dapat menghapus pasien apabila pasien tersebut telah selesai pelayanan,

### Data TRIASE :

1. Nama Pasien :

- Alphabet
- min. 10 karakter max. 50 karakter
- Required
- Jika text field tidak diisi maka memunculkan message : Perlu mengisi nama
- Jika text field diisi melebihi 50 karakter maka memunculkan message : Jumlah karakter
  maksimal 50 karakter

2. Alamat

- Alpanumeric
- min. 10 karakter max. 100 karakter
- Required
- Show message error required : Perlu mengisi alamat

3. Jenis Kelamin

- Laki-laki/Perempuan
- Pilih salah satu
- Required
- Show message error required : Perlu mengisi jenis kelamin

4. Nama Orang tua

- Alphabet
- min. 10 karakter max. 50 karakter
- Show message error required : Jumlah karakter maksimal 50 karakter

5. Nama Penanggung Jawab

- Alphabet
- min. 10 karakter max. 50 karakter
- Show message error required : Jumlah karakter maksimal 50 karakter

6. Kesadaran

- Pilih salah satu dari Sadar penuh/ Respon Suara/ Respon Nyeri/ Tidak Nyeri

7. Tekanan Darah

- numeric
- min. 2 digit max. 3 digit
- Required
- Show message error required : Perlu mengisi tekanan darah

8. Nadi

- numeric
- 2 digit- Required
- Show message error required : Perlu mengisi nadi

9. RR

- numeric
- 2 digit
- Required
- Show message error required : Perlu mengisi respiration rate

10. Suhu

- numeric
- 2 digit
- Required
- Show message error required : Perlu mengisi suhu

11. Saturasi O2

- numeric
- 2 digit
- Required
- Show message error required : Perlu mengisi saturasi O2

12. Nyeri

- numeric
- 1 digit
- Required
- Show message error required : Perlu mengisi angka nyeri

13. Berat badan

- numeric
- min. 2 digit max. 3 digit

14. Tinggi Badan

- numeric
- min. 2 digit max. 3 digit

### Page Working Psychological Scoring System (WPSS) :

Data ini akan muncul berdasarkan penjelasan sistem scoring sesuai requirement
product yg ada di bawah:

1. Kesadaran :

   > Sadar Penuh : Skor 0

   > Selain Sadar Penuh : Skor 3

2. Tekanan darah sistolik :

   > 100-140 : Skor 0

   > <100 atau >140 : Skor 1

   > <=89 atau >=160 : Skor 2

3. Temperatur :

   > 36-37,5 : skor 0>37,5 : skor 1

   > <35,5 : skor 3

4. Nadi :

   > 60-100 : skor 0

   > 101-120 : skor 1

   > 120 atau <60 : skor 2

5. Respirasi :

   > 16-24 : skor 0

   > 25-28 : skor 1

   > <=16 atau >=28: skor 2

6. Saturasi :

   > 96-100 : skor 0

   > 94-95 : skor 1

   > 90-93 : skor 2

   > <90 : skor 3

### Product Requirement :

1. Saat user mengisi triase, sistem menggenerate nomor registrasi (index/nomor antrian)
2. Kategori skoring pada setiap kategori kesadaran, tekanan darah sistolik, temperatur, nadi,
   respirasi, dan saturasi berdasarkan dari inputan tanda-tanda vital pada page TRIASE
   misal :
   nadi : 110 berarti skor tekanan darahnya 0
3. Perhitungan kesimpulan Working Psychological Scoring System (WPSS) diambil dari total
   skor dari kategori kesadaran, tekanan darah sistolik, temperatur, nadi, respirasi, dan
   saturasi berdasarkan dari inputan tanda-tanda vital.

### Kesimpulan :

> Ruang resusitasi : skor 7-9

> Ruang non resusitasi : skor 3-6

> Klinik Umum : skor 0-2

> Death on Arrival : skor 10

## Daftar TO DO

1.  Menampilkan tanggal dengan format hari, tanggal bulan tahun
2.  Menampilkan data pasien yang didapat dari backend
3.  Membuat Tampilan untuk menambahkan data baru
4.  Membuat fungsi untuk menambahkan data baru ke backend
5.  Membuat Tampilan untuk mengubah data
6.  Membuat fungsi untuk mengubah data dan menyimpan ke backend
7.  Menghapus entri

## How To Submit 

1. buat branch dengan format interviewee-'Nama anda' 
2. push ke repositori

### Catatan

- Dokumentasi Backend ada di documentation/triasePatient.http

