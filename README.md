
#include <iostream>
#include <iomanip>

using namespace std;

// Mendefinisikan struktur untuk menyimpan informasi produk
struct Product {
    string name;
    double price;
};

int main() {
    const int MAX_PRODUCTS = 10;
    Product products[MAX_PRODUCTS];
    int numProducts = 0;

    // Fungsi untuk menambahkan produk
    auto addProduct = [&](const string& name, double price) {
        if (numProducts < MAX_PRODUCTS) {
            products[numProducts++] = {name, price};
            cout << "Produk berhasil ditambahkan." << endl;
        } else {
            cout << "Maaf, kapasitas produk penuh." << endl;
        }
    };

    // Fungsi untuk menampilkan daftar produk
    auto showProducts = [&]() {
        cout << "Daftar Produk:" << endl;
        cout << setw(20) << left << "Nama Produk" << setw(10) << right << "Harga" << endl;
        cout << setfill('-') << setw(30) << "" << setfill(' ') << endl;
        for (int i = 0; i < numProducts; ++i) {
            cout << setw(20) << left << products[i].name << setw(10) << right << products[i].price << endl;
        }
    };

    // Fungsi untuk melakukan transaksi
    auto makeTransaction = [&]() {
        double total = 0;
        int quantity;
ymm
        showProducts();

        // Memilih produk
        int productIndex;
        cout << "Masukkan nomor produk yang akan dibeli: ";
        cin >> productIndex;

        if (productIndex >= 0 && productIndex < numProducts) {
            // Memasukkan jumlah barang yang akan dibeli
            cout << "Masukkan jumlah barang yang akan dibeli: ";
            cin >> quantity;

            // Menghitung total harga
            total = products[productIndex].price * quantity;

            cout << "Total harga: " << total << endl;
        } else {
            cout << "Produk tidak valid." << endl;
        }
    };

    // Menu utama
    int choice;
    do {
        cout << "\nProgram Kasir Sederhana\n";
        cout << "1. Tambah Produk\n";
        cout << "2. Lihat Daftar Produk\n";
        cout << "3. Transaksi\n";
        cout << "0. Keluar\n";
        cout << "Pilih menu: ";
        cin >> choice;

        switch (choice) {
            case 1:
                {
                    string name;
                    double price;
                    cout << "Masukkan nama produk: ";
                    cin.ignore();
                    getline(cin, name);
                    cout << "Masukkan harga produk: ";
                    cin >> price;
                    addProduct(name, price);
                }
                break;
            case 2:
                showProducts();
                break;
            case 3:
                makeTransaction();
                break;
            case 0:
                cout << "Terima kasih. Program keluar.\n";
                break;
            default:
                cout << "Pilihan tidak valid. Silakan coba lagi.\n";
        }

    } while (choice != 0);

    return 0;
}


    
