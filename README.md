<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0ea5e9,50:6366f1,100:8b5cf6&height=220&section=header&text=sang.ceo&fontSize=76&fontColor=ffffff&animation=fadeIn&fontAlignY=36&desc=registry%20terbuka%20untuk%20subdomain%20dan%20email%20gratis&descAlignY=60&descSize=19" width="100%" alt="sang.ceo registry" />

<a href="https://sang.ceo">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=2600&pause=900&color=0EA5E9&center=true&vCenter=true&repeat=true&width=760&height=48&lines=Satu+subdomain%2C+satu+berkas%2C+satu+pull+request.;Klaim+dari+situs%2C+merge+otomatis.;DNS+dan+mailbox+langsung+jadi." alt="sang.ceo" />
</a>

<br/>

[![Buka situs](https://img.shields.io/badge/sang.ceo-buka_situs-0ea5e9?style=for-the-badge&logo=googlechrome&logoColor=white)](https://sang.ceo)
[![Klaim subdomain](https://img.shields.io/badge/klaim_subdomain-8b5cf6?style=for-the-badge&logo=rocket&logoColor=white)](https://sang.ceo/daftar)
[![Klaim email](https://img.shields.io/badge/klaim_email-6366f1?style=for-the-badge&logo=maildotru&logoColor=white)](https://sang.ceo/email)

<br/>

![subdomain](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2FNauvalunesa%2FSangceo%2Fcontents%2Fdata%2Fdomains&query=%24.length&label=subdomain&color=0ea5e9&style=flat-square)
![mailbox](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2FNauvalunesa%2FSangceo%2Fcontents%2Fdata%2Femails&query=%24.length&label=mailbox&color=8b5cf6&style=flat-square)
![penjaga PR](https://github.com/Nauvalunesa/Sangceo/actions/workflows/pr-jaga.yml/badge.svg)
![terakhir diubah](https://img.shields.io/github/last-commit/Nauvalunesa/Sangceo?label=terakhir%20diubah&color=22c55e&style=flat-square)

</div>

---

## Ambil satu, sekarang

```mermaid
flowchart LR
    A([Pilih nama]) --> B[Berkas JSON<br/>dibuat otomatis]
    B --> C[Pull request]
    C --> D{Bot memeriksa}
    D -->|ada yang salah| E[PR ditutup<br/>beserta alasannya]
    D -->|lolos| F[merge otomatis]
    F --> G([DNS aktif<br/>dan mailbox jadi])
    E -.->|perbaiki| C

    style A fill:#0ea5e9,stroke:#0369a1,color:#fff
    style G fill:#22c55e,stroke:#15803d,color:#fff
    style D fill:#f59e0b,stroke:#b45309,color:#fff
    style E fill:#ef4444,stroke:#b91c1c,color:#fff
    style F fill:#8b5cf6,stroke:#6d28d9,color:#fff
```

Tidak perlu menulis berkas manual. Buka generator, isi kolomnya, tekan tombol. GitHub
terbuka dengan isi yang sudah terisi.

<div align="center">

| | Langkah | Hasil |
|:---:|:---|:---|
| 1 | Buka [sang.ceo/daftar](https://sang.ceo/daftar) | Isi nama dan tujuan |
| 2 | Tekan **Klaim lewat GitHub** | Fork, berkas, dan PR sekaligus |
| 3 | Tunggu beberapa detik | Komentar pratinjau dan merge otomatis |
| 4 | Arahkan domain di hosting | Sertifikat SSL terbit sendiri |

</div>

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:0ea5e9,100:8b5cf6&height=3&section=footer" width="100%" alt="" />

</div>

## Berkas klaim

<table>
<tr><th>Subdomain</th><th>Mailbox</th></tr>
<tr><td valign="top">

`data/domains/namamu.sang.ceo.json`

```json
{
  "domain": "sang.ceo",
  "subdomain": "namamu",
  "owner": "username-github",
  "records": {
    "CNAME": "cname.vercel-dns.com"
  }
}
```

</td><td valign="top">

`data/emails/alamat.json`

```json
{
  "domain": "sang.ceo",
  "address": "alamat",
  "type": "mailbox",
  "owner": "username-github"
}
```

</td></tr>
</table>

`owner` terisi sendiri dari akun yang membuka pull request. Kalau ditulis tangan dan
berbeda dengan pembukanya, PR ditolak. Aturan inilah yang mencegah orang mengambil alih
klaim bukan miliknya.

## Tipe record

| Tipe | Isi | Contoh |
|:---|:---|:---|
| `A` | Alamat IPv4 | `76.76.21.21` |
| `AAAA` | Alamat IPv6 | `2606:4700::6810:84e5` |
| `CNAME` | Nama host, tanpa `http://` | `cname.vercel-dns.com` |
| `TXT` | Teks bebas, maksimal 2000 karakter | `verifikasi=abc123` |
| `SRV` | `prioritas bobot port target` | `10 5 443 contoh.com` |
| `CAA` | `flag tag nilai` | `0 issue letsencrypt.org` |

<div align="center">

**Tidak tersedia di sini:** `MX` dan `NS`. `MX` bisa membelokkan surat orang, `NS` bisa
mengambil alih seluruh zona beserta semua subdomain di dalamnya. `PTR`, `SOA`, dan
`DNSKEY` tidak berlaku untuk subdomain klaim.

</div>

CNAME harus satu-satunya record pada namanya. Itu aturan DNS (RFC 1034 dan 1035), bukan
pilihan kami: resolver yang menerima CNAME bersama record lain akan menjawab dengan hasil
yang tidak bisa ditebak.

## Batas yang berlaku

<div align="center">

| Aturan | Batas | Alasan |
|:---|:---:|:---|
| Subdomain per akun | **3** | supaya tetap ada jatah untuk orang lain |
| Record tambahan per subdomain | **10** | cukup untuk verifikasi penyedia |
| Mailbox gratis | **3** | jatah dari penyedia email |
| Panjang TXT | **2000** | batas teknis DNS |
| Berkas di luar `data/` | **ditolak** | repo ini data klaim, bukan kode |

</div>

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:0ea5e9,100:8b5cf6&height=3&section=footer" width="100%" alt="" />

</div>

## Struktur

```text
.
├── data/
│   ├── domains/                    # satu subdomain per berkas
│   │   └── nama.sang.ceo.json
│   └── emails/                     # satu mailbox per berkas
│       └── nama.json
├── scripts/
│   ├── validate.mjs                # aturan validasi, dipakai penjaga
│   └── jaga-pr.sh                  # memeriksa, mengomentari, menutup, dan merge
└── .github/workflows/
    ├── pr-beri-tahu.yml            # pemicu secepat mungkin setelah PR dibuka
    └── pr-jaga.yml                 # pekerjaan yang butuh izin tulis
```

## Cara bot bekerja

```mermaid
sequenceDiagram
    autonumber
    participant K as Kamu
    participant G as GitHub
    participant P as Penjaga

    K->>G: buka pull request
    G->>P: picu lewat "Kabari penjaga"
    P->>P: periksa bentuk berkas,<br/>nama, tipe, nilai, dan pemilik
    alt ada yang salah
        P->>G: komentar berisi alasannya
        P->>G: tutup pull request
    else lolos
        P->>G: komentar pratinjau
        P->>G: merge otomatis
    end
    G-->>K: pemberitahuan
```

Pemicunya dipisah dua berkas dengan sengaja. Workflow yang dipicu pull request dari fork
hanya menerima token baca-saja, sekalipun `permissions:` menulis `write`. Jadi berkas
pertama hanya memberi tahu, dan pekerjaan yang butuh izin tulis dilakukan berkas kedua
yang berjalan di repo ini. Hasilnya PR baru ditangani dalam hitungan detik, tanpa tombol
persetujuan yang harus ditekan pemilik repo.

Sesudah merge, pengelola menjalankan sinkronisasi yang membuat record DNS dan akun
mailbox, lalu mengirim sandinya ke email akun GitHub pembuka pull request.

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:0ea5e9,100:8b5cf6&height=3&section=footer" width="100%" alt="" />

</div>

## Untuk kontributor

Ingin mengubah aturan, validator, atau alur bot? Baca [CONTRIBUTING.md](./CONTRIBUTING.md)
lebih dulu. PR yang mengubah berkas di luar `data/` ditutup otomatis. Bukan karena tidak
diinginkan, tetapi supaya aturan validasi tidak bisa dilonggarkan lewat pull request yang
terlihat seperti perbaikan biasa.

Validator dijalankan dari versi `main`, bukan versi yang dibawa PR, justru untuk itu.

<div align="center">

---

<sub>Repo ini hanya berisi data klaim. Kode situs, kredensial, dan proses provisioning
tidak ada di sini. Sandi mailbox tidak pernah ditulis ke Git.</sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8b5cf6,50:6366f1,100:0ea5e9&height=140&section=footer" width="100%" alt="" />

</div>
