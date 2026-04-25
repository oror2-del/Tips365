<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AAA365 | Premium Analytics</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Assistant:wght@200;400;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Assistant', sans-serif; background: #05070a; color: #fff; overflow-x: hidden; }
        .premium-card { background: rgba(255, 255, 255, 0.03); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.05); border-radius: 24px; }
        .win-gradient { background: linear-gradient(135deg, #22c55e 0%, #15803d 100%); }
        .modal { display: none; position: fixed; inset: 0; z-index: 50; background: rgba(0,0,0,0.9); backdrop-filter: blur(10px); }
    </style>
</head>
<body class="p-6">
    <div class="flex justify-between items-center mb-12">
        <div>
            <h1 class="text-4xl font-extrabold tracking-tighter">AAA365<span class="text-blue-500">.</span></h1>
            <p class="text-gray-500 text-sm">PREMIUM ALGORITHMS</p>
        </div>
        <div class="w-12 h-12 rounded-full border border-white/10 flex items-center justify-center">
            <div class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
        </div>
    </div>

    <div class="space-y-4">
        <div onclick="openModal()" class="premium-card p-6 flex items-center justify-between cursor-pointer active:scale-95 transition-all">
            <div class="flex items-center gap-4">
                <div class="w-14 h-14 rounded-2xl bg-orange-500/10 flex items-center justify-center text-3xl text-orange-500">🏀</div>
                <div>
                    <h2 class="text-xl font-bold">ניתוח NBA</h2>
                    <p class="text-green-500 text-xs font-bold">2 זכיות חדשות ✅</p>
                </div>
            </div>
            <div class="text-gray-600">◀</div>
        </div>
    </div>

    <div id="nbaModal" class="modal p-6 overflow-y-auto">
        <div class="flex justify-between items-center mb-8">
            <h2 class="text-3xl font-bold">תוצאות NBA</h2>
            <button onclick="closeModal()" class="text-2xl text-gray-500">✕</button>
        </div>
        
        <div class="space-y-4">
            <div class="premium-card p-6 border-l-4 border-green-500">
                <div class="flex justify-between items-start">
                    <div>
                        <p class="text-gray-400 text-xs">דנבר - לייקרס</p>
                        <h3 class="text-lg font-bold uppercase">Denver Win</h3>
                    </div>
                    <span class="bg-green-500/20 text-green-500 text-xs px-2 py-1 rounded">✅ זכה</span>
                </div>
                <p class="mt-2 text-2xl font-bold text-white">2,760 <span class="text-xs text-gray-500">RUB</span></p>
            </div>

            <div class="premium-card p-6 border-l-4 border-green-500">
                <div class="flex justify-between items-start">
                    <div>
                        <p class="text-gray-400 text-xs">אורלנדו (4+)</p>
                        <h3 class="text-lg font-bold uppercase">Orlando Magic</h3>
                    </div>
                    <span class="bg-green-500/20 text-green-500 text-xs px-2 py-1 rounded">✅ זכה</span>
                </div>
                <p class="mt-2 text-2xl font-bold text-white">3,375 <span class="text-xs text-gray-500">RUB</span></p>
            </div>
        </div>
    </div>

    <script>
        function openModal() { document.getElementById('nbaModal').style.display = 'block'; }
        function closeModal() { document.getElementById('nbaModal').style.display = 'none'; }
    </script>
</body>
</html>
