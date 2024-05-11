# sib6_project5
# Project 5 - Create CRUD API Using Flask and Docker

Tools yang harus disiapkan:

- Docker
- Postman
- Visual Code Studio
- DBeaver

API yang dibuat:

- Create User
- Update User
- Get User
- Delete User

# Langkah-langkah
1. Buat File docker-compose.yml

   Buat file docker-compose.yml. Tentukan service dan setting environment-nya, juga build volume external untuk menyimpan data ke lokal. Lalu jalankan `docker-compose up -d`.

   Catatan: Buat docker-compose untuk PostgreSQL dahulu untuk memastikan kita sudah terhubung dengan PostgreSQL lewat DBeaver. Jika berhasil, tambahkan docker-compose untuk Flask.

2. Jika sudah berhasil menjalankan file docker-compose, selanjutnya koneksikan pada database dengan host, database, user, password, dan port yang sesuai dengan setting environments di docker-compose sebelumnya. Pastikan koneksi berhasil.

3. Buat File Requirements.txt

4. Buat File Dockerfile untuk membuat image project5

5. Jalankan `docker build -t project5 .` untuk membangun sebuah image Docker dengan nama "project5" dari Dockerfile.

6. Run script membuat table di bawah ini di PostgreSQL:

```sql
CREATE SEQUENCE user_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;

CREATE TABLE public.users (
    user_id int4 NOT NULL DEFAULT nextval('user_id_seq'::regclass),
    name varchar(100) NULL,
    city varchar(50) NULL,
    telp varchar(14) NULL,
    CONSTRAINT users_pkey PRIMARY KEY (user_id)
);
```

7. Run pada localhost:5000 untuk mengetahui apakah Flask bisa terkoneksi dengan database menggunakan psycopg2.

8. Lalu, untuk melakukan testing CRUD API-nya, kita menggunakan Postman.
