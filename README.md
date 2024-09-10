<!DOCTYPE html>
<html>
<head>
    <title>Camera Capture</title>
</head>
<body>
    <h1>التقاط الصورة</h1>
    <video id="video" width="640" height="480" autoplay></video>
    <button id="capture">التقاط</button>
    <canvas id="canvas" width="640" height="480"></canvas>

    <script>
        // الوصول إلى الكاميرا
        const video = document.getElementById('video');

        navigator.mediaDevices.getUserMedia({ video: true })
            .then(stream => {
                video.srcObject = stream;
            })
            .catch(err => {
                console.error("حدث خطأ:", err);
            });

        // التقاط الصورة
        const captureButton = document.getElementById('capture');
        const canvas = document.getElementById('canvas');
        const context = canvas.getContext('2d');

        captureButton.addEventListener('click', () => {
            context.drawImage(video, 0, 0, canvas.width, canvas.height);
        });
    </script>
</body>
</html>
