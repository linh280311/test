<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chúc mừng 8/3</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            font-family: Arial, sans-serif;
            text-align: center;
            color: white;
            overflow: hidden;
        }
        h1 {
            margin-top: 50px;
            font-size: 50px;
            animation: fadeIn 3s ease-in-out;
        }
        p {
            margin-top: 20px;
            font-size: 30px;
            font-weight: bold;
            animation: slideUp 3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .falling-heart {
            position: absolute;
            top: -50px;
            color: red;
            font-size: 24px;
            animation: fall linear infinite;
        }
        @keyframes fall {
            from { transform: translateY(-50px); opacity: 1; }
            to { transform: translateY(100vh); opacity: 0; }
        }
        #playButton {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: rgba(255, 255, 255, 0);
            color: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 30px;
            cursor: pointer;
            opacity: 0.05;
            transition: opacity 0.3s ease, color 0.3s ease, border 0.3s ease;
        }
        #playButton:hover {
            opacity: 0.3;
            color: rgba(255, 255, 255, 0.7);
            border: 1px solid rgba(255, 255, 255, 0.7);
        }
    </style>
</head>
<body>
    <h1>Chúc mừng 8/3!</h1>
    <p>chúc toàn thể các bạn nữ lớp 8B cũng như cô giáo chủ nhiệm một ngày 8-3 vui vẻ mạnh khỏe và hạnh phúc!</p>
    <p>Chúc các bạn có một ngày thật đặc biệt và tràn đầy yêu thương! ❤️</p>

    <audio id="myAudio" loop preload="auto">
        <source src="nhac.mp3" type="audio/mpeg">
    </audio>

    <button id="playButton">Phát nhạc</button>

    <script>
        const audio = document.getElementById('myAudio');
        const playButton = document.getElementById('playButton');

        document.body.addEventListener('click', () => {
            audio.play().catch(() => {});
        }, { once: true });

        playButton.addEventListener('click', () => {
            audio.currentTime = 0;
            audio.play().catch((error) => {
                console.log('Không phát được nhạc:', error);
            });
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.innerHTML = '❤️';
            heart.classList.add('falling-heart');
            heart.style.left = Math.random() * window.innerWidth + 'px';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
        setInterval(createHeart, 300);

        function requestFullScreen() {
            const elem = document.documentElement;
            if (elem.requestFullscreen) {
                elem.requestFullscreen();
            } else if (elem.webkitRequestFullscreen) {
                elem.webkitRequestFullscreen();
            } else if (elem.msRequestFullscreen) {
                elem.msRequestFullscreen();
            }
        }

        document.addEventListener('click', requestFullScreen, { once: true });
    </script>
</body>
</html>
