# oracle-dba-portfolio
Project Administration and Optimization Oracle Database

# Oracle DBA Projects & Solutions
## Daftar Isi

1.  [SQL Performance Tuning Case Study](#1-sql-performance-tuning-case-study)
2.  [RMAN Backup & Recovery Scenario](#2-rman-backup--recovery-scenario)
3.  [Oracle Database Setup & Automation](#3-oracle-database-setup--automation)
4.  [Konsep Oracle Cloud Database (Opsional)](#4-konsep-oracle-cloud-database-opsional)

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
* **Tools:** SQL*Plus, SQL Developer, RMAN, Oracle Enterprise Manager (konseptual), VirtualBox/Docker.
* **Scripting:** Bash Shell Scripting.

---

### 1. SQL Performance Tuning Case Study

**Direktori:** `./01-SQL-Performance-Tuning-Case-Study`

**Deskripsi:**
Studi kasus ini menunjukkan proses *tuning* sebuah *query* SQL yang memiliki performa buruk pada sebuah *dataset* [sebutkan jenis dataset, contoh: penjualan fiktif]. Saya mendemonstrasikan identifikasi *bottleneck*, analisis *execution plan*, dan langkah-langkah optimasi yang berhasil meningkatkan waktu eksekusi secara signifikan.

**Poin-Poin Penting:**
* **Masalah Awal:** [Sebutkan masalahnya secara singkat, contoh: Query mengambil data produk dari beberapa tabel dengan JOIN kompleks, durasi 30 detik.]
* **Analisis:** Menggunakan [Sebutkan metode/tools, contoh: `EXPLAIN PLAN` dan `v$` views] untuk mengidentifikasi penyebab utama kelambatan (misal: *full table scan* yang tidak perlu, *nested loops* yang tidak efisien).
* **Solusi:** Implementasi [Sebutkan solusi, contoh: penambahan indeks, penulisan ulang *subquery* menjadi CTE, atau penggunaan *hint* strategis].
* **Hasil:** [Sebutkan hasil konkret, contoh: Waktu eksekusi berkurang dari 30 detik menjadi 2 detik (peningkatan 93%).]

**File Kunci:**
* `initial_sql_query.sql`: SQL Query sebelum tuning.
* `optimized_sql_query.sql`: SQL Query setelah tuning.
* `execution_plan_before.txt`: Execution plan awal.
* `execution_plan_after.txt`: Execution plan setelah optimasi.
* `tuning_process_notes.md`: Catatan detail proses tuning dan pertimbangan yang diambil.
* `performance_metrics_comparison.png`: Screenshot perbandingan metrik performa (opsional).

---

### 2. RMAN Backup & Recovery Scenario

**Direktori:** `./02-RMAN-Backup-Recovery-Scenario`

**Deskripsi:**
Proyek ini mendemonstrasikan implementasi strategi *backup* database Oracle menggunakan RMAN dan skenario pemulihan dari kegagalan disk/datafile. Tujuannya adalah memastikan *data availability* dan *integrity* setelah insiden.

**Poin-Poin Penting:**
* **Strategi Backup:** [Sebutkan strategi, contoh: Full backup mingguan, Incremental Level 0 bulanan, Incremental Level 1 harian, Archivelog backup setiap 15 menit.]
* **Skenario Pemulihan:** Simulasi kehilangan satu atau lebih *datafile* yang kritis dan proses *point-in-time recovery* (jika memungkinkan).
* **Alat:** RMAN command-line interface.

**File Kunci:**
* `rman_backup_scripts.sql`: Skrip RMAN untuk berbagai jenis backup.
* `recovery_scenario_description.md`: Penjelasan detail skenario bencana dan tujuan pemulihan.
* `recovery_steps_and_scripts.sql`: Langkah-langkah dan skrip RMAN untuk melakukan pemulihan.
* `recovery_log_output.txt`: Output log dari proses recovery yang berhasil.
* `database_architecture_diagram.png`: Diagram sederhana arsitektur database yang di-backup.

---

### 3. Oracle Database Setup & Automation

**Direktori:** `./03-Oracle-Database-Setup-Automation`

**Deskripsi:**
Repositori ini berisi skrip dan panduan langkah demi langkah untuk melakukan instalasi dasar Oracle Database [versi] di lingkungan [OS, contoh: Oracle Linux] dan beberapa skrip otomatisasi tugas DBA harian.

**Poin-Poin Penting:**
* **Instalasi:** Proses instalasi *unzip*, `runInstaller`, dan konfigurasi dasar.
* **Post-Installation Configuration:** Konfigurasi `listener.ora`, `tnsnames.ora`, pembuatan *tablespace* dasar, manajemen *user*.
* **Otomatisasi Sederhana:** Contoh *shell script* untuk monitoring *tablespace* usage, membersihkan *old logs*, atau menjalankan *RMAN backup* terjadwal.

**File Kunci:**
* `oracle_19c_installation_steps.md`: Panduan instalasi step-by-step.
* `post_install_config.sql`: Skrip SQL untuk konfigurasi awal DB.
* `monitor_tablespace.sh`: Contoh skrip monitoring *tablespace*.
* `cleanup_logs.sh`: Contoh skrip pembersihan log.
* `vm_setup_notes.md`: Catatan setup mesin virtual (opsional).

---

### 4. Konsep Oracle Cloud Database (Opsional)

**Direktori:** `./04-Konsep-Oracle-Cloud-Database`

**Deskripsi:**
Bagian ini menyajikan pemahaman konseptual saya tentang layanan database Oracle di *cloud*, khususnya Oracle Cloud Infrastructure (OCI) Database Cloud Service dan Autonomous Database. Tujuannya adalah menunjukkan kesadaran saya akan tren modern dalam pengelolaan database.

**Poin-Poin Penting:**
* **Database as a Service (DBaaS):** Perbandingan arsitektur *on-premise* vs. DBaaS di OCI.
* **Autonomous Database:** Penjelasan tentang fitur *self-driving, self-securing, self-repairing*.
* **Strategi Migrasi:** Pertimbangan dan pendekatan untuk migrasi database Oracle dari *on-premise* ke OCI.

**File Kunci:**
* `oci_db_system_overview.md`: Penjelasan konsep OCI DB System (VM DB, Bare Metal DB).
* `autonomous_db_concepts.md`: Detail tentang ATP (Autonomous Transaction Processing) dan ADW (Autonomous Data Warehouse).
* `cloud_migration_considerations.md`: Dokumen diskusi tentang faktor-faktor migrasi.
* `cloud_database_architecture.png`: Diagram arsitektur sederhana.

---

## Cara Menjalankan Proyek Ini (Opsional, tapi Direkomendasikan)

Untuk menjalankan dan mereplikasi lingkungan ini, Anda akan membutuhkan:
* Virtualisasi software seperti Oracle VirtualBox.
* File ISO [nama OS, contoh: Oracle Linux 7/8].
* Installer Oracle Database [versi].

Ikuti instruksi di direktori masing-masing untuk detail lebih lanjut.

---

## Tentang Saya

Saya adalah seorang profesional DBA berpengalaman yang kembali aktif di dunia teknologi setelah [sebutkan singkat jeda Anda, contoh: jeda singkat untuk refleksi diri]. Dengan minat kuat dalam optimasi performa dan menjaga stabilitas sistem, saya berdedikasi untuk memberikan solusi database yang efisien dan andal.

[Tautan ke Website Portfolio Anda]

---
