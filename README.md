# pratikum6
## Program Input Nilai
```python
data_mahasiswa = {}

def lihat_data():
    if not data_mahasiswa:
        print("Daftar Nilai")
        print("=" * 81)
        print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
        print("=" * 81)
        print(f"{'TIDAK ADA DATA'.center(75)}")
        print("=" * 81)
        return
    print("Daftar Nilai")
    print("=" * 81)
    print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
    print("=" * 81)
    for i, (nim, mhs) in enumerate(data_mahasiswa.items(), start=1):
        print(f"{str(i).center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)}|")
    print("=" * 81)

def tambah_data():
    print("Tambah Data")
    nim = input("NIM: ")
    if nim in data_mahasiswa:
        print("Data dengan NIM tersebut sudah ada!")
        return
    nama = input("Nama: ")
    tugas = float(input("Nilai Tugas: "))
    uts = float(input("Nilai UTS: "))
    uas = float(input("Nilai UAS: "))
    nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

    data_mahasiswa[nim] = {
        "nama": nama,
        "tugas": tugas,
        "uts": uts,
        "uas": uas,
        "nilai_akhir": nilai_akhir
    }
    print("Data berhasil ditambahkan!")

def ubah_data():
    if not data_mahasiswa:
        return

    nama = input("Masukkan nama data yang akan diubah: ")
    for nim, mhs in data_mahasiswa.items():
        if mhs['nama'].lower() == nama.lower():
            # Tampilkan data yang ditemukan
            print("Data yang akan diubah:")
            print("=" * 81)
            print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
            print("=" * 81)
            print(f"{'1'.center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)}|")
            print("=" * 81)

            # Masukkan data baru
            print("Masukkan Data Baru (tekan Enter jika tidak ingin mengubah nilai tertentu)")
            nim_baru = input("NIM : ").strip() or nim  # Gunakan NIM lama jika kosong
            nama_baru = input("Nama : ").strip() or mhs['nama']  # Gunakan nama lama jika kosong
            tugas = input("Nilai Tugas: ").strip()
            tugas = float(tugas) if tugas else mhs['tugas']
            uts = input("Nilai UTS : ").strip()
            uts = float(uts) if uts else mhs['uts']
            uas = input("Nilai UAS: ").strip()
            uas = float(uas) if uas else mhs['uas']
            nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

            # Perbarui data
            del data_mahasiswa[nim]  # Hapus data lama
            data_mahasiswa[nim_baru] = {
                "nama": nama_baru,
                "tugas": tugas,
                "uts": uts,
                "uas": uas,
                "nilai_akhir": nilai_akhir
            }
            print("Data berhasil diubah!")
            return
    print("Nama tidak ditemukan!")

def hapus_data():
    lihat_data()
    if not data_mahasiswa:
        return

    nama = input("Masukkan nama data yang akan dihapus: ")
    for nim, mhs in list(data_mahasiswa.items()):
        if mhs['nama'].lower() == nama.lower():
            del data_mahasiswa[nim]
            print("Data berhasil dihapus!")
            return
    print("Nama tidak ditemukan!")

while True:
    pilihan = input("[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : ").lower()
    if pilihan == 't':
        tambah_data()
    elif pilihan == 'u':
        ubah_data()
    elif pilihan == 'h':
        hapus_data()
    elif pilihan == 'l':
        lihat_data()
    elif pilihan == 'k':
        print("Program selesai.")
        break
    else:
        print("Pilihan tidak valid!")
```
## Contoh Output Program
```python
[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : l
Daftar Nilai
=================================================================================
  No |      Nama     |   NIM    | Nilai Tugas |Nilai UTS |Nilai UAS |Nilai Akhir|
=================================================================================
                               TIDAK ADA DATA
=================================================================================
[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : t
=================================================================================
  1  |Aziz           |  070704  |     90.0    |   89.0   |   87.0   |  88.60   |
=================================================================================
Masukkan Data Baru (tekan Enter jika tidak ingin mengubah nilai tertentu)
NIM :
Nama :
Nilai Tugas: 97
Nilai UTS :
Nilai UAS:
Data berhasil diubah!
[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : l
Daftar Nilai
=================================================================================
  No |      Nama     |   NIM    | Nilai Tugas |Nilai UTS |Nilai UAS |Nilai Akhir|
=================================================================================
  1  |Aziz           |  070704  |     97.0    |   89.0   |   87.0   |  90.70   |
=================================================================================
[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : k
Program selesai.
```
## Penjelasan program

1. Variabel data_mahasiswa
   -
   data_mahasiswa adalah sebuah dictionary (kamus) yang digunakan untuk menyimpan data mahasiswa. Setiap data mahasiswa disimpan dengan NIM (Nomor Induk Mahasiswa) sebagai key. Nilai (value) untuk setiap key adalah dictionary yang berisi informasi berikut: 
   - nama : Nama Mahasiswa
   - tugas : Nilai Tugas
   - uts : Nilai UTS
   - uas : Nilai UAS
   - nilai_akhir : Nilai akhir yang dihitung berdasarkan rumus
2. Fungsi lihat_data()
    -
   Fungsi ini digunakan untuk menampilkan seluruh data mahasiswa yang tersimpan dalam data_mahasiswa.
   - Jika data_mahasiswa kosong, program akan menampilkan pesan "TIDAK ADA DATA"
   - Jika ada data, program akan ermenampilkan tabel yang berisi informasi mahasiswa seperti:
      - Nama
      - NIM
      - Nilai Tugas
      - Nilai UTS
      - Nilai UAS
      - Nilai Akhir
Tabel ini disusun rapi menggunakan metode center() dan ljust() untuk pengaturan teks dan angka agar tampak simetris.

3. Fungsi tambah_data()
   -
   Fungsi ini memungkinkan pengguna untuk menambahkan data mahasiswa baru.
   - Pengguna diminta untuk memasukkan
      - NIM
      - Nama
      - Niali Tugas
      - Nilai UTS
      - Nilai UAS
    - Jika NIM yang dimasukkan sudah ada dalam data_mahasiswa, program akan memberi tahu bahwa data sudah ada dan tidak akan menambahkannya
    - Nilai nilai_akhir dihitung dengan rumus:
       Nilai Akhir = (0.3 × Nilai Tugas) + (0.35 × Nilai UTS) + (0.35 × Nilai UAS)
    - Setelah itu data mahasiswa baru akan disimpan dalam data_mahasiswa menggunakan NIM sebagai key.

4. Fungsi ubah_data()
   -
   Fungsi ini memungkinkan pengguna untuk mengubah data mahasiswa yang sudah ada:
   - Pengguna diminta untuk memasukkan nama mahasiswa yang datanya ingin diubah.
   - Jika data mahasiswa ditemukan berdasarkan nama:
     - Program akan menampilkan data lama mahasiswa tersebut.
     - Pengguna bisa mengubah NIM, Nama, Nilai Tugas, Nilai UTS, atau Nilai UAS. Jika salah satu nilai tidak ingin diubah, pengguna cukup menekan Enter.
   - Setelah perubahan dilakukan, nilai_akhir dihitung ulang, dan data lama akan dihapus dari data_mahasiswa. Data baru akan disimpan dengan NIM baru jika ada perubahan NIM.

5. Fungsi hapus_data()
   -
   Fungsi ini memungkinkan pengguna untuk menghapus data mahasiswa yang sudah ada:
    - Fungsi ini pertama-tama akan memanggil fungsi lihat_data() untuk menampilkan data mahasiswa yang ada.
    - Pengguna diminta untuk memasukkan nama mahasiswa yang akan dihapus.
    - Program akan mencari mahasiswa berdasarkan nama:
        - Jika ditemukan, data mahasiswa tersebut akan dihapus dari data_mahasiswa.
        - Jika nama tidak ditemukan, program akan memberi tahu bahwa "Nama tidak ditemukan!".

6. Bagian Utama Program (Loop)
   -
   Program ini berjalan dalam sebuah loop while True yang menunggu input dari pengguna. Pilihan yang dapat dipilih oleh pengguna adalah sebagai berikut:
   - (L)ihat: Menampilkan seluruh data mahasiswa.
   - (T)ambah: Menambahkan data mahasiswa baru.
   - (U)bah: Mengubah data mahasiswa yang sudah ada.
   - (H)apus: Menghapus data mahasiswa.
   - (K)eluar: Keluar dari program.
   Jika input pengguna tidak valid, program akan memberi tahu dengan pesan "Pilihan tidak valid!".
7. Cara Kerja Program
   -
   Program akan terus berjalan dan menunggu pilihan dari pengguna. Berikut adalah alur kerja setiap pilihan:
   1. Tambah Data:
      -
      - Pengguna memilih opsi T.
      - Program meminta input untuk NIM, Nama, Nilai Tugas, Nilai UTS, dan Nilai UAS.
      - Nilai akhir dihitung dan data mahasiswa disimpan dalam data_mahasiswa.
   2. Lihat Data:
      -
      - Pengguna memilih L untuk melihat seluruh data yang telah dimasukkan sebelumnya.
      - Program menampilkan data dalam format tabel.
   3. Ubah Data:
      -
      - Pengguna memilih U dan diminta untuk memasukkan nama mahasiswa yang datanya ingin diubah.
      - Program akan mencari dan menampilkan data lama. Pengguna dapat mengubah NIM, Nama, Nilai Tugas, UTS, atau UAS.
      - Setelah perubahan, nilai akhir dihitung ulang dan data baru disimpan.
   4. Hapus Data:
      -
      - Pengguna memilih H dan diminta memasukkan nama mahasiswa yang akan dihapus.
      - Jika nama ditemukan, data mahasiswa tersebut dihapus dari data_mahasiswa.
   5. Keluar
      -
      - Pengguna memilih K untuk keluar dari Program
    

   

