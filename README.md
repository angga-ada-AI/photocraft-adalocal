# PhotoCraft — adaLOCAL

Resep pemasangan **PhotoCraft** untuk [adaLOCAL](https://adacode.ai) di adaCODE App: editor foto ala Photoshop
(layer, mask, kurva, PSD) yang ditulis dari nol dengan Rust, dipasang dengan satu klik.

- App asli: https://github.com/storytold/photocraft (organisasi ArtCraft / storytold)
- Lisensi app asli: MIT atau Apache-2.0. Repo ini hanya berisi resep pemasangan, bukan kode app-nya.
- Status hulu: **early alpha** (v0.10.0).

## Isi repo

| Berkas | Fungsi |
|---|---|
| `adacode.json` | Manifes: unduh zip portabel resmi, cocokkan SHA-256, bongkar ke `app/`, jalankan `app\photocraft.exe`. |
| `photocraft.png`, `gambar.jpg` | Ikon (MIT/Apache-2.0, dari repo PhotoCraft) dan tangkapan layar resmi untuk kartu katalog. |

## Cara kerja resep

1. Mengunduh `photocraft-<versi>-windows-x64-portable.zip` dari rilis resmi GitHub.
2. Mencocokkan SHA-256 dengan `SHA256SUMS.txt` rilis yang sama. Berkas yang tak cocok dihapus dan pemasangan berhenti.
3. Membongkar dengan `tar.exe` bawaan Windows (jalur lengkap, karena GNU tar dari Git for Windows menolak zip).
4. Mode portabel: `portable.txt` membuat PhotoCraft menyimpan setelan, preset, dan autosave di `app\PhotoCraftData`,
   tidak di `%APPDATA%`. Perbarui hanya menimpa berkas program, jadi data pengguna tetap utuh.

Memperbarui ke versi baru = ganti versi, nama berkas, dan SHA-256 di `adacode.json`, commit, lalu admin adaCODE
menyimpan commit SHA barunya di `/admin/app-katalog`.

## Agen AI

PhotoCraft menjalankan 500+ perintah yang sama dari menu, CLI, dan server MCP:

```
app\photocraft-cli.exe mcp
```

Agen AI (Claude Code, adaVIBE, adaGENTIC dengan model adaCODE) bisa memakai server MCP ini untuk menyunting foto.
Lapisan AI bawaan Craft (`craft-ai-integrations`) sudah punya adapter OpenAI-compatible, tapi masih draf dan belum
tersambung ke app, jadi model adaCODE belum disuntik ke dalam PhotoCraft.

## Batas pilot

Hanya Windows x64. Rilis Linux (tar.gz/AppImage) dan Mac (dmg) tersedia di hulu, belum diuji di adaLOCAL.
