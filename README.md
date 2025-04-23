![Image](https://github.com/user-attachments/assets/5e9baa70-9e7a-4aa3-a921-1f07989e06ae)
![Image](https://github.com/user-attachments/assets/be327e5f-d701-42d3-bad1-531513f3fa4e)
Tahap / Fungsi | Deskripsi Operasi | Waktu (Time) | Ruang (Space)
1. Data Retrieval | • Buka file CSV• Baca baris demi baris (n baris)• Parse id, label, x, y dengan stringstream | O(n) | O(n) untuk menyimpan semua Point di memori
2. Sorting | • std::sort(points.begin(), points.end(), cmp)  – Urutkan by x ↑, tiebreak by y ↓ | O(n log n) | O(log n) tambahan (stack rekursi sort)
3. Skyline Computation (Stack) | • Iterasi satu-pass pada points (n elemen)• Untuk tiap p:   – Pop selagi dominates(p, peek)   – Skip jika dominates(peek, p)   – Push(p) ke stack | Amortized O(n) | O(n) untuk node linked-list stack
— dominates(a,b) | • Cek `(a.x<=b.x && a.y>=b.y) && (a.x<b.x |  | a.y>b.y)`
— Stack::push/pop/peek | • Alokasi / dealokasi satu Node• Akses pointer | O(1) each | O(1) per elemen
4. Output Results | • Pop semua elemen stack (m = ukuran skyline)• Cetak id,label,x,y | O(m) | O(m) untuk vektor skyline
5. Memory Measurement | • Panggilan API OS (Win: GetProcessMemoryInfo) | O(1) | O(1)
TOTAL TIME | Dominasi oleh tahap sorting + skyline pass | O(n log n) | O(n)
TOTAL SPACE | Vektor points + stack linked-list (+ overhead CSV buffer) | O(n) | 
