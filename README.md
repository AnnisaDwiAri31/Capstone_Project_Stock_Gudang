# Capstone_Project_Stock_Gudang
Capstone Project berupa aplikasi sederhana dengan Tema 'Stock Gudang' yang berisi beberapa menu yaitu Read, Create, Update dan Delete

# Import Tabulate
from tabulate import tabulate

*Library untuk menampilkan tabel agar terlihat rapi dan mudah dipahami* 

# Data
list_sepatu :

*Data yang digunakan menggunakan Collection Data Type Dictionary di dalam List. Bisa juga menggunakan collection data type nya hanya list saja*

# TABEL
def tampilkan(list_sepatu):

*Function diatas merupakan tampilan tabel dari data yang ada di list_sepatu, dengan headers nya adalah keys nya sedangkan format pada tabel nya adalah grid*

# READ DATA
def show_data() :

*Function untuk Menampilkan data, dimana pada function ini terdapat 3 menu didalamnya*


# ADD DATA
def add_data():

*Function ini untuk menambahkan data baru ke data yang sebelumnya*

# UPDATE DATA
def update_data():

*Function ini digunakan untuk mengupdate data berdasarkan kode sepatu yang dimasukkan oleh user, dan terdapat 3 menu di dalamnya kemudian dapat di update harga ataupun stock sepatu secara mandiri oleh user*

# MENGHAPUS DATA
def delete_data():

*Function ini digunakan untuk menghapus data berdasarkan kode sepatu yang dimasukkan oleh user*


# Main Menu

* while True:
    try:
        Home = int(input('''\nSELAMAT DATANG DI GUDANG SEPATU JAYA SELALU
--------------------------------------------
        List menu :
            1. Menampilkan Daftar Sepatu
            2. Menambahkan Daftar Sepatu
            3. Mengupdate Daftar Sepatu
            4. Hapus Daftar Sepatu
            5. Keluar Program
        \nSilahkan Masukkan menu yang akan anda pilih : '''))
        if Home == 1:
            show_data()

        elif Home == 2:
            add_data()

        elif Home == 3:
            update_data()

        elif Home == 4:
            delete_data()

        elif Home == 5:
            print('\n\t\t==========Aplikasi selesai!========== \n\t\t ==========HAVE A GOOD DAY==========')
            break

        else:
            print('Pilihan Tidak Terdaftar, Masukkan yang benar!')
    except: 
        print('Masukkan Angka yang benar!')
