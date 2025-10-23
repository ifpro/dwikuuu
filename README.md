<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Halo Dwi Safitri,-</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&family=Pacifico&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
    
    <style>
        /* --- Variabel & Dasar --- */
        :root {
            --primary-color: #ff4081; /* Pink Cerah */
            --secondary-color: #e91e63; /* Pink Gelap */
            --bg-color: #fce4ec; /* Latar Belakang Lembut */
            --card-bg: #ffffff;
        }

        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            text-align: center;
            color: var(--primary-color);
            overflow-x: hidden;
            perspective: 1500px; /* Untuk efek 3D */
        }

        /* --- Kartu dan Wrapper 3D --- */
        .card-wrapper {
            position: relative;
            width: 380px; 
            height: 550px;
            transform-style: preserve-3d;
            transition: transform 1s cubic-bezier(0.68, -0.55, 0.265, 1.55); /* Transisi Flip Dramatis */
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            margin: 20px;
        }

        .container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--card-bg);
            border-radius: 15px;
            padding: 30px;
            box-sizing: border-box;
            backface-visibility: hidden; 
            z-index: 10;
            transition: opacity 0.5s;
        }
        
        .intro { z-index: 100; display: flex; flex-direction: column; justify-content: center; }
        .main-content { position: relative; } 
        /* Halaman video dihapus */
        /* .video-page { transform: rotateY(180deg); opacity: 0; pointer-events: none; } */ 

        /* --- Slide / Halaman Kartu --- */
        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            padding: 30px;
            box-sizing: border-box;
            background: var(--card-bg);
            border-radius: 15px;
            opacity: 0;
            z-index: 1;
            transform: scale(0.95);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }

        .slide.active {
            opacity: 1;
            z-index: 5;
            transform: scale(1);
        }

        /* --- Konten & Animasi Teks --- */
        .title {
            font-family: 'Pacifico', cursive;
            font-size: 2.2em;
            color: var(--secondary-color);
            margin-bottom: 10px;
        }

        .message {
            font-size: 1em;
            color: #333;
            line-height: 1.6;
        }

        .heart {
            font-size: 2.5em;
            color: var(--primary-color);
            animation: pulse 1s infinite;
            margin: 10px 0;
        }

        .image img {
            width: 130px;
            height: 130px;
            object-fit: cover;
            border-radius: 50%;
            border: 4px solid var(--primary-color);
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            margin-top: 15px;
        }

        .signature {
            font-size: 0.9em;
            margin-top: 15px;
            color: #555;
            font-style: italic;
        }

        /* --- Tombol --- */
        .next-btn, .start-btn, .send-btn { /* video-btn dihapus */
            background-color: var(--primary-color);
            color: #fff;
            border: 2px solid var(--secondary-color);
            padding: 12px 20px;
            font-size: 1em;
            border-radius: 8px;
            margin-top: 20px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.3s ease;
            font-weight: bold;
        }
        
        .next-btn:hover, .start-btn:hover, .send-btn:hover { /* .video-btn:hover dihapus */
            background-color: var(--secondary-color);
            transform: scale(1.05);
        }

        /* --- Animasi Flower/Confetti --- */
        .flower {
            position: absolute;
            width: 40px;
            height: 40px;
            background: url('FOTO1.PNG') no-repeat center; /* Ganti ini dengan URL/path gambar confetti/bunga Anda */
            background-size: contain;
            animation: fall linear infinite;
            z-index: 0;
            pointer-events: none;
        }

        @keyframes fall {
            0% { transform: translateY(-100px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
        }

        /* --- Video Container --- */
        /* Kontainer video dihapus */
        /*
        .video-container {
            position: relative;
            padding-top: 56.25%; 
            height: 0;
            overflow: hidden;
            max-width: 100%;
            border-radius: 15px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            background-color: #000;
            margin-top: 15px;
        }

        .video-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        */
        
        /* --- Responsif Media Queries --- */
        @media (max-width: 600px) {
            
            /* 1. Responsivitas Kartu Utama */
            .card-wrapper {
                width: 90vw; /* Lebar Kartu mengambil 90% dari viewport width */
                height: 70vh; /* Tinggi Kartu mengambil 70% dari viewport height */
                max-width: 350px;
            }

            /* 2. Ukuran Font yang Lebih Kecil di Mobile */
            .title {
                font-size: 1.8em;
            }

            .message {
                font-size: 0.9em;
            }
            
            /* 3. Ukuran Foto yang Lebih Kecil */
            .image img {
                width: 100px;
                height: 100px;
            }
            
            /* 4. Padding dan Input */
            .container {
                padding: 15px;
            }
            
            #userName {
                padding: 10px !important;
                font-size: 1em !important;
            }
            
            /* 5. Tombol */
            .next-btn, .start-btn, .send-btn {
                padding: 10px 15px;
                font-size: 0.9em;
            }
            
            /* 6. Flower */
            .flower {
                width: 30px;
                height: 30px;
            }
        }
    </style>
</head>
<body>
    <audio id="background-music" loop>
        <source src="lagu1.mp3" type="audio/mp3">
        Your browser does not support the audio element.
    </audio>

    <div id="intro-screen" class="container intro">
        <div class="title animate__animated animate__fadeInDown">Halo Dwi Safitrikuu!</div>
        <div class="message animate__animated animate__fadeInUp">Nama Kamu Biar bisalanjat:</div>
        <input type="text" id="userName" placeholder="*Nama Lengkap" style="padding: 12px; font-size: 1.1em; border-radius: 8px; border: 1px solid #ffabab; width: calc(100% - 24px); box-sizing: border-box; margin-bottom: 15px;">
        <button class="start-btn animate__animated animate__bounceIn" onclick="startExperience()">Start <i class="fas fa-play"></i></button>
        <p style="font-size: 0.8em; color: gray; margin-top: 40px;">Dibuat Oleh PT. Inspirasi Cemerlang Indonesia (Andi Irfan Maulana) | All Rights reserved</p>
    </div>

    <div class="card-wrapper" id="card-wrapper" style="display: none;">
        <div class="container main-content" id="main-slides">
            
            <div class="slide active" data-animation="bounceInDown">
                <div class="title animate__animated">Untukmu yang Berbahagia, <span id="displayName"></span>!</div>
                <div class="message animate__animated">
                    Setelah sekian banyak 'Telepat' yang terasa hampa, aku sempat berpikir mungkin pencarian ini harus kuakhiri. Lalu kamu muncul. Entah kenapa, di tengah lelahnya hati, saat mendengarmu berbicara itu seperti janji kecil yang tak terucapkan. Jadi, dengan sisa keberanian yang ada, aku meminta user igmu. Semoga kali ini, 'telepat' ini bukan sekadar algoritma, tapi awal dari cerita yang dulu sempat hilang keyakinannya.
                </div>
                <div class="heart animate__animated">❤️</div>
                <div class="image animate__animated">
                    <img src="dwi 1.jpg" alt="Your Love's Picture 1">
                </div>
                <div class="signature animate__animated">With all my hopes, Andi Irfan Maulana</div>
                <button class="next-btn animate__animated" onclick="nextSlide()">Next <i class="fas fa-arrow-right"></i></button>
            </div>

            <div class="slide" data-animation="rubberBand">
                <div class="title animate__animated">Mulai Mengenalmu</div>
                <div class="message animate__animated">
                    "Hai,
Setelah semua obrolan panjang kita, dari yang sekadar 'telepati' di aplikasi ini, berlanjut ke tukar-menukar cerita di Instagram, bahkan sampai malam-malam penuh tawa dan keheningan dalam sleep call... aku pikir kita sudah lebih dari sekadar kenalan.
Saat aku meminta TikTok atau bahkan nomor WhatsApp-mu, itu bukan karena terburu-buru, tapi karena aku ingin semua 'dunia' kita terhubung. Aku ingin kamu tahu, betapa berharganya setiap detik yang kita habiskan bersama—betapa langkah kecil itu terasa seperti lompatan besar dalam hidupku yang sepi.
                </div>
                <div class="heart animate__animated">💖</div>
                <div class="image animate__animated">
                    <img src="dwi6.jpg" alt="Your Love's Picture 2">
                </div>
                <div class="signature animate__animated">Forever yours, Dwi Safitrikuu</div>
                <button class="next-btn animate__animated" onclick="nextSlide()">Next <i class="fas fa-arrow-right"></i></button>
            </div>
            
            <div class="slide" data-animation="lightSpeedIn">
                <div class="title animate__animated">Mulai Mengenalmu Part 2</div>
                <div class="message animate__animated">
                    Kamu bukan hanya sekadar obrolan di layar. Kamu adalah alasan aku tersenyum sebelum tidur dan alasan aku bersemangat bangun di pagi hari. Setiap cerita darimu, baik tentang hari yang melelahkan atau mimpi-mimpi kecilmu, semuanya terasa penting. Aku merasa kita membangun sesuatu yang nyata, di tengah dunia maya yang seringkali menipu. Aku ingin terus mengenalmu, bukan hanya sebagai 'teman sleep call', tapi sebagai bagian utuh dari masa depanku.
                </div>
                <div class="heart animate__animated">✨</div>
                <div class="image animate__animated">
                    <img src="dwi7.jpg" alt="Your Love's Picture 3">
                </div>
                <div class="signature animate__animated">With all my heart, Andi Irfan Maulana</div>
                <button class="next-btn animate__animated" onclick="nextSlide()">Next <i class="fas fa-arrow-right"></i></button>
            </div>
            
            <div class="slide" data-animation="wobble">
                <div class="title animate__animated">Lanjutkan Cerita Kita</div>
                <div class="message animate__animated">
                    Kini, semua yang telah kita lalui—tawa, sedikit salah paham, hingga rencana-rencana kecil yang kita rajut—telah mengantarkanku pada satu keyakinan: Aku ingin menjadikan semua ini lebih dari sekadar kenangan. Aku ingin menjagamu, dan melihatmu bertumbuh bersamaku. Aku tahu mungkin ini terlalu cepat, tapi saat bersamamu, waktu terasa berhenti. Terima kasih sudah menjadi kejutan terbaik dalam hidupku, Dwi.
                </div>
                <div class="heart animate__animated">🥂</div>
                <div class="image animate__animated">
                    <img src="dwi3.jpg" alt="Your Love's Picture 4">
                </div>
                <div class="signature animate__animated">Always thinking of you, Dwi Safitrikuu</div>
                <button class="next-btn send-btn animate__animated" onclick="sendGiftRequest()">Hubungi Aku Sekarang (WA) <i class="fab fa-whatsapp"></i></button>
            </div>

            </div>

        </div>

    <script>
        const cardWrapper = document.getElementById('card-wrapper');
        const introScreen = document.getElementById('intro-screen');
        const backgroundMusic = document.getElementById("background-music");
        
        // mainVideo dihapus
        // const mainVideo = document.getElementById("mainVideo");
        
        // videoPage dihapus
        // const videoPage = document.getElementById('video-page'); 

        const slides = document.querySelectorAll(".slide"); 
        let currentSlideIndex = 0;
        
        // --- Utility untuk Animasi ---
        const animatePrefix = 'animate__';
        const animationClasses = ['animated', 'animate__fadeIn', 'animate__bounceInDown', 'animate__rubberBand', 'animate__rollIn', 'animate__heartBeat', 'animate__zoomIn', 'animate__wobble', 'animate__fadeInUp', 'animate__lightSpeedIn', 'animate__fadeInDown', 'animate__pulse'];

        function removeAllAnimationClasses(element) {
            element.className = element.className.split(' ').filter(c => !c.startsWith(animatePrefix)).join(' ').trim();
        }

        function applySlideAnimation(slideElement, animationName) {
            // Hapus semua animasi dari semua elemen di slide
            slideElement.querySelectorAll('.animate__animated').forEach(el => removeAllAnimationClasses(el));
            
            // Tambahkan kelas dasar Animate.css pada semua elemen yang ditargetkan
            slideElement.querySelectorAll('.animate__animated').forEach(el => el.classList.add('animate__animated'));

            // Terapkan animasi spesifik
            slideElement.querySelector('.title')?.classList.add(animatePrefix + animationName);
            slideElement.querySelector('.message')?.classList.add(animatePrefix + 'fadeIn');
            slideElement.querySelector('.heart')?.classList.add(animatePrefix + 'pulse');
            slideElement.querySelector('.image')?.classList.add(animatePrefix + 'zoomIn');
            slideElement.querySelector('.signature')?.classList.add(animatePrefix + 'fadeInUp');
            slideElement.querySelector('.next-btn')?.classList.add(animatePrefix + 'fadeInUp');
        }

        // --- Fungsi Utama Navigasi ---
        
        function startExperience() {
            var userName = document.getElementById("userName").value;
            if (userName.trim() !== "") {
                document.getElementById("displayName").textContent = userName;
                introScreen.style.opacity = '0';
                
                setTimeout(() => {
                    introScreen.style.display = 'none';
                    cardWrapper.style.display = 'block';
                    // Mulai musik setelah interaksi
                    backgroundMusic.play().catch(e => console.log("Music Autoplay failed:", e));
                    updateSlideDisplay();
                }, 500); 

            } else {
                alert("Masukkan namamu dulu ya!");
            }
        }

        function updateSlideDisplay() {
            slides.forEach((slide, i) => {
                if (i === currentSlideIndex) {
                    slide.classList.add("active");
                    const animationName = slide.getAttribute('data-animation') || 'fadeIn';
                    applySlideAnimation(slide, animationName);
                } else {
                    slide.classList.remove("active");
                }
            });
        }

        function nextSlide() {
            // Memperbarui kondisi batas akhir. Sekarang ada 4 slide (indeks 0 hingga 3).
            if (currentSlideIndex < slides.length - 1) { 
                currentSlideIndex++;
                updateSlideDisplay();
            }
            // Setelah slide terakhir, tidak ada aksi (video page sudah dihapus)
        }

        // Fungsi showVideoPage() dan backToSlides() DIHAPUS

        function sendGiftRequest() {
            var userName = document.getElementById("userName").value;
            // Pastikan nomor WhatsApp di format internasional (dengan kode negara)
            var url = "https://api.whatsapp.com/send?phone=+6285158571195&text=" + encodeURIComponent("Halo Dwi, kamu sudah membaca semua pesannya? Mari kita lanjutkan cerita ini. " + userName);
            window.open(url, "_blank");
        }
        
        // --- Efek Flower/Confetti Dinamis ---
        function createFlower() {
            const flower = document.createElement('div');
            flower.classList.add('flower');
            
            flower.style.left = `${Math.random() * 100}vw`; 
            
            const duration = Math.random() * 8 + 5; 
            const delay = Math.random() * 6; 
            const size = Math.random() * 10 + 20; // Ukuran acak 20px-30px
            
            flower.style.width = `${size}px`;
            flower.style.height = `${size}px`;
            flower.style.animationDuration = `${duration}s`;
            flower.style.animationDelay = `${delay}s`;

            document.body.appendChild(flower);

            setTimeout(() => {
                flower.remove();
            }, (duration + delay) * 1000); 
        }

        // Buat 20 bunga secara acak
        for (let i = 0; i < 20; i++) { 
            createFlower();
        }
    </script>
</body>
</html>
