# yang belum

**Ilmu baru yang belum ada di kode**

Frame weekly dengan 3 boxes. Ini instruksi yang paling sering diulang Eliz: buka weekly, gambar 3 box (supply atas, no-trade tengah, demand bawah). Engine hanya punya 4H (21 hari) dan 1D (120 hari). Frame 1W perlu ditambahkan sebagai konteks HTF.
Absorption dan volume sebagai konfirmasi. PDF 2 menyebut absorption (volume tinggi tapi harga tidak lanjut) sebagai tanda ada pihak yang menyerap order. Engine belum memakai volume untuk sinyal sama sekali. Bisa ditambahkan flag: sweep dengan volume di atas rata-rata 20 candle dan close kembali ke dalam range.
Layer trigger timeframe lebih kecil. PDF 2 menyebut turun ke H4/H1/15m untuk trigger. Engine berhenti di 4H dan 12H. Untuk setup scalp altcoin, perlu layer 1H.
Pisahkan investasi spot dari trading. Post TAO di PDF 1 sangat tegas: spot itu investasi jangka panjang yang siap turun ke nol, tanpa stop, dan itu bukan trading. Engine justru memasukkannya sebagai tipe “spot (SL lebar)” dengan SL sampai 30% di daftar setup. Sebaiknya dibuat kategori terpisah, atau dikeluarkan dari daftar setup.
PDF 1 bisa jadi data uji. Isinya sekitar 25 post dengan tanggal, koin, level, dan hasil. Contohnya SOL 15 Agustus (“73–75 hold, lalu 80, lalu 85+”), yang kemudian tercatat hit 80 pada 19 Agustus. Ini bisa dipakai untuk mengecek apakah engine menghasilkan setup yang sama dengan yang Eliz tandai.

**Yang perlu direvisi**

Label “Dari Eliz” di tab Strategi terlalu lebar. Item berikut tidak ada di dua PDF: Three Tap/Three Top, Double Deviation, Wolf, SL ketat 3–5% dan 10–15%, ambil profit bertahap 60–80%, dan berita FOMC sebagai noise. Item-item ini sebaiknya diberi label “Tafsiran” kecuali kamu punya sumber lain. Wolf dan Double Deviation paling perlu dicek.
Definisi Monday Range belum jelas. Kode memakai seluruh hari Senin dalam UTC. Grok menulis “sering antara buka Eropa–AS”, yang merupakan rentang sesi berbeda. Keduanya belum terverifikasi. Pilih salah satu dan tandai sebagai tafsiran.
Klaim “Eliz tidak pernah memprediksi” bertentangan dengan PDF 1. Di sana ada “I continue to expect the upward trend to continue” dan “could see a spike towards 85–86k”. Lebih akurat: ia bereaksi pada level, tapi sering menyampaikan skenario arah. Engine boleh menampilkan skenario, asal jangan dilabeli sebagai metode yang “tidak memprediksi”.
Klasifikasi scalp vs swing memakai lebar SL. Eliz membedakannya dari timeframe dan lama hold. Kalau dipertahankan, tandai sebagai tafsiran.
Sweep di tengah range masih lolos. Filter keep hanya membuang bo, zone, dan wolf di tengah range. Mungkin perlu membuang semua sinyal di tengah kecuali sweep yang benar-benar di tepi.

**belum menjalankannya dengan data Binance asli karena sandbox-ku tidak bisa menjangkau Binance.**

**Dugaan yang diuji oleh hasilnya**

Ini dugaan dari membaca kode, belum terbukti.

Eliz sering memakai range lokal 2H atau 1H yang sempit (BTC 28–30 Juli, LTC, ETH), sedangkan engine hanya punya range 4H selama 21 hari dan 1D selama 120 hari. Kalau benar, engine akan menyebut “tengah range” saat Eliz sedang trading di tepi range lokalnya.
Frame mingguan dengan 3 box (FET) memang belum ada di engine.
Volume dan absorption belum dipakai sama sekali.

**Yang belum kuubah**

Wolf, Double Deviation, dan lebar SL tidak kusentuh. Short Wolf 1D masih jadi setup terbaik di FLOKI, BTC-0712, dan SOL-0625, dan semuanya dinilai berbeda dari Eliz. Kalau v2 dan v2t sudah stabil, itu kandidat berikutnya, dan kuusulkan juga batas jarak entry untuk semua jenis setup, bukan hanya tlb.

**Yang belum ada, dan perlu diuji**
Invalidasi berbasis close. Ini yang paling penting. Engine menaruh SL di bawah wick sweep, dan itulah sebab sebagian besar SL cepat di hasil uji kita. Varian baru (v4) akan menaruh SL di bawah level invalidasi struktural (close), lalu dibandingkan dengan v1 pada dataset dan pembanding acak. Konsekuensinya jelas: SL lebih lebar, jadi R per trade lebih kecil.
Rencana bertingkat. Setiap rencana Eliz punya entry (reclaim), konfirmasi (break dan close), target makro, dan invalidasi. Engine baru punya TP1 sampai TP3 dan SL. Aku akan menambahkan field konf dan inval ke plan.
Ichimoku cloud. Chart SOL dan SUI di kedua PDF maupun Discord memakai awan Ichimoku. Ini bertentangan dengan catatan PDF 2 bahwa Eliz hampir tidak memakai indikator. Mungkin dipakai hanya sebagai konteks tren, atau catatan PDF 2 sudah usang. Yang bisa diuji: filter “harga di atas awan untuk long, di bawah untuk short”.
Zona makro manual. Zona seperti BTC 65K sampai 68K tidak bisa diturunkan dari data. Ini perlu input dari pengguna, lalu sistem menilai posisi harga terhadap zona itu.
Kategori asimetris. Setup seperti SUI dan TAO sebaiknya masuk kategori terpisah, sama seperti investasi spot, dengan SL lebar dan target jauh. Jangan dicampur dengan setup trading biasa.
Definisi double deviation perlu dicek. Diagram mensyaratkan urutan: deviasi pertama lebih dalam, lalu reclaim, lalu deviasi kedua lebih dangkal, lalu reclaim lagi. Aku belum memeriksa apakah dd di engine mensyaratkan semua itu. Ini perlu dicek di kode sebelum mengklaim engine sudah sesuai.


**yang belum ada**
Breakout trendline adalah pola baru: dua close melewati garis, breakout masih baru, harga belum jauh dari garis. Ini muncul di 5 dari 21 post Eliz (ALICE, TURBO, FLOKI, FET, SOL) dan v1 tidak punya pola itu.
Kotak S/R weekly dihitung dari pivot weekly yang dihormati berulang kali. Ini belum tampil di UI, hanya masuk ke penilaian level.

**Peringatan**
Angka ambangnya tebakan. Jendela 48 jam, batas “aktif” 0,5%, dan jarak breakout 2 ATR belum diuji pada data asli. Kalau hasilnya buruk, aku ubah dari angka itu.
Perkiraan hasil nyata. Short palsu SOL-0815, LTC, dan SOL-0625 seharusnya hilang, tapi itu baru bisa jadi “tidak terdeteksi”, bukan otomatis jadi long yang benar. Mendapat setup long yang benar butuh pola baru.
Yang sengaja tidak kuubah. Lebar SL, Wolf, dan Double Deviation tidak kusentuh. XPL kena SL satu jam setelah entry lalu naik 30%, tapi satu kasus tidak cukup untuk melonggarkan SL tanpa data.
Sampel kecil. 18 entri dan 100 sampel acak tetap menghasilkan angka yang berisik. Selisih satu-dua poin antara v1 dan v2 belum berarti apa-apa.

**Yang belum kuubah**

Wolf, Double Deviation, dan lebar SL tidak kusentuh. Short Wolf 1D masih jadi setup terbaik di FLOKI, BTC-0712, dan SOL-0625, dan semuanya dinilai berbeda dari Eliz. Kalau v2 dan v2t sudah stabil, itu kandidat berikutnya, dan kuusulkan juga batas jarak entry untuk semua jenis setup, bukan hanya tlb.

Atau kalau kamu ingin berhenti di sini, pakai v1 sebagai engine di situs, dan kita catat bahwa engine ini belum punya edge yang terbukti (rata-rata sekitar 0,1R di pembanding acak dengan dominasi trade besar, dan median -1R).

**v3 belum diuji dengan data Binance asli.**

**Yang belum selesai:**

Klaster independen dan bootstrap. Ini dijalankan dengan Python dan hasilnya sudah ada: 79 klaster dari 91 trade. Selang kepercayaan selisih rata-rata R mencakup nol, sekitar -0,26 sampai 0,59. Median selisihnya positif, sekitar 0,33 sampai 1,91, tapi itu bergantung pada banyak trade bernilai nol.
Harness JS. Perubahan di validate.mjs dan engine.mjs baru sampai tahap sintaks lolos. Belum ada uji fungsional, dan belum diuji dengan server palsu. Jadi v5 dan v6 belum divalidasi.
Perbaikan tab Uji belum kulakukan, sehingga layar belum menampilkan v5, v6, atau selang kepercayaan.

**hasilnya lebih rapuh dari kesan angka itu:**

Sampel tumpang tindih. 91 trade ternyata hanya 79 klaster independen. Selisih rata-rata per klaster +0,18R dengan selang 95% dari -0,24 sampai +0,57, jadi belum terbukti berbeda dari nol. Hanya median yang lebih baik secara statistik.
Dua peristiwa mendominasi. SOL menyumbang +13,7R dari total selisih +13,5R. Tanpa SOL, selisihnya hampir nol. ALICE menyumbang -22,6R, dengan dua sampel kembar dari satu peristiwa (-11,7R dan -10,9R).
Cara kerjanya: dari 58 trade yang kena SL di v1, 20 selamat di v4 dan rata-rata +1,93R (19 positif). Sisanya 38 tetap kena stop, tapi kini rata-rata -2,19R, bukan -1R. Keuntungan dan kerugiannya hampir saling menutup.
Konsisten arahnya. Kedua paruh periode sama-sama positif (+6,2R dan +7,3R).

**Yang perlu kamu tahu tentang v1**

v1 juga belum terbukti punya edge. Median trade-nya -1R, dan rata-rata yang sedikit positif (0,04R di seed 8, 0,23R di seed 7) bergantung pada beberapa trade besar dan posisi yang belum selesai. Jadi engine ini sebaiknya dipakai sebagai alat analisis, bukan sinyal trading.

Satu catatan metodologis: batas 2R kupilih setelah melihat seed 7, lalu diuji lagi di seed 8. Seed 8 pada dasarnya sudah menjadi uji lepas, dan keduanya tetap gagal. Mengubah angka stop lagi berdasarkan dua seed ini hanya akan menjadi overfitting.

**Yang belum kuubah**

Wolf, Double Deviation, dan lebar SL tidak kusentuh. Short Wolf 1D masih jadi setup terbaik di FLOKI, BTC-0712, dan SOL-0625, dan semuanya dinilai berbeda dari Eliz. Kalau v2 dan v2t sudah stabil, itu kandidat berikutnya, dan kuusulkan juga batas jarak entry untuk semua jenis setup, bukan hanya tlb.

**Versi baru belum mengalahkan v1.**
Angka
Dataset (18 dinilai):
v1: skor 50%, rata-rata 2,49R, tanpa trade terbaik 0,03R
v2 (tlb mati): skor 50%, rata-rata 1,20R, tanpa trade terbaik -0,15R
v2t (tlb aktif): skor 47%, rata-rata 1,28R, tanpa trade terbaik 0,08R

Pembanding acak (200 sampel):
v1: rata-rata 0,28R, tanpa terbaik 0,14R
v2: rata-rata 0,10R, tanpa terbaik -0,05R
v2t: rata-rata 0,06R, tanpa terbaik -0,07R

Pada 26 sampel yang setup-nya berbeda antar versi, v1 rata-rata 1,62R (median -0,13R), sedangkan v2 dan v2t sama-sama -0,6R sampai -0,7R dengan median -1R.

Yang bisa disimpulkan
1. v2 dan v2t sama-sama kalah dari v1 pada sampel yang berbeda. Ini bagian terpentingnya. Versi baru membuang setup yang ternyata sebagian besar menang di v1 (misalnya setup Monday sweep yang dulu valid). Setup yang tersisa malah lebih sering kena SL. Jadi mematikan short Monday High yang “palsu” ternyata juga membuang long yang benar.

2. Perbaikan tlb tidak membuat tlb menguntungkan. Di pembanding acak, setup tlb dari v2t selalu gagal atau tidak terisi di sampel yang kulihat (misalnya LTC, ALICE, SOL, ETH). Retest yang diperketat mengurangi kesalahan jarak, tapi tidak membuat pola ini sebuah edge. Karena itu tlb tetap mati.

3. Angka dataset tidak bisa membedakan versi. Skor 47% sampai 50% sama dengan selisih satu atau dua poin dari 18 penilaian. Yang berbeda hanya kualitas simulasi, dan itu didominasi satu-dua trade besar (PHA +13R, ALICE, FET). Tanpa 18 sampel itu, rata-rata v1 juga turun.

4. Kelemahan penilaian dataset yang kelihatan jelas: ETH-0717 dan BTC-0712 dinilai “beda” di semua versi, tapi itu karena engine memberi short di tempat Eliz diam atau bullish, dan itu memang perbedaan nyata. Sebaliknya BTC-0729 kini “sama” di semua versi, dan itu juga nyata.

**Yang belum ada, dan perlu diuji**
Invalidasi berbasis close. Ini yang paling penting. Engine menaruh SL di bawah wick sweep, dan itulah sebab sebagian besar SL cepat di hasil uji kita. Varian baru (v4) akan menaruh SL di bawah level invalidasi struktural (close), lalu dibandingkan dengan v1 pada dataset dan pembanding acak. Konsekuensinya jelas: SL lebih lebar, jadi R per trade lebih kecil.
Rencana bertingkat. Setiap rencana Eliz punya entry (reclaim), konfirmasi (break dan close), target makro, dan invalidasi. Engine baru punya TP1 sampai TP3 dan SL. Aku akan menambahkan field konf dan inval ke plan.
Ichimoku cloud. Chart SOL dan SUI di kedua PDF maupun Discord memakai awan Ichimoku. Ini bertentangan dengan catatan PDF 2 bahwa Eliz hampir tidak memakai indikator. Mungkin dipakai hanya sebagai konteks tren, atau catatan PDF 2 sudah usang. Yang bisa diuji: filter “harga di atas awan untuk long, di bawah untuk short”.
Zona makro manual. Zona seperti BTC 65K sampai 68K tidak bisa diturunkan dari data. Ini perlu input dari pengguna, lalu sistem menilai posisi harga terhadap zona itu.
Kategori asimetris. Setup seperti SUI dan TAO sebaiknya masuk kategori terpisah, sama seperti investasi spot, dengan SL lebar dan target jauh. Jangan dicampur dengan setup trading biasa.
Definisi double deviation perlu dicek. Diagram mensyaratkan urutan: deviasi pertama lebih dalam, lalu reclaim, lalu deviasi kedua lebih dangkal, lalu reclaim lagi. Aku belum memeriksa apakah dd di engine mensyaratkan semua itu. Ini perlu dicek di kode sebelum mengklaim engine sudah sesuai.

**Yang belum dikerjakan**
Filter Ichimoku. Materi Discord memakainya, dan ini bertentangan dengan catatan PDF 2.
Tampilan “konfirmasi dan invalidasi” di kartu setup. Datanya sudah ada di plan v4, tapi UI belum menampilkannya.
Input zona makro manual, dan kategori setup asimetris (seperti SUI dan TAO).
Aturan double deviation belum kuperiksa terhadap diagram Eliz.

**Yang belum selesai:**
Klaster independen dan bootstrap. Ini dijalankan dengan Python dan hasilnya sudah ada: 79 klaster dari 91 trade. Selang kepercayaan selisih rata-rata R mencakup nol, sekitar -0,26 sampai 0,59. Median selisihnya positif, sekitar 0,33 sampai 1,91, tapi itu bergantung pada banyak trade bernilai nol.
Harness JS. Perubahan di validate.mjs dan engine.mjs baru sampai tahap sintaks lolos. Belum ada uji fungsional, dan belum diuji dengan server palsu. Jadi v5 dan v6 belum divalidasi.
Perbaikan tab Uji belum kulakukan, sehingga layar belum menampilkan v5, v6, atau selang kepercayaan.

**v4 hasilnya lebih rapuh dari kesan angka itu:**

Sampel tumpang tindih. 91 trade ternyata hanya 79 klaster independen. Selisih rata-rata per klaster +0,18R dengan selang 95% dari -0,24 sampai +0,57, jadi belum terbukti berbeda dari nol. Hanya median yang lebih baik secara statistik.
Dua peristiwa mendominasi. SOL menyumbang +13,7R dari total selisih +13,5R. Tanpa SOL, selisihnya hampir nol. ALICE menyumbang -22,6R, dengan dua sampel kembar dari satu peristiwa (-11,7R dan -10,9R).
Cara kerjanya: dari 58 trade yang kena SL di v1, 20 selamat di v4 dan rata-rata +1,93R (19 positif). Sisanya 38 tetap kena stop, tapi kini rata-rata -2,19R, bukan -1R. Keuntungan dan kerugiannya hampir saling menutup.
Konsisten arahnya. Kedua paruh periode sama-sama positif (+6,2R dan +7,3R).

**Yang belum ada, dan perlu diuji**
Invalidasi berbasis close. Ini yang paling penting. Engine menaruh SL di bawah wick sweep, dan itulah sebab sebagian besar SL cepat di hasil uji kita. Varian baru (v4) akan menaruh SL di bawah level invalidasi struktural (close), lalu dibandingkan dengan v1 pada dataset dan pembanding acak. Konsekuensinya jelas: SL lebih lebar, jadi R per trade lebih kecil.
Rencana bertingkat. Setiap rencana Eliz punya entry (reclaim), konfirmasi (break dan close), target makro, dan invalidasi. Engine baru punya TP1 sampai TP3 dan SL. Aku akan menambahkan field konf dan inval ke plan.
Ichimoku cloud. Chart SOL dan SUI di kedua PDF maupun Discord memakai awan Ichimoku. Ini bertentangan dengan catatan PDF 2 bahwa Eliz hampir tidak memakai indikator. Mungkin dipakai hanya sebagai konteks tren, atau catatan PDF 2 sudah usang. Yang bisa diuji: filter “harga di atas awan untuk long, di bawah untuk short”.
Zona makro manual. Zona seperti BTC 65K sampai 68K tidak bisa diturunkan dari data. Ini perlu input dari pengguna, lalu sistem menilai posisi harga terhadap zona itu.
Kategori asimetris. Setup seperti SUI dan TAO sebaiknya masuk kategori terpisah, sama seperti investasi spot, dengan SL lebar dan target jauh. Jangan dicampur dengan setup trading biasa.
Definisi double deviation perlu dicek. Diagram mensyaratkan urutan: deviasi pertama lebih dalam, lalu reclaim, lalu deviasi kedua lebih dangkal, lalu reclaim lagi. Aku belum memeriksa apakah dd di engine mensyaratkan semua itu. Ini perlu dicek di kode sebelum mengklaim engine sudah sesuai.

**Yang belum dikerjakan**
Filter Ichimoku. Materi Discord memakainya, dan ini bertentangan dengan catatan PDF 2.
Tampilan “konfirmasi dan invalidasi” di kartu setup. Datanya sudah ada di plan v4, tapi UI belum menampilkannya.
Input zona makro manual, dan kategori setup asimetris (seperti SUI dan TAO).
Aturan double deviation belum kuperiksa terhadap diagram Eliz.

**Yang belum selesai:**
Klaster independen dan bootstrap. Ini dijalankan dengan Python dan hasilnya sudah ada: 79 klaster dari 91 trade. Selang kepercayaan selisih rata-rata R mencakup nol, sekitar -0,26 sampai 0,59. Median selisihnya positif, sekitar 0,33 sampai 1,91, tapi itu bergantung pada banyak trade bernilai nol.
Harness JS. Perubahan di validate.mjs dan engine.mjs baru sampai tahap sintaks lolos. Belum ada uji fungsional, dan belum diuji dengan server palsu. Jadi v5 dan v6 belum divalidasi.
Perbaikan tab Uji belum kulakukan, sehingga layar belum menampilkan v5, v6, atau selang kepercayaan.

**Yang perlu kamu tahu tentang v1**
v1 juga belum terbukti punya edge. Median trade-nya -1R, dan rata-rata yang sedikit positif (0,04R di seed 8, 0,23R di seed 7) bergantung pada beberapa trade besar dan posisi yang belum selesai. Jadi engine ini sebaiknya dipakai sebagai alat analisis, bukan sinyal trading.
Satu catatan metodologis: batas 2R kupilih setelah melihat seed 7, lalu diuji lagi di seed 8. Seed 8 pada dasarnya sudah menjadi uji lepas, dan keduanya tetap gagal. Mengubah angka stop lagi berdasarkan dua seed ini hanya akan menjadi overfitting.

