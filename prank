<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>System Security Alert</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: #000;
            color: #ff0000;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .ransom-container {
            background: #111;
            border: 2px solid #ff0000;
            border-radius: 10px;
            padding: 40px;
            max-width: 600px;
            text-align: center;
            box-shadow: 0 0 30px rgba(255, 0, 0, 0.5);
            animation: glitch 2s infinite;
        }

        @keyframes glitch {
            0%, 100% { transform: translate(0); }
            20% { transform: translate(-2px, 2px); }
            40% { transform: translate(-2px, -2px); }
            60% { transform: translate(2px, 2px); }
            80% { transform: translate(2px, -2px); }
        }

        .warning-icon {
            font-size: 80px;
            margin-bottom: 20px;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.1); }
        }

        h1 {
            font-size: 36px;
            margin-bottom: 20px;
            text-shadow: 0 0 10px #ff0000;
        }

        .warning-text {
            font-size: 18px;
            line-height: 1.6;
            margin-bottom: 30px;
        }

        .countdown {
            font-size: 24px;
            margin: 20px 0;
            padding: 15px;
            background: #222;
            border: 1px solid #ff0000;
            border-radius: 5px;
        }

        .payment-section {
            background: #1a1a1a;
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
            border: 1px solid #ff0000;
        }

        .qr-placeholder {
            width: 150px;
            height: 150px;
            background: #fff;
            margin: 20px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            color: #000;
        }

        .bitcoin-address {
            font-family: monospace;
            word-break: break-all;
            background: #222;
            padding: 10px;
            margin: 10px 0;
            border-radius: 3px;
            font-size: 14px;
        }

        .fake-button {
            background: #ff0000;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            margin: 10px;
            transition: all 0.3s;
        }

        .fake-button:hover {
            background: #cc0000;
            transform: scale(1.05);
        }

        .hidden-exit {
            position: absolute;
            bottom: 20px;
            right: 20px;
            background: transparent;
            border: 1px solid #333;
            color: #333;
            padding: 5px 10px;
            font-size: 12px;
            cursor: pointer;
            border-radius: 3px;
            transition: all 0.3s;
        }

        .hidden-exit:hover {
            background: #333;
            color: #fff;
        }

        .terminal {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 100px;
            background: rgba(0, 0, 0, 0.8);
            padding: 10px;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            color: #0f0;
            overflow-y: auto;
            border-top: 1px solid #333;
        }

        .terminal-line {
            margin: 2px 0;
        }

        .error-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: #222;
            border: 2px solid #ff0000;
            padding: 20px;
            border-radius: 5px;
            display: none;
            z-index: 1000;
        }
    </style>
</head>
<body>
    <div class="ransom-container">
        <div class="warning-icon">⚠️</div>
        <h1>YOUR FILES HAVE BEEN ENCRYPTED!</h1>
        
        <div class="warning-text">
            <p>All your documents, photos, databases and other important files have been locked with our unique encryption.</p>
            <p>You cannot access them without our decryption key.</p>
            <p>If you want to restore your files, you must pay a ransom of <strong>0.5 BTC</strong> within the time limit.</p>
        </div>

        <div class="countdown">
            <div>TIME REMAINING:</div>
            <div id="timer">10:00</div>
        </div>

        <div class="payment-section">
            <h3>Payment Instructions</h3>
            <p>Send exactly 0.5 BTC to this address:</p>
            <div class="bitcoin-address">1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa</div>
            <div class="qr-placeholder">
                <div>QR Code<br>(Scan to pay)</div>
            </div>
            <p>After payment, your files will be automatically decrypted within 1 hour.</p>
        </div>

        <button class="fake-button" onclick="showPaymentError()">Pay Now</button>
        <button class="fake-button" onclick="showDecryptionError()">Decrypt Files</button>
    </div>

    <div class="hidden-exit" onclick="exitPrank()">[X]</div>

    <div class="terminal" id="terminal">
        <div class="terminal-line">> Initializing encryption module...</div>
        <div class="terminal-line">> Scanning file system...</div>
        <div class="terminal-line">> Encrypting files: 100% complete</div>
        <div class="terminal-line">> Deleting shadow copies...</div>
        <div class="terminal-line">> System locked. Waiting for payment...</div>
    </div>

    <div class="error-message" id="errorMessage">
        <h3>ERROR</h3>
        <p id="errorText">Payment failed. Try again later.</p>
        <button class="fake-button" onclick="hideError()">OK</button>
    </div>

    <script>
        // Countdown timer
        let timeLeft = 600; // 10 minutes in seconds
        const timerElement = document.getElementById('timer');
        
        const countdown = setInterval(() => {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            timerElement.textContent = `${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            
            if (timeLeft <= 0) {
                clearInterval(countdown);
                timerElement.textContent = "TIME EXPIRED";
                timerElement.style.color = "#ff0000";
                showTerminalMessage("> Payment time expired. Files will be deleted permanently.");
            }
            timeLeft--;
        }, 1000);

        // Terminal messages
        function showTerminalMessage(message) {
            const terminal = document.getElementById('terminal');
            const line = document.createElement('div');
            line.className = 'terminal-line';
            line.textContent = "> " + message;
            terminal.appendChild(line);
            terminal.scrollTop = terminal.scrollHeight;
        }

        // Error messages
        function showPaymentError() {
            document.getElementById('errorText').textContent = "Payment gateway unavailable. Please try again later.";
            document.getElementById('errorMessage').style.display = 'block';
            showTerminalMessage("> Payment attempt failed - network error");
        }

        function showDecryptionError() {
            document.getElementById('errorText').textContent = "Decryption key required. Payment must be completed first.";
            document.getElementById('errorMessage').style.display = 'block';
            showTerminalMessage("> Decryption attempt failed - no valid key found");
        }

        function hideError() {
            document.getElementById('errorMessage').style.display = 'none';
        }

        // Exit prank
        function exitPrank() {
            if (confirm("Are you sure you want to exit the prank?")) {
                document.body.innerHTML = `
                    <div style="display: flex; justify-content: center; align-items: center; height: 100vh; background: #000; color: #0f0; font-family: monospace; text-align: center;">
                        <div>
                            <h1>PRANK COMPLETE!</h1>
                            <p>Your files were never actually encrypted.</p>
                            <p>This was just a joke - hope you enjoyed it!</p>
                            <button onclick="location.reload()" style="margin-top: 20px; padding: 10px 20px; background: #0f0; color: #000; border: none; cursor: pointer; border-radius: 5px;">Run Prank Again</button>
                        </div>
                    </div>
                `;
            }
        }

        // Simulate "hacking" activity
        const hackingMessages = [
            "Scanning network vulnerabilities...",
            "Bypassing security protocols...",
            "Installing persistence mechanisms...",
            "Exfiltrating sensitive data...",
            "Encrypting cloud backups...",
            "Disabling system restore...",
            "Hiding forensic traces..."
        ];

        setInterval(() => {
            const randomMessage = hackingMessages[Math.floor(Math.random() * hackingMessages.length)];
            showTerminalMessage(randomMessage);
        }, 5000);

        // Prevent closing with standard methods
        window.addEventListener('beforeunload', (e) => {
            e.preventDefault();
            e.returnValue = 'Your files are still encrypted! Are you sure you want to leave?';
        });
    </script>
</body>
</html>
