# Ganga-Bhumi-Club
Login Portal for the users of Ganga Bhumi Club


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ganga Bhumi Club Login</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            position: relative;
            background: orange; /* Background color set to orange */
        }

        .container {
            background: rgba(255, 255, 255, 0.9); /* White background with some transparency */
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
            max-width: 400px;
            width: 100%;
            position: relative;
            z-index: 1; /* Ensure it stays above the background */
            transition: transform 0.3s ease; /* Smooth transition for scaling */
        }

        .container:hover {
            transform: scale(1.02); /* Slightly enlarge on hover */
        }

        h1 {
            text-align: center;
            color: #4CAF50; /* Forest green */
            font-size: 2rem;
            margin-bottom: 1.5rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #555;
        }

        input {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 1rem;
            background: #f4f4f9;
            box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: border-color 0.3s ease; /* Smooth transition for border color */
        }

        input:focus {
            outline: none;
            border-color: #4CAF50; /* Green border on focus */
            background: #e3e3f2;
        }

        button {
            width: 100%;
            padding: 0.8rem;
            background: #4CAF50; /* Green button */
            color: #fff;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }

        .redirect {
            text-align: center;
            margin-top: 1rem;
        }

        .redirect a {
            color: #4CAF50;
            text-decoration: none;
            font-weight: bold;
        }

        .redirect a:hover {
            text-decoration: underline;
        }

        /* Error Message Styles */
        .error-message {
            color: red;
            font-size: 0.9rem;
            margin-top: 0.5rem;
            display: none; /* Initially hidden */
            animation: fadeIn 0.3s ease; /* Animation for error message */
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        /* Animated Background */
        .background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .sun {
            position: absolute;
            background: radial-gradient(circle, red 40%, transparent 50%); /* Sun color set to red */
            border-radius: 50%;
            width: 100px;
            height: 100px;
            top: 20%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: rise 10s ease-in-out infinite;
        }

        @keyframes rise {
            0% {
                top: 20%;
                opacity: 0;
            }
            50% {
                top: 10%;
                opacity: 1;
            }
            100% {
                top: 20%;
                opacity: 0;
            }
        }

        .bird {
            position: absolute;
            width: 50px;
            height: 30px;
            background: url('https://example.com/path/to/bird.png') no-repeat center center; /* Replace with your bird image */
            background-size: contain;
            animation: fly 10s linear infinite;
        }

        @keyframes fly {
            0% {
                left: -10%;
                transform: translateY(0);
            }
            100% {
                left: 110%;
                transform: translateY(-50px);
            }
        }

        /* Add multiple birds with different animation delays */
        .bird:nth-child(1) { animation-delay: 0s; }
        .bird:nth-child(2) { animation-delay: 2s; }
        .bird:nth-child(3) { animation-delay: 4s; }
        .bird:nth-child(4) { animation-delay: 6s; }
        .bird:nth-child(5) { animation-delay: 8s; }

        /* River Animation */
        .river {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: url('https://example.com/path/to/river.png') repeat-x; /* Replace with your river image */
            animation: flow 5s linear infinite;
        }

        @keyframes flow {
            from {
                background-position: 0 0;
            }
            to {
                background-position: 100% 0;
            }
        }

        .title {
            position: absolute;
            top: 5%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            color: black; /* Title color set to black */
            text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.7);
            z-index: 1;
        }
    </style>
</head>
<body>
    <div class="background">
        <div class="sun"></div>
        <div class="bird" style="top: 15%;"></div>
        <div class="bird" style="top: 25%;"></div>
        <div class="bird" style="top: 35%;"></div>
        <div class="bird" style="top: 45%;"></div>
        <div class="bird" style="top: 55%;"></div>
        <div class="river"></div>
    </div>
    <div class="title">Ganga Bhumi Club</div>
    <div class="container" id="loginPage">
        <h1>Login</h1>
        <form id="loginForm">
            <div class="form-group">
                <label for="loginEmailOrMobile">Email/Mobile Number</label>
                <input type="text" id="loginEmailOrMobile" placeholder="Enter your email or mobile number" required>
                <div class="error-message" id="loginEmailError">Invalid email or mobile number.</div>
            </div>
            <div class="form-group">
                <label for="loginPassword">Password</label>
                <input type="password" id="loginPassword" placeholder="Enter your password" required>
                <div class="error-message" id="loginPasswordError">Password cannot be empty.</div>
            </div>
            <button type="button" onclick="handleLogin()">Login</button>
        </form>
        <div class="redirect">
            <p>New user? <a href="#" onclick="redirectToSignUp()">Sign-Up</a></p>
        </div>
    </div>
    <script>
        function validateEmail(email) {
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            const phoneRegex = /^[0-9]{10}$/; // Assuming a 10-digit mobile number
            return emailRegex.test(email) || phoneRegex.test(email);
        }

        function handleLogin() {
            const loginEmailOrMobile = document.getElementById("loginEmailOrMobile").value;
            const loginPassword = document.getElementById("loginPassword").value;
            const loginEmailError = document.getElementById("loginEmailError");
            const loginPasswordError = document.getElementById("loginPasswordError");

            // Clear previous error messages
            loginEmailError.style.display = "none";
            loginPasswordError.style.display = "none";

            // Validate email/mobile number
            if (!validateEmail(loginEmailOrMobile)) {
                loginEmailError.style.display = "block";
                loginEmailError.classList.add('fadeIn');
                return;
            }

            // Validate password
            if (loginPassword.trim() === "") {
                loginPasswordError.style.display = "block";
                loginPasswordError.classList.add('fadeIn');
                return;
            }

            // Simulate successful login (replace with actual login logic)
            alert("Login Successful!");
        }

        function redirectToSignUp() {
            // Redirect to sign-up logic
            alert("Redirecting to Sign-Up page...");
        }
    </script>
</body>
</html>
