# Menjalankan Storage Node di 0G Network

## 1. Persyaratan Perangkat Keras
Pastikan perangkat keras yang digunakan memenuhi spesifikasi berikut:

| Komponen | Storage Node |
|----------|-------------|
| RAM      | 32 GB       |
| CPU      | 8 Cores     |
| Disk     | 500GB / 1TB NVMe SSD |
| Bandwidth | 100 Mbps (Download/Upload) |

**Catatan:**
- Gunakan NVMe SSD untuk memastikan operasi baca/tulis cepat yang diperlukan dalam penyimpanan dan pengambilan data.

---

## 2. Instalasi Dependensi
Sebelum mengatur storage node, pastikan untuk menginstal semua dependensi yang diperlukan.

### Untuk Linux (Debian/Ubuntu):
```sh
sudo apt-get update
sudo apt-get install clang cmake build-essential pkg-config libssl-dev
```

### Instal Rust
Karena perangkat lunak 0G node ditulis dalam Rust, instal `rustup` terlebih dahulu:
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

---

## 3. Unduh dan Bangun Kode Sumber
Clone repositori kode sumber dari GitHub:
```sh
git clone -b <latest_tag> https://github.com/0glabs/0g-storage-node.git
```

Masuk ke direktori proyek:
```sh
cd 0g-storage-node
```

Bangun kode dalam mode rilis:
```sh
cargo build --release
```

---

## 4. Konfigurasi Storage Node
Setelah proses build selesai, konfigurasi node dengan mengedit file `config.toml`.

Masuk ke direktori konfigurasi:
```sh
cd run
```

Buka file konfigurasi:
```sh
nano config.toml
```

Salin konfigurasi default dari testnet jika diperlukan:
```sh
cp config-testnet-turbo.toml config.toml
```

**Contoh konfigurasi dasar:**
```toml
network_listen_address = "0.0.0.0"
network_enr_tcp_port = 1234
network_enr_udp_port = 1234
network_libp2p_port = 1234
network_discovery_port = 1234
network_target_peers = 100
rpc_enabled = true
rpc_listen_address = "0.0.0.0:5678"
blockchain_rpc_endpoint = "https://16600.rpc.thirdweb.com/"
mine_contract_address = "0x6815F41019255e00D6F34aAB8397a6Af5b6D806f"
miner_key = ""  # Isi dengan private key untuk menambang PoRA
```

Simpan dan keluar dari editor (`CTRL+X`, lalu `Y` dan `Enter`).

---

## 5. Menjalankan Storage Node
Jalankan storage node dengan perintah berikut:
```sh
./target/release/0g-storage-node --config config.toml
```

Untuk memastikan node tetap berjalan meskipun terminal tertutup, jalankan dalam mode `screen` atau `tmux`:
```sh
screen -S 0g-node ./target/release/0g-storage-node --config config.toml
```
Tekan `CTRL+A`, lalu `D` untuk keluar dari screen tanpa menghentikan proses.

---

## 6. Monitoring dan Logging
Gunakan perintah berikut untuk memantau log node:
```sh
tail -f 0g-storage-node/run/log/zgs.log.2025.XX.XX
```

Cek status koneksi:
```sh
netstat -tulnp | grep 0g-storage-node
```

---

## 7. Troubleshooting
Jika node tidak berjalan, coba:
1. Periksa apakah semua dependensi sudah terinstal dengan benar.
2. Pastikan tidak ada firewall atau aturan jaringan yang memblokir port.
3. Jalankan ulang node dengan `RUST_BACKTRACE=1` untuk mendapatkan informasi debug lebih lanjut:
   ```sh
   RUST_BACKTRACE=1 ./target/release/0g-storage-node --config config.toml
   ```

---

## 8. Menutup Node
Untuk menghentikan node, gunakan perintah:
```sh
pkill -f 0g-storage-node
```

Atau jika dijalankan dalam `screen`, masuk kembali dengan:
```sh
screen -r 0g-node
```
Lalu tekan `CTRL+C` untuk menghentikan proses.

---

Dengan menyelesaikan langkah-langkah di atas, storage node Anda akan berjalan dan berkontribusi dalam jaringan 0G, memungkinkan Anda untuk memperoleh insentif dari partisipasi dalam ekosistem desentralisasi penyimpanan data.

