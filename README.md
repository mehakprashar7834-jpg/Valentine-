<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Favorite Person</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --primary-pink: #ffafcc;
            --dark-red: #d80032;
            --soft-white: #fff5f5;
        }

        body {
            margin: 0; padding: 0; display: flex; flex-direction: column;
            justify-content: center; align-items: center; height: 100vh;
            background-color: var(--soft-white);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }

        #card {
            text-align: center; background: white; padding: 2.5rem;
            border-radius: 30px; box-shadow: 0 15px 35px rgba(255, 175, 204, 0.3);
            max-width: 450px; width: 90%; z-index: 10;
            position: relative;
        }

        #valentine-gif {
            width: 100%; max-width: 250px; border-radius: 20px;
            margin-bottom: 1.5rem; cursor: pointer;
            transition: transform 0.2s;
        }
        #valentine-gif:active { transform: scale(0.95); }

        h1 { color: var(--dark-red); font-size: 1.6rem; min-height: 80px; transition: all 0.3s; }

        .btn-container {
            display: flex; justify-content: center; align-items: center;
            gap: 20px; height: 100px; position: relative;
        }

        button {
            padding: 12px 28px; font-size: 1.1rem; border: none;
            border-radius: 50px; cursor: pointer; font-weight: bold;
            transition: transform 0.15s ease-out, background-color 0.3s;
        }

        #yesBtn { background-color: #ff477e; color: white; z-index: 100; }
        #noBtn { background-color: #a0a0a0; color: white; position: relative; }

        /* Secret Note Styles */
        #secret-heart {
            position: fixed; bottom: 15px; right: 15px;
            font-size: 1.2rem; cursor: pointer; opacity: 0.1;
            transition: opacity 0.5s;
        }
        #secret-heart:hover { opacity: 1; color: red; }

        .modal {
            display: none; position: fixed; z-index: 1000;
            left: 0; top: 0; width: 100%; height: 100%;
            background-color: rgba(0,0,0,0.6); backdrop-filter: blur(5px);
        }
        .modal-content {
            background-color: white; margin: 15% auto; padding: 30px;
            border-radius: 25px; width: 80%; max-width: 350px; text-align: left;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }

        .calendar-btn {
            display: inline-block; margin-top: 20px; padding: 10px 20px;
            background: #4285F4; color: white; text-decoration: none;
            border-radius: 10px; font-size: 0.9rem;
        }

        .hidden { display: none; }
    </style>
</head>
<body>

    <div id="card">
        <img id="valentine-gif" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueGZ3bmZqZzR3eXp3eXp3eXp3eXp3eXp3eXp3eXp3eXp3JnB0PWEmZXA9djFfaW50ZXJuYWxfZ2lmX2J5X2lkJmN0PWc/c76IJLufpNUMo/giphy.gif" alt="Begging Puppy">
        
        <div id="question-ui">
            <h1 id="main-text">Will you be my Valentine? 🥺</h1>
            <div class="btn-container">
                <button id="yesBtn">YES!</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div id="success-ui" class="hidden">
            <h1 style="color: #ff477e;">Yay! Best decision ever! ❤️✨</h1>
            <p>I can't wait to spend the day with you!</
