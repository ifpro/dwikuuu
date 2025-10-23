<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday, Ex! - Kartu Interaktif</title>
    
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
        .video-page { transform: rotateY(180deg); opacity: 0; pointer-events: none; } 

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
        .next-btn, .start-btn, .send-btn, .video-btn {
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
        
        .next-btn:hover, .start-btn:hover, .send-btn:hover, .video-btn:hover {
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
        .video-container {
            position: relative;
            padding-top: 56.25%; /* 16:9 Aspect Ratio */
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
            .next-btn, .start-btn, .send-btn, .video-btn {
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
        <source src="selamatulangtahun.mp3" type="audio/mp3">
        Your browser does not support the audio element.
    </audio>

    <div id="intro-screen" class="container intro">
        <div class="title animate__animated animate__fadeInDown">Halo Ex Hehehe!</div>
        <div class="message animate__animated animate__fadeInUp">Kasih masukki namata biar bisaki lanjut:</div>
        <input type="text" id="userName" placeholder="*Nama Lengkap" style="padding: 12px; font-size: 1.1em; border-radius: 8px; border: 1px solid #ffabab; width: calc(100% - 24px); box-sizing: border-box; margin-bottom: 15px;">
        <button class="start-btn animate__animated animate__bounceIn" onclick="startExperience()">Start <i class="fas fa-play"></i></button>
        <p style="font-size: 0.8em; color: gray; margin-top: 40px;">Dibuat Oleh PT. Inspirasi Cemerlang Indonesia (Andi Irfan Maulana) | All Rights reserved</p>
    </div>

    <div class="card-wrapper" id="card-wrapper" style="display: none;">
        <div class="container main-content" id="main-slides">
            
            <div class="slide active" data-animation="bounceInDown">
                <div class="title animate__animated">Untukmu yang Berbahagia, <span id="displayName"></span>!</div>
                <div class="message animate__animated">
                    Hari ini adalah hari yang sangat spesial, karena ini adalah hari lahirmu. Aku bersyukur atas setiap detik yang pernah kita lewati bersama. Kamu adalah anugrah yang pernah hadir dalam hidupku.
                </div>
                <div class="heart animate__animated">❤️</div>
                <div class="image animate__animated">
                    <img src="foto1.png" alt="Your Love's Picture 1">
                </div>
                <div class="signature animate__animated">With all my hopes, Andi Irfan Maulana</div>
                <button class="next-btn animate__animated" onclick="nextSlide()">Next <i class="fas fa-arrow-right"></i></button>
            </div>

            <div class="slide" data-animation="rubberBand">
                <div class="title animate__animated">Kenangan Manis</div>
                <div class="message animate__animated">
                    Di hari ini, mari kita kembali mengingat semua kenangan manis yang pernah kita lalui. Terima kasih telah menjadi bagian dari hidupku, walaupun sekarang kita mungkin sudah berbeda tujuan.
                </div>
                <div class="heart animate__animated">💖</div>
                <div class="image animate__animated">
                    <img src="foto2.png" alt="Your Love's Picture 2">
                </div>
                <div class="signature animate__animated">Forever yours, Fatri Utami Zeizar</div>
                <button class="next-btn animate__animated" onclick="nextSlide()">Next <i class="fas fa-arrow-right"></i></button>
            </div>

            <div class="slide" data-animation="rollIn">
                <div class="title animate__animated">Selalu Dihati</div>
                <div class="message animate__animated">
                    Meskipun kita mungkin tidak lagi bersama, kamu akan selalu memiliki tempat di hatiku. Terima kasih telah memberi warna dalam hidupku. Dinonton nah video yang dibawah sampai selesai.
                </div>
                <div class="heart animate__animated">💞</div>
                <div class="image animate__animated">
                    <img src="foto3.png" alt="Your Love's Picture 3">
                </div>
                <button class="next-btn video-btn animate__animated" onclick="showVideoPage()"> >>DINONTON SAMPAI SELESAI<< <i class="fas fa-video"></i></button>
            </div>
        </div>

        <div class="container video-page" id="video-page">
            <div class="title animate__animated animate__fadeInDown">Pesan Video Spesial 🎥</div>
            <div class="message animate__animated animate__fadeIn">Tontonlah dengan hati.</div>
            <div class="video-container animate__animated animate__zoomIn">
                <video controls id="mainVideo">
                    <source src="awaldanakhir.mp4" type="video/mp4">
                    Your browser does not support the video tag.
                </video>
            </div>
            <button class="next-btn" onclick="backToSlides()">Kembali <i class="fas fa-undo"></i></button>
            <button class="send-btn" onclick="sendGiftRequest()">Spesial Request (WA) <i class="fab fa-whatsapp"></i></button>
        </div>
    </div>

    <script>
        const cardWrapper = document.getElementById('card-wrapper');
        const introScreen = document.getElementById('intro-screen');
        const backgroundMusic = document.getElementById("background-music");
        const mainVideo = document.getElementById("mainVideo");
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
            if (currentSlideIndex < slides.length - 1) {
                currentSlideIndex++;
                updateSlideDisplay();
            }
        }

        function showVideoPage() {
            // Efek 3D Flip
            cardWrapper.style.transform = "rotateY(180deg)";
            
            videoPage.style.opacity = '1';
            videoPage.style.pointerEvents = 'auto';
            
            mainVideo.load(); 
            backgroundMusic.pause();
        }

        function backToSlides() {
            // Efek 3D Flip Kembali
            cardWrapper.style.transform = "rotateY(0deg)";
            
            videoPage.style.opacity = '0';
            videoPage.style.pointerEvents = 'none';

            mainVideo.pause(); 
            backgroundMusic.play().catch(e => console.log("Music play failed:", e));
        }

        function sendGiftRequest() {
            var userName = document.getElementById("userName").value;
            // Pastikan nomor WhatsApp di format internasional (dengan kode negara)
            var url = "https://api.whatsapp.com/send?phone=+6285345674445&text=" + encodeURIComponent("Happy Birthday! dihari spesialta mauki kado apa? " + userName);
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
Dibuat Oleh PT. Inspirasi Cemerlang Indonesia 
( Andi Irfan Maualana )
All Rights reserved
