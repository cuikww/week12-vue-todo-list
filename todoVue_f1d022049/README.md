# Assignment: Vue.js – Simple To-Do List

## Identitas
- **Nama** : I Nengah Dwi Putra Witarsana
- **NIM** : F1D022049

---

## Deskripsi Tugas
Pada tugas ini saya membuat aplikasi To-Do List sederhana menggunakan Vue.js 3 (Composition API).
Aplikasi memiliki fitur utama:
- Menambah tugas baru ke dalam daftar.
- Menghapus tugas yang sudah selesai atau tidak diinginkan.
- Menampilkan pesan informatif saat daftar tugas kosong.
- Menggunakan reaktifitas Vue dengan `ref()` untuk pengelolaan state.

---

## Hasil

### 1. Screenshot Hasil Program

> *[Panduan: Masukkan gambar screenshot aplikasi Anda di sini. Anda bisa mengupload gambar ke folder project lalu link-kan seperti format di bawah, atau drag-and-drop jika mengedit langsung di GitHub]*

![Tampilan Aplikasi](![alt text](image.png))

*(Pastikan Anda menyertakan screenshot saat list kosong dan saat ada isinya)*

### 2. Penjelasan Singkat

Berikut adalah penjelasan teknis mengenai fitur utama aplikasi:

#### a. Menambah Tugas (`addTask`)
Fungsi `addTask` dijalankan saat form disubmit.
1. Sistem mengecek apakah input (`newTask`) tidak kosong.
2. Jika ada isi, teks dimasukkan ke dalam array `tasks` menggunakan `.push()`.
3. Input form dikosongkan kembali (`newTask.value = ''`) agar siap untuk input berikutnya.
4. Menggunakan modifier `@submit.prevent` pada form untuk mencegah halaman refresh otomatis.

#### b. Menampilkan Data (`v-for`)
Daftar tugas ditampilkan menggunakan direktif `v-for="(task, index) in tasks"`. 
- `task`: Menyimpan teks tugas.
- `index`: Digunakan sebagai `:key` unik dan parameter untuk menghapus tugas.

#### c. Menghapus Tugas
Tombol hapus memiliki event listener `@click="removeTask(index)"`.
- Fungsi ini menerima `index` dari item yang diklik.
- Menggunakan metode JavaScript `splice(index, 1)` untuk menghapus 1 item dari array `tasks` pada posisi tersebut.
- Karena `tasks` adalah reactive (`ref`), tampilan akan otomatis diperbarui (item menghilang).

#### d. Kondisi Kosong (`v-if`)
Elemen paragraf "Tidak ada tugas" hanya akan dirender jika `tasks.length === 0`. Jika array memiliki isi, elemen ini otomatis disembunyikan dan digantikan oleh list tugas (`v-else`).

---