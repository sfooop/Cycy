<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أسعار الذهب في مصر لحظة بلحظة</title>
    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #f9f9f9;
            color: #333;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #d4af37;
            padding: 20px;
            text-align: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
        }
        main {
            padding: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            background-color: white;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        th, td {
            padding: 15px;
            text-align: center;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #f0e68c;
        }
        .update-time {
            margin-top: 10px;
            text-align: center;
            font-size: 14px;
            color: #666;
        }
        footer {
            background-color: #222;
            color: #aaa;
            text-align: center;
            padding: 15px;
            margin-top: 30px;
        }
        canvas {
            margin-top: 40px;
            display: block;
            max-width: 100%;
            margin-left: auto;
            margin-right: auto;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>

<header>
    أسعار الذهب في مصر لحظة بلحظة
</header>

<main>
    <h2 style="text-align:center;">أسعار الذهب اليوم</h2>
    <table>
        <thead>
            <tr>
                <th>العيار</th>
                <th>السعر بالجنيه المصري</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>عيار 24</td>
                <td id="gold24">3050 جنيه</td>
            </tr>
            <tr>
                <td>عيار 22</td>
                <td id="gold22">2795 جنيه</td>
            </tr>
            <tr>
                <td>عيار 21</td>
                <td id="gold21">2660 جنيه</td>
            </tr>
            <tr>
                <td>عيار 18</td>
                <td id="gold18">2285 جنيه</td>
            </tr>
            <tr>
                <td>الجنيه الذهب</td>
                <td id="goldCoin">21280 جنيه</td>
            </tr>
            <tr>
                <td>أونصة الذهب</td>
                <td id="goldOunce">2375 دولار</td>
            </tr>
        </tbody>
    </table>

    <div class="update-time" id="lastUpdate">
        آخر تحديث: 27 إبريل 2025 - 2:00 مساءً
    </div>

    <canvas id="goldChart" width="400" height="200"></canvas>
</main>

<footer>
    جميع الحقوق محفوظة © 2025
</footer>

<script>
// محاكاة جلب البيانات (يمكنك استخدام API حقيقي هنا)
async function fetchGoldPrices() {
    try {
        const goldPrices = {
            gold24: 3050,
            gold22: 2795,
            gold21: 2660,
            gold18: 2285,
            goldCoin: 21280,
            goldOunce: 2375
        };

        // تحديث الأسعار في الجدول
        document.getElementById('gold24').innerText = `${goldPrices.gold24} جنيه`;
        document.getElementById('gold22').innerText = `${goldPrices.gold22} جنيه`;
        document.getElementById('gold21').innerText = `${goldPrices.gold21} جنيه`;
        document.getElementById('gold18').innerText = `${goldPrices.gold18} جنيه`;
        document.getElementById('goldCoin').innerText = `${goldPrices.goldCoin} جنيه`;
        document.getElementById('goldOunce').innerText = `${goldPrices.goldOunce} دولار`;

        // تحديث وقت آخر تحديث
        const now = new Date();
        const timeString = now.toLocaleString('ar-EG');
        document.getElementById('lastUpdate').innerText = `آخر تحديث: ${timeString}`;

    } catch (error) {
        console.error("حدث خطأ أثناء جلب الأسعار:", error);
    }
}

// استدعاء التحديث أول ما تفتح الصفحة
fetchGoldPrices();

// تحديث تلقائي كل 10 دقائق
setInterval(fetchGoldPrices, 10 * 60 * 1000);

// رسم بياني لحركة الأسعار
const ctx = document.getElementById('goldChart').getContext('2d');
const goldChart = new Chart(ctx, {
    type: 'line',
    data: {
        labels: ['السبت', 'الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة'],
        datasets: [{
            label: 'سعر الذهب عيار 24',
            data: [3000, 3020, 3040, 3030, 3050
