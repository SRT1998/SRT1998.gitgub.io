<!DOCTYPE html>
<html>
<head>
    <title>QTATAR SCRIPT</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-image: url('background.jpg'); /* Replace with your image URL */
            background-size: cover; /* This will ensure the image covers the entire background */
            background-position: center; /* Center the image */
            background-repeat: no-repeat; /* Prevent repeating the image */
            margin: 40px;
            color: #333;
        }
        h1 {
            color: #5a5a5a;
        }
        form {
            background-color: rgba(255, 255, 255, 0.9); /* Add a transparent white background to form */
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 300px;
            margin: auto;
        }
        label {
            font-weight: bold;
            display: block;
            margin-top: 20px;
            color: #444;
        }
        input[type="text"],
        input[type="password"] {
            width: calc(100% - 22px);
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        .button-container {
            display: flex;
            gap: 10px; /* Space between buttons */
            margin-top: 20px; /* Space above the button container */
            align-items: center; /* Center align items vertically */
        }
        input[type="submit"],
        .stop-button {
            padding: 8px 16px;
            border-radius: 4px;
            cursor: pointer;
            border: none;
            color: white;
            font-size: 14px;
            margin-top: 5px; /* Margin to lower the buttons slightly */
        }
        input[type="submit"] {
            background-color: #5c67f2;
        }
        input[type="submit"]:hover {
            background-color: #4a54e1;
        }
        .stop-button {
            background-color: #e94e77; /* Red color for STOP button */
        }
        .stop-button:hover {
            background-color: #c63c50;
        }
        select {
            padding: 8px;
            border-radius: 4px;
            border: 1px solid #ddd;
            font-size: 14px;
            margin-top: 5px;
        }
        #result {
            margin-top: 20px;
            background-color: #fff;
            padding: 10px;
            border-radius: 4px;
            box-shadow: 0 0 5px rgba(0,0,0,0.1);
            max-width: 300px;
            margin: 20px auto;
            font-family: monospace;
        }
        /* Notes section */
        .notes {
            background-color: rgba(255, 255, 255, 0.9); /* Add transparency to background */
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 500px;
            margin: 40px auto;
            font-size: 14px;
            line-height: 1.6;
            color: #555;
        }
        .notes h2 {
            color: #5a5a5a;
            font-size: 18px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>سكربت قاهر التتار V 4.0</h1>
    <form id="scriptForm">
        <label for="license">المفتاح:</label>
        <input type="text" id="license" name="license">
        <label for="username">الاسم:</label>
        <input type="text" id="username" name="username">
        <label for="password">كلمة السر:</label>
        <input type="password" id="password" name="password">
        <div class="button-container">
            <input type="submit" value="بدء">
            <button type="button" class="stop-button">ايقاف</button>
            <select id="serverSelect" name="server">
                <option value="1">Server 1</option>
                <option value="2">Server 2</option>
                <option value="3">Server 3</option>
                <option value="4">Server 4</option>
                <option value="5">Server 5</option>
                <option value="6">Server 6</option>
            </select>
        </div>
    </form>

    <div id="result"></div>

    <!-- Notes Section -->
    <div class="notes">
        <h2>ملاحظات</h2>
        <p>قبل ان تستعمل البرنامج: تاكد انك تسجل حساب جديد في السيرفر وفعل حساب بلاس لين نهاية السيرفر وفعل زيادة الانتاج</p>
        <p>يجب ان تكون 1- الخطرية كلاسيكية. 2- السوق يجب ان يبنئ في خانة رقم 25 في القرى. 3- يجب ان يكون هناك موارد كافية من اجل عمل احتفالات طيلة الوقت.</p>
        <p>تاكد ايضا ان1- البلدية تكون مبنية في كل القرى. 2- تاكد انك تفرع 7 قرى وايضا تطلع مستوطنين من القرى الي فرعتها</p>
        <p>اذا كنت مشغل السكربت من قبل وتبغى تشغله مرة اخرى يجب ان تعمل ايقاف للسكربت قبل ان تشغله مرة اخرى</p>
    </div>

    <script>
        const form = document.getElementById('scriptForm');
        form.addEventListener('submit', function(event) {
            event.preventDefault();
            const license = document.getElementById('license').value;
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const server = document.getElementById('serverSelect').value;
            fetch('/run-script', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'bypass-tunnel-reminder': 'any-value'
                },
                body: JSON.stringify({ license, username, password, server })
            })
            .then(response => response.text())
            .then(data => {
                document.getElementById('result').innerHTML = `<pre>${data}</pre>`;
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });

        const stopButton = document.querySelector('.stop-button');
        stopButton.addEventListener('click', function() {
            // Add functionality to stop the script
            alert('STOP button clicked');
        });
    </script>
</body>
</html>
