# SOAL 1: Data Definition & Relasi [Bobot: 40%]

> **(SCPMK0720801 - DDL & Relasi)** Pembuatan struktur fisik dan ketepatan relasi.

1. Pilihlah 3 tabel dari proyek kelompok Anda yang saling berelasi (Contoh: 2 Tabel Induk/Master dan 1 Tabel Transaksi/Anak).
2. Tuliskan kode SQL `CREATE TABLE` untuk ketiga tabel tersebut!
3. **Syarat Wajib:**
   - Tentukan tipe data yang rasional dan `Primary Key` yang valid.
   - Harus ada deklarasi `FOREIGN KEY` yang menghubungkan Tabel Transaksi dengan kedua Tabel Induk.

---


## 1. Tabel Master Mahasiswa

```sql
CREATE TABLE `mahasiswa` (
  `nim` VARCHAR(100) NOT NULL,
  `nama` VARCHAR(100) NOT NULL,
  `semester` INT NOT NULL,
  CONSTRAINT `pk_mahasiswa` PRIMARY KEY (`nim`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

## 2. Tabel Master Matkul

```sql
CREATE TABLE `matkul` (
  `kode_mk` VARCHAR(100) NOT NULL,
  `nama_mk` VARCHAR(100) NOT NULL,
  `sks` INT NOT NULL,
  CONSTRAINT `pk_matkul` PRIMARY KEY (`kode_mk`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

## 3. Tabel Transaksi KRS

```sql
CREATE TABLE `krs` (
  `id_krs` VARCHAR(20) NOT NULL,
  `nim` VARCHAR(100) NOT NULL,
  `kode_mk` VARCHAR(100) NOT NULL,
  `semester` VARCHAR(20) NOT NULL,
  `tahun_akademik` VARCHAR(20) NOT NULL,
  CONSTRAINT `pk_krs` PRIMARY KEY (`id_krs`),
  CONSTRAINT `fk_krs_mahasiswa` FOREIGN KEY (`nim`) 
      REFERENCES `mahasiswa` (`nim`) 
      ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `fk_krs_matkul` FOREIGN KEY (`kode_mk`) 
      REFERENCES `matkul` (`kode_mk`) 
      ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```