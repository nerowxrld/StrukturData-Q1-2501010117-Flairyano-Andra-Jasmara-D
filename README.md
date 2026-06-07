# Jawaban Quis 1 Struktur Data

**Nama:** Flairyano Andra Jasmara  
**NIM:** 2501010117  
**Materi:** Array dan Linked List

---

## 1. Karakteristik Memori dan Akses Data

**Mengapa akses elemen Array O(1) sedangkan Singly Linked List O(n)?**

- **Array** dialokasikan dalam memori secara **kontigu (berurutan)**. Alamat setiap elemen dapat dihitung langsung dengan rumus:  
  `address(i) = base_address + i * ukuran_elemen`  
  Karena itu, waktu akses ke elemen ke-i bersifat konstan, tidak tergantung ukuran array → **O(1)**.

- **Singly Linked List** dialokasikan secara **non-kontigu (tersebar)**. Setiap node hanya menyimpan alamat node berikutnya. Untuk mengakses elemen ke-i, kita harus menelusuri dari node pertama (head) sebanyak i langkah → **O(n)**.

---

## 2. Analisis Efisiensi Operasi Manipulasi

**Kapan Linked List lebih unggul dari Array untuk insertion/deletion?**

Linked List lebih unggul ketika:

1. **Insertion/deletion di tengah atau awal** sering dilakukan, karena:
   - Pada array, penyisipan/penghapusan di awal/tengah membutuhkan pergeseran elemen (O(n)).
   - Pada linked list, cukup ubah pointer node sebelumnya/berikutnya (O(1) setelah posisi ditemukan).

2. **Ukuran data dinamis & tidak diketahui sebelumnya**, karena:
   - Array statis memiliki kapasitas tetap → resiko pemborosan memori atau perlu resizing.
   - Linked list tumbuh & menyusut sesuai kebutuhan tanpa alokasi ulang besar.

**Catatan:** Pencarian posisi tetap O(n) pada linked list. Jadi keunggulan ini berlaku jika posisi sudah diketahui (misal: sedang iterasi).

---

## 3. Konsep Doubly Linked List

**Struktur node Doubly Linked List:**

| Field       | Fungsi                                |
|-------------|---------------------------------------|
| `prev`      | Pointer ke node sebelumnya            |
| `data`      | Nilai/data yang disimpan               |
| `next`      | Pointer ke node berikutnya             |

**Dampak pointer tambahan (`prev`):**

- **Memori:** Lebih boros (2 pointer per node vs 1 pointer pada singly).
- **Fleksibilitas penelusuran:**
  - Bisa traversing maju (`next`) dan mundur (`prev`).
  - Penghapusan node tertentu lebih mudah karena tidak perlu tahu node sebelumnya.
  - Cocok untuk implementasi struktur seperti **deque (double-ended queue)**.

---

## 4. Mekanisme Circular Linked List

**Perbedaan teoritis dengan linked list biasa:**

- Linked list biasa: node terakhir menunjuk ke `null` (atau `None`).
- Circular linked list: node terakhir menunjuk kembali ke node **pertama** (head), membentuk lingkaran.

**Contoh use case yang lebih efektif:**

- **Round-robin scheduling** pada sistem operasi atau game turn-based.
  - Proses/player dijalankan bergantian secara melingkar tanpa batas.
  - Circular linked list memudahkan perputaran tanpa perlu mereset pointer ke awal secara eksplisit.

---

## 5. Array Dinamis di Python

**Mekanisme di balik layar saat Dynamic Array (Python list) kehabisan kapasitas pada operasi `append`:**

1. Python list menyimpan elemen dalam memori kontigu dengan kapasitas tertentu (`allocated size`) lebih besar dari panjang aktual (`size`).
2. Saat `append` dan `size == capacity`, Python akan:
   - Mengalokasikan blok memori baru dengan kapasitas lebih besar (biasanya **1.125 × capacity** untuk list besar, atau ukuran tetap untuk list kecil).
   - Menyalin semua elemen lama ke memori baru (O(n)).
   - Membebaskan memori lama.
   - Menambahkan elemen baru di akhir.
3. Teknik ini disebut **amortized O(1)** untuk `append`, karena meskipun sesekali mahal (O(n)), rata-rata per operasi tetap konstan.

---
