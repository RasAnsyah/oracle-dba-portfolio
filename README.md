# oracle-dba-portfolio
Project Administration and Optimization Oracle Database

# Oracle DBA Projects & Solutions
## Daftar Isi

1.  [SQL Performance Tuning Case Study](#1-sql-performance-tuning-case-study)
2.  [RMAN Backup & Recovery Scenario](#2-rman-backup--recovery-scenario)
3.  [Oracle Database Setup & Automation](#3-oracle-database-setup--automation)
4.  [Konsep Oracle Cloud Database (Opsional)](#4-konsep-oracle-cloud-database-opsional)
5.  [Real-World DBA Operations – Monthly Report (Desember 2022)](#5-real-world-dba-operations--monthly-report-desember-2022)

---

## Keahlian yang Didemonstrasikan

* **Performance Tuning:** Identifikasi *bottleneck*, optimasi *query* SQL, analisis *execution plan*.
* **Backup & Recovery (RMAN):** Implementasi strategi *backup*, skenario *point-in-time recovery*, penanganan *data loss*.
* **Administrasi Database:** Instalasi, konfigurasi, manajemen *user* dan keamanan, *space management*.
* **Otomatisasi:** Dasar *shell scripting* untuk tugas DBA harian.
* **Pemecahan Masalah:** Analisis *error*, diagnostik sistem.
* **Pemahaman Konsep Cloud Database:** Kesadaran terhadap tren Database as a Service (DBaaS) dan Autonomous Database di OCI.

---

## Teknologi yang Digunakan

* **Database:** Oracle Database 10g - 19c
* **Sistem Operasi:** Oracle Linux / Solaris
* **Tools:** SQL*Plus, TOAD, SQL Developer, RMAN/DMP, Oracle Enterprise Manager (konseptual), VirtualBox/Docker.
* **Scripting:** Bash Shell Scripting.

---

### 1. SQL Performance Tuning Case Study

**Direktori:** `./01-SQL-Performance-Tuning-Case-Study`

**Deskripsi:**
Studi kasus ini menunjukkan proses *tuning* sebuah *query* SQL yang memiliki performa buruk pada sebuah *dataset* internal. Query mengambil data kapal berdasarkan nomor dokumen referensi, namun mengalami Full Table Scan yang menghambat performa.

---

#### 🔧 Tuning Case – Full Table Scan to Index Range Scan

**📌 SQL ID:** `0r7t74avwxp3g`

```sql
SELECT NAMA_KAPAL
FROM REMOTE.ITGR_HEADER
WHERE REF_DOC_NO = :REF_DOC_NO AND ROWNUM = 1;
```

**Masalah:**
Query mengalami Full Table Scan karena kolom `REF_DOC_NO` belum memiliki index. Hal ini menyebabkan query lambat meskipun hanya membutuhkan satu baris data.

**Before (Execution Plan):**

![alt text](<EP BEFORE.png>)

- Access Path: FULL TABLE SCAN on `REMOTE.ITGR_HEADER`
- Cost: 1.634
- Estimasi: membaca seluruh data di tabel

**Tindakan Perbaikan:**
```sql
CREATE INDEX REMOTE.ITGR_HEADER_IDX01
ON REMOTE.ITGR_HEADER(REF_DOC_NO);
```

**After (Execution Plan):**

![alt text](<EP AFTER.png>)

- Access Path: INDEX RANGE SCAN → TABLE ACCESS BY INDEX ROWID
- Cost menurun drastis
- Oracle Optimizer memilih path yang lebih efisien

**Hasil:**
- Query menjadi jauh lebih cepat
- Beban I/O lebih rendah
- Performa sistem meningkat signifikan saat query digunakan oleh aplikasi

**File Repositori:**
- `initial_sql_query.sql`
- `optimized_sql_query.sql`
- `execution_plan_before.txt`
- `execution_plan_after.txt`
- `create_index_script.sql`
- `tuning_notes_ref_doc_no.md`

---

### 2. RMAN Backup & Recovery Scenario

**Direktori:** `./02-RMAN-Backup-Recovery-Scenario`

Deskripsi dan file sama seperti sebelumnya.

---

### 3. Oracle Database Setup & Automation

**Direktori:** `./03-Oracle-Database-Setup-Automation`

Deskripsi dan file sama seperti sebelumnya.

---

### 4. Konsep Oracle Cloud Database (Opsional)

**Direktori:** `./04-Konsep-Oracle-Cloud-Database`

Deskripsi dan file sama seperti sebelumnya.

---

### 5. Real-World DBA Operations – Monthly Report (Desember 2022)

**Direktori:** `./05-Real-World-DBA-Ops`

Deskripsi dan file sama seperti sebelumnya.

---

## Cara Menjalankan Proyek Ini (Opsional, tapi Direkomendasikan)

Untuk menjalankan dan mereplikasi lingkungan ini, Anda akan membutuhkan:
* Virtualisasi software seperti Oracle VirtualBox.
* File ISO [nama OS, contoh: Oracle Linux 7/8].
* Installer Oracle Database [versi].

Ikuti instruksi di direktori masing-masing untuk detail lebih lanjut.

---

## Tentang Saya

Saya adalah seorang profesional DBA berpengalaman yang kembali aktif di dunia teknologi setelah jeda singkat untuk refleksi diri dan pengembangan skill. Dengan minat kuat dalam optimasi performa dan menjaga stabilitas sistem, saya berdedikasi untuk memberikan solusi database yang efisien dan andal.

[Website Portfolio](https://iamfarras.my.id) • [LinkedIn](https://linkedin.com/in/iamfarras) • [GitHub](https://github.com/iamfarras) • contact@iamfarras.my.id
