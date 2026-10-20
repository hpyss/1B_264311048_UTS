# 🗄️ UTS Praktik Basis Data — 1B_264311048

> **Nama:** Muhammad Amirul Hafidz
> **Mata Kuliah:** Praktik Basis Data  
> **NIM:** 264311048  
> **Kelas:** 1B  
> **Prodi:** TRPL

---

## 📁 Struktur Repository

```
1B_264311048_UTS/
├── soal_1.md              # Soal 1 — DDL & Relasi (Bobot 40%)
├── soal_2.md              # Soal 2 — Operasi CRUD Dasar (Bobot 50%)
├── soal_3.md              # Soal 3 — Query Kompleks & Agregasi (Bobot 10%)
├── assets/
│   └── img/
│       ├── screenshot_insert.png   # Bukti INSERT phpMyAdmin
│       ├── screenshot_select.png   # Bukti SELECT phpMyAdmin
│       ├── screenshot_update.png   # Bukti UPDATE phpMyAdmin
│       ├── screenshot_delete.png   # Bukti DELETE phpMyAdmin
│       └── screenshot_soal3.png    # Bukti query agregasi phpMyAdmin
└── README.md
```

---

## 📝 Ringkasan Soal & Jawaban

### Soal 1 — Data Definition & Relasi `[Bobot: 40%]`

Membuat 3 tabel yang saling berelasi menggunakan `CREATE TABLE`:

| Tabel | Tipe | Primary Key | Keterangan |
|---|---|---|---|
| `mahasiswa` | Induk | `nim` | Data mahasiswa |
| `matkul` | Induk | `kode_mk` | Data mata kuliah |
| `krs` | Transaksi | `id_krs` | KRS sebagai penghubung |

Tabel `krs` memiliki **FOREIGN KEY** ke `mahasiswa` dan `matkul` dengan `ON DELETE CASCADE ON UPDATE CASCADE`.

---

### Soal 2 — Operasi CRUD Dasar `[Bobot: 50%]`

Operasi CRUD pada 3 tabel:

| Operasi | Perintah | Keterangan |
|---|---|---|
| **CREATE** | `INSERT INTO` | 3 baris × 3 tabel = 9 baris data dummy |
| **READ** | `SELECT *` | Menampilkan seluruh data tabel `mahasiswa` |
| **UPDATE** | `UPDATE ... WHERE` | Mengubah `tahun_akademik` di tabel `krs` |
| **DELETE** | `DELETE ... WHERE` | Menghapus 1 baris dari tabel `krs` |

---

### Soal 3 — Query Kompleks & Agregasi `[Bobot: 10%]`

Query tunggal yang menggabungkan `SELECT`, `JOIN`, `WHERE`, dan `GROUP BY`:

```sql
SELECT
    m.nama              AS nama_mahasiswa,
    COUNT(k.id_krs)     AS jumlah_matkul,
    SUM(mk.sks)         AS total_sks
FROM mahasiswa m
JOIN krs k   ON m.nim      = k.nim
JOIN matkul mk ON k.kode_mk = mk.kode_mk
WHERE k.tahun_akademik = '2024/2025'
GROUP BY m.nim, m.nama;
```

---

## 🛠️ Tools yang Digunakan

- **MySQL** via **phpMyAdmin 5.2.3**
- **XAMPP** (localhost)
- **Markdown** untuk dokumentasi

---

## 📸 Screenshots

Bukti eksekusi SQL di phpMyAdmin tersedia di folder [`assets/img/`](assets/img/).
