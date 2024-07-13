
## OPERASI GEOMETRIX CITRA
Operasi geometri adalah proses perubahan hubungan spasial antara setiap pixel pada sebuah citra. Operasi geometri memetakan kembali pixel citra input dari posisi awal (x1,y1) ke posisi baru (x2,y2) pada citra output. Proses yang tergolong ke dalam operasi geometri di antaranya adalah rotated, resized (scale), cropped, flipped (reflect), dan translated.
## OPERASI GEOMETRIX CITRA
Operasi geometri adalah proses perubahan hubungan spasial antara setiap pixel pada sebuah citra. Operasi geometri memetakan kembali pixel citra input dari posisi awal (x1,y1) ke posisi baru (x2,y2) pada citra output. Proses yang tergolong ke dalam operasi geometri di antaranya adalah rotated, resized (scale), cropped, flipped (reflect), dan translated.
### A. Rotated
Rotasi merupakan suatu transformasi geometri memindahkan nilai-nilai pixel dari posisi awal menuju ke posisi akhir yang ditentukan melalui nilai variabel rotasi sebesar θ derajat terhadap sudut 0 derajat atau garis horizontal dari citra.
Proses rotasi dapat dilakukan dengan rumus sebagai berikut:
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhArp1ogJ9mv2u-7yKx0krVJ19CELfMidzhl_SvvVhgWZhLwOTSFqqM3_yww8HIr2Wqk5VwaYRqBr76Ih-N99V95R58psOCooIa7pzU2CSeriHbxgKZxiNRKt_I3-lx1nN83OqYD4_PwL4/s1600/rotasi.jpg)

Di mana (x0,y0) adalah koordinat titik pusat dari citra input dan θ adalah sumbu putar. Sumbu putar pada umumnya memiliki arah putar searah jarum jam dengan garis horizontal. Seperti halnya operasi translasi, hasil perhitungan posisi hasil rotasi dapat memberikan nilai di luar batas citra output (apabila ukuran citra outputsama dengan citra input). Untuk kasus seperti itu, ada beberapa implementasi yang membiarkan nilai pixel tersebut tanpa dipetakan ulang dan ada yang memetakan ke citra output sehingga menyebabkan ukuran citra membesar.

### Penjelasan Kode Program Rotated - Cara 1
Pada program ini, saya menggunakan OpenCV untuk membaca gambar 'objek.jpg' dan mengkonversi warna dari BGR ke RGB. Saya mengatur sudut rotasi sebesar 45 derajat dan menghitung pusat rotasi berdasarkan lebar dan tinggi gambar. Kemudian, saya melakukan rotasi pixel demi pixel dengan menggunakan persamaan transformasi geometri untuk rotasi. Hasil rotasi disimpan dalam citra baru cgr2. Setelah itu, saya menampilkan citra asli dan citra hasil rotasi menggunakan matplotlib.

### Penjelasan Kode Program Rotated - Cara Alternatif
Program ini menggunakan metode alternatif untuk melakukan rotasi gambar menggunakan fungsi bawaan OpenCV, cv2.getRotationMatrix2D dan cv2.warpAffine. Saya menghitung matriks transformasi rotasi berdasarkan pusat rotasi dan sudut rotasi yang telah ditentukan sebelumnya. Setelah mendapatkan matriks rotasi, saya menerapkan transformasi ini ke gambar menggunakan cv2.warpAffine dan menyimpan hasilnya dalam cg4. Sama seperti sebelumnya, hasil rotasi ditampilkan menggunakan matplotlib.




## B. Resized (Scale)
Penskalaan adalah sebuah operasi geometri yang memberikan efek memperbesar atau memperkecil ukuran citra input sesuai dengan variabel penskalaan citranya. Ukuran baru hasil penskalaan didapat melalui perkalian antara ukuran citra input dengan variable penskalaan. Proses penskalaan dapat dilakukan dengan rumus:
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEinwCbL8LktcHJ2Btm8E0QxxLpQCbMlnaPAGDNreKky1YG9h_0JQQTcWUYOLNF7u-10D1f_RLyVYKo29_C9uu554CPmr9M8_sNjKiqyaZnnNJNt5MWS4k4G7KFHnAZEo3plKEdgSt7SdpU/s1600/Penskalaan.jpg)

Di mana (Pi ,Li) adalah ukuran citra input, (Po, Lo) adalah ukuran citra output, dan ( Sp , Si ) adalah variabel penskalaan yang diinginkan. Jika variabel penskalaan bernilai lebih besar dari 1 maka hasil penskalaannya akan memperbesar ukuran citra, sebaliknya apabila variabel penskalaannya lebih kecil dari 1 maka hasilnya akan memperkecil ukuran citra.

### Penjelasan Kode Program Resized (Scale) - Cara 1
Pada bagian ini, saya menggunakan OpenCV untuk membaca gambar dan mengkonversi warnanya. Saya menentukan faktor skala untuk menyekalakan gambar, dengan faktor skala horizontal sx sebesar 0.5 dan faktor skala vertikal sy sebesar 1. Saya menghitung dimensi baru untuk gambar hasil sesuai dengan faktor skala yang telah ditentukan. Setelah itu, saya melakukan operasi penyekalaan dengan memproyeksikan piksel-piksel dari gambar asli ke gambar hasil dengan cara membagi koordinat piksel asli dengan faktor skala yang sesuai. Hasil penyekalaan ditampilkan menggunakan matplotlib.

### Penjelasan Kode Program Resized (Scale) - Cara Alternatif
Program alternatif ini menggunakan fungsi cv2.resize dari OpenCV untuk menyekalakan gambar dengan faktor skala 2 kali lipat, baik secara horizontal maupun vertikal. Saya menggunakan interpolasi cv2.INTER_LINEAR untuk menghasilkan gambar yang lebih halus setelah penyekalaan. Hasil penyekalaan ditampilkan menggunakan matplotlib.
## C. Cropped
Cropping adalah memotong satu bagian
dari citra sehingga diperoleh citra yang
berukuran lebih kecil. Operasi ini pada dasarnya adalah operasi translasi, yaitu menggeser koordinat titik citra. Cropping memiliki rumus sebagai berikut:
- x' = x - xL untuk x = xL sampai xR
- y' = y - yT untuk y = yT sampai yB

(xL,yT) dan (xR,yB) adalah koordinat titik pojok kiri atas dan pojok kanan bawah citra yang
akan di-crop. Ukuran citra menjadi : 
- w' = xR - xL
- h' = yB - YT

### Penjelasan Kode Program Cropped - Cara 1
Pada implementasi ini, saya menentukan area yang akan dipotong dari gambar asli dengan menentukan koordinat x dan y pada gambar. Saya membuat citra baru cgc dengan dimensi sesuai dengan area yang dipotong, dan mengisi citra tersebut dengan piksel-piksel dari gambar asli sesuai dengan koordinat yang telah ditentukan. Hasil pemotongan ditampilkan menggunakan matplotlib.

### Penjelasan Kode Program Cropped - Cara Alternatif
Program alternatif ini menggunakan metode potongan langsung dengan memanfaatkan indeksing NumPy pada gambar. Saya menentukan batas-batas koordinat x dan y yang akan dipotong dari gambar asli. Dengan menggunakan indeksing langsung cf[y1:y2, x1:x2], saya mendapatkan citra hasil yang merupakan potongan dari gambar asli. Hasil pemotongan ditampilkan menggunakan matplotlib.



## D. Flipped (Reflect)
Refleksi atau pencerminan adalah proses pengolahan citra secara geometri dengan memindahkan nilai-nilai pixel pada posisi awal (x1,y1) menuju ke posisi baru di (x2,y2) pada citra output sesuai dengan posisi pencerminan. Posisi pencerminan ada tiga jenis yaitu pencerminan terhadap sumbu x, pencerminan terhadap sumbu y, dan pencerminan terhadap sumbu x dan y. Pencerminan terhadap sumbu x di posisi x0 dapat digambarkan dengan rumus berikut ini.
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh8KIw5DIw4xzshJ-o15GC0Y4swNfQEFk1eI61jfi3nAlOC2xjfCYgMvCjraLkw4Ie8r4nojyTn7Gy07gmOG97yehzHDDB8Ixa_m5Gx1V0zj8fbNQWGScFgbwNeSBBUvmDaod-Rhgr69_Q/s1600/refleksi.jpg)

Sedangkan untuk pencerminan terhadap sumbu y di posisi y0 adalah:
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOAVmpsRV7vQUokE_U1zrHuK8rIR44H4gWEDdaiUjUbEqd3fgdwOo12SNjJCQyVpn2SKT16iPD577U_6FkMLv4YTZ6ErPByb6nh8CC_LKvtveMvJ9g4J9yEkA2rT7V3Xpnf87eUPHSYRQ/s1600/refleksi+2.jpg)

Dan untuk pencerminan yang dilakukan terhadap kedua sumbu baik  x dan y di posisi (x0,y0) adalah:
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg2z5g6PlvqwLadcVeUoXBhrO3Db2PfF49UqVSEuRGgTek-_OHv9S3TKW-uB4RO4cTfobl5w4adkRtgjY5V1bfoKgrQh3Y836qTWxgXxZqGVr-JF4C_irGF_viQ6JAy_RJ7Oo5ps4Fo9UE/s1600/refleksi+3.jpg)

### Penjelasan Kode Program Flipped (Reflect) - Cara 1
Pada bagian ini, saya melakukan operasi flipping terhadap gambar menggunakan pendekatan matriks transformasi langsung. Saya membuat gambar output cgf dengan ukuran yang sama seperti gambar asli dan mengisi piksel-pikselnya dari gambar asli yang sudah di-flip sesuai dengan koordinat yang sesuai. Pada bagian ini saya mencetak output pada pencerminan terhadap sumbu x. Jika ingin melakukan pencerminan terhadap sumbu y maka sintax yang telah ditandai dirubah agar tidak dalam bentuk komentar.

### Penjelasan Kode Program Flipped (Reflect) - Cara Alternatif
Program alternatif ini menggunakan fungsi cv2.flip dari OpenCV untuk melakukan flipping pada gambar. Saya dapat memilih untuk melakukan flipping terhadap sumbu x dengan cv2.flip(im1, 1) atau terhadap sumbu y dengan cv2.flip(im1, 0). Hasil flipping ditampilkan menggunakan matplotlib.

## E. Translated
Operasi translasi adalah memindahkan setiap elemen pixel citra input ke posisi baru pada citra output di mana dimensi dari kedua citra (citra masukan dan citra output) pada umumnya adalah sama. Posisi baru dari suatu pixel ditentukan dari nilai variabel translasi (p,q). Secara umum operasi translasi melakukan perubahan dengan cara menambahkan koordinat awal dengan nilai variabel translasi.
![App Screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgh7WF6TEJKA0Y4hHPIUWXDQcdNOP6pp_vyr0sW1GeIE10XBoVEgU47yXdIoPMgjyd_Yon9GHmYFA_p-ITSju_Q-hueVh6RPXjICPtUeStbzFZNBtilsYBUPwWBOQ1Eoa4WXRGi4cxYrzA/s1600/translasi.jpg)

Jika ukuran citra output diset sama dengan citra input maka bila terdapat posisi hasil yang berada di luar batas citra output, pixel tersebut tidak dipetakan. Untuk posisi citra output yang tidak memiliki nilai pixel diset dengan nilai 0 atau warna hitam.

### Penjelasan Kode Program Translated - Cara 1
Pada bagian ini, saya melakukan operasi translasi pada gambar menggunakan pendekatan langsung dengan memproyeksikan setiap piksel dari gambar asli ke posisi yang baru sesuai dengan variabel translasi sx dan sy. Saya memastikan bahwa piksel hasil translasi tetap berada di dalam batas gambar asli, dan jika piksel translasi keluar dari batas, saya mengisi dengan warna hitam. Hasil translasi ditampilkan menggunakan matplotlib.

### Penjelasan Kode Program Translated - Cara Alternatif
Program alternatif ini menggunakan fungsi cv2.warpAffine dari OpenCV untuk melakukan translasi pada gambar. Saya menentukan matriks translasi M dengan menggunakan variabel sx dan sy, lalu menerapkan matriks ini pada gambar menggunakan cv2.warpAffine. Hasil translasi ditampilkan menggunakan matplotlib.