<p align="center">
  <a href="https://idguard.ai.id/">
    <img src="https://idguard.ai.id/assets/img/logo.png" alt="IDGUARD AI CTI" width="150">
  </a>
</p>

<h1 align="center">IDGUARD AI Threat Intel</h1>

<p align="center">
  <b>Autonomous Cyber Threat Intelligence & Recursive DNS SOC</b><br>
  Membantu Anda berselancar secara aman dan terhindar dari ancaman siber!
</p>

<p align="center">
  <a href="https://idguard.ai.id/"><img src="https://img.shields.io/badge/Website-idguard.ai.id-blue?style=flat-square" alt="Website"></a>
  <a href="#"><img src="https://img.shields.io/badge/Uptime-99.98%25-brightgreen?style=flat-square" alt="Uptime"></a>
  <a href="#"><img src="https://img.shields.io/badge/Engine-Unbound_1.20%2B-orange?style=flat-square" alt="DNS Engine"></a>
  <a href="#"><img src="https://img.shields.io/badge/Blocklist-2.8M%2B_Domains-red?style=flat-square" alt="Blocklist"></a>
</p>

---

## 📋 Daftar Isi

* [Peladen DNS Utama](#-peladen-dns-utama)
  * [Standard DNS](#1-standard-dns)
  * [DNS-over-TLS (DoT)](#2-dns-over-tls-dot)
  * [DNS-over-HTTPS (DoH)](#3-dns-over-https-doh)
* [Daftar Blokir DNS (Blocklist)](#-daftar-blokir-dns-blocklist)
* [Panduan Pemasangan](#-panduan-pemasangan)
  * [Android](#android)
  * [iOS / macOS](#ios--macos)
  * [Peramban Web (Browser)](#peramban-web-browser)
  * [MikroTik RouterOS](#mikrotik-routeros)
  * [Linux (systemd-resolved)](#linux-systemd-resolved)
* [Status Peladen & Uji Keamanan](#-status-peladen--uji-keamanan)
* [Pelaporan & Kontak](#-pelaporan--kontak)
* [Lisensi & Kredit](#-lisensi--kredit)

---

## ℹ️ Tentang

**IDGUARD AI CTI** adalah implementasi *DNS Resolver* berbasis *Cyber Threat Intelligence* yang dilengkapi pemfilteran otomatis untuk memblokir malware, phishing, scam, judi online, dan ancaman siber lainnya secara *real-time*.

Diprakarsai oleh tim **JawaTimur Cyber Security** dan **DevHunter Security**, IDGUARD menjamin privasi pengguna dan tidak pernah menyimpan catatan kueri (*query logs*) kecuali saat terjadi pelaporan masalah teknis untuk melacak *bug*.

---

## 🌐 Peladen DNS Utama

### 1. Standard DNS
Gunakan alamat IP berikut pada router, server, atau adapter jaringan perangkat Anda:

| Protokol | Alamat IP | Port |
| :--- | :--- | :--- |
| **IPv4 Primary** | `103.133.222.156` | `53` |
| **IPv6 Primary** | `2001:df4:b100:3:1:1:8c2a:131b` | `53` |

### 2. DNS-over-TLS (DoT)
Khusus untuk fitur *Private DNS* pada Android (v9+), iOS Profile, atau Linux `systemd-resolved`:

| Protokol | Alamat / Hostname | Port |
| :--- | :--- | :--- |
| **DNS-over-TLS** | `dns.idguard.ai.id` | `853` |

### 3. DNS-over-HTTPS (DoH)
Dapat digunakan pada peramban web modern (Chrome, Firefox, Brave, Edge) serta RouterOS v7:

| Protokol | URL Endpoint | Port |
| :--- | :--- | :--- |
| **DNS-over-HTTPS** | `https://dns.idguard.ai.id/dns-query` | `443` |

---

## 🛡️ Daftar Blokir DNS (Blocklist)

IDGUARD mengintegrasikan berbagai sumber *threat intelligence* tepercaya untuk memastikan perlindungan optimal:

* **IDGUARD AI CTI Custom Rules**
* **PhishDestroy & URLHaus** (Phishing & Malware)
* **HaGeZi Threat Intelligence**
* **TrustPositif** (Komdigi / Regulasi Indonesia)
* **OISD Big**

---

## 🚀 Panduan Pemasangan

### Android
1. Buka menu **Pengaturan (Settings)** > **Koneksi / Jaringan & Internet**.
2. Pilih **Pengaturan Koneksi Lainnya** > **DNS Pribadi (Private DNS)**.
3. Pilih **Nama Host Penyedia DNS Pribadi**.
4. Isi dengan hostname: `dns.idguard.ai.id`
5. Simpan perubahan.

### iOS / macOS
1. Unduh atau buat Profil DoH/DoT Apple.
2. Buka **Settings** > **Profile Downloaded** lalu klik **Install**.
3. Aktifkan profile IDGUARD DNS pada pengaturan *VPN & Device Management*.

### Peramban Web (Browser)
1. Buka **Pengaturan (Settings)** peramban web Anda.
2. Cari menu **Security** / **Keamanan & Privasi**.
3. Aktifkan opsi **Gunakan DNS Aman (Use Secure DNS)**.
4. Pilih **Kustom (Custom)** lalu masukkan URL berikut:
   ```text
   https://dns.idguard.ai.id/dns-query
   ```

### MikroTik RouterOS
Gunakan baris perintah berikut pada Terminal RouterOS v7:

```routeros
/tool fetch url="https://curl.se/ca/cacert.pem" download=yes
/certificate import file-name=cacert.pem passphrase=""
/ip dns set use-doh-server="https://dns.idguard.ai.id/dns-query" verify-doh-cert=yes
/ip dns cache flush
```

### Linux (systemd-resolved)
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

---

## 📊 Status Peladen & Uji Keamanan

| Pengujian | Status / Nilai | Keterangan |
| :--- | :--- | :--- |
| **SLA Uptime** | `99.98%` | *Monitored 24/7* |
| **Response Action** | `NXDOMAIN` | Menghentikan domain berbahaya secara langsung |
| **SSL Security Test** | `A+` | ImmuniWeb & SSL Labs Qualified |

---

## 📩 Pelaporan & Kontak

Jika menemukan situs yang mengalami *False Positive* (salah blokir) atau ingin melaporkan indikasi domain ancaman siber baru:

* **Telegram Bot/Group:** [t.me/idguard-report](https://t.me/idguard-report)
* **Email:** [report@idguard.ai.id](mailto:report@idguard.ai.id)
* **Waktu Respon SLA:** `< 24 Jam`

---

## 🤝 Lisensi & Kredit

Dikembangkan dan dikelola bersama oleh:
* **JawaTimur Cyber Security**
* **DevHunter Security**
