Menguji Portabilitas Container: Dari Python ke Cloud dengan Docker

**Pendahuluan**
Dalam dunia cloud computing, developer harus memastikan aplikasi mereka dapat berjalan di berbagai sistem tanpa masalah. Containerization adalah teknologi yang mempermudah hal ini yaitu dengan container, aplikasi dan semua dependensinya dikemas dalam satu paket yang konsisten. Tidak perlu melihat di mana container dijalankan seperti Linux, Windows, atau macOS  hasilnya akan tetap sama.

**Tujuan Project**
Project kecil saya yaitu Greeting App. Aplikasi ini menggunakan bahasa Python, hanya menampilkan ucapan “Hello” disertai waktu lokal. Tujuannya sederhana yaitu menguji apakah image Docker yang sama bisa dijalankan di dua sistem operasi berbeda dengan hasil yang sama. Dari situ saya ingin memahami konsep portabilitas container secara real time.

**Langkah Langkah**
Saya memulai project ini dengan membuat repositori di GitHub bernama greeting-app. Setelah itu saya membuat file [app.py](http://app.py/), Dockerfile, dan [README.md](http://readme.md/). File Dockerfile menggunakan image dasar python:3.11 slim. Saya menentukan directory kerja atau app, mengsalin file aplikasi, lalu menjalankan perintah pip install untuk dependensi.

Setelah semua file siap, saya membangun image dengan perintah seperti :

docker build -t greeting-app:1.0 .

Docker membaca Dockerfile dan menghasilkan image baru. Selanjutnya saya jalankan pada Linux:

docker run --rm greeting-app:1.0 

Output-nya menampilkan:

![image.png](attachment:afea69c8-0b82-47a5-afb4-43d38f737dd3:image.png)

Saya ulangi perintah yang sama di Windows 10 melalui PowerShell, dan hasilnya identik. Artinya image tersebut berjalan konsisten di dua OS tanpa harus mengubah kode sama sekali.

Untuk memastikan pipeline DevOps berjalan otomatis, saya menambahkan file workflow .github/workflows/ci.yml agar GitHub Actions membangun dan menguji image setiap kali ada push ke branch main. Dengan demikian, setiap perubahan kode langsung diuji tanpa manual build.

**Hasil & Pembahasan**
Hasil pengujian menunjukkan bahwa containerization membuat aplikasi sangat mudah dipindahkan. Hanya dengan satu image, saya dapat menjalankannya di dua sistem berbeda, bahkan bisa diunggah ke registry seperti Docker Hub untuk dibagikan ke orang lain. Dari percobaan ini, saya juga memahami perbedaan kecil seperti timezone output, tetapi struktur dan fungsi program tetap sama.

**Refleksi & Kesimpulan**
Project ini mengajarkan saya bahwa container bukan hanya alat untuk menjalankan aplikasi, tetapi fondasi utama dari praktik DevOps. Integrasi GitHub Actions, containerization, dan version control membentuk workflow yang modern, cepat, dan dapat diulang.

Dengan container, developer tidak perlu khawatir soal “di komputer saya jalan, di server nggak jalan”. Image Docker membuat semua environment identik. Hal ini memperkuat konsep Infrastructure as Code yang menjadi dasar cloud computing.

Bagi saya pribadi, pengalaman ini menjadi pintu masuk ke dunia DevOps dan membuat saya memahami mengapa hampir semua perusahaan cloud menggunakan container sebagai standar deployment mereka.
