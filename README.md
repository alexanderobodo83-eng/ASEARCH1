
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#ffffff">
    <title>Asearch – Private & Fast Search</title>

    <style>
        :root {
            --primary: #5f6368;          /* Subtle gray-blue like Google links */
            --primary-hover: #1a73e8;    /* Light blue on hover/focus only */
            --text: #202124;             /* Google's dark text */
            --gray: #5f6368;
            --light-gray: #f1f3f4;       /* Very light background */
            --bg: #ffffff;
            --border: #dadce0;
            --shadow: rgba(60,64,67,0.12);
        }

        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        header {
            width: 100%;
            padding: 16px 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255,255,255,0.96);
            backdrop-filter: blur(12px);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid var(--border);
        }

        .logo {
            font-size: 2.2rem;
            font-weight: 700;
            letter-spacing: -1px;
            color: #202124;
        }

        main {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 100%;
            max-width: 680px;
            padding: 0 24px;
        }

        h1 {
            margin: 48px 0 32px;
            font-size: 3.2rem;
            font-weight: 400;
            color: #202124;
        }

        .search-wrapper {
            position: relative;
            width: 100%;
            margin: 40px 0 24px;
        }

        .search-box {
            width: 100%;
            height: 56px;
            padding: 0 24px;
            border: 1px solid var(--border);
            border-radius: 8px;                /* Rectangular with soft corners */
            font-size: 17px;
            background: var(--light-gray);
            transition: all .2s;
            box-shadow: 0 1px 6px var(--shadow);
        }

        .search-box:focus {
            outline: none;
            border-color: var(--primary-hover);
            box-shadow: 0 1px 10px rgba(26,115,232,0.2);
        }

        .action-btns {
            display: flex;
            gap: 16px;
            margin: 24px 0;
        }

        .btn {
            padding: 10px 24px;
            border-radius: 6px;
            font-size: 15px;
            font-weight: 500;
            cursor: pointer;
            transition: all .2s;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
            border: none;
        }

        .btn-primary:hover,
        .btn-primary:focus {
            background: var(--primary-hover);
        }

        .btn-secondary {
            background: #ffffff;
            color: var(--text);
            border: 1px solid var(--border);
        }

        .btn-secondary:hover {
            background: var(--light-gray);
        }

        .alex-box {
            width: 100%;
            max-width: 600px;
            padding: 24px;
            background: white;
            border-radius: 16px;
            box-shadow: 0 4px 20px var(--shadow);
            margin-top: 32px;
        }

        .alex-header {
            display: flex;
            align-items: center;
            gap: 16px;
            margin-bottom: 16px;
        }

        .alex-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background: linear-gradient(135deg, #9e9e9e, #616161);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            font-weight: bold;
        }

        .alex-name { font-size: 20px; font-weight: 500; }

        .alex-chat {
            background: var(--light-gray);
            padding: 16px;
            border-radius: 12px;
            min-height: 60px;
            margin-bottom: 16px;
        }

        .input-area {
            display: flex;
            gap: 12px;
        }

        .alex-input {
            flex: 1;
            padding: 12px 16px;
            border: 1px solid var(--border);
            border-radius: 8px;                /* Also rectangular for consistency */
            font-size: 16px;
        }

        .send-btn {
            background: var(--primary);
            color: white;
            border: none;
            width: 48px;
            height: 48px;
            border-radius: 8px;                /* Rectangular send button */
            font-size: 20px;
            cursor: pointer;
        }

        .send-btn:hover { background: var(--primary-hover); }

        /* Full-screen Ad */
        #ad-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.85);
            z-index: 9999;
            color: white;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }

        .ad-content {
            background: white;
            color: black;
            padding: 32px;
            border-radius: 16px;
            max-width: 90%;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
        }

        .ad-close {
            margin-top: 20px;
            padding: 12px 32px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
        }

        .ad-close:hover { background: var(--primary-hover); }

        /* Sponsored Footer Banner */
        .sponsor-banner {
            width: 100%;
            background: #f8f9fa;
            padding: 16px;
            text-align: center;
            border-top: 1px solid var(--border);
            margin-top: auto;
        }

        .sponsor-banner h3 {
            margin-bottom: 8px;
            color: var(--gray);
        }

        .sponsor-banner a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
        }

        .sponsor-banner a:hover {
            color: var(--primary-hover);
            text-decoration: underline;
        }

        footer {
            padding: 16px 24px;
            color: var(--gray);
            font-size: 13px;
            text-align: center;
        }
    </style>
</head>
<body>

<div id="loading-bar" style="position:fixed;top:0;left:0;width:0%;height:3px;background:var(--primary-hover);transition:width 0.6s;z-index:9999;"></div>

<main>
    <header>
        <div class="logo">Asearch</div>
    </header>

    <h1>Private & Intelligent Search</h1>

    <div class="search-wrapper">
        <input type="text" id="query" class="search-box" placeholder="Search privately..." autocomplete="off">
    </div>

    <div class="action-btns">
        <button class="btn btn-primary" onclick="search()">Search</button>
        <button class="btn btn-secondary" onclick="lucky()">I'm Feeling Lucky</button>
    </div>

    <!-- Alex AI -->
    <div class="alex-box">
        <div class="alex-header">
            <div class="alex-avatar">A</div>
            <div>
                <div class="alex-name">Alex</div>
                <div style="color:var(--gray);font-size:14px;">Your private intelligent assistant</div>
            </div>
        </div>

        <div class="alex-chat" id="alexChat">
            Hello! I'm Alex — your fast, private assistant.
        </div>

        <div class="input-area">
            <input type="text" id="alexInput" class="alex-input" placeholder="Ask Alex anything...">
            <button class="send-btn" onclick="askAlex()">➤</button>
        </div>
    </div>
</main>

<!-- Full-screen Ad Overlay (every 30 seconds) -->
<div id="ad-overlay">
    <div class="ad-content">
        <h2 style="margin-bottom:16px;">Sponsored Advertisement</h2>
        <h3>UK Shoes Empire</h3>
        <p>We sell quality products at affordable prices.</p>
        <p>Call or WhatsApp us:<br>
        <a href="tel:+2347025643110">+234 702 564 3110</a></p>
        <p>Chat on WhatsApp:<br>
        <a href="https://wa.me/2347025643110" target="_blank" style="color:var(--primary);">Click here</a></p>
        <button class="ad-close" onclick="closeAd()">Continue to Asearch</button>
    </div>
</div>

<!-- Sponsored Footer Banner -->
<div class="sponsor-banner">
    <h3>Sponsored by UK Shoes Empire</h3>
    <p>Quality shoes at affordable prices • Call/WhatsApp: <a href="tel:+2347025643110">+234 702 564 3110</a></p>
    <p>Chat now: <a href="https://wa.me/2347025643110" target="_blank">Message on WhatsApp</a></p>
</div>

<footer>
    <p>© 2026 Asearch — 100% private, no tracking. <a href="#privacy" style="color:var(--primary);">Privacy Policy</a></p>
</footer>

<script>
// Fast Search
function search() {
    const q = document.getElementById('query').value.trim();
    if (!q) return;
    showLoading();
    setTimeout(() => {
        window.location.href = "https://duckduckgo.com/?q=" + encodeURIComponent(q);
    }, 600);
}

function lucky() {
    const q = document.getElementById('query').value.trim() || "privacy search";
    showLoading();
    setTimeout(() => {
        window.location.href = "https://duckduckgo.com/?q=" + encodeURIComponent(q);
    }, 600);
}

function showLoading() {
    const bar = document.getElementById('loading-bar');
    bar.style.width = '0%';
    requestAnimationFrame(() => bar.style.width = '100%');
    setTimeout(() => bar.style.width = '0%', 1200);
}

// Alex AI
function askAlex() {
    const input = document.getElementById('alexInput').value.trim();
    if (!input) return;

    const chat = document.getElementById('alexChat');
    chat.innerHTML += `<p style="margin:8px 0;color:#202124;"><strong>You:</strong> ${input}</p>`;

    let reply = "I'm happy to assist. Could you please clarify?";

    const q = input.toLowerCase();
    if (/hi|hello|hey/.test(q)) reply = "Hello! I'm Alex — your private assistant. How may I assist you today?";
    else if (/weather|temperature/.test(q)) reply = "I don't have live weather data yet — try searching 'weather in [city]' for instant results.";
    else if (/time|date|clock/.test(q)) reply = `It's currently ${new Date().toLocaleString('en-US', { timeZone: 'Africa/Lagos' })}.`;
    else if (/joke|laugh/.test(q)) reply = "Why do programmers prefer dark mode? Because light attracts bugs. 😏";
    else if (/who|what are you/.test(q)) reply = "I'm Alex — your fast, privacy-first AI assistant built exclusively for Asearch. No tracking, no data collection.";
    else reply = `Excellent question! Try searching "${input}" for the best results.`;

    chat.innerHTML += `<p style="margin:8px 0;color:#1a73e8;"><strong>Alex:</strong> ${reply}</p>`;
    chat.scrollTop = chat.scrollHeight;
}

// ────────────────────────────────────────────────
// AD LOGIC: Full-screen ad every 30 seconds
// ────────────────────────────────────────────────

function showAd() {
    document.getElementById('ad-overlay').style.display = 'flex';
}

function closeAd() {
    document.getElementById('ad-overlay').style.display = 'none';
}

setInterval(showAd, 30000);

</script>
</body>
</html>
