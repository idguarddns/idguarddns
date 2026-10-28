<p align="center">
  <a href="https://idguard.ai.id/">
    <img src="https://github.com/idguarddns.png" alt="IDGUARD AI CTI Logo" width="128" height="128">
  </a>
</p>

<h1 align="center">IDGUARD AI THREAT INTEL</h1>

<p align="center">
  <strong>Autonomous Cyber Threat Intelligence & Recursive DNS SOC</strong>
</p>

<p align="center">
  Pusat Komando Security Operations Center (SOC) dengan mesin filtering DNS cerdas. Menggabungkan enkripsi DoH & DoT dengan integrasi basis data ancaman siber real-time.
</p>

<p align="center">
  <a href="https://idguard.ai.id/"><img src="https://img.shields.io/badge/Website-idguard.ai.id-blue?style=flat-square" alt="Website"></a>
  <a href="#"><img src="https://img.shields.io/badge/Uptime-99.98%25-brightgreen?style=flat-square" alt="Uptime"></a>
  <a href="#"><img src="https://img.shields.io/badge/Blocklist-2.8M%2B_Domains-red?style=flat-square" alt="Blocklist"></a>
  <a href="#"><img src="https://img.shields.io/badge/Engine-Unbound_1.20%2B-orange?style=flat-square" alt="Engine"></a>
</p>

---

<details open>
  <summary><b>📌 DAFTAR ISI (Klik untuk Membuka / Menutup)</b></summary>
  <br>

  - [ℹ️ Tentang](#-tentang)
  - [🌐 Peladen DNS Utama](#-peladen-dns-utama)
  - [🛡️ Daftar Blokir DNS (Blocklist)](#%EF%B8%8F-daftar-blokir-dns-blocklist)
  - [🚀 Panduan Pemasangan](#-panduan-pemasangan)
  - [📊 Status Peladen & Uji Keamanan](#-status-peladen--uji-keamanan)
  - [📩 Pelaporan & Kontak](#-pelaporan--kontak)
  - [🤝 Lisensi & Kredit](#-lisensi--kredit)
</details>

---

## ℹ️ Tentang

**IDGUARD AI CTI** adalah implementasi *DNS Resolver* berbasis *Cyber Threat Intelligence* yang dilengkapi pemfilteran otomatis untuk memblokir malware, phishing, scam, judi online, dan ancaman siber lainnya secara *real-time*.

Diprakarsai oleh tim **JawaTimur Cyber Security** dan **DevHunter Security**, IDGUARD menjamin privasi pengguna dan tidak pernah menyimpan catatan kueri (*query logs*) kecuali saat terjadi pelaporan masalah teknis untuk melacak *bug*.

---

## 🌐 Peladen DNS Utama

<details>
  <summary><b>1. Standard DNS (IPv4 / IPv6)</b></summary>
  <br>

Gunakan alamat IP berikut pada router, server, atau adapter jaringan perangkat Anda:

| Protokol | Alamat IP | Port |
| :--- | :--- | :--- |
| **IPv4 Primary** | `103.133.222.156` | `53` |
| **IPv6 Primary** | `2001:df4:b100:3:1:1:8c2a:131b` | `53` |
</details>

<details>
  <summary><b>2. DNS-over-TLS (DoT)</b></summary>
  <br>

Khusus untuk fitur *Private DNS* pada Android (v9+), iOS Profile, atau Linux `systemd-resolved`:

| Protokol | Alamat / Hostname | Port |
| :--- | :--- | :--- |
| **DNS-over-TLS** | `dns.idguard.ai.id` | `853` |
</details>

<details>
  <summary><b>3. DNS-over-HTTPS (DoH)</b></summary>
  <br>

Dapat digunakan pada peramban web modern (Chrome, Firefox, Brave, Edge) serta RouterOS v7:

| Protokol | URL Endpoint | Port |
| :--- | :--- | :--- |
| **DNS-over-HTTPS** | `https://dns.idguard.ai.id/dns-query` | `443` |
</details>

---

## 🛡️ Daftar Blokir DNS (Blocklist)

<details>
  <summary><b>Lihat Sumber & Kategori Blocklist</b></summary>
  <br>

IDGUARD mengintegrasikan berbagai sumber *threat intelligence* tepercaya untuk memastikan perlindungan optimal:

- **IDGUARD AI CTI Custom Rules**
- **PhishDestroy & URLHaus** (Phishing & Malware)
- **HaGeZi Threat Intelligence**
- **TrustPositif** (Kominfo / Regulasi Lokal)
- **OISD Big & SmartDNS Rules**
</details>

---

## 🚀 Panduan Pemasangan

<details>
  <summary><b>📱 Android (Private DNS)</b></summary>
  <br>

1. Buka menu **Pengaturan (Settings)** > **Koneksi / Jaringan & Internet**.
2. Pilih **Pengaturan Koneksi Lainnya** > **DNS Pribadi (Private DNS)**.
3. Pilih **Nama Host Penyedia DNS Pribadi**.
4. Isi dengan hostname: `dns.idguard.ai.id`
5. Simpan perubahan.
</details>

<details>
  <summary><b>🍏 iOS / macOS</b></summary>
  <br>

1. Unduh atau buat Profil DoH/DoT Apple.
2. Buka **Settings** > **Profile Downloaded** lalu klik **Install**.
3. Aktifkan profile IDGUARD DNS pada pengaturan *VPN & Device Management*.
</details>

<details>
  <summary><b>🌐 Peramban Web (Browser)</b></summary>
  <br>

1. Buka **Pengaturan (Settings)** peramban web Anda.
2. Cari menu **Security** / **Keamanan & Privasi**.
3. Aktifkan opsi **Gunakan DNS Aman (Use Secure DNS)**.
4. Pilih **Kustom (Custom)** lalu masukkan URL berikut:
   ```text
   https://dns.idguard.ai.id/dns-query
   ```
</details>

<details>
  <summary><b>📶 MikroTik RouterOS</b></summary>
  <br>

Gunakan baris perintah berikut pada Terminal RouterOS v7:

```routeros
/tool fetch url="https://curl.se/ca/cacert.pem" download=yes
/certificate import file-name=cacert.pem passphrase=""
/ip dns set use-doh-server="https://dns.idguard.ai.id/dns-query" verify-doh-cert=yes
/ip dns cache flush
```
</details>

<details>
  <summary><b>🐧 Linux (systemd-resolved)</b></summary>
  <br>

Edit berkas `/etc/systemd/resolved.conf`:

```ini
[Resolve]
DNS=103.133.222.156#dns.idguard.ai.id
FallbackDNS=2001:df4:b100:3:1:1:8c2a:131b#dns.idguard.ai.id
DNSOverTLS=yes
```

Lalu jalankan ulang layanannya:
```bash
sudo systemctl restart systemd-resolved
```
</details>

---

## 📊 Status Peladen & Uji Keamanan

<details>
  <summary><b>Lihat Matriks Status & SLA</b></summary>
  <br>

| Pengujian | Status / Nilai | Keterangan |
| :--- | :--- | :--- |
| **SLA Uptime** | `99.98%` | *Monitored 24/7* |
| **Response Action** | `NXDOMAIN` | Menghentikan domain berbahaya secara langsung |
| **SSL Security Test** | `A+` | ImmuniWeb & SSL Labs Qualified |
</details>

---

## 📩 Pelaporan & Kontak

<details>
  <summary><b>Lihat Informasi Pelaporan (False Positive / Malware)</b></summary>
  <br>

Jika menemukan situs yang mengalami *False Positive* (salah blokir) atau ingin melaporkan indikasi domain ancaman siber baru:

- **Telegram Bot/Group:** [t.me/idguard-report](https://t.me/idguard-report)
- **Email:** [report@idguard.ai.id](mailto:report@idguard.ai.id)
- **Waktu Respon SLA:** `< 24 Jam`
</details>

---

## 🤝 Lisensi & Kredit

Dikembangkan dan dikelola bersama oleh:
- **JawaTimur Cyber Security**
- **DevHunter Security**
