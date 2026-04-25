<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AAA365 | Premium</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Assistant:wght@200;400;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Assistant', sans-serif; background: #05070a; color: #fff; min-height: 100vh; position: relative; }
        body::before {
            content: ""; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: url('https://images.unsplash.com/photo-1546519638-68e109498ffc?q=80&w=2000') center/cover;
            filter: blur(40px) brightness(0.2); z-index: -1;
        }
        .premium-card { background: rgba(255, 255, 255, 0.03); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.05); transition: all 0.4s ease; cursor: pointer; }
        .tip-entry { border-right: 4px solid; background: rgba(0,0,0,0.3); margin-bottom: 1rem; border-radius: 12px; }
        .hidden-list { display: none; animation: slideIn 0.4s ease-out; }
        @keyframes slideIn { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="p-6 md:p-12">
    <div class="max-w-xl mx-auto">
        <header class="mb-12 text-center">
            <h1 class="text-4xl font-black tracking-tighter mb-1">AAA<span class="text-amber-500">365</span></h1>
            <p class="text-[10px] text-gray-500 tracking-[0.2em] uppercase font-bold text-center">קופה: 1,000₪ | ניהול חכם</p>
        </header>
        <div class="space-y-4">
            <div onclick="toggle('nba')" class="premium-card rounded-[2rem] p-8">
                <div class="flex justify-between items-center">
                    <div class="flex items-center gap-4"><span class="text-2xl">🏀</span><h2 class="text-lg font-bold">טפסי NBA</h2></div>
                    <span id="nba-count" class="text-[10px] text-amber-500">מנתח...</span>
                </div>
                <div id="nba-list" class="hidden-list mt-8"></div>
            </div>
            <div onclick="toggle('math')" class="premium-card rounded-[2rem] p-8">
                <div class="flex justify-between items-center">
                    <div class="flex items-center gap-4"><span class="text-2xl">💎</span><h2 class="text-lg font-bold">מצוינות מתמטית</h2></div>
                    <span id="math-count" class="text-[10px] text-emerald-400">מנתח...</span>
                </div>
                <div id="math-list" class="hidden-list mt-8"></div>
            </div>
            <div onclick="toggle('league')" class="premium-card rounded-[2rem] p-8">
                <div class="flex justify-between items-center">
                    <div class="flex items-center gap-4"><span class="text-2xl">⚽</span><h2 class="text-lg font-bold">ליגות בכירות</h2></div>
                    <span id="league-count" class="text-[10px] text-blue-400">מנתח...</span>
                </div>
                <div id="league-list" class="hidden-list mt-8"></div>
            </div>
        </div>
    </div>
    <script>
        function toggle(id) {
            const list = document.getElementById(id + '-list');
            list.style.display = (list.style.display === 'block') ? 'none' : 'block';
        }
        async function fetchTips() {
            try {
                const r = await fetch('/api/get-tips');
                const d = await r.json();
                const colors = { nba: '#f59e0b', math: '#10b981', league: '#3b82f6' };
                ['nba', 'math', 'league'].forEach(cat => {
                    const filtered = d.tips.filter(t => t.cat === cat);
                    document.getElementById(cat + '-count').innerText = filtered.length + " טפסים";
                    document.getElementById(cat + '-list').innerHTML = filtered.map(t => `
                        <div class="tip-entry p-5" style="border-right-color: ${colors[cat]}">
                            <h4 class="font-bold text-white mb-2">${t.m}</h4>
                            <div class="flex justify-between items-end">
                                <div><p class="text-amber-400 font-bold">${t.p}</p><p class="text-[10px] text-gray-500">יחס: ${t.o}</p></div>
                                <div class="text-right"><p class="text-lg font-black text-white">${t.s}</p></div>
                            </div>
                        </div>
                    `).join('');
                });
            } catch(e) {}
        }
        fetchTips();
        setInterval(fetchTips, 30000);
    </script>
</body>
</html>
