# 🚀 GUACAMOLE UNIVERSAL INSTALLER - USER JOURNEY

```
═══════════════════════════════════════════════════════════════════════════
                    GUACAMOLE UNIVERSAL INSTALL SCRIPT
                         guacamole-universal-install.sh
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ 🧭 FASE 00: PRASYARAT & VALIDASI SISTEM                                │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CHECK] Apakah script dijalankan sebagai root/sudo?
│   ├─── ✓ YES → Lanjut
│   └─── ✗ NO  → ERROR: "Script harus dijalankan dengan sudo!"
│                 EXIT
│
├─► [CHECK] Sistem operasi = Ubuntu?
│   ├─── ✓ YES → Lanjut
│   └─── ✗ NO  → ERROR: "Script ini hanya support Ubuntu!"
│                 EXIT
│
├─► [CHECK] Arsitektur = x86_64?
│   ├─── ✓ YES → Lanjut
│   └─── ✗ NO  → ERROR: "Arsitektur tidak didukung!"
│                 EXIT
│
└─► [CHECK] Koneksi internet aktif?
    ├─── ✓ YES → INFO: "✓ Semua prasyarat terpenuhi"
    │            Lanjut ke FASE 01
    └─── ✗ NO  → ERROR: "Tidak ada koneksi internet!"
                  EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔢 FASE 01: DETEKSI & KONFIRMASI IP PUBLIK                             │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [AUTO-DETECT] Mencoba deteksi IP publik...
│   │             (curl -s ifconfig.me / ipinfo.io/ip / icanhazip.com)
│   │
│   ├─── ✓ SUKSES → Terdeteksi: 35.208.16.99
│   │              
│   │              TAMPILAN:
│   │              ┌─────────────────────────────────────────┐
│   │              │ IP publik terdeteksi: 35.208.16.99      │
│   │              │ Gunakan IP ini? [Y/n]:                  │
│   │              └─────────────────────────────────────────┘
│   │              
│   │              USER INPUT:
│   │              ├─► [Y] atau [Enter] → Simpan IP: 35.208.16.99
│   │              │                      Lanjut ke FASE 02
│   │              │
│   │              └─► [n] → "Masukkan IP manual: _____"
│   │                        Simpan IP yang diinput
│   │                        Lanjut ke FASE 02
│   │
│   └─── ✗ GAGAL → WARNING: "Tidak dapat mendeteksi IP otomatis"
│                  
│                   TAMPILAN:
│                   ┌─────────────────────────────────────────┐
│                   │ Masukkan IP publik server:              │
│                   │ > _____                                 │
│                   └─────────────────────────────────────────┘
│                   
│                   USER INPUT: (contoh: 35.208.16.99)
│                   Simpan IP yang diinput
│                   Lanjut ke FASE 02


┌─────────────────────────────────────────────────────────────────────────┐
│ 🌐 FASE 02: INPUT DOMAIN (OPSIONAL)                                    │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [PROMPT] 
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Apakah Anda ingin menggunakan domain? (y/N):               │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [N] atau [Enter] → INFO: "Akan menggunakan IP: 35.208.16.99"
    │                      SET: USE_DOMAIN=false
    │                      SET: DOMAIN=""
    │                      Lanjut ke FASE 03
    │
    └─► [y] → TAMPILAN:
              ┌─────────────────────────────────────────────────┐
              │ Masukkan domain (contoh: guac.example.com):     │
              │ > _____                                         │
              └─────────────────────────────────────────────────┘
              
              USER INPUT: (contoh: guac.example.com)
              
              [VALIDASI] Apakah format domain valid?
              ├─── ✓ VALID → SET: USE_DOMAIN=true
              │              SET: DOMAIN="guac.example.com"
              │              INFO: "Domain dikonfigurasi: guac.example.com"
              │              Lanjut ke FASE 03
              │
              └─── ✗ INVALID → ERROR: "Format domain tidak valid!"
                                Ulangi input domain


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔐 FASE 03: PILIH METODE SSL                                           │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [MENU] 
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Pilih metode SSL:                                           │
    │                                                             │
    │ [1] Self-signed SSL (Generate otomatis)                     │
    │     • Gratis, cepat setup                                   │
    │     • Browser akan warning "Not Secure"                     │
    │     • Cocok untuk testing/internal                          │
    │                                                             │
    │ [2] Let's Encrypt (Gratis, Trusted)                         │
    │     • Membutuhkan domain valid                              │
    │     • Auto-renewal setiap 90 hari                           │
    │     • Tidak ada browser warning                             │
    │                                                             │
    │ [3] Cloudflare (Managed SSL)                                │
    │     • SSL dikelola oleh Cloudflare                          │
    │     • Tidak generate di server                              │
    │     • Harus pakai Cloudflare Tunnel                         │
    │                                                             │
    │ Masukkan pilihan [1-3]: _                                   │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [1] → SET: SSL_METHOD="selfsigned"
    │         INFO: "SSL self-signed akan di-generate nanti"
    │         Lanjut ke FASE 04
    │
    ├─► [2] → [CHECK] Apakah USE_DOMAIN=true?
    │         ├─── ✓ YES → SET: SSL_METHOD="letsencrypt"
    │         │            INFO: "Let's Encrypt akan disetup dengan certbot"
    │         │            Lanjut ke FASE 04
    │         │
    │         └─── ✗ NO  → ERROR: "Let's Encrypt membutuhkan domain!"
    │                      Kembali ke FASE 02 (input domain)
    │
    ├─► [3] → SET: SSL_METHOD="cloudflare"
    │         INFO: "SSL akan dikelola Cloudflare (proxy mode)"
    │         Lanjut ke FASE 04
    │
    └─► [Invalid] → ERROR: "Pilihan tidak valid!"
                    Ulangi FASE 03


┌─────────────────────────────────────────────────────────────────────────┐
│ 🌤️ FASE 04: PILIH METODE AKSES                                         │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [MENU] 
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Pilih metode akses ke Guacamole:                            │
    │                                                             │
    │ [A] Port Terbuka (Standard)                                 │
    │     • Akses langsung via IP/domain                          │
    │     • Firewall: 80, 443, 8080 (terbuka)                     │
    │     • Cocok untuk: Server publik standar                    │
    │                                                             │
    │ [B] Cloudflare Tunnel (Zero Trust)                          │
    │     • Tidak ada port publik terbuka                         │
    │     • SSH via IAP: 35.235.240.0/20 → 22                     │
    │     • Cocok untuk: GCP dengan keamanan maksimal             │
    │     • Membutuhkan: Tunnel ID + credential JSON              │
    │                                                             │
    │ Masukkan pilihan [A/B]: _                                   │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [A] → SET: ACCESS_METHOD="port"
    │         INFO: "Port 80, 443, 8080 akan dibuka"
    │         Lanjut ke FASE 05
    │
    └─► [B] → SET: ACCESS_METHOD="cloudflare-tunnel"
              INFO: "Cloudflare Tunnel akan dikonfigurasi"
              
              ┌─────────────────────────────────────────────────┐
              │ Masukkan Cloudflare Tunnel ID:                  │
              │ > _____                                         │
              └─────────────────────────────────────────────────┘
              
              USER INPUT: (contoh: abc123-def456-ghi789)
              SET: TUNNEL_ID="abc123-def456-ghi789"
              
              ┌─────────────────────────────────────────────────┐
              │ Paste credential JSON (multi-line):             │
              │ (Ketik 'END' pada baris baru untuk selesai)     │
              │ > _____                                         │
              └─────────────────────────────────────────────────┘
              
              USER INPUT: (paste JSON)
              {
                "AccountTag": "...",
                "TunnelSecret": "...",
                "TunnelID": "..."
              }
              END
              
              VALIDASI JSON:
              ├─── ✓ VALID → Simpan ke ~/cloudflared/credentials.json
              │              INFO: "Tunnel credentials disimpan"
              │              Lanjut ke FASE 05
              │
              └─── ✗ INVALID → ERROR: "Format JSON tidak valid!"
                                Ulangi input credential


┌─────────────────────────────────────────────────────────────────────────┐
│ 📦 FASE 05: PILIH DATABASE                                             │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [MENU] 
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Pilih database backend:                                     │
    │                                                             │
    │ [1] MySQL 8.0 (Recommended)                                 │
    │     • Lebih stabil untuk Guacamole                          │
    │     • Dokumentasi lengkap                                   │
    │     • Init: mysql/schema/*.sql                              │
    │                                                             │
    │ [2] PostgreSQL (Alternative)                                │
    │     • Performa lebih baik untuk high load                   │
    │     • Init: postgresql/schema/*.sql                         │
    │                                                             │
    │ Masukkan pilihan [1-2]: _                                   │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [1] → SET: DB_TYPE="mysql"
    │         SET: DB_IMAGE="mysql:8.0"
    │         SET: DB_INIT_URL="https://raw.githubusercontent.com/.../mysql/schema/"
    │         INFO: "MySQL 8.0 akan digunakan"
    │         Lanjut ke FASE 06
    │
    ├─► [2] → SET: DB_TYPE="postgresql"
    │         SET: DB_IMAGE="postgres:15"
    │         SET: DB_INIT_URL="https://raw.githubusercontent.com/.../postgresql/schema/"
    │         INFO: "PostgreSQL akan digunakan"
    │         Lanjut ke FASE 06
    │
    └─► [Invalid] → ERROR: "Pilihan tidak valid!"
                    Ulangi FASE 05


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔑 FASE 06: INPUT KREDENSIAL DATABASE                                  │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [PROMPT] Password Root Database
│   
│   TAMPILAN:
│   ┌─────────────────────────────────────────────────────────────┐
│   │ Masukkan password ROOT database:                            │
│   │ (Input tersembunyi, min 8 karakter)                         │
│   │ > ********                                                  │
│   └─────────────────────────────────────────────────────────────┘
│   
│   USER INPUT: (hidden)
│   
│   VALIDASI:
│   ├─── ✓ Length >= 8 → SET: MYSQL_ROOT_PASSWORD="********"
│   │                    Lanjut ke password user
│   └─── ✗ Too short   → ERROR: "Password minimal 8 karakter!"
│                         Ulangi input
│
└─► [PROMPT] Password User Database
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Masukkan password USER database (guacamole_user):           │
    │ (Input tersembunyi, min 8 karakter)                         │
    │ > ********                                                  │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT: (hidden)
    
    VALIDASI:
    ├─── ✓ Length >= 8 → SET: MYSQL_PASSWORD="********"
    │                    
    │                    [SIMPAN] Buat file .env
    │                    └─► ~/guacamole/.env
    │                        ├─ MYSQL_ROOT_PASSWORD=********
    │                        └─ MYSQL_PASSWORD=********
    │                    
    │                    [SECURE] chmod 600 .env
    │                    INFO: "✓ Kredensial database tersimpan aman"
    │                    Lanjut ke FASE 07
    │
    └─── ✗ Too short   → ERROR: "Password minimal 8 karakter!"
                          Ulangi input


┌─────────────────────────────────────────────────────────────────────────┐
│ 🛡️ FASE 07: KONFIGURASI KEAMANAN OPSIONAL                              │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CONDITIONAL] Jika ACCESS_METHOD="cloudflare-tunnel":
│   
│   TAMPILAN:
│   ┌─────────────────────────────────────────────────────────────┐
│   │ Konfigurasi Cloudflare Access (Zero Trust):                 │
│   │                                                             │
│   │ Masukkan email untuk whitelist (kosongkan jika skip):      │
│   │ > _____                                                     │
│   └─────────────────────────────────────────────────────────────┘
│   
│   USER INPUT:
│   ├─► [Email] → SET: ZERO_TRUST_EMAIL="user@example.com"
│   │            INFO: "Email akan di-whitelist di Cloudflare Access"
│   └─► [Empty] → SET: ZERO_TRUST_EMAIL=""
│                 INFO: "Cloudflare Access dilewati"
│
└─► [PROMPT] Metode SSH Awal
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────────────────┐
    │ Metode SSH yang digunakan sekarang:                         │
    │                                                             │
    │ [1] Identity-Aware Proxy (IAP)                              │
    │     • Recommended untuk GCP                                 │
    │     • Source: 35.235.240.0/20                               │
    │                                                             │
    │ [2] Akses langsung (0.0.0.0/0)                              │
    │     • Kurang aman                                           │
    │     • Akan ditutup setelah setup selesai                    │
    │                                                             │
    │ Masukkan pilihan [1-2]: _                                   │
    └─────────────────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [1] → SET: SSH_METHOD="iap"
    │         SET: SSH_SOURCE="35.235.240.0/20"
    │         INFO: "UFW akan allow SSH dari IAP range only"
    │         Lanjut ke FASE 08
    │
    └─► [2] → SET: SSH_METHOD="direct"
              SET: SSH_SOURCE="0.0.0.0/0"
              WARNING: "SSH terbuka publik (sementara)"
              Lanjut ke FASE 08


┌─────────────────────────────────────────────────────────────────────────┐
│ 💾 FASE 08: BUAT SWAP MEMORY 2GB                                       │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CHECK] Apakah swap sudah ada?
│   │       (free -h | grep Swap)
│   │
│   ├─── Swap > 0 → INFO: "✓ Swap sudah ada (${SWAP_SIZE})"
│   │               Lanjut ke FASE 09
│   │
│   └─── Swap = 0 → INFO: "Membuat swap 2GB..."
│                   
│                   [EXECUTE]
│                   ├─► fallocate -l 2G /swapfile
│                   ├─► chmod 600 /swapfile
│                   ├─► mkswap /swapfile
│                   ├─► swapon /swapfile
│                   ├─► echo '/swapfile none swap sw 0 0' >> /etc/fstab
│                   └─► sysctl vm.swappiness=10
│                   
│                   [VERIFY] free -h
│                   ├─── Swap: 2.0G → INFO: "✓ Swap 2GB berhasil dibuat"
│                   │                 Lanjut ke FASE 09
│                   └─── Swap: 0    → ERROR: "Gagal membuat swap!"
│                                     EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 📦 FASE 09: INSTALL DEPENDENCIES                                       │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [EXECUTE] apt update && apt upgrade -y
    │         (with progress bar)
    │
    ├─► [EXECUTE] apt install -y \
    │             curl wget git nano ufw net-tools htop mc micro nginx
    │             (with progress bar)
    │
    └─► [VERIFY] Semua package terinstal?
        ├─── ✓ YES → INFO: "✓ Dependencies terinstal"
        │            Lanjut ke FASE 10
        └─── ✗ NO  → ERROR: "Gagal install dependencies!"
                      Tampilkan error log
                      EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 🐳 FASE 10: INSTALL DOCKER (VIA get.docker.com)                        │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CHECK] Apakah Docker sudah terinstal?
│   │       (docker --version)
│   │
│   ├─── ✓ Installed → INFO: "✓ Docker sudah terinstal (${VERSION})"
│   │                  Lanjut ke FASE 11
│   │
│   └─── ✗ Not found → INFO: "Menginstal Docker..."
│                     
│                      [EXECUTE]
│                      ├─► curl -fsSL https://get.docker.com -o get-docker.sh
│                      ├─► sh get-docker.sh
│                      │   (Menginstal otomatis:)
│                      │   ├─ Docker Engine
│                      │   ├─ containerd
│                      │   ├─ runc
│                      │   ├─ Docker Compose Plugin
│                      │   └─ Docker Buildx Plugin
│                      │
│                      ├─► systemctl start docker
│                      ├─► systemctl enable docker
│                      └─► usermod -aG docker $USER
│                      
│                      [VERIFY] docker --version && docker compose version
│                      ├─── ✓ OK → INFO: "✓ Docker terinstal"
│                      │          INFO: "  - Docker: ${DOCKER_VERSION}"
│                      │          INFO: "  - Compose: ${COMPOSE_VERSION}"
│                      │          Lanjut ke FASE 11
│                      │
│                      └─── ✗ Failed → ERROR: "Gagal install Docker!"
│                                       EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 📁 FASE 11: BUAT STRUKTUR DIREKTORI                                    │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [EXECUTE] mkdir -p ~/guacamole/{mysql,postgres,init,drive,record}
    │
    └─► [VERIFY] Direktori dibuat?
        ├─── ✓ YES → INFO: "✓ Struktur direktori siap"
        │            
        │            STRUKTUR:
        │            ~/guacamole/
        │            ├── mysql/      (untuk data MySQL)
        │            ├── postgres/   (untuk data PostgreSQL)
        │            ├── init/       (untuk SQL init scripts)
        │            ├── drive/      (untuk file transfers)
        │            └── record/     (untuk session recordings)
        │            
        │            Lanjut ke FASE 12
        │
        └─── ✗ NO  → ERROR: "Gagal membuat direktori!"
                      EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 🗃️ FASE 12: DOWNLOAD INIT SCRIPT DATABASE                              │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [INFO] "Mengunduh SQL init scripts untuk ${DB_TYPE}..."
    │
    ├─► cd ~/guacamole/init
    │
    ├─► [DOWNLOAD] 001-create-schema.sql
    │   wget ${DB_INIT_URL}/001-create-schema.sql -O 001-create-schema.sql
    │   
    │   [VERIFY]
    │   ├─── ✓ Sukses (HTTP 200) → INFO: "✓ Schema downloaded"
    │   └─── ✗ Gagal  (HTTP 404) → ERROR: "Gagal download schema!"
    │                                EXIT
    │
    └─► [DOWNLOAD] 002-create-admin-user.sql
        wget ${DB_INIT_URL}/002-create-admin-user.sql -O 002-create-admin-user.sql
        
        [VERIFY]
        ├─── ✓ Sukses (HTTP 200) → INFO: "✓ Admin user script downloaded"
        │                          INFO: "✓ Init scripts siap"
        │                          Lanjut ke FASE 13
        │
        └─── ✗ Gagal  (HTTP 404) → ERROR: "Gagal download admin script!"
                                    EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 📜 FASE 13: BUAT docker-compose.yml                                    │
└─────────────────────────────────────────────────────────────────────────┘
│
└─► [INFO] "Membuat docker-compose.yml dengan konfigurasi optimized..."
    │
    ├─► [CONDITIONAL] Port exposure berdasarkan ACCESS_METHOD:
    │   │
    │   ├─── ACCESS_METHOD="port" → 
    │   │    Port 8080 di-expose: "8080:8080"
    │   │    (Akses langsung via IP:8080)
    │   │
    │   └─── ACCESS_METHOD="cloudflare-tunnel" → 
    │        Port 8080 TIDAK di-expose
    │        (Hanya internal via localhost)
    │
    ├─► [GENERATE] docker-compose.yml
    │   
    │   KONTEN:
    │   ┌─────────────────────────────────────────────────┐
    │   │ version: '3.8'                                  │
    │   │                                                 │
    │   │ services:                                       │
    │   │   guacd:                                        │
    │   │     image: guacamole/guacd                      │
    │   │     container_name: guacd                       │
    │   │     restart: unless-stopped                     │
    │   │     deploy:                                     │
    │   │       resources:                                │
    │   │         limits:                                 │
    │   │           memory: 256M                          │
    │   │                                                 │
    │   │   ${DB_TYPE}:                                   │
    │   │     image: ${DB_IMAGE}                          │
    │   │     container_name: guacamole-${DB_TYPE}        │
    │   │     restart: unless-stopped                     │
    │   │     environment:                                │
    │   │       MYSQL_ROOT_PASSWORD: ${...}               │
    │   │       MYSQL_DATABASE: guacamole_db              │
    │   │       MYSQL_USER: guacamole_user                │
    │   │       MYSQL_PASSWORD: ${...}                    │
    │   │     volumes:                                    │
    │   │       - ./${DB_TYPE}:/var/lib/${DB_TYPE}        │
    │   │       - ./init:/docker-entrypoint-initdb.d:ro   │
    │   │     deploy:                                     │
    │   │       resources:                                │
    │   │         limits:                                 │
    │   │           memory: 384M                          │
    │   │     command: --innodb-buffer-pool-size=128M     │
    │   │                                                 │
    │   │   guacamole:                                    │
    │   │     image: guacamole/guacamole                  │
    │   │     container_name: guacamole                   │
    │   │     restart: unless-stopped                     │
    │   │     ports:                                      │
    │   │       - "8080:8080"  # (conditional)            │
    │   │     environment:                                │
    │   │       GUACD_HOSTNAME: guacd                     │
    │   │       MYSQL_HOSTNAME: ${DB_TYPE}                │
    │   │       MYSQL_DATABASE: guacamole_db              │
    │   │       MYSQL_USER: guacamole_user                │
    │   │       MYSQL_PASSWORD: ${...}                    │
    │   │     depends_on:                                 │
    │   │       - guacd                                   │
    │   │       - ${DB_TYPE}                              │
    │   │     deploy:                                     │
    │   │       resources:                                │
    │   │         limits:                                 │
    │   │           memory: 384M                          │
    │   │                                                 │
    │   │ networks:                                       │
    │   │   guacamole-net:                                │
    │   │     driver: bridge                              │
    │   └─────────────────────────────────────────────────┘
    │
    └─► [SAVE] ~/guacamole/docker-compose.yml
        
        [VERIFY] File created?
        ├─── ✓ YES → INFO: "✓ docker-compose.yml dibuat"
        │            Lanjut ke FASE 14
        └─── ✗ NO  → ERROR: "Gagal membuat docker-compose.yml!"
                      EXIT



┌─────────────────────────────────────────────────────────────────────────┐
│ 🚀 FASE 14: JALANKAN GUACAMOLE                                         │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [INFO] "Memulai Guacamole containers..."
│   
├─► cd ~/guacamole
│
├─► [EXECUTE] docker compose up -d
│   │         (with progress)
│   │
│   │         OUTPUT:
│   │         ┌─────────────────────────────────────┐
│   │         │ [+] Running 4/4                     │
│   │         │  ✔ Network guacamole_default        │
│   │         │  ✔ Container guacd                  │
│   │         │  ✔ Container guacamole-mysql        │
│   │         │  ✔ Container guacamole              │
│   │         └─────────────────────────────────────┘
│   │
│   └─► [WAIT] Tunggu 20 detik untuk init database...
│           sleep 20
│
├─► [VERIFY] Containers berjalan?
│   │       docker ps
│   │
│   │       EXPECTED OUTPUT:
│   │       ┌─────────────────────────────────────────────────┐
│   │       │ CONTAINER ID   NAME              STATUS         │
│   │       │ abc123         guacd              Up 25 seconds  │
│   │       │ def456         guacamole-mysql    Up 30 seconds  │
│   │       │ ghi789         guacamole          Up 22 seconds  │
│   │       └─────────────────────────────────────────────────┘
│   │
│   ├─── ✓ All Running → INFO: "✓ Semua container aktif (3/3)"
│   │                    Lanjut ke health check
│   │
│   └─── ✗ Some Failed → ERROR: "Container gagal start!"
│                        
│                        [TROUBLESHOOT]
│                        ┌─────────────────────────────────────┐
│                        │ Cek logs error:                     │
│                        │                                     │
│                        │ docker compose logs guacamole       │
│                        │ docker compose logs mysql           │
│                        │ docker compose logs guacd           │
│                        └─────────────────────────────────────┘
│                        
│                        COMMON ISSUES & FIXES:
│                        
│                        Issue 1: MySQL password error
│                        ├─► cat .env
│                        ├─► Cek MYSQL_ROOT_PASSWORD & MYSQL_PASSWORD
│                        └─► Fix: Edit .env, lalu:
│                            docker compose down
│                            docker compose up -d
│                        
│                        Issue 2: Init SQL tidak tereksekusi
│                        ├─► ls -la init/*.sql
│                        └─► Fix: Re-download init files (FASE 12)
│                        
│                        Issue 3: Port 8080 sudah dipakai
│                        ├─► netstat -tlnp | grep 8080
│                        └─► Fix: Stop service lain atau ganti port
│                        
│                        Issue 4: Memory insufficient
│                        ├─► free -h
│                        └─► Fix: Restart dengan swap (FASE 08)
│                        
│                        Jika masih error: EXIT
│
├─► [CHECK] Container health status
│   │       docker compose ps
│   │
│   │       EXPECTED OUTPUT:
│   │       ┌─────────────────────────────────────────────────┐
│   │       │ NAME              STATE    HEALTH              │
│   │       │ guacd             running  healthy             │
│   │       │ guacamole-mysql   running  healthy             │
│   │       │ guacamole         running  healthy             │
│   │       └─────────────────────────────────────────────────┘
│   │
│   ├─── ✓ All Healthy → INFO: "✓ Containers healthy"
│   │                    Lanjut ke service check
│   │
│   └─── ✗ Unhealthy → WARNING: "Container tidak healthy"
│                       
│                       [DIAGNOSIS]
│                       ├─► docker inspect guacamole | grep Health -A 10
│                       └─► docker compose logs --tail=50
│                       
│                       Wait 30 seconds dan cek lagi
│                       Jika masih unhealthy: Lanjut dengan WARNING
│
├─► [TEST] Guacamole service responding?
│   │      curl -I http://localhost:8080/guacamole/
│   │
│   │      EXPECTED OUTPUT:
│   │      ┌─────────────────────────────────────┐
│   │      │ HTTP/1.1 200 OK                     │
│   │      │ Content-Type: text/html             │
│   │      │ Content-Length: ...                 │
│   │      └─────────────────────────────────────┘
│   │
│   ├─── ✓ HTTP 200 → INFO: "✓ Guacamole responding"
│   │                 Lanjut ke database check
│   │
│   ├─── HTTP 302 → INFO: "✓ Redirect OK (normal behavior)"
│   │                Lanjut ke database check
│   │
│   └─── ✗ Failed → ERROR: "Guacamole tidak responding!"
│                   
│                   [DEBUG]
│                   ├─► docker compose logs guacamole | tail -50
│                   ├─► docker exec guacamole ps aux
│                   └─► netstat -tlnp | grep 8080
│                   
│                   Common causes:
│                   ├─ Tomcat belum fully started (wait 30s more)
│                   ├─ Database connection failed
│                   └─ Memory/resource constraint
│                   
│                   Retry atau EXIT
│
├─► [TEST] Database connectivity & initialization
│   │      docker exec guacamole-mysql mysql \
│   │        -uguacamole_user -p${MYSQL_PASSWORD} \
│   │        guacamole_db -e "SHOW TABLES;"
│   │
│   │      EXPECTED OUTPUT:
│   │      ┌─────────────────────────────────────┐
│   │      │ Tables_in_guacamole_db              │
│   │      │ guacamole_connection                │
│   │      │ guacamole_user                      │
│   │      │ guacamole_user_password_history     │
│   │      │ ... (20+ tables)                    │
│   │      └─────────────────────────────────────┘
│   │
│   ├─── ✓ Shows tables → INFO: "✓ Database initialized successfully"
│   │                     INFO: "  Tables found: $(count)"
│   │                     Lanjut ke user check
│   │
│   └─── ✗ Empty/Error → ERROR: "Database tidak terinisialisasi!"
│                        
│                        [FIX ATTEMPT]
│                        INFO: "Mencoba reinit database..."
│                        
│                        ├─► docker compose down
│                        ├─► rm -rf mysql/*
│                        ├─► Verify init files: ls -la init/*.sql
│                        ├─► docker compose up -d
│                        ├─► sleep 30
│                        └─► Retry database check
│                        
│                        If still failed: EXIT
│
├─► [TEST] Default admin user exists?
│   │      docker exec guacamole-mysql mysql \
│   │        -uguacamole_user -p${MYSQL_PASSWORD} \
│   │        guacamole_db \
│   │        -e "SELECT username FROM guacamole_entity WHERE name='guacadmin';"
│   │
│   │      EXPECTED OUTPUT:
│   │      ┌─────────────────────────────────────┐
│   │      │ username                            │
│   │      │ guacadmin                           │
│   │      └─────────────────────────────────────┘
│   │
│   ├─── ✓ Found → INFO: "✓ Default admin user ready"
│   │              INFO: "  Username: guacadmin"
│   │              INFO: "  Password: guacadmin (CHANGE THIS!)"
│   │              Lanjut ke access test
│   │
│   └─── ✗ Not found → WARNING: "Admin user tidak ditemukan!"
│                       ERROR: "Init script 002-create-admin-user.sql mungkin gagal"
│                       
│                       MANUAL FIX:
│                       ┌─────────────────────────────────────────┐
│                       │ docker exec -it guacamole-mysql mysql \ │
│                       │   -uroot -p${MYSQL_ROOT_PASSWORD}       │
│                       │                                         │
│                       │ USE guacamole_db;                       │
│                       │ -- Check if admin exists                │
│                       │ SELECT * FROM guacamole_entity;         │
│                       │                                         │
│                       │ -- If empty, reinit database            │
│                       └─────────────────────────────────────────┘
│                       
│                       EXIT
│
├─► [TEST] External access test (conditional)
│   │
│   ├─── [CONDITIONAL] ACCESS_METHOD="port"
│   │    │
│   │    ├─► [INFO] "Testing akses via port..."
│   │    │   
│   │    │   [EXECUTE]
│   │    │   curl -I http://${PUBLIC_IP}:8080/guacamole/
│   │    │   
│   │    │   ├─── ✓ HTTP 200/302 → INFO: "✓ Port 8080 accessible"
│   │    │   │                      INFO: "  Akses: http://${PUBLIC_IP}:8080/guacamole"
│   │    │   │
│   │    │   └─── ✗ Timeout/Failed → WARNING: "Port tidak accessible dari luar"
│   │    │                           INFO: "Possible causes:"
│   │    │                           ├─ GCP Firewall belum dibuka
│   │    │                           ├─ UFW belum allow 8080
│   │    │                           └─ Network issue
│   │    │                           
│   │    │                           [INSTRUCTIONS]
│   │    │                           ┌─────────────────────────────────┐
│   │    │                           │ Fix sekarang atau nanti:        │
│   │    │                           │                                 │
│   │    │                           │ 1. GCP Console → Firewall       │
│   │    │                           │    Allow tcp:8080               │
│   │    │                           │                                 │
│   │    │                           │ 2. UFW:                         │
│   │    │                           │    ufw allow 8080/tcp           │
│   │    │                           │                                 │
│   │    │                           │ Akan disetup di FASE 15-18      │
│   │    │                           └─────────────────────────────────┘
│   │    │                           
│   │    │                           Lanjut ke summary
│   │    
│   └─── [CONDITIONAL] ACCESS_METHOD="cloudflare-tunnel"
│        │
│        └─► INFO: "Port 8080 tidak exposed (internal only)"
│            INFO: "External access via Cloudflare Tunnel di FASE 17"
│            Lanjut ke summary
│
├─► [CHECK] Resource usage
│   │       free -h && docker stats --no-stream
│   │
│   │       OUTPUT:
│   │       ┌─────────────────────────────────────────────────┐
│   │       │ Memory Usage:                                   │
│   │       │   Total: 1.0G                                   │
│   │       │   Used:  650M (65%)                             │
│   │       │   Free:  350M                                   │
│   │       │   Swap:  2.0G (200M used)                       │
│   │       │                                                 │
│   │       │ Container Stats:                                │
│   │       │   guacd:    120M / 256M (47%)                   │
│   │       │   mysql:    280M / 384M (73%)                   │
│   │       │   guacamole: 320M / 384M (83%)                  │
│   │       └─────────────────────────────────────────────────┘
│   │
│   ├─── Memory < 90% → INFO: "✓ Resource usage normal"
│   │
│   └─── Memory > 90% → WARNING: "Memory usage tinggi!"
│                       INFO: "Monitor dengan: docker stats"
│                       INFO: "Optimize jika perlu (kurangi limit)"
│
└─► [SUMMARY] Installation Status

    ════════════════════════════════════════════════════════════════════
                        ✅ FASE 14 COMPLETE
    ════════════════════════════════════════════════════════════════════
    
    📦 CONTAINER STATUS:
    ├─ guacd:           ✓ Running
    ├─ guacamole-mysql: ✓ Running
    └─ guacamole:       ✓ Running
    
    🗄️ DATABASE STATUS:
    ├─ Connection:      ✓ OK
    ├─ Tables:          ✓ Initialized (${table_count} tables)
    └─ Admin user:      ✓ Created (guacadmin)
    
    🌐 SERVICE STATUS:
    ├─ Internal:        ✓ http://localhost:8080/guacamole
    └─ External:        ${external_status}
    
    💾 RESOURCE USAGE:
    ├─ Memory:          ${memory_usage}
    ├─ Swap:            ${swap_usage}
    └─ CPU:             ${cpu_usage}
    
    ⚠️  IMPORTANT NOTES:
    ├─ Default credentials: guacadmin / guacadmin
    ├─ MUST change password after first login!
    ├─ Database password: Check ~/.guacamole/.env
    └─ Nginx & SSL setup: FASE 15-17
    
    📁 IMPORTANT FILES:
    ├─ Config:      ~/guacamole/docker-compose.yml
    ├─ Credentials: ~/guacamole/.env (chmod 600)
    ├─ Data:        ~/guacamole/mysql/
    └─ Logs:        docker compose logs -f
    
    🔧 QUICK COMMANDS:
    ├─ View logs:    docker compose logs -f
    ├─ Restart:      docker compose restart
    ├─ Stop:         docker compose down
    ├─ Start:        docker compose up -d
    └─ Stats:        docker stats
    
    ════════════════════════════════════════════════════════════════════
    
    ✅ Guacamole core installation SUCCESSFUL!
    
    NEXT: FASE 15 - Setup Nginx Reverse Proxy & SSL
    
    ════════════════════════════════════════════════════════════════════


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔍 TROUBLESHOOTING REFERENCE - FASE 14                                 │
└─────────────────────────────────────────────────────────────────────────┘

PROBLEM 1: Container exits immediately
├─► Symptom: docker ps shows nothing or exited status
├─► Diagnosis:
│   ├─ docker compose logs
│   └─ docker compose ps -a
└─► Solutions:
    ├─ Check .env passwords (no special chars that break)
    ├─ Verify init SQL files exist in init/
    ├─ Check disk space: df -h
    └─ Restart: docker compose down && docker compose up -d

PROBLEM 2: MySQL fails to start
├─► Symptom: guacamole-mysql container keeps restarting
├─► Diagnosis:
│   ├─ docker compose logs mysql
│   └─ Check: "Can't start server" or "Cannot allocate memory"
└─► Solutions:
    ├─ Check swap is active: free -h
    ├─ Reduce MySQL memory limit in docker-compose.yml
    ├─ Clean old data: rm -rf mysql/* (WARNING: deletes data)
    └─ Verify innodb-buffer-pool-size setting

PROBLEM 3: Guacamole can't connect to database
├─► Symptom: "Connection refused" in guacamole logs
├─► Diagnosis:
│   ├─ docker compose logs guacamole | grep -i error
│   └─ docker exec guacamole ping mysql
└─► Solutions:
    ├─ Wait 30s more (MySQL still initializing)
    ├─ Check network: docker network ls
    ├─ Verify MYSQL_PASSWORD matches in .env
    └─ Restart guacamole only: docker compose restart guacamole

PROBLEM 4: Database empty (no tables)
├─► Symptom: SHOW TABLES returns empty set
├─► Diagnosis:
│   ├─ ls -la init/*.sql (files exist?)
│   └─ docker compose logs mysql | grep init
└─► Solutions:
    ├─ Verify init files downloaded correctly
    ├─ Check file permissions: chmod 644 init/*.sql
    ├─ Full reset:
    │   ├─ docker compose down
    │   ├─ rm -rf mysql/*
    │   ├─ Re-download init files (FASE 12)
    │   └─ docker compose up -d
    └─ Manual init if needed (run SQL manually)

PROBLEM 5: Port 8080 not accessible
├─► Symptom: curl fails, browser can't connect
├─► Diagnosis:
│   ├─ netstat -tlnp | grep 8080
│   ├─ docker port guacamole
│   └─ curl -I http://localhost:8080/guacamole
└─► Solutions:
    ├─ UFW: sudo ufw allow 8080/tcp
    ├─ GCP Firewall: Add rule for tcp:8080
    ├─ Check Docker port mapping in compose file
    └─ Verify container is actually listening

PROBLEM 6: High memory usage / OOM
├─► Symptom: Containers killed, system slow, swap maxed
├─► Diagnosis:
│   ├─ free -h
│   ├─ docker stats
│   └─ dmesg | grep -i kill
└─► Solutions:
    ├─ Reduce memory limits in docker-compose.yml
    ├─ Increase swap size to 4GB
    ├─ Restart containers one by one
    ├─ Upgrade to higher tier VM (2GB+ RAM)
    └─ Monitor with: watch -n 1 free -h

PROBLEM 7: Guacadmin user not found
├─► Symptom: Can't login with default credentials
├─► Diagnosis:
│   ├─ Check user in DB:
│   │   docker exec guacamole-mysql mysql -uroot -p${ROOT_PASS} \
│   │     guacamole_db -e "SELECT * FROM guacamole_entity;"
│   └─ Check init logs: docker compose logs mysql | grep 002
└─► Solutions:
    ├─ Verify 002-create-admin-user.sql was executed
    ├─ Manually create user:
    │   ├─ Get into MySQL: docker exec -it guacamole-mysql mysql -uroot -p
    │   ├─ SOURCE /docker-entrypoint-initdb.d/002-create-admin-user.sql;
    │   └─ FLUSH PRIVILEGES;
    ├─ Or full reinit database
    └─ Check password hasn't been changed already

PROBLEM 8: Slow performance
├─► Symptom: Web UI sluggish, connections timeout
├─► Diagnosis:
│   ├─ docker stats (check CPU/MEM)
│   ├─ htop (system load)
│   └─ vmstat 1 (swap activity)
└─► Solutions:
    ├─ Reduce concurrent connections
    ├─ Lower recording quality/resolution
    ├─ Disable unnecessary services
    ├─ Optimize MySQL queries
    └─ Consider VM upgrade

EMERGENCY FULL RESET:
┌─────────────────────────────────────────────────┐
│ cd ~/guacamole                                  │
│ docker compose down -v                          │
│ rm -rf mysql/* postgres/*                       │
│ docker compose up -d                            │
│ sleep 30                                        │
│ docker compose logs -f                          │
└─────────────────────────────────────────────────┘

LOG LOCATIONS:
├─ Container logs: docker compose logs [service]
├─ Docker daemon: /var/log/docker.log
├─ System: journalctl -u docker
└─ Nginx (later): /var/log/nginx/guacamole-*.log


┌─────────────────────────────────────────────────────────────────────────┐
│ 🌐 FASE 15: SETUP NGINX REVERSE PROXY                                  │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CHECK] Apakah ACCESS_METHOD="cloudflare-tunnel"?
│   │
│   ├─── ✓ YES → INFO: "Nginx tidak diperlukan (Cloudflare handles SSL)"
│   │            Lanjut ke FASE 17
│   │
│   └─── ✗ NO (port) → INFO: "Menginstall Nginx..."
│                      
│                      [EXECUTE]
│                      ├─► apt install -y nginx
│                      ├─► systemctl start nginx
│                      ├─► systemctl enable nginx
│                      └─► nginx -v
│                      
│                      [VERIFY]
│                      ├─── ✓ Installed → INFO: "✓ Nginx terinstal"
│                      │                 Lanjut ke SSL setup
│                      └─── ✗ Failed   → ERROR: "Gagal install Nginx!"
│                                        EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔐 FASE 16: GENERATE SSL CERTIFICATE                                   │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CONDITIONAL] Berdasarkan SSL_METHOD:
│   │
│   ├─► SSL_METHOD="selfsigned"
│   │   │
│   │   ├─► [INFO] "Membuat self-signed certificate..."
│   │   │   
│   │   │   [EXECUTE]
│   │   │   ├─► mkdir -p /etc/nginx/ssl
│   │   │   ├─► openssl req -x509 -nodes -days 365 \
│   │   │   │   -newkey rsa:2048 \
│   │   │   │   -keyout /etc/nginx/ssl/guacamole.key \
│   │   │   │   -out /etc/nginx/ssl/guacamole.crt \
│   │   │   │   -subj "/C=ID/ST=Jakarta/L=Jakarta/O=IT/CN=${IP_OR_DOMAIN}"
│   │   │   └─► openssl dhparam -out /etc/nginx/ssl/dhparam.pem 2048
│   │   │   
│   │   │   [VERIFY]
│   │   │   ├─── ✓ Files created → INFO: "✓ Self-signed SSL ready"
│   │   │   │                      Lanjut ke Nginx config
│   │   │   └─── ✗ Failed → ERROR: "Gagal generate SSL!"
│   │   │                    EXIT
│   │   
│   ├─► SSL_METHOD="letsencrypt"
│   │   │
│   │   ├─► [INFO] "Menginstall Certbot untuk Let's Encrypt..."
│   │   │   
│   │   │   [EXECUTE]
│   │   │   ├─► apt install -y certbot python3-certbot-nginx
│   │   │   ├─► certbot --nginx -d ${DOMAIN} --non-interactive \
│   │   │   │   --agree-tos --email admin@${DOMAIN} --redirect
│   │   │   └─► certbot renew --dry-run
│   │   │   
│   │   │   [VERIFY]
│   │   │   ├─── ✓ Certificate issued → INFO: "✓ Let's Encrypt configured"
│   │   │   │                           INFO: "  Auto-renewal enabled"
│   │   │   │                           Lanjut ke Nginx config
│   │   │   └─── ✗ Failed → ERROR: "Gagal generate Let's Encrypt!"
│   │   │                    Possible causes:
│   │   │                    ├─ Domain tidak pointing ke server
│   │   │                    ├─ Port 80 tidak accessible
│   │   │                    └─ Rate limit reached
│   │   │                    EXIT
│   │   
│   └─► SSL_METHOD="cloudflare"
│       │
│       └─► INFO: "SSL dihandle Cloudflare, skip certificate generation"
│           Lanjut ke Nginx config


┌─────────────────────────────────────────────────────────────────────────┐
│ 📝 FASE 17: KONFIGURASI NGINX                                          │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CONDITIONAL] Jika ACCESS_METHOD="port":
│   │
│   ├─► [INFO] "Membuat Nginx reverse proxy config..."
│   │   
│   │   [CREATE FILE] /etc/nginx/sites-available/guacamole
│   │   
│   │   KONTEN (CONDITIONAL SSL_METHOD):
│   │   ┌─────────────────────────────────────────────────┐
│   │   │ # HTTP to HTTPS redirect                        │
│   │   │ server {                                        │
│   │   │     listen 80;                                  │
│   │   │     server_name ${IP_OR_DOMAIN};                │
│   │   │     return 301 https://$server_name$request_uri;│
│   │   │ }                                               │
│   │   │                                                 │
│   │   │ # HTTPS Server                                  │
│   │   │ server {                                        │
│   │   │     listen 443 ssl http2;                       │
│   │   │     server_name ${IP_OR_DOMAIN};                │
│   │   │                                                 │
│   │   │     # SSL Config (conditional)                  │
│   │   │     ssl_certificate /etc/nginx/ssl/...;         │
│   │   │     ssl_certificate_key /etc/nginx/ssl/...;     │
│   │   │     ssl_protocols TLSv1.2 TLSv1.3;              │
│   │   │                                                 │
│   │   │     # Security Headers                          │
│   │   │     add_header X-Frame-Options "SAMEORIGIN";    │
│   │   │     add_header X-Content-Type-Options "nosniff";│
│   │   │     add_header Strict-Transport-Security        │
│   │   │       "max-age=31536000";                       │
│   │   │                                                 │
│   │   │     # Proxy to Guacamole                        │
│   │   │     location / {                                │
│   │   │         proxy_pass http://localhost:8080/...;   │
│   │   │         proxy_buffering off;                    │
│   │   │         proxy_http_version 1.1;                 │
│   │   │         proxy_set_header Upgrade $http_upgrade; │
│   │   │         proxy_set_header Connection $...;       │
│   │   │         proxy_set_header X-Real-IP $remote_addr;│
│   │   │         proxy_set_header X-Forwarded-For $...;  │
│   │   │     }                                           │
│   │   │                                                 │
│   │   │     # WebSocket support                         │
│   │   │     location /guacamole/websocket-tunnel {      │
│   │   │         proxy_pass http://localhost:8080/...;   │
│   │   │         proxy_http_version 1.1;                 │
│   │   │         proxy_set_header Upgrade $http_upgrade; │
│   │   │         proxy_set_header Connection "upgrade";  │
│   │   │         proxy_connect_timeout 7d;               │
│   │   │         proxy_read_timeout 7d;                  │
│   │   │     }                                           │
│   │   │ }                                               │
│   │   └─────────────────────────────────────────────────┘
│   │   
│   │   [EXECUTE]
│   │   ├─► rm /etc/nginx/sites-enabled/default
│   │   ├─► ln -s /etc/nginx/sites-available/guacamole \
│   │   │        /etc/nginx/sites-enabled/
│   │   ├─► nginx -t
│   │   └─► systemctl reload nginx
│   │   
│   │   [VERIFY]
│   │   ├─── ✓ syntax ok → INFO: "✓ Nginx configured"
│   │   │                 Lanjut ke FASE 18
│   │   └─── ✗ Failed → ERROR: "Nginx config error!"
│   │                    cat /var/log/nginx/error.log
│   │                    EXIT
│   
└─► [CONDITIONAL] Jika ACCESS_METHOD="cloudflare-tunnel":
    │
    └─► [INFO] "Menginstall Cloudflared..."
        
        [EXECUTE]
        ├─► wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
        ├─► dpkg -i cloudflared-linux-amd64.deb
        ├─► mkdir -p ~/.cloudflared
        ├─► cp ~/cloudflared/credentials.json ~/.cloudflared/${TUNNEL_ID}.json
        └─► cat > ~/.cloudflared/config.yml << EOF
            tunnel: ${TUNNEL_ID}
            credentials-file: ~/.cloudflared/${TUNNEL_ID}.json
            ingress:
              - hostname: ${DOMAIN}
                service: http://localhost:8080
              - service: http_status:404
            EOF
        
        [SERVICE SETUP]
        ├─► cloudflared service install
        ├─► systemctl start cloudflared
        ├─► systemctl enable cloudflared
        └─► systemctl status cloudflared
        
        [VERIFY]
        ├─── ✓ Running → INFO: "✓ Cloudflare Tunnel aktif"
        │                INFO: "  Akses via: https://${DOMAIN}"
        │                Lanjut ke FASE 18
        └─── ✗ Failed → ERROR: "Cloudflared gagal start!"
                         journalctl -u cloudflared -n 50
                         EXIT


┌─────────────────────────────────────────────────────────────────────────┐
│ 🔥 FASE 18: KONFIGURASI FIREWALL                                       │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [CONDITIONAL] Berdasarkan ACCESS_METHOD & SSH_METHOD:
│   │
│   ├─► ACCESS_METHOD="port"
│   │   │
│   │   ├─► [INFO] "Membuka port publik..."
│   │   │   
│   │   │   [EXECUTE] UFW Rules
│   │   │   ├─► ufw allow from ${SSH_SOURCE} to any port 22 proto tcp
│   │   │   ├─► ufw allow 80/tcp
│   │   │   ├─► ufw allow 443/tcp
│   │   │   ├─► ufw --force enable
│   │   │   └─► ufw status numbered
│   │   │   
│   │   │   [INFO] "Membuka GCP Firewall..."
│   │   │   
│   │   │   TAMPILAN:
│   │   │   ┌─────────────────────────────────────────────┐
│   │   │   │ Buka GCP Console:                           │
│   │   │   │ VPC Network → Firewall → Create Rule        │
│   │   │   │                                             │
│   │   │   │ Name: allow-guacamole-https                 │
│   │   │   │ Targets: All instances                      │
│   │   │   │ Source IP: 0.0.0.0/0                        │
│   │   │   │ Protocols: tcp:80,443                       │
│   │   │   │                                             │
│   │   │   │ Press Enter setelah selesai...              │
│   │   │   └─────────────────────────────────────────────┘
│   │   │   
│   │   │   USER INPUT: [Enter]
│   │   │   
│   │   │   [VERIFY]
│   │   │   ├─► curl -I http://localhost
│   │   │   └─► curl -kI https://localhost
│   │   │   
│   │   │   ├─── ✓ OK → INFO: "✓ Firewall configured"
│   │   │   │          Lanjut ke FASE 19
│   │   │   └─── ✗ Failed → WARNING: "Cek manual GCP firewall"
│   │   │                    Lanjut ke FASE 19
│   │   
│   └─► ACCESS_METHOD="cloudflare-tunnel"
│       │
│       └─► [INFO] "Menutup semua port publik..."
│           
│           [EXECUTE] UFW Rules (Restrictive)
│           ├─► ufw --force reset
│           ├─► ufw default deny incoming
│           ├─► ufw default allow outgoing
│           ├─► ufw allow from 35.235.240.0/20 to any port 22 proto tcp
│           ├─► ufw --force enable
│           └─► ufw status
│           
│           OUTPUT:
│           ┌─────────────────────────────────────┐
│           │ Status: active                      │
│           │                                     │
│           │ To          From                    │
│           │ 22/tcp      35.235.240.0/20         │
│           └─────────────────────────────────────┘
│           
│           INFO: "✓ Zero Trust mode - hanya IAP SSH allowed"
│           INFO: "  Public ports: NONE"
│           INFO: "  Akses Guacamole: Via Cloudflare only"
│           Lanjut ke FASE 19


┌─────────────────────────────────────────────────────────────────────────┐
│ 🧪 FASE 19: TESTING & VERIFIKASI                                       │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [TEST 1] Container Health Check
│   │
│   ├─► docker ps
│   ├─► docker compose logs guacamole | tail -20
│   └─► curl -I http://localhost:8080/guacamole/
│   
│   [VERIFY]
│   ├─── ✓ HTTP 200 → INFO: "✓ Guacamole responding"
│   └─── ✗ Error   → ERROR: "Guacamole not ready!"
│                    docker compose logs guacamole
│                    Troubleshoot FASE 14
│
├─► [TEST 2] Database Connectivity
│   │
│   ├─► docker exec guacamole-mysql mysql -uguacamole_user \
│   │   -p${MYSQL_PASSWORD} guacamole_db -e "SHOW TABLES;"
│   │
│   [VERIFY]
│   ├─── ✓ Shows tables → INFO: "✓ Database initialized"
│   └─── ✗ Failed → ERROR: "Database connection failed!"
│                    Cek password di .env
│
├─► [TEST 3] External Access
│   │
│   ├─► [CONDITIONAL] ACCESS_METHOD="port"
│   │   │
│   │   ├─► curl -kI https://${IP_OR_DOMAIN}/
│   │   │
│   │   └─── [VERIFY]
│   │        ├─── ✓ HTTP 200/302 → INFO: "✓ External access OK"
│   │        └─── ✗ Failed → ERROR: "Firewall atau Nginx issue!"
│   │                         Cek GCP firewall
│   │
│   └─► [CONDITIONAL] ACCESS_METHOD="cloudflare-tunnel"
│       │
│       ├─► curl -I https://${DOMAIN}/
│       │
│       └─── [VERIFY]
│            ├─── ✓ HTTP 200 → INFO: "✓ Cloudflare Tunnel working"
│            └─── ✗ Failed → ERROR: "Tunnel not connected!"
│                             systemctl status cloudflared
│
└─► [TEST 4] Login Test
    
    TAMPILAN:
    ┌─────────────────────────────────────────────────┐
    │ Buka browser dan akses:                         │
    │                                                 │
    │ URL: https://${ACCESS_URL}/                     │
    │                                                 │
    │ Default credentials:                            │
    │   Username: guacadmin                           │
    │   Password: guacadmin                           │
    │                                                 │
    │ Apakah login berhasil? [Y/n]:                   │
    └─────────────────────────────────────────────────┘
    
    USER INPUT:
    ├─► [Y] → INFO: "✓ Installation SUCCESSFUL!"
    │         Lanjut ke FASE 20
    │
    └─► [n] → ERROR: "Login failed!"
              Possible issues:
              ├─ Database tidak terinisialisasi
              ├─ Wrong password di .env
              └─ Init SQL tidak tereksekusi
              
              [FIX ATTEMPT]
              ├─► cd ~/guacamole
              ├─► docker compose down
              ├─► rm -rf mysql/*
              ├─► docker compose up -d
              └─► Tunggu 30 detik, coba login lagi


┌─────────────────────────────────────────────────────────────────────────┐
│ 🎉 FASE 20: POST-INSTALLATION & INFO AKHIR                             │
└─────────────────────────────────────────────────────────────────────────┘
│
├─► [DISPLAY] Installation Summary
│   
│   ════════════════════════════════════════════════════════════════════
│                   ✅ GUACAMOLE INSTALLATION COMPLETE!
│   ════════════════════════════════════════════════════════════════════
│   
│   📊 SYSTEM INFO:
│   ├─ OS: Ubuntu $(lsb_release -rs)
│   ├─ RAM: $(free -h | awk '/^Mem:/ {print $2}')
│   ├─ Swap: $(free -h | awk '/^Swap:/ {print $2}')
│   ├─ Docker: $(docker --version | cut -d' ' -f3)
│   └─ Compose: $(docker compose version | cut -d' ' -f4)
│   
│   🌐 ACCESS INFORMATION:
│   ├─ Method: ${ACCESS_METHOD}
│   ├─ URL: https://${ACCESS_URL}/
│   ├─ SSL: ${SSL_METHOD}
│   └─ Database: ${DB_TYPE}
│   
│   🔐 DEFAULT CREDENTIALS (CHANGE IMMEDIATELY!):
│   ├─ Username: guacadmin
│   └─ Password: guacadmin
│   
│   🔑 DATABASE CREDENTIALS:
│   ├─ Host: localhost (internal only)
│   ├─ Database: guacamole_db
│   ├─ User: guacamole_user
│   └─ Password: (stored in ~/.guacamole/.env)
│   
│   🛡️ FIREWALL STATUS:
│   ├─ SSH: ${SSH_SOURCE}
│   ├─ HTTP: $(ufw status | grep 80)
│   └─ HTTPS: $(ufw status | grep 443)
│   
│   📁 IMPORTANT PATHS:
│   ├─ Config: ~/guacamole/docker-compose.yml
│   ├─ Data: ~/guacamole/mysql/
│   ├─ Records: ~/guacamole/record/
│   ├─ Nginx: /etc/nginx/sites-available/guacamole
│   └─ Logs: /var/log/nginx/guacamole-*.log
│   
│   ════════════════════════════════════════════════════════════════════
│
├─► [SECURITY REMINDERS]
│   
│   ⚠️  CRITICAL - DO THESE NOW:
│   ┌─────────────────────────────────────────────────┐
│   │ 1. Change default password:                     │
│   │    Login → Settings → guacadmin → Password      │
│   │                                                 │
│   │ 2. Create new admin user:                       │
│   │    Settings → Users → New User                  │
│   │    Give admin permissions                       │
│   │                                                 │
│   │ 3. Disable/Delete guacadmin (optional):         │
│   │    After creating new admin                     │
│   │                                                 │
│   │ 4. Setup MFA (if available):                    │
│   │    Settings → Preferences → TOTP                │
│   └─────────────────────────────────────────────────┘
│
├─► [USEFUL COMMANDS]
│   
│   📝 Management Commands:
│   ┌─────────────────────────────────────────────────┐
│   │ # View logs                                     │
│   │ cd ~/guacamole && docker compose logs -f        │
│   │                                                 │
│   │ # Restart services                              │
│   │ docker compose restart                          │
│   │                                                 │
│   │ # Stop/Start                                    │
│   │ docker compose down                             │
│   │ docker compose up -d                            │
│   │                                                 │
│   │ # Database backup                               │
│   │ docker exec guacamole-mysql mysqldump \         │
│   │   -uroot -p${MYSQL_ROOT_PASSWORD} \             │
│   │   guacamole_db > backup.sql                     │
│   │                                                 │
│   │ # Check resource usage                          │
│   │ docker stats                                    │
│   │ htop                                            │
│   │                                                 │
│   │ # Nginx reload                                  │
│   │ systemctl reload nginx                          │
│   └─────────────────────────────────────────────────┘
│
├─► [MONITORING SETUP]
│   
│   📊 Recommended monitoring:
│   ┌─────────────────────────────────────────────────┐
│   │ # Install monitoring tools                      │
│   │ apt install -y htop iotop nethogs               │
│   │                                                 │
│   │ # Setup log rotation                            │
│   │ cat > /etc/logrotate.d/guacamole << 'EOF'       │
│   │ /var/log/nginx/guacamole-*.log {                │
│   │     daily                                       │
│   │     rotate 7                                    │
│   │     compress                                    │
│   │     delaycompress                               │
│   │     notifempty                                  │
│   │     create 640 www-data adm                     │
│   │ }                                               │
│   │ EOF                                             │
│   └─────────────────────────────────────────────────┘
│
├─► [BACKUP RECOMMENDATIONS]
│   
│   💾 What to backup:
│   ├─ Database: ~/guacamole/mysql/
│   ├─ Config: ~/guacamole/docker-compose.yml
│   ├─ Env: ~/guacamole/.env
│   ├─ Recordings: ~/guacamole/record/
│   └─ Nginx config: /etc/nginx/sites-available/guacamole
│   
│   Backup command:
│   tar -czf guacamole-backup-$(date +%Y%m%d).tar.gz \
│     ~/guacamole /etc/nginx/sites-available/guacamole
│
└─► [NEXT STEPS]
    
    🎯 Recommended next actions:
    ┌─────────────────────────────────────────────────┐
    │ 1. Add RDP/SSH/VNC connections                  │
    │    Settings → Connections → New Connection      │
    │                                                 │
    │ 2. Create user groups                           │
    │    Settings → Groups → New Group                │
    │                                                 │
    │ 3. Configure recording settings                 │
    │    Connection → Recording → Enable              │
    │                                                 │
    │ 4. Setup connection sharing                     │
    │    Connection → Concurrency Limits              │
    │                                                 │
    │ 5. Test session recording                       │
    │    Files saved to: ~/guacamole/record/          │
    │                                                 │
    │ 6. Monitor resource usage for 24h               │
    │    Watch for memory/swap usage                  │
    │                                                 │
    │ 7. Plan backup strategy                         │
    │    Daily/weekly automated backups               │
    └─────────────────────────────────────────────────┘

════════════════════════════════════════════════════════════════════════
                            🎊 INSTALLATION COMPLETE! 🎊
════════════════════════════════════════════════════════════════════════

Access your Guacamole instance:
👉 https://${ACCESS_URL}/

Need help? Check logs:
📝 docker compose -f ~/guacamole/docker-compose.yml logs -f

Thank you for using this installer! 🚀
════════════════════════════════════════════════════════════════════════
```
