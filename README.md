StrukturData-Q1-2501010117-Flairyano-Andra-Jasmara-D

1. Karakteristik Memori dan Akses Data. Mengapa Array O(1) dan Singly Linked List O(n)?
Perbedaan fundamental terletak pada pola alokasi memori dan cara menghitung alamat elemen.

-Array (Memori Kontigu): Array dialokasikan dalam blok memori yang kontigu (berurutan). Setiap elemen menempati ukuran byte yang tetap (misal, 4 byte untuk int).
-Alamat memori elemen ke-i dapat dihitung langsung dengan rumus:
Address(Array[i]) = Base_Address + (i × size_of_element)

Karena perhitungan ini bersifat aritmatika sederhana dan tanpa perlu penelusuran, waktu aksesnya selalu konstan, O(1). Prosesor dapat langsung menuju ke alamat tersebut (random access).

-Singly Linked List (Memori Non-Kontigu): Node-node dialokasikan secara sporadis (non-kontigu) di memori heap. Tidak ada jaminan node berikutnya terletak setelah node sebelumnya.

Setiap node hanya menyimpan data dan sebuah pointer ke alamat node berikutnya.

Untuk mengakses elemen ke-i, Anda harus memulai dari head (node pertama), lalu mengikuti pointer satu per satu:
head -> node1 -> node2 -> ... -> node(i-1) -> node(i)

Jumlah langkah yang diperlukan sebanding dengan indeks yang dicari, sehingga kompleksitasnya O(n) (sequential access). Tidak ada rumus matematis untuk langsung "melompat" ke node tertentu.

Kesimpulan: Akses acak O(1) array adalah konsekuensi langsung dari memori kontigu; sedangkan linked list mengorbankan akses cepat demi fleksibilitas alokasi memori dinamis.

2. Analisis Efisiensi Operasi Manipulasi. Kapan Linked List Lebih Unggul dari Array?
Linked List lebih diunggulkan untuk operasi penyisipan (insertion) dan penghapusan (deletion) ketika operasi tersebut terjadi di tengah-tengah struktur data dan Anda sudah memiliki pointer ke node lokasi operasi (misal, node hasil pencarian sebelumnya).
3. 
