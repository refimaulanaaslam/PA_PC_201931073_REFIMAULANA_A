
# Deteksi Plat Nomer

#### REFI MAULANA ASLAM (201931073)

Mendeteksi plat nomor kendaraan merupakan salah satu tugas penting dalam pengenalan pola pada sistem pengawasan lalu lintas, pemantauan parkir, dan aplikasi lainnya. Dalam panduan ini, kami akan menggunakan OpenCV, sebuah library populer untuk pengolahan gambar dan komputerisasi penglihatan, serta Python sebagai bahasa pemrograman utama. Kami akan menjalankannya di lingkungan Jupyter Notebook yang memungkinkan kita untuk menggabungkan kode, hasil visualisasi, dan penjelasan dalam satu dokumen yang interaktif.

Langkah pertama dalam proses deteksi plat nomor kendaraan adalah membaca gambar kendaraan yang akan dianalisis. Dengan menggunakan fungsi cv2.imread(), kita dapat membaca gambar dari sistem file dan menyimpannya ke dalam variabel. Pastikan untuk menentukan path dan nama file gambar kendaraan yang sesuai.

Setelah membaca gambar, kita akan melakukan beberapa langkah praproses pada gambar tersebut. Langkah pertama adalah mengkonversi gambar ke dalam skala abu-abu menggunakan fungsi cv2.cvtColor(). Hal ini dilakukan untuk mengurangi kompleksitas pemrosesan dan mempermudah deteksi tepi plat nomor.

Selanjutnya, kita akan menerapkan operasi deteksi tepi pada gambar abu-abu. Operasi ini akan membantu kita dalam menemukan tepi yang signifikan pada plat nomor. Dalam panduan ini, kita akan menggunakan algoritma Canny, yang telah terbukti efektif dalam mendeteksi tepi dalam berbagai kondisi. Dengan menggunakan fungsi cv2.Canny(), kita dapat menghasilkan gambar biner yang menunjukkan tepi yang terdeteksi.

Setelah mendapatkan gambar tepi, kita akan mencari kontur dalam gambar tersebut menggunakan fungsi cv2.findContours(). Kontur merupakan garis yang menghubungkan titik-titik sejajar pada tepi objek. Dalam konteks deteksi plat nomor, kita berharap untuk menemukan kontur yang mengelilingi plat nomor kendaraan pada gambar. Dalam fungsi cv2.findContours(), kita perlu menyediakan gambar biner tepi yang dihasilkan sebelumnya dan mode retrival serta metode aproksimasi kontur. Pada umumnya, mode retrival cv2.RETR_EXTERNAL digunakan untuk mendapatkan kontur eksternal, sedangkan metode aproksimasi cv2.CHAIN_APPROX_SIMPLE digunakan untuk mengurangi jumlah titik dalam kontur yang tidak penting.

Selanjutnya, kita akan memilih kontur dengan luas terbesar yang kemungkinan adalah plat nomor kendaraan. Dalam OpenCV, kita dapat menggunakan fungsi cv2.contourArea() untuk menghitung luas kontur. Dalam panduan ini, kita akan memilih kontur terbesar menggunakan fungsi max() dengan argumen key=cv2.contourArea.

Setelah memilih kontur terbesar, kita akan menggambar kotak persegi panjang di sekitar plat nomor menggunakan fungsi cv2.rectangle(). Fungsi ini membutuhkan koordinat sudut kiri atas dan sudut kanan bawah dari kotak persegi panjang yang ingin digambar. Untuk mendapatkan koordinat tersebut, kita dapat menggunakan fungsi cv2.boundingRect() dengan argumen kontur terbesar yang telah dipilih sebelumnya.

Terakhir, kita akan menampilkan gambar hasil deteksi menggunakan library matplotlib. Dengan menggunakan fungsi plt.imshow() dan plt.show(), kita dapat menampilkan gambar dengan kotak persegi panjang yang mengelilingi plat nomor kendaraan. Pastikan untuk menggunakan fungsi cv2.cvtColor() untuk mengonversi skema warna gambar dari BGR (yang digunakan oleh OpenCV) ke RGB (yang digunakan oleh matplotlib).

Dengan mengikuti langkah-langkah di atas dan menyesuaikan parameter serta path file sesuai kebutuhan Anda, Anda akan dapat melakukan deteksi plat nomor kendaraan menggunakan OpenCV dan Python dalam lingkungan Jupyter Notebook.

