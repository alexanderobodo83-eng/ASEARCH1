<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#ffffff">
    <title>Asearch – Private & Fast Search</title>

    <!-- Unity Ads SDK -->
    <script src="https://unityads.unity3d.com/webgl/unityads.js"></script>

    <style>
        :root {
            --primary: #1a73e8;
            --text: #202124;
            --gray: #5f6368;
            --bg: #ffffff;
        }

        body {
            margin: 0;
            font-family: system-ui, sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding-bottom: 120px; /* space for sponsor banner */
        }

        .logo {
            font-size: 5.5rem;
            font-weight: 900;
            letter-spacing: -5px;
            color: #000000;
            margin: 60px 0 80px;
        }

        .search-container {
            width: 100%;
            max-width: 620px;
            padding: 0 24px;
        }

        .search-bar {
            background: white;
            border-radius: 999px;
            padding: 18px 28px;
            box-shadow: 0 6px 24px rgba(0,0,0,0.15);
            font-size: 1.25rem;
            border: 1px solid #dadce0;
        }

        .search-bar input {
            width: 100%;
            border: none;
            outline: none;
            background: transparent;
            font-size: inherit;
            color: var(--text);
        }

        .sponsor-banner {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: #f8f9fa;
            padding: 16px;
            text-align: center;
            border-top: 1px solid #dadce0;
            font-size: 1rem;
            z-index: 10;
        }

        .sponsor-banner a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
        }
    </style>
</head>
<body>

<div class="search-container">
    <div class="logo">Asearch</div>

    <div class="search-bar">
        <input type="text" id="query" placeholder="Search or type web address" autocomplete="off">
    </div>
</div>

<div class="sponsor-banner">
    <strong>Sponsored by UK Shoes Empire</strong> • Quality shoes at affordable prices • 
    Call/WhatsApp: <a href="tel:+2347025643110">+234 702 564 3110</a> • 
    <a href="https://wa.me/2347025643110" target="_blank">Chat now</a>
</div>

<script>
// Unity Ads – your real details
const unityGameId = '6049700';
const interstitialPlacement = 'Interstitial_Android';

// Initialize Unity Ads and show interstitial immediately on load
if (typeof unityads !== 'undefined') {
    unityads.init(unityGameId, true, function() {  // true = test mode (change to false for real ads)
        console.log('Unity Ads initialized');
        unityads.show(interstitialPlacement);
    });
} else {
    console.log('Unity Ads SDK not loaded');
}

// Search – loads Google in the same window (inside app/webview)
document.getElementById('query').addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
        const q = this.value.trim();
        if (q) {
            window.location.href = `https://www.google.com/search?q=${encodeURIComponent(q)}`;
        }
    }
});

</script>
</body>
</html>
