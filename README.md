# 🎯 TikTok Region API - @slrmyapi/tikreg

Pakej **TikReg API** membolehkan anda mendapatkan maklumat lengkap akaun TikTok berdasarkan username, termasuk ID pengguna, nama panggilan, avatar, dan negara.

---

## 📦 **Pemasangan**

```sh
npm install @slrmyapi/tikreg
```

## **Cara Penggunaan**

```javascript
const { gettikreg } = require("@slrmyapi/tikreg");

// Contoh: Semak maklumat pengguna TikTok berdasarkan username
gettikreg("slrmyshop").then(console.log);

/*
Output:
{
  "status": "success",
  "data": {
    "id": "7061080971211572225",
    "uniqueId": "slrmyshop",
    "nickname": "Slrmy Shop",
    "avatarLarger": "https://p16-common-sign-sg.tiktokcdn-us.com/...",
    "avatarMedium": "https://p16-common-sign-sg.tiktokcdn-us.com/...",
    "avatarThumb": "https://p16-common-sign-sg.tiktokcdn-us.com/...",
    "signature": "copyright | 2019 - 2024",
    "createTime": 1646273078,
    "verified": false,
    "region": "MY",
    "language": "en"
  },
  "country_data": {
    "nama": "Malaysia",
    "penduduk": 33600000,
    "emoji": "🇲🇾",
    "kod_telefon": "+60",
    "mata_wang": {
      "kod": "MYR",
      "simbol": "RM",
      "nama": "Ringgit Malaysia"
    },
    "bahasa_rasmi": {
      "kod": "ms",
      "nama_melayu": "Melayu",
      "nama_asal": "Bahasa Melayu"
    },
    "rantau": "Asia Tenggara"
  },
  "devInfo": {
    "GitHub": "https://github.com/slrmyshopofficial",
    "NPM": "@slrmyapi/tikreg",
    "WhatsApp": "+601136871190",
    "Instagram": "@slrmyshopofficial"
  }
}
*/
```

## **Contoh Kod Lengkap**

```javascript
const { gettikreg } = require("@slrmyapi/tikreg");

async function semakTikTok(username) {
    try {
        const result = await gettikreg(username);
        if (result.status !== "success") {
            console.log("⚠️ Error:", result.message);
        } else {
            console.log("✅ Keputusan:", result);
        }
    } catch (error) {
        console.error("❌ API Bermasalah:", error);
    }
}

// Contoh penggunaan:
semakTikTok("slrmyshop");
```

## 📊 Penerangan Data dalam Respons API TikReg

| **Nama Kunci**                   | **Penerangan** |
|----------------------------------|---------------|
| `status`                         | Status permintaan API (`true` jika berjaya, `false` jika gagal). |
| `devinfo.pemaju`                 | Nama pemaju API. |
| `devinfo.versi`                  | Versi API yang sedang digunakan. |
| `devinfo.tarikh`                 | Tarikh data diambil (dalam format Malaysia). |
| `devinfo.masa`                   | Masa data diambil (dalam format Malaysia). |
| `devinfo.GitHub`                 | Pautan ke repositori GitHub pemaju API. |
| `devinfo.NPM`                    | Nama pakej API di NPM. |
| `devinfo.WhatsApp`               | Nombor WhatsApp untuk sokongan API. |
| `devinfo.Instagram`              | Akaun Instagram pemaju API. |
| `data.pengguna.id`               | ID unik pengguna TikTok. |
| `data.pengguna.id_pendek`        | ID pendek pengguna (jika ada). |
| `data.pengguna.nama_pengguna`    | Nama pengguna (username) TikTok. |
| `data.pengguna.nama_paparan`     | Nama paparan pengguna TikTok. |
| `data.pengguna.gambar_profil_besar` | URL gambar profil dalam saiz besar. |
| `data.pengguna.gambar_profil_sederhana` | URL gambar profil dalam saiz sederhana. |
| `data.pengguna.gambar_profil_kecil` | URL gambar profil dalam saiz kecil. |
| `data.pengguna.bio`              | Bio pengguna TikTok. |
| `data.pengguna.masa_dicipta`     | Waktu akaun dicipta dalam format Unix timestamp. |
| `data.pengguna.sahkan`           | Status akaun sama ada `true` (disahkan) atau `false` (tidak disahkan). |
| `data.pengguna.secUid`           | ID keselamatan akaun pengguna. |
| `data.pengguna.akaun_peribadi`   | Status akaun sama ada peribadi (`true`) atau umum (`false`). |
| `data.pengguna.akaun_rahsia`     | Status akaun sebagai rahsia atau tidak (`true`/`false`). |
| `data.pengguna.kategori_akaun`   | Kategori pengguna (contoh: `Gaming`). |
| `data.pengguna.tetapan_komen`    | Tetapan komen pada profil pengguna. |
| `data.pengguna.tetapan_duet`     | Tetapan duet untuk video pengguna. |
| `data.pengguna.tetapan_stitch`   | Tetapan stitch untuk video pengguna. |
| `data.pengguna.tetapan_muat_turun` | Tetapan muat turun video pengguna. |
| `data.pengguna.region`           | Kod negara pengguna berdasarkan lokasi TikTok. |
| `data.pengguna.bahasa_utama.kod` | Kod bahasa utama yang digunakan oleh pengguna TikTok. |
| `data.pengguna.bahasa_utama.nama_melayu` | Nama bahasa dalam Bahasa Melayu. |
| `data.pengguna.bahasa_utama.nama_asal` | Nama asal bahasa dalam skrip asal. |
| `data.pengguna.pautan_bio.link`  | Pautan dalam bio pengguna TikTok. |
| `data.pengguna.pautan_bio.tahap_risiko` | Tahap risiko pautan bio (`0` = selamat). |
| `data.pengguna.senarai_acara`    | Senarai acara yang dijadualkan oleh pengguna. |
| `data.pengguna.organisasi`       | Status akaun sama ada organisasi (`1`) atau individu (`0`). |
| `data.statistik.pengikut`        | Jumlah pengikut pengguna. |
| `data.statistik.mengikuti`       | Jumlah akaun yang diikuti oleh pengguna. |
| `data.statistik.like`            | Jumlah keseluruhan "like" yang diterima oleh pengguna. |
| `data.statistik.kandungan`       | Jumlah video yang telah dimuat naik oleh pengguna. |
| `negara.kod`                     | Kod negara pengguna. |
| `negara.nama`                    | Nama penuh negara pengguna. |
| `negara.emoji`                   | Emoji bendera negara pengguna. |
| `negara.kod_telefon`             | Kod telefon antarabangsa negara pengguna. |
| `negara.mata_wang.kod`           | Kod mata wang negara. |
| `negara.mata_wang.simbol`        | Simbol mata wang rasmi negara. |
| `negara.mata_wang.nama`          | Nama penuh mata wang negara. |
| `negara.bahasa_rasmi.kod`        | Kod bahasa rasmi negara pengguna. |
| `negara.bahasa_rasmi.nama_melayu` | Nama bahasa rasmi dalam Bahasa Melayu. |
| `negara.bahasa_rasmi.nama_asal`  | Nama asal bahasa rasmi dalam skrip asal. |
| `negara.rantau`                  | Rantau atau kawasan geografi negara pengguna. |
| `negara.global_selatan`          | Status sama ada negara tergolong dalam Global Selatan. |

---

📌 **Nota Tambahan:**
- `data.pengguna.masa_dicipta` adalah dalam bentuk **Unix Timestamp** dan perlu ditukar kepada format tarikh yang lebih mudah dibaca.
- `data.pengguna.region` boleh digunakan bersama **API Country** untuk mendapatkan maklumat lanjut seperti nama negara, emoji bendera, mata wang, dan bahasa rasmi.
- `data.pengguna.bahasa_utama.kod` menunjukkan kod bahasa utama pengguna dan boleh dibandingkan dengan `negara.bahasa_rasmi.kod` untuk melihat kesesuaian bahasa berdasarkan negara pengguna.

---

# 👨‍💻 Developer Info

<p align="left">
  <a href="https://github.com/slrmyshopofficial">
    <img src="https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  </a>
  <a href="https://www.npmjs.com/package/@slrmyapi/">
    <img src="https://img.shields.io/badge/NPM-CB3837?style=for-the-badge&logo=npm&logoColor=white" alt="NPM">
  </a>
  <a href="https://wa.me/601136871190">
    <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>
  <a href="https://instagram.com/slrmyshopofficial">
    <img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram">
  </a>
</p>
---
