<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            overflow: hidden;
            background: linear-gradient(120deg, #232526, #414345);
            position: relative;
            flex-direction: column;
        }

        /* Navigationsleiste */
        .navbar {
            width: 100%;
            background-color: rgba(0, 0, 0, 0.6);
            color: #f1f1f1;
            display: flex;
            justify-content: center;
            padding: 15px 0;
            position: absolute;
            top: 0;
            left: 0;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }

        .navbar a {
            color: #f1f1f1;
            text-decoration: none;
            padding: 10px 20px;
            font-size: 16px;
            transition: background-color 0.3s ease, color 0.3s ease;
            margin: 0 10px;
        }

        .navbar a:hover {
            background-color: rgba(255, 255, 255, 0.2);
            color: #fff;
            border-radius: 5px;
        }

        /* Regentropfen */
        .rain-drop {
            position: absolute;
            width: 2px; /* Dünnere Tropfen */
            height: 20px; /* Tropfenhöhe */
            background: rgba(173, 216, 230, 0.8); /* Helles Blau für die Tropfen */
            box-shadow: 0 0 10px rgba(173, 216, 230, 0.8), 0 0 20px rgba(173, 216, 230, 0.6);
            animation: rainFall 0.8s infinite linear;
        }

          /* Hintergrundbild */
          .background-image {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1; /* Bild hinter allen anderen Elementen */
        }

        .rain-drop::after {
            content: "";
            position: absolute;
            width: 8px;
            height: 8px;
            background: rgba(173, 216, 230, 0.6);
            border-radius: 50%;
            transform: scale(0);
            opacity: 0;
            animation: splash 0.2s ease-out;
        }

        /* Animationspositionen und -dauern */
        /* Hier fügen wir mehr Tropfen hinzu */
        .rain-drop1 { left: 5%; animation-duration: 0.8s; animation-delay: 0s; }
        .rain-drop2 { left: 10%; animation-duration: 0.9s; animation-delay: 0.1s; }
        .rain-drop3 { left: 15%; animation-duration: 0.7s; animation-delay: 0.2s; }
        .rain-drop4 { left: 20%; animation-duration: 0.9s; animation-delay: 0.3s; }
        .rain-drop5 { left: 25%; animation-duration: 0.8s; animation-delay: 0.4s; }
        .rain-drop6 { left: 30%; animation-duration: 0.7s; animation-delay: 0.5s; }
        .rain-drop7 { left: 35%; animation-duration: 0.6s; animation-delay: 0.6s; }
        .rain-drop8 { left: 40%; animation-duration: 0.7s; animation-delay: 0.7s; }
        .rain-drop9 { left: 45%; animation-duration: 0.8s; animation-delay: 0.8s; }
        .rain-drop10 { left: 50%; animation-duration: 0.9s; animation-delay: 0.9s; }
        .rain-drop11 { left: 55%; animation-duration: 0.6s; animation-delay: 1s; }
        .rain-drop12 { left: 60%; animation-duration: 0.7s; animation-delay: 1.1s; }
        .rain-drop13 { left: 65%; animation-duration: 0.8s; animation-delay: 1.2s; }
        .rain-drop14 { left: 70%; animation-duration: 0.9s; animation-delay: 1.3s; }
        .rain-drop15 { left: 75%; animation-duration: 0.6s; animation-delay: 1.4s; }
        .rain-drop16 { left: 80%; animation-duration: 0.7s; animation-delay: 1.5s; }
        .rain-drop17 { left: 85%; animation-duration: 0.8s; animation-delay: 1.6s; }
        .rain-drop18 { left: 90%; animation-duration: 0.9s; animation-delay: 1.7s; }
        .rain-drop19 { left: 95%; animation-duration: 0.8s; animation-delay: 1.8s; }
        .rain-drop20 { left: 10%; animation-duration: 0.7s; animation-delay: 1.2s; }
        .rain-drop21 { left: 15%; animation-duration: 0.6s; animation-delay: 1.4s; }
        .rain-drop22 { left: 20%; animation-duration: 0.8s; animation-delay: 0.9s; }
        .rain-drop23 { left: 25%; animation-duration: 0.7s; animation-delay: 1.3s; }
        .rain-drop24 { left: 30%; animation-duration: 0.9s; animation-delay: 1s; }
        .rain-drop25 { left: 35%; animation-duration: 0.6s; animation-delay: 1.5s; }

        /* Regenanimation */
        @keyframes rainFall {
            0% { top: -10%; opacity: 0.8; }
            100% { top: 100%; opacity: 1; }
        }

        /* Splash-Animation für den Aufprall */
        @keyframes splash {
            0% {
                transform: scale(0);
                opacity: 0;
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }

        /* Login-Container */
        .login-container {
            width: 350px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            border-radius: 10px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
            color: #FFFFFF;
            text-align: center;
            z-index: 1;
            margin-top: 100px;
        }

        .login-container h2 {
            margin-bottom: 20px;
            font-size: 24px;
            font-weight: bold;
            color: #f1f1f1;
        }

        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .form-group label {
            display: block;
            font-weight: bold;
            color: #cfcfcf;
            font-size: 14px;
            margin-bottom: 5px;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border-radius: 5px;
            border: none;
            outline: none;
            font-size: 16px;
            color: #333;
        }

        .login-button {
            width: 100%;
            padding: 12px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0px 4px 15px rgba(0, 255, 0, 0.3);
        }

        .login-button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }

        .forgot-password {
            margin-top: 15px;
            display: block;
            font-size: 14px;
            color: #ddd;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .forgot-password:hover {
            color: #fff;
        }

    </style>
</head>
<body>

    <img src="./Bilder/yzkzzz.jfif" alt="Hintergrundbild" class="background-image">


    <div class="navbar">
        <a href="#home">Home</a>
        <a href="#forum">Forum</a>
        <a href="#contact">Kontakt</a>
    </div>

    <!-- Regentropfen -->
    <div class="rain-drop rain-drop1"></div>
    <div class="rain-drop rain-drop2"></div>
    <div class="rain-drop rain-drop3"></div>
    <div class="rain-drop rain-drop4"></div>
    <div class="rain-drop rain-drop5"></div>
    <div class="rain-drop rain-drop6"></div>
    <div class="rain-drop rain-drop7"></div>
    <div class="rain-drop rain-drop8"></div>
    <div class="rain-drop rain-drop9"></div>
    <div class="rain-drop rain-drop10"></div>
    <div class="rain-drop rain-drop11"></div>
    <div class="rain-drop rain-drop12"></div>
    <div class="rain-drop rain-drop13"></div>
    <div class="rain-drop rain-drop14"></div>
    <div class="rain-drop rain-drop15"></div>
    <div class="rain-drop rain-drop16"></div>
    <div class="rain-drop rain-drop17"></div>
    <div class="rain-drop rain-drop18"></div>
    <div class="rain-drop rain-drop19"></div>
    <div class="rain-drop rain-drop20"></div>
    <div class="rain-drop rain-drop21"></div>
    <div class="rain-drop rain-drop22"></div>
    <div class="rain-drop rain-drop23"></div>
    <div class="rain-drop rain-drop24"></div>
    <div class="rain-drop rain-drop25"></div>

    <!-- Login-Container -->
    <div class="login-container">
        <h2>Willkommen zurück</h2>
        <form action="/login" method="post">
            <div class="form-group">
                <label for="username">Benutzername</label>
                <input type="text" id="username" name="username" placeholder="Benutzername">
            </div>
            <div class="form-group">
                <label for="password">Passwort</label>
                <input type="password" id="password" name="password" placeholder="Passwort">
            </div>
            <button class="login-button" type="submit">Einloggen</button>
        </form>
        <a href="#forgot-password" class="forgot-password">Passwort vergessen?</a>
    </div>

</body>
</html>
