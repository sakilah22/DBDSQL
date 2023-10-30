#Data Manipulation Language-Praktikum 3#
```
create database schema_akademik
```

```
use schema_akademik
```

```
create table FAKULTAS (
	ID_FAKULTAS smallint primary key not null,
	FAKULTAS VARCHAR(45) not null
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABLE%20FAKULTAS.png)

```
create table JURUSAN(
	ID_JURUSAN smallint primary key not null,
	ID_FAKULTAS smallint not null,
	JURUSAN VARCHAR(45),
	foreign key (ID_FAKULTAS) references FAKULTAS (ID_FAKULTAS)
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABLE%20JURUSAN.png)

```
create table STRATA(
	ID_STRATA smallint primary key not null,
	SINGKAT VARCHAR(10) not null,
	STRATA VARCHAR(45) not null 
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABLE%20STRATA.png)

```
create table SELEKSI_MASUK(
	ID_SELEKSI_MASUK smallint primary key not null,
	SINGKAT VARCHAR(12) not null,
	SELEKSI_MASUK VARCHAR(100) not null 
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABLE%20SELEKSI_MASUK.png)

```
create table PROGRAM_STUDI(
	ID_PROGRAM_STUDI smallint primary key not null,
	ID_STRATA smallint,
	ID_JURUSAN smallint,
	PROGRAM_STUDI VARCHAR(60),
	foreign key (ID_STRATA) references STRATA(ID_STRATA),
	foreign key (ID_JURUSAN) references JURUSAN(ID_JURUSAN)
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABEL%20PROGRAM%20STUDI.png)

```
create table MAHASISWA (
	NIM VARCHAR(15) primary key not null,
	ID_SELEKSI_MASUK smallint,
	ID_PROGRAM_STUDI smallint,
	NAMA VARCHAR(45),
	ANGKATAN smallint,
	TGL_LAHIR DATE,
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1),
	foreign key (ID_SELEKSI_MASUK) references SELEKSI_MASUK(ID_SELEKSI_MASUK),
	foreign key (ID_PROGRAM_STUDI) references PROGRAM_STUDI(ID_PROGRAM_STUDI),
	constraint CK_JENIS_KELAMIN check (JENIS_KELAMIN in('W', 'P'))
)
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/TABLE%20MAHASISWA.png)


```
insert into FAKULTAS(ID_FAKULTAS, FAKULTAS)
VALUES(1, 'Ekonomi & Bisnis'), (2, 'Ilmu Komputer')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20FAKULTAS.png)

```
insert into JURUSAN (ID_JURUSAN, ID_FAKULTAS, JURUSAN)
values(21, 2, 'Informatika'), (22, 2, 'Sistem Informasi'), (23, 2, 'Teknik Komputer')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20JURUSAN.png)

```
insert into STRATA(ID_STRATA, SINGKAT, STRATA)
VALUES(1, 'D1', 'Diploma'), (2, 'S1', 'Sarjana'), (3, 'S2', 'Magister')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20STRATA.png)

```
insert into PROGRAM_STUDI(ID_PROGRAM_STUDI, ID_STRATA, ID_JURUSAN, PROGRAM_STUDI)
VALUES(211, 2, 21, 'Teknik Informatika'), (212, 2, 21, 'Teknik Komputer'), (219, 3, 21, 'Magister Ilmu Komputer')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20PROGRAM%20STUDI.png)

```
insert into SELEKSI_MASUK(ID_SELEKSI_MASUK, SINGKAT, SELEKSI_MASUK)
VALUES(1, 'SNMPTN', 'SELEKSI NASIONAL MAHASISWA PERGURUAN TINGGI NEGERI'), (2, 'SBMPTN', 'SELEKSI BERSAMA MAHASISWA PERGURUAN TINGGI NEGERI')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20SELEKSI%20MASUK.png)

```
insert into MAHASISWA (NIM, ID_SELEKSI_MASUK, ID_PROGRAM_STUDI, NAMA, ANGKATAN, TGL_LAHIR, KOTA_LAHIR, JENIS_KELAMIN)
VALUES('155150400', 1, 211, 'JONI', 2015, 1/1/1997, 'Malang', 'W'), ('155150401', 2, 212, 'JONI', 2015, 2/10/1997, 'Situbondo', 'P')
```
![alt text](https://github.com/sakilah22/DBDSQL-DML-PRAK3/blob/main/SELECT%20MAHASISWA.png)

