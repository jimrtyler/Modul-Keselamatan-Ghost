# 👻 Modul Keselamatan Ghost
**Alat Pengukuhan Keselamatan Windows dan Azure Berasaskan PowerShell**

> **Pengukuhan keselamatan proaktif untuk titik akhir Windows dan persekitaran Azure.** Ghost menyediakan fungsi pengukuhan berasaskan PowerShell yang boleh membantu mengurangkan vektor serangan biasa dengan melumpuhkan perkhidmatan dan protokol yang tidak diperlukan.

## ⚠️ Penafian Penting

**UJIAN DIPERLUKAN**: Sentiasa uji Ghost dalam persekitaran bukan pengeluaran terlebih dahulu. Melumpuhkan perkhidmatan mungkin memberi kesan kepada fungsi perniagaan yang sah.

**TIADA JAMINAN**: Walaupun Ghost menyasarkan vektor serangan biasa, tiada alat keselamatan boleh mencegah semua serangan. Ini adalah satu komponen dalam strategi keselamatan yang komprehensif.

**KESAN OPERASI**: Sesetengah fungsi mungkin menjejaskan kefungsian sistem. Semak setiap tetapan dengan teliti sebelum penyebaran.

**PENILAIAN PROFESIONAL**: Untuk persekitaran pengeluaran, berunding dengan pakar keselamatan untuk memastikan tetapan sejajar dengan keperluan organisasi anda.

## 📊 Landskap Keselamatan

Kerosakan ransomware mencecah **$57 bilion pada 2025**, dengan penyelidikan menunjukkan bahawa banyak serangan berjaya mengeksploitasi perkhidmatan Windows asas dan salah konfigurasi. Vektor serangan biasa termasuk:

- **90% daripada insiden ransomware** melibatkan eksploitasi RDP
- **Kelemahan SMBv1** membolehkan serangan seperti WannaCry dan NotPetya
- **Makro dokumen** kekal sebagai kaedah penyampaian malware utama
- **Serangan berasaskan USB** terus menyasarkan rangkaian jurang udara
- **Penyalahgunaan PowerShell** telah meningkat dengan ketara dalam tahun-tahun kebelakangan ini

## 🛡️ Fungsi Keselamatan Ghost

Ghost menyediakan **16 fungsi pengukuhan Windows** tambah **integrasi keselamatan Azure**:

### Pengukuhan Titik Akhir Windows

| Fungsi | Tujuan | Pertimbangan |
|----------|---------|----------------|
| `Set-RDP` | Mengurus akses Remote Desktop | Mungkin menjejaskan pentadbiran jarak jauh |
| `Set-SMBv1` | Mengawal protokol SMB lama | Diperlukan untuk sistem lama |
| `Set-AutoRun` | Mengawal AutoPlay/AutoRun | Mungkin menjejaskan kemudahan pengguna |
| `Set-USBStorage` | Mengehadkan peranti storan USB | Mungkin menjejaskan penggunaan USB yang sah |
| `Set-Macros` | Mengawal pelaksanaan makro Office | Mungkin menjejaskan dokumen yang diaktifkan makro |
| `Set-PSRemoting` | Mengurus PowerShell remoting | Mungkin menjejaskan pengurusan jarak jauh |
| `Set-WinRM` | Mengawal Windows Remote Management | Mungkin menjejaskan pentadbiran jarak jauh |
| `Set-LLMNR` | Mengurus protokol resolusi nama | Biasanya selamat untuk dilumpuhkan |
| `Set-NetBIOS` | Mengawal NetBIOS melalui TCP/IP | Mungkin menjejaskan aplikasi lama |
| `Set-AdminShares` | Mengurus perkongsian pentadbiran | Mungkin menjejaskan akses fail jarak jauh |
| `Set-Telemetry` | Mengawal pengumpulan data | Mungkin menjejaskan keupayaan diagnostik |
| `Set-GuestAccount` | Mengurus akaun Tetamu | Biasanya selamat untuk dilumpuhkan |
| `Set-ICMP` | Mengawal respons ping | Mungkin menjejaskan diagnostik rangkaian |
| `Set-RemoteAssistance` | Mengurus Remote Assistance | Mungkin menjejaskan operasi help desk |
| `Set-NetworkDiscovery` | Mengawal penemuan rangkaian | Mungkin menjejaskan pelayaran rangkaian |
| `Set-Firewall` | Mengurus Windows Firewall | Kritikal untuk keselamatan rangkaian |

### Keselamatan Awan Azure

| Fungsi | Tujuan | Keperluan |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Membolehkan keselamatan asas Azure AD | Kebenaran Microsoft Graph |
| `Set-AzureConditionalAccess` | Mengkonfigurasi dasar akses | Pelesenan Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Mengaudit akaun berprivilej | Kebenaran Global Admin |

### Pilihan Penyebaran Perusahaan

| Kaedah | Kes Penggunaan | Keperluan |
|--------|----------|--------------|
| **Pelaksanaan Langsung** | Ujian, persekitaran kecil | Hak pentadbir tempatan |
| **Group Policy** | Persekitaran domain | Pentadbir domain, pengurusan GP |
| **Microsoft Intune** | Peranti yang diuruskan awan | Pelesenan Intune, Graph API |

## 🚀 Permulaan Pantas

### Penilaian Keselamatan
```powershell
# Muatkan modul Ghost
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Periksa postur keselamatan semasa
Get-Ghost
```

### Pengukuhan Asas (Uji Dahulu)
```powershell
# Pengukuhan penting - uji dalam persekitaran makmal terlebih dahulu
Set-Ghost -SMBv1 -AutoRun -Macros

# Semak perubahan
Get-Ghost
```

### Penyebaran Perusahaan
```powershell
# Penyebaran Group Policy (persekitaran domain)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Penyebaran Intune (peranti yang diuruskan awan)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Kaedah Pemasangan

### Pilihan 1: Muat Turun Langsung (Ujian)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Pilihan 2: Pemasangan Modul
```powershell
# Pasang dari PowerShell Gallery (apabila tersedia)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Pilihan 3: Penyebaran Perusahaan
```powershell
# Salin ke lokasi rangkaian untuk penyebaran Group Policy
# Konfigurasikan skrip PowerShell Intune untuk penyebaran awan
```

## 💼 Contoh Kes Penggunaan

### Perniagaan Kecil
```powershell
# Perlindungan asas dengan kesan minimum
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Persekitaran Penjagaan Kesihatan
```powershell
# Pengukuhan berfokuskan HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Perkhidmatan Kewangan
```powershell
# Konfigurasi keselamatan tinggi
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organisasi Awan-Pertama
```powershell
# Penyebaran yang diuruskan Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Butiran Fungsi

### Fungsi Pengukuhan Teras

#### Perkhidmatan Rangkaian
- **RDP**: Menyekat akses desktop jarak jauh atau rawakkan port
- **SMBv1**: Melumpuhkan protokol perkongsian fail lama
- **ICMP**: Mencegah respons ping untuk reconnaissance
- **LLMNR/NetBIOS**: Menyekat protokol resolusi nama lama

#### Keselamatan Aplikasi
- **Macros**: Melumpuhkan pelaksanaan makro dalam aplikasi Office
- **AutoRun**: Mencegah pelaksanaan automatik dari media boleh tanggal

#### Pengurusan Jarak Jauh
- **PSRemoting**: Melumpuhkan sesi PowerShell jarak jauh
- **WinRM**: Menghentikan Windows Remote Management
- **Remote Assistance**: Menyekat sambungan bantuan jarak jauh

#### Kawalan Akses
- **Admin Shares**: Melumpuhkan perkongsian C$, ADMIN$
- **Guest Account**: Melumpuhkan akses akaun Tetamu
- **USB Storage**: Mengehadkan penggunaan peranti USB

### Integrasi Azure
```powershell
# Sambung ke penyewa Azure
Connect-AzureGhost -Interactive

# Dayakan lalai keselamatan
Set-AzureSecurityDefaults -Enable

# Konfigurasikan akses bersyarat
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Audit pengguna berprivilej
Set-AzurePrivilegedUsers -AuditOnly
```

### Integrasi Intune (Baharu dalam v2)
```powershell
# Sambung ke Intune
Connect-IntuneGhost -Interactive

# Sebar melalui dasar Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Pertimbangan Penting

### Keperluan Ujian
- **Persekitaran Makmal**: Uji semua tetapan dalam persekitaran terpencil terlebih dahulu
- **Penyebaran Berperingkat**: Gulung keluar secara beransur untuk mengenal pasti isu
- **Rancangan Rollback**: Pastikan anda boleh membalikkan perubahan jika diperlukan
- **Dokumentasi**: Rekodkan tetapan mana yang berfungsi untuk persekitaran anda

### Kesan Berpotensi
- **Produktiviti Pengguna**: Sesetengah tetapan mungkin menjejaskan aliran kerja harian
- **Aplikasi Lama**: Sistem lama mungkin memerlukan protokol tertentu
- **Akses Jarak Jauh**: Pertimbangkan kesan ke atas pentadbiran jarak jauh yang sah
- **Proses Perniagaan**: Sahkan tetapan tidak memecahkan fungsi kritikal

### Had Keselamatan
- **Pertahanan Mendalam**: Ghost adalah satu lapisan keselamatan, bukan penyelesaian lengkap
- **Pengurusan Berterusan**: Keselamatan memerlukan pemantauan dan kemas kini berterusan
- **Latihan Pengguna**: Kawalan teknikal mesti dipasangkan dengan kesedaran keselamatan
- **Evolusi Ancaman**: Kaedah serangan baharu mungkin memintas perlindungan semasa

## 🎯 Contoh Senario Serangan

Walaupun Ghost menyasarkan vektor serangan biasa, pencegahan khusus bergantung kepada pelaksanaan dan ujian yang betul:

### Serangan Gaya WannaCry
- **Mitigasi**: `Set-Ghost -SMBv1` melumpuhkan protokol yang terdedah
- **Pertimbangan**: Pastikan tiada sistem lama memerlukan SMBv1

### Ransomware Berasaskan RDP
- **Mitigasi**: `Set-Ghost -RDP` menyekat akses desktop jarak jauh
- **Pertimbangan**: Mungkin memerlukan kaedah akses jarak jauh alternatif

### Malware Berasaskan Dokumen
- **Mitigasi**: `Set-Ghost -Macros` melumpuhkan pelaksanaan makro
- **Pertimbangan**: Mungkin menjejaskan dokumen yang diaktifkan makro yang sah

### Ancaman Dihantar USB
- **Mitigasi**: `Set-Ghost -USBStorage -AutoRun` mengehadkan kefungsian USB
- **Pertimbangan**: Mungkin menjejaskan penggunaan peranti USB yang sah

## 🏢 Ciri Perusahaan

### Sokongan Group Policy
```powershell
# Aplikasikan tetapan melalui registry Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Tetapan digunakan di seluruh domain selepas penyegaran GP
gpupdate /force
```

### Integrasi Microsoft Intune
```powershell
# Cipta dasar Intune untuk tetapan Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Dasar disebarkan ke peranti yang diuruskan secara automatik
```

### Pelaporan Pematuhan
```powershell
# Jana laporan penilaian keselamatan
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Laporan postur keselamatan Azure
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Amalan Terbaik

### Sebelum Penyebaran
1. **Dokumentasikan Keadaan Semasa**: Jalankan `Get-Ghost` sebelum perubahan
2. **Uji Dengan Teliti**: Sahkan dalam persekitaran bukan pengeluaran
3. **Rancang Rollback**: Ketahui cara membalikkan setiap tetapan
4. **Semakan Pemegang Kepentingan**: Pastikan unit perniagaan meluluskan perubahan

### Semasa Penyebaran
1. **Pendekatan Berperingkat**: Sebar kepada kumpulan perintis terlebih dahulu
2. **Pantau Kesan**: Perhatikan aduan pengguna atau isu sistem
3. **Dokumentasikan Isu**: Rekodkan sebarang masalah untuk rujukan masa depan
4. **Komunikasikan Perubahan**: Maklumkan pengguna tentang penambahbaikan keselamatan

### Selepas Penyebaran
1. **Penilaian Berkala**: Secara berkala jalankan `Get-Ghost` untuk mengesahkan tetapan
2. **Kemas Kini Dokumentasi**: Kekalkan konfigurasi keselamatan terkini
3. **Semak Keberkesanan**: Pantau untuk insiden keselamatan
4. **Penambahbaikan Berterusan**: Laraskan tetapan berdasarkan landskap ancaman

## 🔧 Penyelesaian Masalah

### Isu Biasa
- **Ralat Kebenaran**: Pastikan sesi PowerShell ditinggikan
- **Kebergantungan Perkhidmatan**: Sesetengah perkhidmatan mungkin mempunyai kebergantungan
- **Keserasian Aplikasi**: Uji dengan aplikasi perniagaan
- **Ketersambungan Rangkaian**: Sahkan akses jarak jauh masih berfungsi

### Pilihan Pemulihan
```powershell
# Aktifkan semula perkhidmatan khusus jika diperlukan
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Tentang Pengarang

**Jim Tyler** - Microsoft MVP untuk PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ pelanggan)
- **Surat Berita**: [PowerShell.News](https://powershell.news) - Perisikan keselamatan mingguan
- **Pengarang**: "PowerShell for Systems Engineers"
- **Pengalaman**: Dekad automasi PowerShell dan keselamatan Windows

## 📄 Lesen & Penafian

### Lesen MIT
Ghost disediakan di bawah Lesen MIT untuk penggunaan, pengubahsuaian dan pengedaran percuma.

### Penafian Keselamatan
- **Tiada Jaminan**: Ghost disediakan "sebagaimana adanya" tanpa jaminan apa-apa jenis
- **Ujian Diperlukan**: Sentiasa uji dalam persekitaran bukan pengeluaran terlebih dahulu
- **Panduan Profesional**: Berunding dengan pakar keselamatan untuk penyebaran pengeluaran
- **Kesan Operasi**: Pengarang tidak bertanggungjawab untuk sebarang gangguan operasi
- **Keselamatan Komprehensif**: Ghost adalah satu komponen strategi keselamatan lengkap

### Sokongan
- **GitHub Issues**: [Laporkan pepijat atau minta ciri](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentasi**: Gunakan `Get-Help <function> -Full` untuk bantuan terperinci
- **Komuniti**: Forum komuniti PowerShell dan keselamatan

---

**🔒 Kukuhkan postur keselamatan anda dengan Ghost - tetapi sentiasa uji dahulu.**

```powershell
# Mulakan dengan penilaian, bukan andaian
Get-Ghost
```

**⭐ Beri bintang kepada repositori ini jika Ghost membantu meningkatkan postur keselamatan anda!**