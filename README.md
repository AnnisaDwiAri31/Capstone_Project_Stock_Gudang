# Capstone_Project_Stock_Gudang
Capstone Project berupa aplikasi sederhana dengan Tema 'Stock Gudang' yang berisi beberapa menu yaitu Read, Create, Update dan Delete

# Import Tabulate
from tabulate import tabulate

*Library untuk menampilkan tabel agar terlihat rapi dan mudah dipahami* 

# Data
*Data yang digunakan menggunakan Collection Data Type Dictionary di dalam List. Bisa juga menggunakan collection data type nya hanya list saja*

# TABEL
def tampilkan(list_sepatu):
    if len(list_sepatu)>0 :
        print(tabulate(list_sepatu,headers='keys',tablefmt='grid'))

*Function diatas merupakan tampilan tabel dari data yang ada di list_sepatu, dengan headers nya adalah keys nya sedangkan format pada tabel nya adalah grid*

# READ DATA
def show_data():
    while True:
        menu_show_data = '''\n==========MENU SHOW DATA==========
                        \n1. Menampilkan semua data
                        \n2. Melihat sepatu berdasarkan kode
                        \n3. Kembali ke Menu Utama'''

        print(menu_show_data)
        pilihan = int(input("\nSilahkan Masukkan Menu (1-3): "))

        if pilihan == 1:
            tampilkan(list_sepatu)

        elif pilihan == 2:
            cari_kode = input('\nMasukkan Kode Sepatu: ').upper()
            kode_ditemukan = next((sepatu for sepatu in list_sepatu if cari_kode == sepatu['Kode']), None)
            if kode_ditemukan:
                tampilkan([kode_ditemukan])
            else:
                print(f'\nKode Sepatu {cari_kode} tidak ditemukan.'.format(cari_kode))
            
        elif pilihan == 3:
            break


# ADD DATA
def add_data():
    print('\n ==========ADD DATA SEPATU==========\n')
    print('\nPada menu ini Anda akan memasukkan beberapa data, silahkan memasukkan data dengan teliti')
    merk_baru = input('\nMasukkan Merk Sepatu : ').capitalize()
    jenis_baru = input('\nMasukkan Jenis Sepatu : ').capitalize()
    kode_baru = input('\nMasukkan Kode : ').upper()
    harga_baru = int(input('\nMasukkan Harga Sepatu : '))
    stock_baru = int(input('\nMasukkan Stock Sepatu : '))
    print('\nApakah Anda Ingin Menyimpan Data? \n1 : Ya, Data Disimpan \n2 : Tidak,Dibatalkan')

    pilihan = int(input('Pilihan : '))
    if pilihan == 1:
        list_sepatu_baru = {'Kode': kode_baru, 
                            'Merk Sepatu': merk_baru, 
                            'Jenis Sepatu': jenis_baru, 
                            'Harga': harga_baru, 
                            'Stock': stock_baru}
        list_sepatu.append(list_sepatu_baru)
        print('\nData Sepatu Ditambahkan')
        print('\n\n====================LIST SEPATU BARU====================\n')
        tampilkan(list_sepatu)
    
    elif pilihan == 2:
        print('=====Data Dibatalkan=====')
    else :
        print('=====Pilih sesuai menu antara 1 dan 2=====')
    
#UPDATE DATA
def update_data():
    print('\n=====Pada menu ini Anda akan mengupdate barang dengan menggunakan kode sepatu=====')
    kode_sepatu = input('\nMasukkan Kode sepatu : ').upper()

    for sepatu in list_sepatu:
        if kode_sepatu == sepatu['Kode']:
            tampilkan([sepatu])
            tanya = input('\nApakah Anda yakin untuk mengupdate data? (y/t) : ')
            if tanya.lower() == 'y':
                    nanya = int(input('''Apakah Anda ingin melakukan update terhadap :
                                                    1. Harga 
                                                    2. Stock
                                                    3. Harga dan Stock
                                                    4. Kembali ke Menu Utama
                                                    \n Masukkan Menu : '''))

                    if nanya == 1:
                        # Input Baru
                        harga_baru = int(input('Masukkan Harga Sepatu : '))

                        # Update data
                        sepatu['Harga'] = harga_baru
                    
                    elif nanya == 2:
                        # Input Baru
                        stock_baru = int(input('Masukkan Stock Sepatu : '))

                        # Update data
                        sepatu['Stock'] = stock_baru
                    
                    elif nanya == 3:
                        # Input Baru
                        harga_baru = int(input('Masukkan Harga Sepatu : '))
                        stock_baru = int(input('Masukkan Stock Sepatu : '))

                        # Update data
                        sepatu['Harga'] = harga_baru
                        sepatu['Stock'] = stock_baru
                    
                    elif nanya == 4 :
                        break 

                    else :
                        print('Masukkan Menu yang Sesuai!')

                    # Menampilkan data sepatu setelah update
                    tampilkan(list_sepatu)
                    print('\n=====Data Berhasil DI UPDATE!=====')
                    break
                    
            elif tanya.lower() == 't':
                print('\n=====Membatalkan Update pada barang=====')
                break
            
            else :
                print('\n=====Tidak valid, pilih y/t=====')
        else:
            print('\n=====Kode tidak ditemukan!=====')
            break


# MENGHAPUS DATA
def delete_data():
    print('Pada menu ini akan di hapus data berdasarkan kode sepatu')
    tampilkan(list_sepatu)
    kode_sepatu = input('Masukkan Kode Sepatu yang ingin dihapus : ').upper()
    
    tanya = input('Apakah Anda ingin menghapus data diatas? (y/t) : ')

    if tanya.lower() == 'y':
        for sepatu in list_sepatu:
            if kode_sepatu == sepatu['Kode']:
                tampilkan([sepatu])
                tanya_lagi = input('Apakah Anda yakin untuk menghapus data tersebut? (y/t) : ')
                if tanya_lagi == 'y':
                    list_sepatu.remove(sepatu)
                    print('=====Sepatu berhasil di hapus=====')
                    break
                else :
                    print('=====Membatalkan hapus sepatu=====')
                    break
        else :
            print('\n=====Kode sepatu tidak ditemukan=====')
    elif tanya.lower() == 't':
        print('\nData Batal Dihapus!')
    else :
        print('\n=====Masukkan input yang benar (y/t)=====')


while True:
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
