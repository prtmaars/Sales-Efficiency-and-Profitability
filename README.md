# Sales Efficiency and Profitability Analysis
Talent Growth Data Analysis Study Case ✨

## Project Overview
Proyek ini merupakan bagian dari asesmen studi kasus yang diberikan oleh Talent Growth untuk menganalisis performa penjualan dengan menggunakan data historis transaksi dari 1 Januari 2020 hingga 31 Maret 2021. Studi kasus ini mencakup berbagai atribut data seperti revenue, cost, commission, count, dan atribut lain yang relevan untuk mengevaluasi efisiensi dan profitabilitas operasional. Tujuan utama analisis ini adalah untuk mengidentifikasi peluang peningkatan profit, menentukan strategi optimal, dan memberikan dasar bagi pengambilan keputusan untuk keberlanjutan usaha.

## Problem Understanding
Proyek ini berfokus pada delapan pertanyaan utama yang dirancang untuk menggali wawasan mendalam mengenai performa penjualan, profitabilitas, dan keberlanjutan usaha. Berikut adalah daftar masalah yang akan dianalisis:
1. Analisis 2 channel yang menurut Anda memiliki performa penjualan paling baik.
Penilaian ini bertujuan untuk mengidentifikasi dua kanal penjualan yang memberikan kontribusi terbesar terhadap pendapatan dan profit perusahaan. Informasi ini akan digunakan untuk mengoptimalkan strategi pemasaran dan alokasi sumber daya pada kanal yang paling efektif.
2. Analisis 2 channel yang menurut Anda memiliki performa penjualan paling buruk.
Dengan mengevaluasi kanal penjualan yang kurang performa, perusahaan dapat memahami faktor-faktor penyebab penurunan kinerja, seperti rendahnya minat konsumen, biaya tinggi, atau kurangnya promosi. Hasil analisis ini dapat membantu merancang strategi perbaikan atau keputusan untuk menghentikan penggunaan kanal tertentu.
3. Analisis top 2 industri yang paling profitable untuk perusahaan ini.
Analisis ini bertujuan untuk menentukan dua industri yang memberikan keuntungan terbesar bagi perusahaan. Informasi ini dapat digunakan untuk memperkuat kerja sama strategis dengan industri-industri tersebut dan memperluas jangkauan layanan pada sektor yang menguntungkan.
4. Analisis top 2 kategori yang paling profitable untuk perusahaan ini.
Evaluasi kategori produk yang paling menguntungkan bertujuan untuk mengetahui produk atau layanan yang memberikan margin profit tertinggi. Hasil analisis ini akan membantu perusahaan fokus pada kategori yang memiliki potensi untuk meningkatkan pendapatan secara signifikan.
5. Siapa PIC yang memiliki performa paling baik dari profit yang dihasilkan?
Analisis ini bertujuan untuk mengidentifikasi Person in Charge (PIC) dengan kinerja terbaik dalam menghasilkan profit. Informasi ini dapat menjadi dasar untuk memberikan penghargaan, promosi, atau menjadi contoh praktik terbaik bagi tim lain.
6. Siapa PIC yang memiliki performa paling buruk dari profit yang dihasilkan?
Identifikasi PIC dengan performa terburuk akan membantu perusahaan memahami tantangan yang dihadapi individu tersebut dan mencari solusi, seperti pelatihan tambahan atau evaluasi peran untuk meningkatkan kontribusinya terhadap perusahaan.
7. Analisis bagaimana tren profit pada tahun 2020.
Pemantauan tren profit sepanjang tahun 2020 bertujuan untuk mengevaluasi pola pertumbuhan atau penurunan pendapatan. Analisis ini akan memberikan wawasan penting mengenai periode yang paling menguntungkan, dampak musiman, atau pengaruh kondisi eksternal terhadap performa perusahaan.
8. Apakah Anda menyarankan untuk menutup perusahaan ini?
Berdasarkan hasil analisis keseluruhan, rekomendasi mengenai kelayakan operasional perusahaan akan disampaikan. Hal ini mencakup evaluasi apakah perusahaan masih memiliki potensi untuk berkembang atau lebih baik menghentikan operasinya demi efisiensi sumber daya.


## Data Understanding
Dataset yang digunakan mencakup informasi transaksi penjualan dari berbagai kanal dan mencakup periode 1 Januari 2020 hingga 31 Maret 2021. Dataset ini memiliki atribut utama berikut:
1. date: Tanggal transaksi.
2. channel_id: ID kanal penjualan.
3. category_id: ID kategori produk.
4. supplier_id: ID pemasok.
5. status: Status transaksi.
6. revenue: Pendapatan dari transaksi (dalam satuan mata uang).
7. cost: Biaya yang dikeluarkan untuk transaksi.
8. commission: Komisi yang diterapkan pada transaksi.
9. count: Jumlah unit yang terjual.
Dengan atribut-atribut ini, analisis dilakukan untuk mengevaluasi kanal, kategori, dan pemasok yang paling berkontribusi terhadap profitabilitas, serta memantau pola penjualan yang relevan.

## Data Wrangling
Dataset yang digunakan dalam proyek ini terdiri dari satu file utama, yaitu order.csv, dan lima file pendukung: category.csv, channel.csv, industry.csv, supplier.csv, dan pic.csv. Kelima file pendukung tersebut berfungsi sebagai referensi untuk mencocokkan ID pada file order.csv dengan informasi terkait, seperti kategori produk, kanal penjualan, sektor industri, pemasok, dan penanggung jawab transaksi (PIC). Hal ini memungkinkan pengelompokan data yang lebih terstruktur serta analisis yang lebih terfokus.
Berdasarkan hasil pemeriksaan awal, file order.csv tidak mengandung nilai yang hilang atau data duplikat, yang menunjukkan bahwa data sudah cukup bersih untuk diproses lebih lanjut. Namun, ditemukan sejumlah nilai pada kolom cost yang bernilai negatif. Nilai-nilai ini diidentifikasi sebagai kesalahan penginputan dan diubah menjadi nilai absolut agar tetap relevan untuk proses analisis. Selain itu, terdapat satu data dengan nilai yang sangat jauh dari rata-rata (outlier), yang berpotensi memengaruhi hasil analisis secara signifikan. Oleh karena itu, data outlier tersebut dihapus guna menjaga keakuratan dan validitas hasil analisis.
Profit untuk setiap transaksi dihitung menggunakan formula berikut: Profit = Revenue - Cost - Commission
Di mana Revenue mewakili total pendapatan dari transaksi, Cost adalah biaya terkait dengan produk atau layanan, dan Commission adalah biaya tambahan seperti komisi penjualan atau biaya distribusi. Dengan rumus ini, profit dihitung secara komprehensif untuk mencerminkan keuntungan bersih yang dihasilkan oleh setiap transaksi.
Setelah data dibersihkan, dataset dipisahkan berdasarkan kolom status, yang menunjukkan keberhasilan transaksi. Transaksi dengan status = 1 dianggap berhasil dan disimpan dalam dataset bernama data_success, sementara transaksi dengan status = 0 dianggap gagal dan disimpan dalam dataset data_failed. Proses pemisahan ini bertujuan untuk mengklasifikasikan transaksi berdasarkan keberhasilannya, di mana analisis selanjutnya hanya difokuskan pada data_success. Hal ini dilakukan mengingat keberhasilan transaksi menjadi indikator utama dalam menilai performa penjualan serta profitabilitas perusahaan.

## Analysis & Visualization
1. Analisis 2 channel yang menurut Anda memiliki performa penjualan paling baik.
![Visualisasi 1](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/top5channelprofit.png)
Berdasarkan grafik di atas, dapat diidentifikasi lima kanal penjualan dengan profit tertinggi. Salah satu kanal, yaitu Fashionista, menunjukkan performa yang sangat unggul dengan selisih profit yang signifikan dibandingkan kanal-kanal lainnya. Kanal-kanal tersebut adalah Fashionista, Shoppertize, PhasePayment, Galleria, dan Lendena. Dari lima kanal ini, Fashionista dan Shoppertize menempati posisi dua teratas dengan total profit masing-masing sebesar 295.600.557 dan 71.891.789.
![Visualisasi 1a](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/top5channelrevenue.png)
Pada grafik tambahan, terlihat bahwa kanal Fashionista juga mendominasi dalam hal revenue dengan total pendapatan sebesar 16.579.629.220, jauh melampaui kanal lainnya. Kanal dengan revenue tertinggi kedua adalah Galleria, dengan total revenue mencapai 4.078.605.910. Selain itu, tiga kanal lainnya yang termasuk dalam lima besar dari sisi revenue adalah Lendena, Merchwallet, dan Brite Bank.
Hasil ini menunjukkan bahwa Fashionista tidak hanya menjadi yang terdepan dalam profitabilitas tetapi juga dalam kontribusi pendapatan, yang menjadikannya kanal strategis bagi perusahaan. Demikian pula, Shoppertize menonjol sebagai kanal dengan profitabilitas yang layak untuk mendapatkan perhatian lebih lanjut dalam strategi penjualan.

2. Analisis 2 channel yang menurut Anda memiliki performa penjualan paling buruk.
![Visualisasi 2](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/bot5channelprofit.png)
Berdasarkan analisis profit, terdapat lima kanal penjualan dengan performa terendah, yaitu Cashured, ZenGrocery, Paid.ly, Merchwallet, dan Dinostore. Dari kelima kanal ini, Cashured mencatatkan profit negatif terbesar dengan nilai -3.311.437.230, diikuti oleh ZenGrocery dengan nilai -152.250.756. Hasil ini menunjukkan bahwa kedua kanal tersebut memiliki masalah mendasar yang signifikan, baik dari sisi efisiensi operasional maupun strategi pemasaran, sehingga perlu mendapat perhatian khusus untuk perbaikan.
![Visualisasi 2a](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/bot5channelrevenue.png)
Sementara itu, jika dilihat dari sisi revenue, kanal dengan performa terendah adalah Merch and Dish, yang hanya menghasilkan pendapatan sebesar 357.150, diikuti oleh Coinration dengan total revenue sebesar 1.384.860. Tiga kanal lain yang termasuk dalam kategori terendah adalah Metro Bank, Paymentox, dan Psyship.
Performa buruk dari kanal-kanal tersebut dapat menjadi indikator adanya ketidaksesuaian strategi bisnis yang diterapkan, baik dari sisi produk, target pasar, maupun struktur biaya. Untuk meningkatkan kinerja, diperlukan evaluasi menyeluruh terhadap faktor-faktor yang memengaruhi rendahnya profit dan revenue di kanal-kanal tersebut.

3. Analisis top 2 industri yang paling profitable untuk perusahaan ini.
![Visualisasi 3](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/industriesprofit.png)
Berdasarkan analisis profitabilitas, dua industri dengan kinerja paling menguntungkan bagi perusahaan ini adalah Retail dan Banking. Industri Retail menduduki posisi teratas dengan total profit sebesar 300.235.142, diikuti oleh industri Banking dengan profit sebesar 4.301.872. Kedua industri ini menunjukkan kontribusi positif yang signifikan terhadap profitabilitas perusahaan, mengindikasikan bahwa strategi dan operasional pada sektor-sektor tersebut telah berjalan dengan baik dan selaras dengan kebutuhan pasar.
Sebaliknya, beberapa industri lain menunjukkan kinerja yang kurang optimal. Industri seperti Travel mencatatkan kerugian kecil sebesar -171.754, sementara Technology mengalami kerugian lebih besar dengan nilai -10.663.071. Industri E-Commerce dan Finance mencatatkan kerugian terbesar masing-masing sebesar -68.060.048 dan -3.335.103.419. Kerugian ini menunjukkan adanya tantangan signifikan, baik dari sisi efisiensi operasional, penetrasi pasar, maupun daya saing produk atau layanan di sektor-sektor tersebut.

4. Analisis top 2 kategori yang paling profitable untuk perusahaan ini.
![Visualisasi 4](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/top5categoriesprofit.png)
Analisis kategori produk atau layanan mengungkapkan bahwa EMI Payments dan Metro merupakan dua kategori yang memberikan kontribusi profit tertinggi. EMI Payments mencatatkan total profit sebesar 38.781.110, sementara Metro mencatatkan profit sebesar 32.676.337. Kategori ini berhasil memberikan nilai signifikan bagi perusahaan, menunjukkan efektivitas strategi penjualan dan operasional di bidang tersebut.
Selain itu, kategori lain seperti Credit Card Bill (22.338.372), Digital Cable TV (21.615.151), dan Game Voucher (20.377.092) juga menunjukkan performa yang kuat. Kinerja positif ini mencerminkan adanya potensi pertumbuhan lebih lanjut melalui pengembangan layanan tambahan atau peningkatan pengalaman pelanggan di kategori tersebut.

5. Siapa PIC yang memilki performa paling baik dari profit yang dihasilkan?
![Visualisasi 5](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/top3picprofit.png)
Analisis terhadap performa individu menunjukkan bahwa Lala Lailasari adalah PIC dengan kontribusi profit terbesar, mencapai 281.765.322. Di posisi kedua, Fitriani Alika Hastuti berhasil mencatatkan profit sebesar 63.478.859, diikuti oleh Fathonah Hartati dengan profit sebesar 32.592.812. Kontribusi mereka mencerminkan keahlian yang luar biasa dalam mengelola operasional dan memastikan keberhasilan transaksi yang menguntungkan perusahaan. Kinerja mereka dapat dijadikan acuan untuk mengidentifikasi praktik terbaik yang dapat diterapkan oleh PIC lainnya.

6. Siapa PIC yang memilki performa paling buruk dari profit yang dihasilkan?
![Visualisasi 6](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/bot3picprofit.png)
Di sisi lain, beberapa PIC menunjukkan performa yang kurang memuaskan, dengan Ismail Salahudin menjadi PIC dengan kerugian terbesar, mencatatkan nilai negatif sebesar -3.307.028.607. Rahayu Paulin Wulandari berada di posisi kedua dengan kerugian sebesar -197.202.282, diikuti oleh Dewi Rachel Anggraini dengan kerugian sebesar -3.305.881. Data ini mengindikasikan perlunya evaluasi terhadap faktor-faktor yang menyebabkan performa buruk, termasuk kemungkinan adanya masalah pada proses operasional, strategi penjualan, atau pengelolaan sumber daya. Hal ini penting untuk segera ditangani guna mengurangi dampak negatif terhadap profit perusahaan secara keseluruhan.

7. Analisis bagaimana tren profit pada tahun 2020.
![Visualisasi 7](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/2020monthlytrends.png)
Berdasarkan grafik tren profit bulanan tahun 2020, terlihat bahwa profit perusahaan mengalami fluktuasi yang cukup tajam sepanjang tahun tersebut. Pada awal tahun, yakni Januari dan Februari, profit berada dalam zona positif. Namun, memasuki bulan Maret hingga Juli, profit mengalami penurunan drastis dan mencatatkan kerugian terbesar pada bulan Juli.
Penurunan ini sangat mungkin dipengaruhi oleh dampak pandemi COVID-19, yang mulai meluas pada awal tahun 2020. Pandemi memberikan tekanan besar pada berbagai sektor ekonomi, termasuk industri yang menjadi basis operasi perusahaan. Kebijakan pembatasan sosial, penurunan daya beli masyarakat, dan gangguan rantai pasokan global menjadi faktor signifikan yang memengaruhi penurunan kinerja perusahaan.
Meskipun demikian, grafik menunjukkan adanya pemulihan profit setelah bulan Juli, dengan lonjakan yang signifikan pada bulan Agustus. Pemulihan ini mungkin disebabkan oleh adaptasi perusahaan terhadap situasi pandemi, seperti pengalihan fokus pada channel yang lebih resilient atau perubahan strategi operasional untuk menekan kerugian. Tren ini terus menunjukkan perbaikan hingga akhir tahun, meskipun masih jauh dari level profit di awal tahun.
Analisis ini menunjukkan bahwa meskipun dampak pandemi sangat signifikan, ada potensi untuk bangkit jika perusahaan mampu beradaptasi dengan cepat terhadap perubahan lingkungan bisnis.

8. Apakah Anda menyarankan untuk menutup perusahaan ini?
![Visualisasi 8](https://raw.githubusercontent.com/prtmaars/Sales-Efficiency-and-Profitability/master/images/alltimemonthlytrends.png)
Berdasarkan grafik profit sepanjang waktu dan analisis tambahan dari performa channel, kategori, dan industri, keputusan untuk menutup perusahaan bukanlah langkah yang tepat untuk diambil saat ini. Meskipun perusahaan mencatatkan kerugian kumulatif yang signifikan, terutama dari channel seperti Cashured dan ZenGrocery serta sektor industri seperti E-Commerce dan Finance, masih terdapat potensi yang dapat dimanfaatkan untuk memperbaiki kondisi perusahaan.
Beberapa indikator positif yang mendukung keberlanjutan perusahaan adalah performa yang kuat dari channel Fashionista dan kontribusi profit yang konsisten dari kategori seperti EMI Payments dan Metro. Selain itu, industri Retail tetap menjadi salah satu sektor yang profitable, meskipun ada tekanan dari sektor lainnya.
Kerugian besar yang dialami juga harus dianalisis lebih dalam, terutama dengan mempertimbangkan dampak pandemi COVID-19 sebagai faktor eksternal yang tidak dapat dihindari. Banyak perusahaan menghadapi situasi serupa pada tahun 2020 akibat penurunan permintaan pasar, gangguan operasional, dan ketidakpastian ekonomi global.

## Conclusion
Berdasarkan hasil analisis, perusahaan menunjukkan performa yang bervariasi di berbagai kanal penjualan, kategori, dan industri. Kanal Fashionista dan Shoppertize terbukti memberikan kontribusi profit terbesar, sementara kanal seperti Cashured dan ZenGrocery menunjukkan performa yang sangat buruk, bahkan merugikan perusahaan. Industri Retail dan Banking menjadi sektor yang paling menguntungkan, sedangkan sektor E-Commerce dan Finance mencatatkan kerugian signifikan. Tren profit tahun 2020 menunjukkan adanya dampak besar dari pandemi COVID-19, dengan penurunan tajam di tengah tahun, diikuti oleh pemulihan yang stabil hingga akhir tahun. Meskipun terdapat kerugian kumulatif yang besar, indikator positif seperti performa kanal unggulan dan tren pemulihan memberikan dasar kuat untuk mempertahankan dan mengembangkan perusahaan lebih lanjut. Diperlukan strategi yang fokus pada optimalisasi kanal dan kategori yang profitable, adaptasi terhadap perubahan pasar, serta pengelolaan efisiensi untuk memastikan keberlanjutan dan pertumbuhan perusahaan di masa depan.

## Recommendation
Tren pemulihan profit pada akhir tahun memberikan indikasi bahwa perusahaan memiliki kemampuan untuk beradaptasi dengan perubahan pasar dan mulai menunjukkan tanda-tanda kebangkitan. Hal ini memberikan dasar yang kuat untuk mengambil langkah-langkah strategis guna memperbaiki kinerja perusahaan secara keseluruhan dan meningkatkan profitabilitas di masa mendatang. Ke depan, perusahaan disarankan untuk menerapkan strategi berikut:
1. Fokus pada channel dan kategori yang profitable
   Mengalokasikan lebih banyak sumber daya, baik berupa investasi finansial, tenaga kerja, maupun inovasi teknologi, pada channel seperti Fashionista dan kategori EMI Payments yang telah terbukti memberikan kontribusi signifikan terhadap profit perusahaan. Selain itu, sektor Retail, yang terus konsisten menghasilkan keuntungan, perlu dimaksimalkan dengan strategi pemasaran yang lebih agresif dan pendekatan berbasis data untuk mengidentifikasi peluang ekspansi.
2. Mengurangi kerugian pada channel atau sektor yang underperforming
   Channel seperti ZenGrocery, yang terus menunjukkan kinerja buruk tanpa potensi perbaikan, memerlukan evaluasi strategis yang mendalam. Langkah-langkah seperti perombakan model bisnis, penggabungan dengan kanal lain, atau bahkan penghentian operasional harus dipertimbangkan jika channel tersebut terus membebani keuangan perusahaan tanpa prospek pengembalian investasi yang layak.
3. Adaptasi terhadap perubahan pasar
   Dalam era pasca-pandemi, perusahaan harus lebih responsif terhadap dinamika pasar dengan memanfaatkan peluang di sektor digital. Langkah ini dapat mencakup transformasi digital, peningkatan efisiensi operasional, dan pengembangan strategi omnichannel untuk memenuhi kebutuhan konsumen yang terus berubah. Peningkatan investasi pada teknologi analitik data juga dapat membantu perusahaan memahami pola konsumen dan menyesuaikan penawaran produk atau layanan secara real-time.
4. Diversifikasi risiko
   Untuk mengurangi ketergantungan pada sektor atau channel tertentu, perusahaan perlu mengembangkan portofolio produk atau layanan baru yang relevan dengan kebutuhan pasar. Diversifikasi ini tidak hanya meningkatkan stabilitas perusahaan di masa depan, tetapi juga membuka peluang baru untuk pertumbuhan dan inovasi.

___
