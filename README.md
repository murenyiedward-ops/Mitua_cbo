<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>German Institute | Official Registration</title>
    <style>
        /* Modern Purple Blend */
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background: linear-gradient(135deg, #4834d4 0%, #686de0 50%, #2f3542 100%);
            background-attachment: fixed;
            min-height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #2d3436;
        }

        .portal-card {
            background: #ffffff;
            width: 480px;
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .inst-header {
            background: #000;
            color: #fff;
            padding: 25px;
            text-align: center;
            letter-spacing: 3px;
            font-size: 0.8rem;
            border-bottom: 4px solid #dd0000; /* Subtle German flag reference */
        }

        .main-content {
            padding: 40px;
            text-align: center;
        }

        .label {
            font-size: 0.85rem;
            color: #636e72;
            text-transform: uppercase;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .deadline-text {
            font-size: 2.2rem;
            font-weight: 900;
            color: #4834d4;
            margin-bottom: 30px;
        }

        /* The Status Bar / Badge */
        .status-container {
            display: inline-block;
            padding: 10px 24px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.9rem;
            margin-bottom: 30px;
            transition: all 0.3s ease;
        }

        .status-urgent {
            background: #fff3cd;
            color: #856404;
            border: 1px solid #ffeeba;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
            animation: pulse 2s infinite;
        }

        .status-closed {
            background: #ffeaea;
            color: #d63031;
            border: 1px solid #fab1a0;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        .btn-action {
            display: block;
            width: 100%;
            padding: 18px;
            background: #4834d4;
            color: white;
            text-decoration: none;
            border-radius: 12px;
            font-weight: 700;
            transition: background 0.3s;
        }

        .btn-action:hover { background: #3c2bb3; }

        .btn-disabled {
            background: #dfe6e9 !important;
            color: #b2bec3 !important;
            cursor: not-allowed;
            pointer-events: none;
        }
    </style>
</head>
<body>

<div class="portal-card">
    <div class="inst-header">GERMAN INSTITUTE</div>
    
    <div class="main-content">
        <div class="label">Assessment Deadline</div>
        <div class="deadline-text" id="date-display">--</div>

        <div id="status-bar" class="status-container">
            Analyzing Status...
        </div>

        <a href="#" id="reg-link" class="btn-action">PROCEED TO BOOKING NOW</a>
    </div>
</div>

<script>
    // Config: Today (Jan 31, 2026)
    const DEADLINE = new Date(2026, 0, 31);
    const TODAY = new Date();

    function setupPortal() {
        const display = document.getElementById('date-display');
        const statusBar = document.getElementById('status-bar');
        const regLink = document.getElementById('reg-link');

        // Display Date
        display.innerText = DEADLINE.toLocaleDateString('en-GB', {
            day: '2-digit', month: 'long', year: 'numeric'
        });

        // Date logic (Ignoring time for day-based comparison)
        const tDate = new Date(TODAY.getFullYear(), TODAY.getMonth(), TODAY.getDate()).getTime();
        const dDate = new Date(DEADLINE.getFullYear(), DEADLINE.getMonth(), DEADLINE.getDate()).getTime();

        if (tDate === dDate) {
            statusBar.innerHTML = "• FINAL DAY TO REGISTER";
            statusBar.className += " status-urgent";
        } else if (tDate < dDate) {
            statusBar.innerText = "REGISTRATION OPEN";
            statusBar.style.background = "#e3fcef";
            statusBar.style.color = "#006b5f";
        } else {
            statusBar.innerText = "REGISTRATION EXPIRED";
            statusBar.className += " status-closed";
            regLink.innerText = "PORTAL CLOSED";
            regLink.classList.add('btn-disabled');
        }
    }

    window.onload = setupPortal;
</script>

</body>
</html>
