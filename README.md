<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Tebak Angka</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            margin: 0;
            color: white;
        }
        .game-box {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px 20px;
            margin: 20px auto;
            max-width: 400px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.3);
        }
        input {
            width: 80%;
            padding: 15px;
            font-size: 18px;
            border: none;
            border-radius: 30px;
            margin: 10px 0;
            text-align: center;
        }
        button {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            border-radius: 30px;
            margin: 10px 5px;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        #pesan {
            font-size: 20px;
            margin: 20px 0;
            min-height: 60px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="game-box">
        <h1>🎮 TEBAK ANGKA</h1>
        <p>Angka rahasia antara 1-100</p>
        
        <div id="pesan">Mulai menebak!</div>
        
        <input type="number" id="tebakan" placeholder="Masukkan angka..." min="1" max="100">
        
        <div>
            <button onclick="cekAngka()">TEBAK!</button>
            <button onclick="resetGame()">🔄 Reset</button>
        </div>
        
        <div id="jumlahTebakan">
            Percobaan: 0
        </div>
    </div>

    <script>
        let angkaRahasia = Math.floor(Math.random() * 100) + 1;
        let percobaan = 0;
        
        function cekAngka() {
            let tebakan = document.getElementById('tebakan').value;
            let pesan = document.getElementById('pesan');
            
            if (!tebakan) {
                pesan.innerHTML = '⚠️ Isi dulu angkanya!';
                return;
            }
            
            percobaan++;
            tebakan = Number(tebakan);
            
            if (tebakan === angkaRahasia) {
                pesan.innerHTML = '🎉 SELAMAT! Kamu menang! 🎉';
                pesan.style.color = '#ffd700';
                document.getElementById('jumlahTebakan').innerHTML = 'Kamu berhasil dalam ' + percobaan + ' percobaan!';
            } 
            else if (tebakan > angkaRahasia) {
                pesan.innerHTML = '📉 Angka terlalu besar!';
                pesan.style.color = '#ffb8b8';
                document.getElementById('jumlahTebakan').innerHTML = 'Percobaan: ' + percobaan;
            } 
            else {
                pesan.innerHTML = '📈 Angka terlalu kecil!';
                pesan.style.color = '#b8ffb8';
                document.getElementById('jumlahTebakan').innerHTML = 'Percobaan: ' + percobaan;
            }
            
            document.getElementById('tebakan').value = '';
        }
        
        function resetGame() {
            angkaRahasia = Math.floor(Math.random() * 100) + 1;
            percobaan = 0;
            document.getElementById('pesan').innerHTML = 'Mulai menebak!';
            document.getElementById('pesan').style.color = 'white';
            document.getElementById('jumlahTebakan').innerHTML = 'Percobaan: 0';
            document.getElementById('tebakan').value = '';
        }
        
        // Biar bisa enter
        document.getElementById('tebakan').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                cekAngka();
            }
        });
    </script>
</body>
</html>
