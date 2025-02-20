import java.util.ArrayList; // Mengimpor kelas ArrayList digunakan untuk menyimpan daftar. import java.util.Scanner; // Mengimpor kelas Scanner digunakan untuk membaca input dari user. public class Kafe  // nama class. public static void main(String[] args) // main method. Scanner sc = new Scanner(System.in); // Membuat objek Scanner untuk membaca input dari user.
import java.util.ArrayList;
import java.util.Scanner;
public class Kafe {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String[] menu = {
            "Nasi Goreng", "Mie Goreng", "Roti Bakar", 
            "Kentang Goreng", "Teh Tarik", "Cappuccino", "Chocolate Ice"
        };
        int[] harga = {20000, 15000, 12000, 10000, 8000, 20000, 25000};

        ArrayList<String> pesanan = new ArrayList<>();
        ArrayList<Integer> jumlah = new ArrayList<>();
        ArrayList<Integer> totalHarga = new ArrayList<>();

        int pilihan;
        do {
            System.out.println("=== Selamat Datang di Kafe ===");
            System.out.println(" ");
            System.out.println("=== Menu ===");
            for (int i = 0; i < menu.length; i++) {
                System.out.println((i + 1) + ". " + menu[i] + " - Rp" + harga[i]);
            }
            System.out.println(" ");
            System.out.println("Pilih opsi berikut:");
            System.out.println("1. Tambah Pesanan");
            System.out.println("2. Lihat Daftar Pesanan");
            System.out.println("3. Hitung Total Biaya");
            System.out.println("4. Selesai");
            System.out.print("Masukkan pilihan Anda: ");
            pilihan = sc.nextInt();
            sc.nextLine();

            switch (pilihan) {
                case 1:
                    System.out.print("Masukkan nomor menu yang ingin dipesan: ");
                    int nomorMenu = sc.nextInt();
                    if (nomorMenu < 1 || nomorMenu > menu.length) {
                    System.out.println("Nomor menu tidak valid.");
                    break;
                }
                System.out.print("Masukkan jumlah pesanan: ");
                int jumlahPesanan = sc.nextInt();
                sc.nextLine();

                pesanan.add(menu[nomorMenu - 1]);
                jumlah.add(jumlahPesanan);
                totalHarga.add(harga[nomorMenu - 1] * jumlahPesanan);

                System.out.println(jumlahPesanan + " " + menu[nomorMenu - 1] + " berhasil ditambahkan ke pesanan.");
                System.out.println(" ");
                break;


                case 2:
                    System.out.println("=== Daftar Pesanan ===");
                    int totalSementara = 0;
                    for (int i = 0; i < pesanan.size(); i++) {
                        System.out.println((i + 1) + ". " + pesanan.get(i) + " x" + jumlah.get(i) + " - Rp" + totalHarga.get(i));
                        totalSementara += totalHarga.get(i);
                }
                    System.out.println("Total Biaya Sementara: Rp" + totalSementara);
                    System.out.println(" ");
                    break;

                case 3:
                    int totalBiaya = 0;
                    for (int hargaPesanan : totalHarga) {
                        totalBiaya += hargaPesanan;
                }
                    System.out.println("Total biaya seluruh pesanan: Rp" + totalBiaya);
                    System.out.println(" ");
                    break;

                case 4:
                    System.out.println("Terima kasih telah memesan di kafe kami!");
                    break;

                default:
                    System.out.println("Pilihan tidak valid.");
            }
        } while (pilihan != 4);

        sc.close();
    }
}