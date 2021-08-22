# golang-ProjectStructure

## Direktori Go

### `/cmd`

Aplikasi utama untuk proyek ini.

Nama direktori untuk setiap aplikasi harus sesuai dengan nama executable yang ingin Anda miliki (mis., `/cmd/myapp`).

Jangan menaruh banyak kode di direktori aplikasi. Jika menurut Anda kode tersebut dapat diimpor dan digunakan di proyek lain, kode tersebut harus berada di direktori `/pkg`. Jika kode tidak dapat digunakan kembali atau jika Anda tidak ingin orang lain menggunakannya kembali, letakkan kode tersebut di direktori `/internal`. Anda akan terkejut dengan apa yang akan dilakukan orang lain, jadi ungkapkan niat Anda secara eksplisit!

Biasanya memiliki fungsi `main` kecil yang mengimpor dan memanggil kode dari direktori `/internal` dan `/pkg` dan tidak ada yang lain.

Lihat direktori [`/cmd`](cmd/README.md) untuk contoh.

### `/internal`
Aplikasi pribadi dan kode perpustakaan. Ini adalah kode yang Anda tidak ingin orang lain mengimpor di aplikasi atau pustaka mereka. Perhatikan bahwa pola tata letak ini diterapkan oleh kompiler Go itu sendiri. See the Go 1.4 [`release notes`](https://golang.org/doc/go1.4#internalpackages) untuk lebih jelasnya. Perhatikan bahwa Anda tidak terbatas pada direktori `internal` tingkat atas. Anda dapat memiliki lebih dari satu direktori `internal` di level mana pun dari pohon proyek Anda.

Anda dapat secara opsional menambahkan sedikit struktur ekstra ke paket internal Anda untuk memisahkan kode internal bersama dan tidak bersama Anda. Itu tidak diperlukan (terutama untuk proyek yang lebih kecil), tetapi bagus untuk memiliki petunjuk visual yang menunjukkan penggunaan paket yang dimaksudkan. Your actual application code can go in the `/internal/app` directory (e.g., `/internal/app/myapp`) and the code shared by those apps in the `/internal/pkg` directory (e.g., `/internal/pkg/myprivlib`).

