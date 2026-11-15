<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <meta name="theme-color" content="#03060a">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>MK INDUSTRIES | OWNER & CEO FURQAN MK SCANNER</title>
    <!-- Core Production Libraries -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html5-qrcode/2.3.8/html5-qrcode.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        :root {
            --bg-black: #03060a;
            --card-dark: #080d14;
            --neon-blue: #00f3ff;
            --neon-glow: rgba(0, 243, 255, 0.45);
            --text-white: #ffffff;
            --text-gray: #8ca0b3;
            --accent-blue: #0088ff;
            --btn-border: #00f3ff;
            --pure-black: #000000;
            --success-green: #00ff88;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            user-select: none;
            -webkit-user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-black);
            color: var(--text-white);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            min-height: 100svh;
            width: 100vw;
            padding: 6px;
            overflow-x: hidden;
            overflow-y: auto;
        }

        .app-frame {
            width: 100%;
            max-width: 410px;
            height: 98svh;
            max-height: 870px;
            min-height: 540px;
            background: var(--card-dark);
            border-radius: 26px;
            padding: 12px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            border: 2px solid var(--neon-blue);
            box-shadow: 0 0 16px var(--neon-glow), inset 0 0 10px rgba(0, 243, 255, 0.25);
            overflow: hidden;
        }

        .app-top-block {
            display: flex;
            flex-direction: column;
            gap: 6px;
            flex-shrink: 0;
            margin-bottom: 6px;
        }

        .top-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
            padding: 2px 0;
            height: 36px;
        }

        .header-left-slot {
            display: flex;
            align-items: center;
            justify-content: flex-start;
            flex-shrink: 0;
        }

        .header-spacer {
            width: 32px;
            height: 32px;
            display: block;
        }

        .top-left-frame-close-btn {
            background: rgba(0, 243, 255, 0.12);
            border: 1.5px solid var(--neon-blue);
            color: var(--neon-blue);
            width: 32px;
            height: 32px;
            border-radius: 50%;
            font-size: 14px;
            font-weight: 900;
            display: none;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 0 10px rgba(0, 243, 255, 0.35);
            flex-shrink: 0;
        }

        .brand-title {
            flex: 1;
            text-align: center;
            font-size: clamp(10px, 3.2vw, 12px);
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.6px;
            text-transform: uppercase;
            text-shadow: 0 0 8px var(--neon-glow);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            padding: 0 4px;
        }

        .icon-btn {
            background: none;
            border: none;
            color: var(--neon-blue);
            font-size: 22px;
            cursor: pointer;
            padding: 6px;
            flex-shrink: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            line-height: 1;
        }

        button:active, 
        .btn-3d:active, 
        .action-btn:active, 
        .icon-btn:active,
        .top-left-frame-close-btn:active,
        .star-btn:active {
            transform: scale(0.96) !important;
            transition: transform 0.04s ease !important;
        }

        .tab-switcher {
            display: flex;
            background: #0d1622;
            border-radius: 16px;
            padding: 3px;
            border: 1px solid #1a2c40;
            flex-shrink: 0;
            gap: 4px;
        }

        .tab-btn {
            flex: 1;
            padding: 10px 12px;
            border: none;
            background: transparent;
            color: var(--text-gray);
            font-size: 13px;
            font-weight: 700;
            border-radius: 13px;
            cursor: pointer;
            transition: all 0.2s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .tab-btn.active {
            background: linear-gradient(135deg, var(--accent-blue), var(--neon-blue));
            color: #000000;
            box-shadow: 0 0 12px var(--neon-glow);
            font-weight: 800;
        }

        .tab-content { 
            display: none; 
            width: 100%;
            flex: 1;
            flex-direction: column;
            justify-content: space-between;
            min-height: 0;
            overflow: hidden;
        }

        .tab-content.active { 
            display: flex; 
        }

        .tab-scroll-body {
            flex: 1;
            overflow-y: auto;
            overflow-x: hidden;
            scrollbar-width: none;
            padding-bottom: 6px;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .tab-scroll-body::-webkit-scrollbar {
            display: none;
        }

        .scanner-container {
            aspect-ratio: 1 / 1;
            width: min(72vw, 260px);
            height: min(72vw, 260px);
            max-width: 270px;
            max-height: 270px;
            margin: 2px auto;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #000000;
            border-radius: 20px;
            border: 1.5px solid var(--neon-blue);
            box-shadow: 0 0 16px rgba(0, 243, 255, 0.25);
            flex-shrink: 0;
        }

        #reader {
            width: 100% !important;
            height: 100% !important;
            border: none !important;
            background: #000000 !important;
            overflow: hidden !important;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 18px !important;
            position: relative;
        }

        #reader * {
            border: none !important;
            box-shadow: none !important;
            outline: none !important;
        }

        #reader video {
            width: 100% !important;
            height: 100% !important;
            object-fit: contain !important;
            background: #000000;
            border-radius: 18px !important;
        }

        .scanner-error-msg {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 30;
            color: #ff4d4d;
            font-size: 11px;
            font-weight: 800;
            background: rgba(10, 3, 3, 0.92);
            border: 1.5px solid #ff4d4d;
            padding: 8px 14px;
            border-radius: 12px;
            display: none;
            text-align: center;
            letter-spacing: 0.5px;
            box-shadow: 0 0 14px rgba(255, 77, 77, 0.6);
            white-space: nowrap;
        }

        .scanner-viewfinder-hud {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 74%;
            height: 74%;
            pointer-events: none;
            box-sizing: border-box;
            z-index: 6;
        }

        .hud-corner {
            position: absolute;
            width: 24px;
            height: 24px;
            border-color: var(--neon-blue);
            border-style: solid;
        }

        .corner-tl { top: 0; left: 0; border-width: 3.5px 0 0 3.5px; border-top-left-radius: 6px; }
        .corner-tr { top: 0; right: 0; border-width: 3.5px 3.5px 0 0; border-top-right-radius: 6px; }
        .corner-bl { bottom: 0; left: 0; border-width: 0 0 3.5px 3.5px; border-bottom-left-radius: 6px; }
        .corner-br { bottom: 0; right: 0; border-width: 0 3.5px 3.5px 0; border-bottom-right-radius: 6px; }

        .laser-line {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--neon-blue), transparent);
            box-shadow: 0 0 10px var(--neon-blue), 0 0 20px var(--neon-blue);
            animation: laserScan 2.4s ease-in-out infinite;
        }

        @keyframes laserScan {
            0% { top: 4%; opacity: 0; }
            20% { opacity: 1; }
            80% { opacity: 1; }
            100% { top: 96%; opacity: 0; }
        }

        .snapshot-card-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000000;
            border-radius: 18px;
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 15;
            overflow: hidden;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        #snapshot-preview-img {
            width: 100%;
            height: 100%;
            object-fit: contain !important;
            background: #000000;
            display: block;
            border-radius: 18px;
        }

        .floating-lens-pill {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) !important;
            z-index: 25;
            background: rgba(8, 18, 28, 0.95);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1.5px solid var(--neon-blue);
            color: var(--neon-blue);
            padding: 8px 16px;
            border-radius: 26px;
            font-size: 11px;
            font-weight: 800;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.95), 0 0 12px var(--neon-glow);
            display: none;
            align-items: center;
            gap: 8px;
            max-width: 85%;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            cursor: pointer;
        }

        .floating-lens-text {
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        .controls-slot-container {
            margin-top: 2px;
            min-height: 46px;
            flex-shrink: 0;
        }

        .bottom-controls-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 8px;
        }

        .btn-3d {
            background: linear-gradient(145deg, #101e30, #060c14);
            border: 1.5px solid var(--neon-blue);
            color: var(--neon-blue);
            border-radius: 18px;
            padding: 10px 12px;
            font-size: 11px;
            font-weight: 800;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.7), inset 0 1px 1px rgba(255, 255, 255, 0.2);
            text-decoration: none;
            letter-spacing: 0.3px;
        }

        .torch-btn { flex: 1; }
        .torch-btn.active-on {
            background: var(--neon-blue);
            color: #000000;
            box-shadow: 0 0 14px var(--neon-blue), inset 0 1px 2px rgba(255,255,255,0.7);
        }

        .gallery-btn { flex: 1.2; color: #ffffff; }

        .svg-icon {
            width: 16px;
            height: 16px;
            fill: currentColor;
            flex-shrink: 0;
        }

        .file-input-hidden { display: none; }

        .detected-controls-panel {
            display: none;
            background: #09131f;
            border: 1.5px solid var(--neon-blue);
            border-radius: 16px;
            padding: 8px 10px;
            box-shadow: 0 0 18px rgba(0, 0, 0, 0.95), 0 0 10px var(--neon-glow);
            position: relative;
            width: 100%;
        }

        .result-meta-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 4px;
            padding: 0 2px;
        }

        .meta-timestamp {
            font-size: 10.5px;
            color: var(--neon-blue);
            font-weight: 700;
            letter-spacing: 0.5px;
            text-transform: uppercase;
        }

        .format-badge {
            background: rgba(0, 243, 255, 0.15);
            border: 1px solid var(--neon-blue);
            color: var(--neon-blue);
            font-size: 9px;
            font-weight: 800;
            padding: 2px 6px;
            border-radius: 10px;
            text-transform: uppercase;
        }

        .result-text-preview {
            font-size: 13.5px !important;
            font-weight: 700 !important;
            line-height: 1.45 !important;
            color: #ffffff;
            word-break: break-word;
            background: #03080f;
            padding: 10px 12px 34px 12px;
            border-radius: 10px;
            margin-bottom: 6px;
            border: 1.5px solid var(--neon-blue);
            max-height: 115px;
            overflow-y: auto;
            white-space: pre-wrap;
            text-align: left;
            position: relative;
            box-shadow: inset 0 0 10px rgba(0, 243, 255, 0.1);
        }
        .result-text-preview::-webkit-scrollbar {
            width: 5px;
            height: 5px;
        }
        .result-text-preview::-webkit-scrollbar-thumb {
            background-color: var(--neon-blue);
            border-radius: 3px;
        }

        .result-more-btn {
            position: absolute;
            bottom: 52px;
            right: 14px;
            background: var(--neon-blue);
            color: #000000;
            border: none;
            padding: 4px 9px;
            border-radius: 7px;
            font-size: 9.5px;
            font-weight: 900;
            cursor: pointer;
            box-shadow: 0 0 8px var(--neon-glow);
            letter-spacing: 0.5px;
            z-index: 8;
        }

        .action-buttons-group {
            display: flex;
            gap: 6px;
            width: 100%;
        }

        .action-btn {
            flex: 1;
            padding: 10px 4px !important;
            border: none;
            border-radius: 12px;
            background: linear-gradient(135deg, var(--accent-blue), var(--neon-blue));
            color: #000000;
            font-weight: 900;
            font-size: 10.5px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            box-shadow: 0 4px 10px rgba(0, 243, 255, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            flex-shrink: 0;
        }

        .btn-open-link {
            background: #021221;
            color: var(--neon-blue);
            border: 1.5px solid var(--neon-blue);
        }

        .btn-close-detected {
            background: #200a0a;
            color: #ff4d4d;
            border: 1.5px solid #ff4d4d;
        }

        .accidental-safety-divider {
            width: 100%;
            height: 1.5px;
            background: linear-gradient(90deg, transparent, var(--neon-blue), transparent);
            margin: 2px 0 4px 0;
            box-shadow: 0 0 6px var(--neon-blue);
            flex-shrink: 0;
        }

        .create-tab-header {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 0 2px;
            width: 100%;
            margin-bottom: 2px;
        }

        .create-tab-title {
            text-align: center;
            font-size: 11px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.5px;
            text-transform: uppercase;
        }

        .smart-trigger-bar {
            width: 100%;
            background: #08121c;
            border: 1.5px solid var(--neon-blue);
            border-radius: 14px;
            padding: 12px 14px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            cursor: pointer;
            box-shadow: 0 0 10px var(--neon-glow);
            flex-shrink: 0;
        }

        .smart-trigger-left {
            font-size: 10.5px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.3px;
            text-shadow: 0 0 6px var(--neon-glow);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            padding-right: 6px;
        }

        .smart-trigger-btn {
            background: linear-gradient(135deg, var(--accent-blue), var(--neon-blue));
            color: #000000;
            border: none;
            padding: 6px 12px;
            border-radius: 10px;
            font-size: 10px;
            font-weight: 900;
            cursor: pointer;
            box-shadow: 0 0 6px var(--neon-glow);
            flex-shrink: 0;
            letter-spacing: 0.5px;
        }

        .generator-form-container {
            display: flex;
            flex-direction: column;
            gap: 6px;
            width: 100%;
        }

        .neon-input {
            width: 100%;
            box-sizing: border-box;
            padding: 12px 14px;
            background: #08121c !important;
            background-color: #08121c !important;
            border: 1.5px solid #1a2c40;
            border-radius: 12px;
            color: #ffffff !important;
            font-size: 13px;
            font-weight: 600;
            line-height: 1.4;
            outline: none;
            transition: border-color 0.2s, box-shadow 0.2s;
            display: block;
            -webkit-text-fill-color: #ffffff !important;
        }

        .neon-input:-webkit-autofill,
        .neon-input:-webkit-autofill:hover, 
        .neon-input:-webkit-autofill:focus {
            -webkit-box-shadow: 0 0 0 30px #08121c inset !important;
            -webkit-text-fill-color: #ffffff !important;
            caret-color: #ffffff !important;
        }

        .neon-input:focus {
            border-color: var(--neon-blue);
            box-shadow: 0 0 10px var(--neon-glow);
            background: #08121c !important;
            background-color: #08121c !important;
        }

        select.neon-input {
            appearance: none;
            -webkit-appearance: none;
            background-image: url("data:image/svg+xml;charset=UTF-8,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%2300f3ff'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 14px center;
            background-size: 16px;
            padding-right: 36px;
        }

        .schedule-picker-card {
            background: #060d16;
            border: 1.5px solid #142538;
            border-radius: 14px;
            padding: 8px;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .schedule-badge-label {
            font-size: 9.5px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.8px;
            text-transform: uppercase;
        }

        .schedule-dual-inputs {
            display: flex;
            gap: 6px;
        }

        .schedule-sub-input {
            flex: 1;
            padding: 12px 8px !important;
            font-size: 14px !important;
            font-weight: 700 !important;
            text-align: center;
            color-scheme: dark;
            background: #08121c !important;
            color: #ffffff !important;
        }

        .time-input-group {
            display: flex;
            align-items: center;
            gap: 6px;
            flex: 1;
        }

        .ampm-toggle-btn {
            background: rgba(0, 243, 255, 0.15);
            border: 1.5px solid var(--neon-blue);
            color: var(--neon-blue);
            font-size: 10px;
            font-weight: 900;
            padding: 12px 8px;
            border-radius: 10px;
            cursor: pointer;
            text-align: center;
            letter-spacing: 0.5px;
            flex-shrink: 0;
            box-shadow: 0 0 6px rgba(0, 243, 255, 0.2);
        }

        .char-counter {
            font-size: 9.5px;
            color: var(--text-gray);
            text-align: right;
            padding-right: 4px;
            margin-top: -3px;
        }

        .privacy-toggle-container {
            background: #060d16;
            border: 1.5px solid #1a2c40;
            border-radius: 12px;
            padding: 10px 14px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 2px 0;
        }

        .privacy-left-group {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .privacy-lock-icon {
            font-size: 15px;
            color: var(--neon-blue);
            text-shadow: 0 0 6px var(--neon-glow);
        }

        .privacy-toggle-label {
            font-size: 10.5px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.5px;
            text-transform: uppercase;
        }

        .gen-submit-btn {
            width: 100% !important;
            max-width: 100% !important;
            padding: 12px 14px !important;
            border-radius: 14px !important;
            font-size: 11px !important;
            letter-spacing: 0.5px !important;
            margin-top: 2px;
            flex: 0 0 auto !important;
            height: auto !important;
        }

        .luxury-qr-card {
            background: #050811;
            border: 2px solid #00f3ff;
            border-radius: 20px;
            padding: 14px 12px;
            text-align: center;
            box-shadow: 0 0 16px rgba(0, 243, 255, 0.4);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            box-sizing: border-box;
            width: 100%;
            margin-top: auto;
            margin-bottom: auto;
        }

        .plain-qr-wrapper {
            background: #ffffff;
            border-radius: 16px;
            padding: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            width: min(52vw, 190px);
            height: min(52vw, 190px);
            box-sizing: border-box;
        }

        .plain-qr-wrapper canvas,
        .plain-qr-wrapper img {
            width: 100% !important;
            height: 100% !important;
            display: block;
            margin: auto;
            image-rendering: pixelated;
        }

        .qr-url-pill {
            background: #08121c;
            border: 1.5px solid #00f3ff;
            box-shadow: 0 0 8px rgba(0, 243, 255, 0.3);
            color: #ffffff;
            padding: 7px 14px;
            border-radius: 18px;
            font-size: 11px;
            font-weight: 700;
            word-break: break-all;
            max-width: 95%;
            text-align: center;
            line-height: 1.3;
            letter-spacing: 0.5px;
        }

        .btn-clean-download {
            width: auto !important;
            min-width: 180px;
            padding: 12px 22px !important;
            font-size: 11.5px;
            font-weight: 800;
            letter-spacing: 0.6px;
        }

        #category-page-overlay {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: #080d14;
            z-index: 200;
            display: none;
            flex-direction: column;
            justify-content: space-between;
            border-radius: 26px;
            padding: 12px;
            box-sizing: border-box;
            overflow: hidden;
        }

        .cat-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 6px;
            padding-bottom: 6px;
            border-bottom: 1px solid #1a2c40;
            flex-shrink: 0;
        }

        .cat-title {
            font-size: 11.5px;
            font-weight: 900;
            color: var(--neon-blue);
            letter-spacing: 0.6px;
            text-transform: uppercase;
            text-shadow: 0 0 8px var(--neon-glow);
        }

        .cat-close-btn {
            background: rgba(0, 243, 255, 0.15);
            border: 1.5px solid var(--neon-blue);
            color: var(--neon-blue);
            width: 30px;
            height: 30px;
            border-radius: 50%;
            font-size: 13px;
            font-weight: 900;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 0 8px var(--neon-glow);
        }

        .category-scroll-list {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 6px;
            padding-bottom: 6px;
            overflow-y: auto;
            overflow-x: hidden;
            scrollbar-width: none;
        }

        .category-scroll-list::-webkit-scrollbar {
            display: none;
        }

        .category-section-title {
            font-size: 9px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 1px;
            margin-top: 4px;
            margin-bottom: 2px;
            text-transform: uppercase;
            padding-left: 4px;
        }

        .category-item-card {
            background: #0c1624;
            border: 1px solid #1a2c40;
            border-radius: 12px;
            padding: 11px 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            cursor: pointer;
            transition: all 0.15s ease;
        }

        .category-item-card:hover {
            border-color: var(--neon-blue);
            background: rgba(0, 243, 255, 0.1);
            box-shadow: 0 0 8px rgba(0, 243, 255, 0.2);
        }

        .category-item-left {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 11px;
            font-weight: 800;
            color: #e2e8f0;
        }

        .accidental-click-banner {
            background: linear-gradient(135deg, #09192b, #040c14);
            border: 1.5px dashed var(--neon-blue);
            border-radius: 12px;
            padding: 10px 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            cursor: pointer;
            margin: 4px 0;
            box-shadow: 0 0 8px rgba(0, 243, 255, 0.2);
        }

        .admob-banner-container {
            width: 100%;
            height: 48px;
            background: #050a12;
            border: 1px dashed rgba(0, 243, 255, 0.35);
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            margin-top: auto;
            flex-shrink: 0;
            box-sizing: border-box;
            position: relative;
            z-index: 10;
        }

        .admob-label {
            font-size: 7.5px;
            color: var(--text-gray);
            letter-spacing: 1px;
            margin-bottom: 2px;
        }

        .admob-text {
            font-size: 9.5px;
            font-weight: 700;
            color: var(--neon-blue);
        }

        .modal-overlay {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(3, 6, 10, 0.94);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            z-index: 1000;
            display: none;
            align-items: center;
            justify-content: center;
            padding: 14px;
            border-radius: 26px;
            box-sizing: border-box;
        }

        .modal-card {
            background: #08121c;
            border: 1.5px solid var(--neon-blue);
            border-radius: 18px;
            padding: 16px;
            width: 100%;
            max-width: 310px;
            box-shadow: 0 0 22px var(--neon-glow);
            display: flex;
            flex-direction: column;
            gap: 12px;
            box-sizing: border-box;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #1a2a3d;
            padding-bottom: 6px;
        }

        .modal-title {
            font-size: 11.5px;
            font-weight: 800;
            color: var(--neon-blue);
            letter-spacing: 0.5px;
        }

        .setting-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 6px 0;
            border-bottom: 1px solid #0e1a26;
        }

        .setting-label {
            font-size: 10.5px;
            font-weight: 600;
            color: #d1dbe5;
        }

        .setting-desc {
            font-size: 8.5px;
            color: var(--text-gray);
            margin-top: 2px;
        }

        .switch {
            position: relative;
            display: inline-block;
            width: 34px;
            height: 18px;
            flex-shrink: 0;
        }

        .switch input { opacity: 0; width: 0; height: 0; }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0; left: 0; right: 0; bottom: 0;
            background-color: #162433;
            transition: .25s ease;
            border-radius: 18px;
            border: 1px solid #283e54;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 12px; width: 12px;
            left: 2px; bottom: 2px;
            background-color: #ffffff;
            transition: .25s ease;
            border-radius: 50%;
        }

        input:checked + .slider { background-color: var(--neon-blue); border-color: var(--neon-blue); }
        input:checked + .slider:before { transform: translateX(16px); background-color: #000000; }

        .toast-popup {
            position: absolute;
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--neon-blue);
            color: #000000;
            padding: 7px 16px;
            border-radius: 18px;
            font-size: 10.5px;
            font-weight: 800;
            box-shadow: 0 0 12px var(--neon-blue);
            z-index: 10000;
            display: none;
            white-space: nowrap;
        }

        .rating-stars-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 6px;
            margin: 4px 0 2px 0;
        }

        .star-btn {
            background: none;
            border: none;
            font-size: 28px;
            color: #1a2c40;
            cursor: pointer;
            transition: all 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            line-height: 1;
            padding: 2px;
            outline: none;
        }

        .star-btn.active {
            color: var(--neon-blue);
            text-shadow: 0 0 14px var(--neon-glow);
            transform: scale(1.15);
        }

        .rating-modal-buttons {
            display: flex;
            gap: 8px;
            width: 100%;
        }
        .rating-modal-btn {
            flex: 1;
            padding: 10px 8px;
            border-radius: 12px;
            font-weight: 900;
            font-size: 10.5px;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            text-align: center;
            border: 1.5px solid var(--neon-blue);
        }
        .btn-rating-cancel {
            background: #111a24;
            color: #aaa;
            border-color: #333;
        }
        .btn-rating-submit {
            background: linear-gradient(135deg, var(--accent-blue), var(--neon-blue));
            color: #000000;
            box-shadow: 0 4px 10px rgba(0, 243, 255, 0.3);
        }
    </style>
</head>
<body>

    <div id="mainAppFrame" class="app-frame">
        
        <!-- HEADER BLOCK -->
        <div class="app-top-block">
            <div class="top-header">
                <div class="header-left-slot">
                    <div id="header-spacer" class="header-spacer"></div>
                    <button id="page2-close-btn" class="top-left-frame-close-btn" onclick="closeGeneratorTab()" title="Close Generator" aria-label="Close Generator">X</button>
                </div>
                <div class="brand-title">MK INDUSTRIES | OWNER & CEO FURQAN MK</div>
                <button class="icon-btn" onclick="openSettings()" title="Settings" aria-label="Settings">⋮</button>
            </div>

            <!-- TABS -->
            <div class="tab-switcher">
                <button id="tab-scan-btn" class="tab-btn active" onclick="switchTab('scan', this)">SCAN QR CODE</button>
                <button id="tab-create-btn" class="tab-btn" onclick="switchTab('create', this)">CREATE QR CODE</button>
            </div>
        </div>

        <!-- PAGE 1: SCANNER -->
        <div id="scan-tab" class="tab-content active">
            <div class="tab-scroll-body">
                <div class="scanner-container">
                    <div id="reader"></div>
                    
                    <div id="scannerErrorMsg" class="scanner-error-msg">NO QR CODE DETECTED</div>

                    <div id="snapshotCardOverlay" class="snapshot-card-overlay">
                        <img id="snapshot-preview-img" alt="Scanned Snapshot">
                    </div>
                    
                    <div id="scannerHud" class="scanner-viewfinder-hud">
                        <div class="hud-corner corner-tl"></div>
                        <div class="hud-corner corner-tr"></div>
                        <div class="hud-corner corner-bl"></div>
                        <div class="hud-corner corner-br"></div>
                        <div class="laser-line"></div>
                    </div>

                    <div id="floatingLensPill" class="floating-lens-pill" onclick="instantOpenUrl(window.activeScannedRawText)">
                        <span>LINK</span>
                        <span id="floatingLensUrlText" class="floating-lens-text">https://example.com</span>
                        <span>↗</span>
                    </div>
                </div>

                <div class="controls-slot-container">
                    <div id="defaultControls" class="bottom-controls-row">
                        <button id="torch-btn" class="btn-3d torch-btn" onclick="toggleTorchManual()">
                            <svg class="svg-icon" viewBox="0 0 24 24"><path d="M7 2h10v3l-3 4v13H10V9L7 5V2zm2 2v1h6V4H9zm2 6v10h2V10h-2z"/></svg>
                            <span id="torch-text">TORCH OFF</span>
                        </button>

                        <label class="btn-3d gallery-btn">
                            <svg class="svg-icon" viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H5V5h14v14zm-5.04-6.71l-2.75 3.54-1.96-2.36L6.5 17h11l-3.54-4.71z"/></svg>
                            Upload Gallery
                            <input type="file" id="gallery-input" class="file-input-hidden" accept="image/*">
                        </label>
                    </div>

                    <div id="detectedControls" class="detected-controls-panel">
                        <div class="result-meta-row">
                            <div id="result-timestamp" class="meta-timestamp">--:--</div>
                            <div id="result-format-badge" class="format-badge">QR_CODE</div>
                        </div>
                        <div id="result-text-content" class="result-text-preview">---</div>
                        <button class="result-more-btn" onclick="scrollResultBoxDown()">MORE</button>
                        <div class="action-buttons-group">
                            <button class="action-btn" onclick="copyResultText()">COPY</button>
                            <button class="action-btn btn-open-link" onclick="instantOpenUrl(window.activeScannedRawText)">OPEN</button>
                            <button class="action-btn btn-close-detected" onclick="hardResetScannerEngine()">CLOSE</button>
                        </div>
                    </div>
                </div>

                <div class="accidental-safety-divider"></div>
            </div>

            <div id="toastPopup" class="toast-popup">Press back again to exit</div>

            <div class="admob-banner-container">
                <div class="admob-label">ADMOB ADVERTISEMENT BANNER</div>
                <div class="admob-text">Ad Space Reserved (320x50 Banner)</div>
            </div>
        </div>

        <!-- PAGE 2: GENERATOR HUB -->
        <div id="create-tab" class="tab-content">
            <div class="tab-scroll-body" id="createTabScrollBody">
                <div class="create-tab-header">
                    <span class="create-tab-title">GENERATE 3D LUXURY QR</span>
                </div>

                <div id="generatorInputsWrapper" style="display:flex; flex-direction:column; gap:6px; width:100%;">
                    <div class="smart-trigger-bar" onclick="openCategoryPage()">
                        <div id="selectedCategoryDisplayLabel" class="smart-trigger-left">CREATE QR CODE SELECT MODES</div>
                        <button type="button" class="smart-trigger-btn">CLICK</button>
                    </div>

                    <div id="dynamicFormContainer" class="generator-form-container">
                        <input type="text" id="input-field-1" class="neon-input" placeholder="Enter URL, Text or data..." oninput="handleAIAutoDetectInput(this.value)">
                    </div>
                    <div id="charCounterContainer" class="char-counter" style="display:none;">0/8</div>

                    <div class="privacy-toggle-container">
                        <div class="privacy-left-group">
                            <span id="privacyLockIcon" class="privacy-lock-icon">🔒</span>
                            <span class="privacy-toggle-label">HIDE PRIVATE DETAILS</span>
                        </div>
                        <label class="switch">
                            <input type="checkbox" id="global-hide-privacy" checked onchange="updatePrivacyLockIcon(this.checked)">
                            <span class="slider"></span>
                        </label>
                    </div>
                </div>

                <button id="mainGenSubmitBtn" class="action-btn gen-submit-btn" onclick="handleGenerateClick()">GENERATE 3D LUXURY QR</button>
                
                <div id="qr-gen-output" style="width:100%; display:flex; flex-direction:column; align-items:center;"></div>

                <div class="accidental-safety-divider"></div>
            </div>

            <div class="admob-banner-container">
                <div class="admob-label">ADMOB ADVERTISEMENT BANNER</div>
                <div class="admob-text">Ad Space Reserved (320x50 Banner)</div>
            </div>
        </div>

        <!-- PAGE 3: CATEGORIES OVERLAY -->
        <div id="category-page-overlay">
            <div class="cat-header">
                <div class="cat-title">SELECT QR & BARCODE MODE</div>
                <button class="cat-close-btn" onclick="closeCategoryPage()">X</button>
            </div>
            
            <div id="categoryScrollList" class="category-scroll-list"></div>

            <div class="accidental-safety-divider"></div>

            <div class="admob-banner-container">
                <div class="admob-label">ADMOB ADVERTISEMENT BANNER</div>
                <div class="admob-text">Ad Space Reserved (320x50 Banner)</div>
            </div>
        </div>

        <!-- SETTINGS MODAL -->
        <div id="settings-modal" class="modal-overlay">
            <div class="modal-card">
                <div class="modal-header">
                    <div class="modal-title">SETTINGS</div>
                    <button class="icon-btn" onclick="closeSettings()">X</button>
                </div>

                <div class="setting-row">
                    <div>
                        <div class="setting-label">Auto Open URLs</div>
                        <div class="setting-desc">Directly open links in browser</div>
                    </div>
                    <label class="switch">
                        <input type="checkbox" id="set-auto-url" checked onchange="saveSettings()">
                        <span class="slider"></span>
                    </label>
                </div>

                <div class="setting-row">
                    <div>
                        <div class="setting-label">Beep Sound Alert</div>
                        <div class="setting-desc">Sound notification on scan</div>
                    </div>
                    <label class="switch">
                        <input type="checkbox" id="set-sound" checked onchange="saveSettings()">
                        <span class="slider"></span>
                    </label>
                </div>

                <div class="setting-row">
                    <div>
                        <div class="setting-label">Haptic Vibration</div>
                        <div class="setting-desc">Vibrate device upon successful scan</div>
                    </div>
                    <label class="switch">
                        <input type="checkbox" id="set-vibrate" checked onchange="saveSettings()">
                        <span class="slider"></span>
                    </label>
                </div>

                <button class="action-btn gen-submit-btn" style="margin-top: 6px; margin-bottom: 0; width:100%;" onclick="closeSettings()">SAVE & CLOSE</button>
            </div>
        </div>

        <!-- REWARDED AD MODAL -->
        <div id="rewardedAdModal" class="modal-overlay">
            <div class="modal-card" style="text-align: center;">
                <h3 style="color:var(--neon-blue); font-size:12.5px; font-weight:800;">Unlock Luxury QR Code</h3>
                <p style="font-size:10.5px; color:var(--text-gray); line-height: 1.4;">Watch a Rewarded Ad to generate and download your 3D Luxury QR Code.</p>
                <div style="display:flex; gap:8px; margin-top:4px;">
                    <button class="action-btn" style="background:#111a24; color:#aaa; border:1px solid #333; margin-bottom:0;" onclick="closeRewardedModal()">CANCEL</button>
                    <button class="action-btn gen-submit-btn" style="margin-bottom:0;" onclick="startAdCountdown()">WATCH REWARDED AD</button>
                </div>
            </div>
        </div>

        <!-- 5-STAR RATING MODAL POPUP -->
        <div id="ratingModal" class="modal-overlay">
            <div class="modal-card" style="text-align: center;">
                <h3 style="color:var(--neon-blue); font-size:12.5px; font-weight:800; letter-spacing:0.5px; text-transform:uppercase;">Rate Our App</h3>
                <p style="font-size:10.5px; color:var(--text-gray); line-height: 1.4;">If you're enjoying our QR Scanner, please take a moment to rate it. Thanks for your support!</p>
                
                <div class="rating-stars-container" id="ratingStarsGroup">
                    <button type="button" class="star-btn" data-star="1" onclick="selectStarRating(1)" aria-label="1 Star">★</button>
                    <button type="button" class="star-btn" data-star="2" onclick="selectStarRating(2)" aria-label="2 Stars">★</button>
                    <button type="button" class="star-btn" data-star="3" onclick="selectStarRating(3)" aria-label="3 Stars">★</button>
                    <button type="button" class="star-btn" data-star="4" onclick="selectStarRating(4)" aria-label="4 Stars">★</button>
                    <button type="button" class="star-btn" data-star="5" onclick="selectStarRating(5)" aria-label="5 Stars">★</button>
                </div>

                <div class="rating-modal-buttons">
                    <button type="button" class="rating-modal-btn btn-rating-cancel" onclick="handleRatingCancel()">CANCEL</button>
                    <button type="button" id="ratingActionBtn" class="rating-modal-btn btn-rating-submit" onclick="handleRatingAction()">LATER</button>
                </div>
            </div>
        </div>

        <!-- TIMER OVERLAY -->
        <div id="timerOverlay" class="modal-overlay">
            <div style="text-align:center;">
                <p style="color:var(--text-gray); font-size:10.5px; letter-spacing:1px; text-transform:uppercase;">Ad Starting In</p>
                <div id="timerNumber" style="font-size: 56px; font-weight: 900; color: var(--neon-blue); text-shadow: 0 0 22px var(--neon-blue); margin-top: 8px;">5</div>
            </div>
        </div>

        <div id="hidden-file-reader" style="display:none; width:0; height:0; overflow:hidden;"></div>

    </div>

    <script>
        (function() {
            let html5QrCode = null;
            let videoTrack = null;
            let isTorchOn = false;
            let lastBackPressTime = 0;
            let audioCtx = null;
            window.activeScannedRawText = "";
            let isLiveScanning = false;
            window.activeGenCategory = 'url';
            window.generationCount = 0;
            window.isQrGeneratedState = false;
            let currentRating = 0;

            let config = { autoUrl: true, sound: true, vibrate: true };

            const svgIcons = {
                url: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M3.9 12c0-1.71 1.39-3.1 3.1-3.1h4V7H7c-2.76 0-5 2.24-5 5s2.24 5 5 5h4v-1.9H7c-1.71 0-3.1-1.39-3.1-3.1zM8 13h8v-2H8v2zm9-6h-4v1.9h4c1.71 0 3.1 1.39 3.1 3.1s-1.39 3.1-3.1 3.1h-4V17h4c2.76 0 5-2.24 5-5s-2.24-5-5-5z"/></svg>`,
                text: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M2.5 4v3h5v12h3V7h5V4h-13zm19 5h-9v3h3v7h3v-7h3V9z"/></svg>`,
                contact: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>`,
                email: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>`,
                sms: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zM6 9h12v2H6V9zm8 5H6v-2h8v2zm4-6H6V6h12v2z"/></svg>`,
                geo: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>`,
                phone: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>`,
                calendar: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M19 3h-1V1h-2v2H8V1H6v2H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H5V8h14v11z"/></svg>`,
                wifi: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M12 3C6.95 3 2.39 4.86 0 8l12 13L24 8c-2.39-3.14-6.95-5-12-5zm0 4.18c3.82 0 7.32 1.34 9.53 3.49L12 20.08l-9.53-9.41C4.68 8.52 8.18 7.18 12 7.18z"/></svg>`,
                userProfile: `<svg class="svg-icon" viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>`
            };

            const categoriesList = [
                { section: 'STANDARD CATEGORIES' },
                { key: 'myqr', label: 'Create My QR', icon: 'userProfile' },
                { key: 'text', label: 'Text', icon: 'text' },
                { key: 'contact', label: 'Contact', icon: 'contact' },
                { key: 'email', label: 'Email', icon: 'email' },
                { key: 'sms', label: 'SMS', icon: 'sms' },
                { key: 'geo', label: 'Geo Location', icon: 'geo' },
                { key: 'phone', label: 'Phone', icon: 'phone' },
                { key: 'calendar', label: 'Calendar Event', icon: 'calendar' },
                { key: 'wifi', label: 'Wifi', icon: 'wifi' },
                { key: 'url', label: 'URL', icon: 'url' }
            ];

            function renderCategoryList() {
                const listEl = document.getElementById('categoryScrollList');
                if (!listEl) return;
                listEl.innerHTML = "";
                categoriesList.forEach((cat) => {
                    if (cat.section) {
                        const sec = document.createElement('div');
                        sec.className = 'category-section-title';
                        sec.innerText = cat.section;
                        listEl.appendChild(sec);
                    } else {
                        const item = document.createElement('div');
                        item.className = 'category-item-card';
                        item.innerHTML = `
                            <div class="category-item-left">
                                ${svgIcons[cat.icon] || svgIcons.url}
                                <span>${cat.label}</span>
                            </div>
                            <span style="color:var(--neon-blue); font-weight:900;">›</span>
                        `;
                        item.onclick = () => selectCategoryAndMorph(cat.key, cat.label);
                        listEl.appendChild(item);

                        if (cat.key === 'email') {
                            const bannerCard = document.createElement('div');
                            bannerCard.className = 'accidental-click-banner';
                            bannerCard.innerHTML = `
                                <div style="display:flex; align-items:center; gap:10px;">
                                    <svg class="svg-icon" style="color:var(--neon-blue);" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/></svg>
                                    <div>
                                        <div style="font-size:10.5px; font-weight:900; color:var(--neon-blue);">Smart Recommended App</div>
                                        <div style="font-size:8.5px; color:var(--text-gray);">Sponsored Secure Tool</div>
                                    </div>
                                </div>
                                <span style="font-size:9.5px; font-weight:800; background:var(--neon-blue); color:#000; padding:4px 9px; border-radius:9px;">INSTALL</span>
                            `;
                            bannerCard.onclick = () => {
                                initAudio();
                                window.open('https://play.google.com/store/apps', '_blank');
                            };
                            listEl.appendChild(bannerCard);
                        }
                    }
                });
            }

            window.openCategoryPage = function() {
                initAudio();
                const overlay = document.getElementById('category-page-overlay');
                if (overlay) overlay.style.display = 'flex';
                history.pushState({ modal: 'categories' }, "");
            };

            window.closeCategoryPage = function() {
                initAudio();
                const overlay = document.getElementById('category-page-overlay');
                if (overlay) overlay.style.display = 'none';
            };

            window.selectCategoryAndMorph = function(catKey, catLabel) {
                initAudio();
                window.activeGenCategory = catKey;
                const labelEl = document.getElementById('selectedCategoryDisplayLabel');
                if (labelEl) labelEl.innerText = "CREATE QR CODE SELECT MODES";
                closeCategoryPage();
                buildDynamicForm(catKey);
            };

            function getInitialDateString() {
                const now = new Date();
                const y = now.getFullYear();
                const m = String(now.getMonth() + 1).padStart(2, '0');
                const d = String(now.getDate()).padStart(2, '0');
                return `${y}-${m}-${d}`;
            }

            function getInitial24HourTimeString(offsetHours = 0) {
                const now = new Date();
                now.setHours(now.getHours() + offsetHours);
                const h = String(now.getHours()).padStart(2, '0');
                const m = String(now.getMinutes()).padStart(2, '0');
                return `${h}:${m}`;
            }

            window.updatePrivacyLockIcon = function(isChecked) {
                const icon = document.getElementById('privacyLockIcon');
                if (icon) icon.innerText = isChecked ? '🔒' : '🔓';
            };

            window.toggleAmPm = function(btnId) {
                initAudio();
                const btn = document.getElementById(btnId);
                if (!btn) return;
                btn.innerText = btn.innerText === 'AM' ? 'PM' : 'AM';
            };

            function buildDynamicForm(catKey) {
                const container = document.getElementById('dynamicFormContainer');
                const counter = document.getElementById('charCounterContainer');
                if (!container) return;
                container.innerHTML = "";
                if (counter) counter.style.display = 'none';

                if (catKey === 'wifi') {
                    container.innerHTML = `
                        <input type="text" id="wifi-ssid" class="neon-input" placeholder="SSID / Network Name">
                        <input type="password" id="wifi-pass" class="neon-input" placeholder="Password">
                        <select id="wifi-type" class="neon-input">
                            <option value="WPA">WPA / WPA2</option>
                            <option value="WEP">WEP</option>
                            <option value="nopass">No Password</option>
                        </select>
                        <label style="display:flex; align-items:center; gap:8px; font-size:11px; color:var(--text-gray); padding-left:2px;">
                            <input type="checkbox" id="wifi-hidden" style="width:15px; height:15px; accent-color:var(--neon-blue);"> Hidden Network
                        </label>
                    `;
                } else if (catKey === 'calendar') {
                    const defaultDate = getInitialDateString();
                    const defaultStart = getInitial24HourTimeString(0);
                    const defaultEnd = getInitial24HourTimeString(1);
                    container.innerHTML = `
                        <input type="text" id="cal-title" class="neon-input" placeholder="Event Title">
                        <div class="schedule-picker-card">
                            <div class="schedule-badge-label">START SCHEDULE</div>
                            <div class="schedule-dual-inputs">
                                <input type="date" id="cal-start-date" class="neon-input schedule-sub-input" value="${defaultDate}">
                                <div class="time-input-group">
                                    <button type="button" id="start-ampm-btn" class="ampm-toggle-btn" onclick="toggleAmPm('start-ampm-btn')">AM</button>
                                    <input type="time" id="cal-start-time" class="neon-input schedule-sub-input" value="${defaultStart}">
                                </div>
                            </div>
                        </div>
                        <div class="schedule-picker-card">
                            <div class="schedule-badge-label">END SCHEDULE</div>
                            <div class="schedule-dual-inputs">
                                <input type="date" id="cal-end-date" class="neon-input schedule-sub-input" value="${defaultDate}">
                                <div class="time-input-group">
                                    <button type="button" id="end-ampm-btn" class="ampm-toggle-btn" onclick="toggleAmPm('end-ampm-btn')">PM</button>
                                    <input type="time" id="cal-end-time" class="neon-input schedule-sub-input" value="${defaultEnd}">
                                </div>
                            </div>
                        </div>
                        <label style="display:flex; align-items:center; gap:8px; font-size:11px; color:var(--text-gray); padding-left:2px;">
                            <input type="checkbox" id="cal-allday" style="width:15px; height:15px; accent-color:var(--neon-blue);"> All-day Event
                        </label>
                        <input type="text" id="cal-loc" class="neon-input" placeholder="Location">
                        <textarea id="cal-desc" class="neon-input" placeholder="Description" style="height:60px; resize:none;"></textarea>
                    `;
                } else if (catKey === 'contact' || catKey === 'myqr') {
                    container.innerHTML = `
                        <input type="text" id="vc-name" class="neon-input" placeholder="Full Name">
                        <input type="text" id="vc-org" class="neon-input" placeholder="Organization">
                        <input type="text" id="vc-addr" class="neon-input" placeholder="Address">
                        <input type="tel" id="vc-phone" class="neon-input" placeholder="Phone Number">
                        <input type="email" id="vc-email" class="neon-input" placeholder="Email Address">
                        <textarea id="vc-notes" class="neon-input" placeholder="Notes" style="height:55px; resize:none;"></textarea>
                    `;
                } else if (catKey === 'email') {
                    container.innerHTML = `
                        <input type="email" id="em-to" class="neon-input" placeholder="Recipient Email">
                        <input type="text" id="em-sub" class="neon-input" placeholder="Subject">
                        <textarea id="em-body" class="neon-input" placeholder="Message Body" style="height:65px; resize:none;"></textarea>
                    `;
                } else if (catKey === 'sms') {
                    container.innerHTML = `
                        <input type="tel" id="sms-phone" class="neon-input" placeholder="Phone Number">
                        <textarea id="sms-msg" class="neon-input" placeholder="Message" style="height:65px; resize:none;"></textarea>
                    `;
                } else if (catKey === 'geo') {
                    container.innerHTML = `
                        <input type="text" id="geo-lat" class="neon-input" placeholder="Latitude (e.g. 28.6139)">
                        <input type="text" id="geo-lon" class="neon-input" placeholder="Longitude (e.g. 77.2090)">
                        <input type="text" id="geo-query" class="neon-input" placeholder="Query Address (Optional)">
                    `;
                } else if (catKey === 'phone') {
                    container.innerHTML = `
                        <input type="tel" id="phone-num" class="neon-input" placeholder="Phone Number">
                    `;
                } else if (catKey === 'text') {
                    container.innerHTML = `
                        <textarea id="input-field-1" class="neon-input" placeholder="Enter plain text..." style="height:100px; resize:none;" oninput="updateCharCount(this.value)"></textarea>
                    `;
                    if (counter) { counter.style.display = 'block'; counter.innerText = '0 chars'; }
                } else {
                    container.innerHTML = `<input type="text" id="input-field-1" class="neon-input" placeholder="Enter URL, Text or data...">`;
                }
            }

            window.updateCharCount = function(val) {
                const counter = document.getElementById('charCounterContainer');
                if (counter) counter.innerText = `${val ? val.length : 0} chars`;
            };

            window.getCombinedInputValue = function() {
                const cat = window.activeGenCategory;
                if (cat === 'wifi') {
                    const ssidEl = document.getElementById('wifi-ssid');
                    const passEl = document.getElementById('wifi-pass');
                    const typeEl = document.getElementById('wifi-type');
                    const hiddenEl = document.getElementById('wifi-hidden');
                    if (!ssidEl) return "";
                    const s = ssidEl.value.trim();
                    const p = passEl ? passEl.value.trim() : '';
                    const t = typeEl ? typeEl.value : 'WPA';
                    const h = hiddenEl && hiddenEl.checked ? 'true' : 'false';
                    if (!s) return "";
                    return `WIFI:S:${s};T:${t};P:${p};H:${h};;`;
                } else if (cat === 'calendar') {
                    const titleEl = document.getElementById('cal-title');
                    if (!titleEl) return "";
                    const title = titleEl.value.trim();
                    if (!title) return "";
                    const startDateStr = document.getElementById('cal-start-date') ? document.getElementById('cal-start-date').value : getInitialDateString();
                    let startTimeStr = document.getElementById('cal-start-time') ? document.getElementById('cal-start-time').value : getInitial24HourTimeString(0);
                    const endDateStr = document.getElementById('cal-end-date') ? document.getElementById('cal-end-date').value : startDateStr;
                    let endTimeStr = document.getElementById('cal-end-time') ? document.getElementById('cal-end-time').value : getInitial24HourTimeString(1);
                    const loc = document.getElementById('cal-loc') ? document.getElementById('cal-loc').value.trim() : '';
                    const desc = document.getElementById('cal-desc') ? document.getElementById('cal-desc').value.trim() : '';
                    return `BEGIN:VEVENT\nSUMMARY:${title}\nDTSTART:${startDateStr.replace(/-/g, '')}T${startTimeStr.replace(/:/g, '')}00\nDTEND:${endDateStr.replace(/-/g, '')}T${endTimeStr.replace(/:/g, '')}00\nLOCATION:${loc}\nDESCRIPTION:${desc}\nEND:VEVENT`;
                } else if (cat === 'contact' || cat === 'myqr') {
                    const nameEl = document.getElementById('vc-name');
                    if (!nameEl) return "";
                    const n = nameEl.value.trim();
                    if (!n) return "";
                    const org = document.getElementById('vc-org') ? document.getElementById('vc-org').value.trim() : '';
                    const addr = document.getElementById('vc-addr') ? document.getElementById('vc-addr').value.trim() : '';
                    const tel = document.getElementById('vc-phone') ? document.getElementById('vc-phone').value.trim() : '';
                    const email = document.getElementById('vc-email') ? document.getElementById('vc-email').value.trim() : '';
                    const notes = document.getElementById('vc-notes') ? document.getElementById('vc-notes').value.trim() : '';
                    return `BEGIN:VCARD\nVERSION:3.0\nFN:${n}\nORG:${org}\nADR:${addr}\nTEL:${tel}\nEMAIL:${email}\nNOTE:${notes}\nEND:VCARD`;
                } else if (cat === 'email') {
                    const to = document.getElementById('em-to') ? document.getElementById('em-to').value.trim() : '';
                    const sub = document.getElementById('em-sub') ? document.getElementById('em-sub').value.trim() : '';
                    const body = document.getElementById('em-body') ? document.getElementById('em-body').value.trim() : '';
                    if (!to) return "";
                    return `MATMSG:TO:${to};SUB:${sub};BODY:${body};;`;
                } else if (cat === 'sms') {
                    const phone = document.getElementById('sms-phone') ? document.getElementById('sms-phone').value.trim() : '';
                    const msg = document.getElementById('sms-msg') ? document.getElementById('sms-msg').value.trim() : '';
                    if (!phone) return "";
                    return `SMSTO:${phone}:${msg}`;
                } else if (cat === 'geo') {
                    const lat = document.getElementById('geo-lat') ? document.getElementById('geo-lat').value.trim() : '';
                    const lon = document.getElementById('geo-lon') ? document.getElementById('geo-lon').value.trim() : '';
                    if (!lat || !lon) return "";
                    return `geo:${lat},${lon}`;
                } else if (cat === 'phone') {
                    const phone = document.getElementById('phone-num') ? document.getElementById('phone-num').value.trim() : '';
                    if (!phone) return "";
                    return `tel:${phone}`;
                } else {
                    const el = document.getElementById('input-field-1');
                    return el ? el.value.trim() : "";
                }
            };

            function getHumanReadablePillLabel(rawVal) {
                const cat = window.activeGenCategory;
                let cleanLabel = "";

                if (cat === 'contact' || cat === 'myqr') {
                    const nameEl = document.getElementById('vc-name');
                    cleanLabel = "Contact: " + (nameEl && nameEl.value.trim() ? nameEl.value.trim() : "My Profile");
                } else if (cat === 'wifi') {
                    const ssidEl = document.getElementById('wifi-ssid');
                    cleanLabel = "Wifi: " + (ssidEl && ssidEl.value.trim() ? ssidEl.value.trim() : "Network");
                } else if (cat === 'calendar') {
                    const titleEl = document.getElementById('cal-title');
                    cleanLabel = "Event: " + (titleEl && titleEl.value.trim() ? titleEl.value.trim() : "Calendar Schedule");
                } else if (cat === 'email') {
                    const toEl = document.getElementById('em-to');
                    cleanLabel = "Email: " + (toEl && toEl.value.trim() ? toEl.value.trim() : "Recipient");
                } else if (cat === 'sms' || cat === 'phone') {
                    cleanLabel = "Phone: " + rawVal.replace('tel:', '').replace('SMSTO:', '');
                } else if (cat === 'geo') {
                    cleanLabel = "Location: " + rawVal.replace('geo:', '');
                } else {
                    cleanLabel = rawVal;
                }

                return maskSensitiveText(cleanLabel);
            }

            function initAudio() {
                if (!audioCtx) {
                    const AudioContextClass = window.AudioContext || window.webkitAudioContext;
                    if (AudioContextClass) audioCtx = new AudioContextClass();
                }
                if (audioCtx && audioCtx.state === 'suspended') audioCtx.resume();
            }

            function playBeepSound() {
                if (!config.sound) return;
                try {
                    initAudio();
                    if (!audioCtx) return;
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.type = 'sine';
                    osc.frequency.value = 1050;
                    gain.gain.setValueAtTime(0.18, audioCtx.currentTime);
                    gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.08);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start();
                    osc.stop(audioCtx.currentTime + 0.09);
                } catch(e) {}
            }

            function sanitizeInput(str) {
                const temp = document.createElement('div');
                temp.textContent = str;
                return temp.innerHTML;
            }

            function maskSensitiveText(val) {
                if (!val) return "";
                const hidePrivacyEl = document.getElementById('global-hide-privacy');
                if (hidePrivacyEl && hidePrivacyEl.checked) {
                    const str = val.trim();
                    if (str.length <= 2) return '•';
                    return str.charAt(0) + '••••••••' + str.charAt(str.length - 1);
                }
                return val.trim();
            }

            function getFormattedTimestamp() {
                const now = new Date();
                const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
                const day = now.getDate().toString().padStart(2, '0');
                const month = months[now.getMonth()];
                const year = now.getFullYear();
                let hours = now.getHours();
                const minutes = now.getMinutes().toString().padStart(2, '0');
                const ampm = hours >= 12 ? 'PM' : 'AM';
                hours = hours % 12;
                hours = hours ? hours.toString().padStart(2, '0') : '12';
                return `${day} ${month} ${year}, ${hours}:${minutes} ${ampm}`;
            }

            function loadSettings() {
                try {
                    const saved = localStorage.getItem('mk_settings_2026');
                    if (saved) {
                        const bytes = CryptoJS.AES.decrypt(saved, 'MK_SECRET_KEY_2026');
                        config = Object.assign(config, JSON.parse(bytes.toString(CryptoJS.enc.Utf8)));
                    }
                } catch(e) {}
                const autoUrlEl = document.getElementById('set-auto-url');
                const soundEl = document.getElementById('set-sound');
                const vibrateEl = document.getElementById('set-vibrate');
                if (autoUrlEl) autoUrlEl.checked = config.autoUrl;
                if (soundEl) soundEl.checked = config.sound;
                if (vibrateEl) vibrateEl.checked = config.vibrate;
            }

            function saveEncryptedSettings() {
                try {
                    localStorage.setItem('mk_settings_2026', CryptoJS.AES.encrypt(JSON.stringify(config), 'MK_SECRET_KEY_2026').toString());
                } catch(e) {}
            }

            function captureLiveCameraSnapshot() {
                try {
                    const video = document.querySelector("#reader video");
                    if (!video || !video.videoWidth || !video.videoHeight) return null;
                    const canvas = document.createElement('canvas');
                    const vw = video.videoWidth;
                    const vh = video.videoHeight;
                    const cropSize = Math.min(vw, vh);
                    canvas.width = 640; canvas.height = 640;
                    const ctx = canvas.getContext('2d');
                    ctx.drawImage(video, (vw - cropSize) / 2, (vh - cropSize) / 2, cropSize, cropSize, 0, 0, 640, 640);
                    return canvas.toDataURL('image/jpeg', 0.95);
                } catch(err) { return null; }
            }

            window.hardResetScannerEngine = function() {
                initAudio();
                window.activeScannedRawText = "";
                const floatingLens = document.getElementById('floatingLensPill');
                if (floatingLens) floatingLens.style.display = 'none';
                const detectedControls = document.getElementById('detectedControls');
                if (detectedControls) detectedControls.style.display = 'none';
                const resContent = document.getElementById('result-text-content');
                if (resContent) resContent.innerText = "---";
                const snapshotOverlay = document.getElementById('snapshotCardOverlay');
                if (snapshotOverlay) snapshotOverlay.style.display = 'none';
                const snapshotImg = document.getElementById('snapshot-preview-img');
                if (snapshotImg) { snapshotImg.src = ""; snapshotImg.removeAttribute('src'); }
                const fileInput = document.getElementById('gallery-input');
                if (fileInput) fileInput.value = "";
                const hud = document.getElementById('scannerHud');
                if (hud) hud.style.display = 'block';
                const defaultControls = document.getElementById('defaultControls');
                if (defaultControls) defaultControls.style.display = 'flex';
                const errMsg = document.getElementById('scannerErrorMsg');
                if (errMsg) errMsg.style.display = 'none';

                if (html5QrCode) {
                    try { 
                        if (html5QrCode.getState() === 3 || html5QrCode.getState() === 2) {
                            html5QrCode.resume();
                        }
                    } catch(err) { 
                        try { html5QrCode.resume(); } catch(e) {} 
                    }
                }
            };

            window.scrollResultBoxDown = function() {
                initAudio();
                const resContent = document.getElementById('result-text-content');
                if (resContent) {
                    resContent.scrollBy({ top: 90, behavior: 'smooth' });
                }
            };

            function showScannerError(msg) {
                const errMsg = document.getElementById('scannerErrorMsg');
                if (errMsg) {
                    errMsg.innerText = msg || "NO QR CODE DETECTED";
                    errMsg.style.display = 'block';
                    setTimeout(() => { errMsg.style.display = 'none'; }, 2800);
                } else {
                    showToast(msg || "NO QR CODE DETECTED");
                }
            }

            window.instantOpenUrl = function(rawUrl) {
                initAudio();
                const target = rawUrl || window.activeScannedRawText;
                if (!target) { showToast("No URL detected"); return; }
                const formattedUrl = (target.startsWith('http://') || target.startsWith('https://')) ? target : ('https://' + target);
                window.open(formattedUrl, '_blank');
                hardResetScannerEngine();
            };

            function initScanner() {
                if (html5QrCode && isLiveScanning) return;
                html5QrCode = new Html5Qrcode("reader");

                const hdConstraints = {
                    facingMode: "environment",
                    width: { ideal: 1920, min: 1280 },
                    height: { ideal: 1080, min: 720 },
                    advanced: [{ focusMode: "continuous" }, { exposureMode: "continuous" }, { whiteBalanceMode: "continuous" }]
                };

                const scanConfig = { 
                    fps: 30,
                    qrbox: (vw, vh) => { const edge = Math.floor(Math.min(vw, vh) * 0.85); return { width: edge, height: edge }; },
                    aspectRatio: 1.0,
                    videoConstraints: hdConstraints,
                    experimentalFeatures: { useBarCodeDetectorIfSupported: true }
                };

                Html5Qrcode.getCameras().then(devices => {
                    let cameraChoice = { facingMode: "environment" };
                    if (devices && devices.length > 0) cameraChoice = devices[devices.length - 1].id;
                    
                    html5QrCode.start(
                        cameraChoice, scanConfig, 
                        (text, decodedResult) => onScanSuccess(text, decodedResult, false, null)
                    ).then(() => {
                        isLiveScanning = true;
                        const videoEl = document.querySelector("#reader video");
                        if (videoEl && videoEl.srcObject) videoTrack = videoEl.srcObject.getVideoTracks()[0];
                    }).catch(err => { console.warn("Camera fallback note:", err); });
                }).catch(err => { console.warn("Camera enum note:", err); });
            }

            function setTorch(state) {
                if (!videoTrack) { showToast("Torch hardware not ready"); return; }
                const caps = videoTrack.getCapabilities ? videoTrack.getCapabilities() : {};
                if (caps.torch) {
                    videoTrack.applyConstraints({ advanced: [{ torch: state }] })
                        .then(() => { isTorchOn = state; updateTorchUI(); })
                        .catch(() => showToast("Unable to control torch"));
                } else { showToast("Torch not supported on this lens"); }
            }

            window.toggleTorchManual = function() {
                initAudio();
                setTorch(!isTorchOn);
            };

            function updateTorchUI() {
                const btn = document.getElementById('torch-btn');
                const txt = document.getElementById('torch-text');
                if (!btn || !txt) return;
                if (isTorchOn) {
                    btn.classList.add('active-on');
                    txt.innerText = "TORCH ON";
                } else {
                    btn.classList.remove('active-on');
                    txt.innerText = "TORCH OFF";
                }
            }

            function unmaskShortUrl(rawUrl, callback) {
                if (!rawUrl.startsWith('http://') && !rawUrl.startsWith('https://')) { callback(rawUrl); return; }
                if (rawUrl.includes('delivr.com') || rawUrl.includes('bit.ly') || rawUrl.includes('tinyurl.com') || rawUrl.includes('t.co')) {
                    fetch(rawUrl, { method: 'HEAD', redirect: 'follow' })
                        .then(response => { callback(response.url || rawUrl); })
                        .catch(() => callback(rawUrl));
                } else { callback(rawUrl); }
            }

            function parseSmartScanResult(rawText) {
                if (rawText.includes('BEGIN:VEVENT')) {
                    let summary = "Calendar Event";
                    let startFormatted = "";
                    let endFormatted = "";
                    let location = "";
                    let description = "";

                    const parseICalDateTime = (dtStr) => {
                        if (!dtStr) return "";
                        try {
                            const clean = dtStr.trim();
                            const y = clean.substring(0, 4);
                            const mNum = clean.substring(4, 6);
                            const d = clean.substring(6, 8);
                            const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
                            const mName = months[parseInt(mNum, 10) - 1] || mNum;
                            
                            let timePart = "";
                            if (clean.includes('T') && clean.length >= 13) {
                                const t = clean.split('T')[1];
                                let hh = parseInt(t.substring(0, 2), 10);
                                const mm = t.substring(2, 4);
                                const ampm = hh >= 12 ? 'PM' : 'AM';
                                hh = hh % 12;
                                hh = hh ? hh : 12;
                                timePart = `  ${String(hh).padStart(2, '0')}:${mm} ${ampm}`;
                            }
                            return `${d} ${mName} ${y}${timePart}`;
                        } catch(e) { return dtStr; }
                    };

                    rawText.split('\n').forEach(line => {
                        if (line.startsWith('SUMMARY:')) summary = line.replace('SUMMARY:', '').trim();
                        if (line.startsWith('DTSTART:')) startFormatted = parseICalDateTime(line.replace('DTSTART:', '').trim());
                        if (line.startsWith('DTEND:')) endFormatted = parseICalDateTime(line.replace('DTEND:', '').trim());
                        if (line.startsWith('LOCATION:')) location = line.replace('LOCATION:', '').trim();
                        if (line.startsWith('DESCRIPTION:')) description = line.replace('DESCRIPTION:', '').trim();
                    });

                    let resultStr = `EVENT TITLE: ${summary}`;
                    if (startFormatted) resultStr += `\nSTART SCHEDULE: ${startFormatted}`;
                    if (endFormatted) resultStr += `\nEND SCHEDULE: ${endFormatted}`;
                    if (location) resultStr += `\nLOCATION: ${location}`;
                    if (description) resultStr += `\nDESCRIPTION: ${description}`;
                    return resultStr;
                }

                if (rawText.startsWith('upi://')) {
                    try {
                        const urlObj = new URL(rawText);
                        const pa = urlObj.searchParams.get('pa') || '';
                        const pn = urlObj.searchParams.get('pn') || '';
                        const am = urlObj.searchParams.get('am') || '';
                        return `UPI PAYMENT DETECTED\nPayee VPA: ${pa}\nMerchant: ${pn}${am ? '\nAmount: ₹' + am : ''}`;
                    } catch(e) { return rawText; }
                }
                return rawText;
            }

            window.selectStarRating = function(starNum) {
                initAudio();
                currentRating = starNum;
                const stars = document.querySelectorAll('#ratingStarsGroup .star-btn');
                stars.forEach((star, index) => {
                    if (index < starNum) {
                        star.classList.add('active');
                    } else {
                        star.classList.remove('active');
                    }
                });
                const actionBtn = document.getElementById('ratingActionBtn');
                if (actionBtn) {
                    actionBtn.innerText = "SUBMIT";
                }
            };

            window.handleRatingCancel = function() {
                initAudio();
                const modal = document.getElementById('ratingModal');
                if (modal) modal.style.display = 'none';
                try {
                    localStorage.setItem('mk_app_rated_2026', 'cancelled');
                } catch(e) {}
            };

            window.handleRatingAction = function() {
                initAudio();
                const modal = document.getElementById('ratingModal');
                if (currentRating > 0) {
                    try {
                        localStorage.setItem('mk_app_rated_2026', currentRating.toString());
                    } catch(e) {}
                    if (modal) modal.style.display = 'none';
                    showToast("Thank you for your rating!");
                } else {
                    if (modal) modal.style.display = 'none';
                }
            };

            function checkAndShowRatingModal() {
                try {
                    const rated = localStorage.getItem('mk_app_rated_2026');
                    if (rated) return;
                    setTimeout(() => {
                        const modal = document.getElementById('ratingModal');
                        if (modal && modal.style.display !== 'flex') {
                            currentRating = 0;
                            document.querySelectorAll('#ratingStarsGroup .star-btn').forEach(btn => btn.classList.remove('active'));
                            const actionBtn = document.getElementById('ratingActionBtn');
                            if (actionBtn) actionBtn.innerText = "LATER";
                            modal.style.display = 'flex';
                            history.pushState({ modal: 'rating' }, "");
                        }
                    }, 800);
                } catch(e) {}
            }

            function onScanSuccess(text, decodedResult, isFromGallery = false, galleryImageDataUrl = null) {
                if (isTorchOn) setTorch(false);
                playBeepSound();
                if (config.vibrate && navigator.vibrate) navigator.vibrate(80);

                let snapshotDataUrl = galleryImageDataUrl;
                if (!isFromGallery) snapshotDataUrl = captureLiveCameraSnapshot();

                const rawText = text.trim();

                unmaskShortUrl(rawText, function(finalUnmaskedUrl) {
                    const parsedDisplayVal = parseSmartScanResult(finalUnmaskedUrl);
                    window.activeScannedRawText = finalUnmaskedUrl;

                    if (html5QrCode) {
                        try { if (html5QrCode.getState() === 2) html5QrCode.pause(true); } catch(err) {}
                    }

                    const hud = document.getElementById('scannerHud');
                    if (hud) hud.style.display = 'none';
                    const defaultControls = document.getElementById('defaultControls');
                    if (defaultControls) defaultControls.style.display = 'none';
                    const detectedControls = document.getElementById('detectedControls');
                    if (detectedControls) detectedControls.style.display = 'block';

                    const snapshotOverlay = document.getElementById('snapshotCardOverlay');
                    const snapshotImg = document.getElementById('snapshot-preview-img');
                    if (snapshotDataUrl && snapshotImg && snapshotOverlay) {
                        snapshotImg.src = snapshotDataUrl;
                        snapshotOverlay.style.display = 'flex';
                    }

                    const timestampEl = document.getElementById('result-timestamp');
                    if (timestampEl) timestampEl.innerText = getFormattedTimestamp();
                    
                    let formatName = "QR_CODE";
                    if (decodedResult && decodedResult.result && decodedResult.result.format && decodedResult.result.format.formatName) {
                        formatName = decodedResult.result.format.formatName;
                    }
                    const formatBadgeEl = document.getElementById('result-format-badge');
                    if (formatBadgeEl) formatBadgeEl.innerText = formatName;

                    const resTextEl = document.getElementById('result-text-content');
                    if (resTextEl) resTextEl.innerText = parsedDisplayVal;

                    const isUrl = finalUnmaskedUrl.startsWith('http://') || finalUnmaskedUrl.startsWith('https://');
                    const lensPill = document.getElementById('floatingLensPill');
                    const lensText = document.getElementById('floatingLensUrlText');

                    if (isUrl && lensPill && lensText) {
                        lensText.innerText = finalUnmaskedUrl;
                        lensPill.style.display = 'flex';
                    } else if (lensPill) {
                        lensPill.style.display = 'none';
                    }

                    if (config.autoUrl) {
                        if (isUrl) window.open(finalUnmaskedUrl, '_blank');
                    }

                    checkAndShowRatingModal();
                });
            }

            function createEnhancedImageFile(file, contrastBoost = 1.6, binarize = false) {
                return new Promise((resolve) => {
                    const img = new Image();
                    img.onload = () => {
                        const canvas = document.createElement('canvas');
                        canvas.width = img.width;
                        canvas.height = img.height;
                        const ctx = canvas.getContext('2d');
                        ctx.drawImage(img, 0, 0);

                        const imgData = ctx.getImageData(0, 0, canvas.width, canvas.height);
                        const data = imgData.data;

                        for (let i = 0; i < data.length; i += 4) {
                            let avg = (data[i] + data[i + 1] + data[i + 2]) / 3;
                            avg = ((avg - 128) * contrastBoost) + 128;
                            if (binarize) avg = avg > 120 ? 255 : 0;
                            data[i] = avg;
                            data[i + 1] = avg;
                            data[i + 2] = avg;
                        }
                        ctx.putImageData(imgData, 0, 0);
                        canvas.toBlob((blob) => {
                            if (!blob) { resolve(file); return; }
                            const newFile = new File([blob], "enhanced_" + file.name, { type: "image/png" });
                            resolve(newFile);
                        }, "image/png");
                    };
                    img.onerror = () => resolve(file);
                    img.src = URL.createObjectURL(file);
                });
            }

            const galleryInputEl = document.getElementById('gallery-input');
            if (galleryInputEl) {
                galleryInputEl.addEventListener('change', async function(e) {
                    initAudio();
                    const fileInput = e.target;
                    if (!fileInput.files || !fileInput.files.length) return;
                    const file = fileInput.files[0];

                    const reader = new FileReader();
                    reader.onload = async function(event) {
                        const originalDataUrl = event.target.result;
                        let hiddenScanner = null;
                        try { hiddenScanner = new Html5Qrcode("hidden-file-reader"); } catch(err) {}

                        if (!hiddenScanner) {
                            fileInput.value = "";
                            showScannerError("NO QR CODE DETECTED");
                            return;
                        }

                        try {
                            const text = await hiddenScanner.scanFile(file, false);
                            onScanSuccess(text, null, true, originalDataUrl);
                            try { hiddenScanner.clear(); } catch(e) {}
                            fileInput.value = "";
                            return;
                        } catch(err1) {}

                        try {
                            const enhancedFile = await createEnhancedImageFile(file, 1.8, false);
                            const text2 = await hiddenScanner.scanFile(enhancedFile, false);
                            onScanSuccess(text2, null, true, originalDataUrl);
                            try { hiddenScanner.clear(); } catch(e) {}
                            fileInput.value = "";
                            return;
                        } catch(err2) {}

                        try {
                            const binarizedFile = await createEnhancedImageFile(file, 2.2, true);
                            const text3 = await hiddenScanner.scanFile(binarizedFile, false);
                            onScanSuccess(text3, null, true, originalDataUrl);
                            try { hiddenScanner.clear(); } catch(e) {}
                            fileInput.value = "";
                            return;
                        } catch(err3) {
                            showScannerError("NO QR CODE DETECTED");
                            hardResetScannerEngine();
                            try { hiddenScanner.clear(); } catch(e) {}
                            fileInput.value = "";
                        }
                    };
                    reader.readAsDataURL(file);
                });
            }

            window.handleAIAutoDetectInput = function(val) {
                if (!val) return;
                val = val.trim();
                const labelEl = document.getElementById('selectedCategoryDisplayLabel');
                if (val.startsWith('http://') || val.startsWith('https://')) {
                    if (window.activeGenCategory !== 'url') {
                        window.activeGenCategory = 'url';
                        if (labelEl) labelEl.innerText = "CREATE QR CODE SELECT MODES";
                    }
                }
            };

            window.openSettings = function() { 
                initAudio();
                const settingsModal = document.getElementById('settings-modal');
                if (settingsModal) settingsModal.style.display = 'flex'; 
                history.pushState({ modal: 'settings' }, "");
            };

            window.closeSettings = function() { 
                const settingsModal = document.getElementById('settings-modal');
                if (settingsModal) settingsModal.style.display = 'none'; 
            };

            window.saveSettings = function() {
                const autoUrlEl = document.getElementById('set-auto-url');
                const soundEl = document.getElementById('set-sound');
                const vibrateEl = document.getElementById('set-vibrate');
                if (autoUrlEl) config.autoUrl = autoUrlEl.checked;
                if (soundEl) config.sound = soundEl.checked;
                if (vibrateEl) config.vibrate = vibrateEl.checked;
                saveEncryptedSettings();
            };

            window.switchTab = function(tab, btn) {
                initAudio();
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                
                const targetTab = document.getElementById(tab + '-tab');
                if (targetTab) targetTab.classList.add('active');
                if (btn) btn.classList.add('active');

                const page2CloseBtn = document.getElementById('page2-close-btn');
                const headerSpacer = document.getElementById('header-spacer');

                if (tab === 'scan') {
                    if (page2CloseBtn) page2CloseBtn.style.display = 'none';
                    if (headerSpacer) headerSpacer.style.display = 'block';
                    restoreFormStateNormal();
                    hardResetScannerEngine();
                } else if (tab === 'create') {
                    if (page2CloseBtn) page2CloseBtn.style.display = 'flex';
                    if (headerSpacer) headerSpacer.style.display = 'none';
                    hardResetScannerEngine();
                    history.pushState({ tab: 'create' }, "");
                }
            };

            window.closeGeneratorTab = function() {
                initAudio();
                restoreFormStateNormal();
                const scanBtn = document.getElementById('tab-scan-btn');
                switchTab('scan', scanBtn);
            };

            function restoreFormStateNormal() {
                window.isQrGeneratedState = false;
                const qrOutput = document.getElementById('qr-gen-output');
                if (qrOutput) qrOutput.innerHTML = "";
                const inputsWrapper = document.getElementById('generatorInputsWrapper');
                if (inputsWrapper) inputsWrapper.style.display = 'flex';
                const mainBtn = document.getElementById('mainGenSubmitBtn');
                if (mainBtn) mainBtn.style.display = 'block';

                window.activeGenCategory = 'url';
                const labelEl = document.getElementById('selectedCategoryDisplayLabel');
                if (labelEl) labelEl.innerText = "CREATE QR CODE SELECT MODES";
                buildDynamicForm('url');
            }

            window.handleGenerateClick = function() {
                initAudio();
                const rawVal = getCombinedInputValue();
                if (!rawVal) { showToast("Please enter data to generate!"); return; }

                window.generationCount++;
                if (window.generationCount % 6 === 0) {
                    const rewardedModal = document.getElementById('rewardedAdModal');
                    if (rewardedModal) rewardedModal.style.display = 'flex';
                    history.pushState({ modal: 'rewarded' }, "");
                } else {
                    generateLuxuryQRCard(rawVal);
                }
            };

            window.closeRewardedModal = function() {
                const rewardedModal = document.getElementById('rewardedAdModal');
                if (rewardedModal) rewardedModal.style.display = 'none';
            };

            window.startAdCountdown = function() {
                closeRewardedModal();
                const timerOverlay = document.getElementById('timerOverlay');
                const timerNum = document.getElementById('timerNumber');
                if (timerOverlay) timerOverlay.style.display = 'flex';

                let count = 5;
                if (timerNum) timerNum.innerText = count;

                const interval = setInterval(() => {
                    count--;
                    if (count > 0) {
                        if (timerNum) timerNum.innerText = count;
                    } else {
                        clearInterval(interval);
                        if (timerOverlay) timerOverlay.style.display = 'none';
                        const rawVal = getCombinedInputValue();
                        if (rawVal) generateLuxuryQRCard(rawVal);
                    }
                }, 1000);
            };

            function generateLuxuryQRCard(rawVal) {
                const inputsWrapper = document.getElementById('generatorInputsWrapper');
                if (inputsWrapper) inputsWrapper.style.display = 'none';
                const mainBtn = document.getElementById('mainGenSubmitBtn');
                if (mainBtn) mainBtn.style.display = 'none';

                window.isQrGeneratedState = true;
                history.pushState({ qrGenerated: true }, "");

                const outputDiv = document.getElementById('qr-gen-output');
                if (!outputDiv) return;
                outputDiv.innerHTML = "";

                const humanLabel = getHumanReadablePillLabel(rawVal);

                const luxuryCard = document.createElement('div');
                luxuryCard.className = 'luxury-qr-card';
                luxuryCard.innerHTML = `
                    <div class="plain-qr-wrapper" id="qrCanvasBox"></div>
                    <div class="qr-url-pill">${sanitizeInput(humanLabel)}</div>
                    <button id="downloadBtn" class="action-btn btn-clean-download">DOWNLOAD IMAGE</button>
                `;
                outputDiv.appendChild(luxuryCard);

                const qrBox = luxuryCard.querySelector('#qrCanvasBox');
                if (qrBox) {
                    qrBox.innerHTML = "";
                    new QRCode(qrBox, { text: rawVal, width: 170, height: 170, colorDark: "#000000", colorLight: "#ffffff", correctLevel: QRCode.CorrectLevel.H });
                }

                const downloadBtn = luxuryCard.querySelector('#downloadBtn');
                if (downloadBtn) {
                    downloadBtn.onclick = function() {
                        initAudio();
                        exportUltraHD(rawVal);
                    };
                }
                showToast("3D Luxury QR Generated!");
                checkAndShowRatingModal();
            }

            function exportUltraHD(fullRawValue) {
                showToast("Preparing Ultra-HD image download...");
                const offscreenDiv = document.createElement('div');
                offscreenDiv.style.position = 'absolute';
                offscreenDiv.style.left = '-9999px'; offscreenDiv.style.top = '-9999px';
                document.body.appendChild(offscreenDiv);

                new QRCode(offscreenDiv, { text: fullRawValue, width: 720, height: 720, colorDark: "#000000", colorLight: "#ffffff", correctLevel: QRCode.CorrectLevel.H });

                setTimeout(() => {
                    let sourceCanvas = offscreenDiv.querySelector('canvas');
                    let imgSource = offscreenDiv.querySelector('img');

                    const processExport = (imgElement) => {
                        const masterCanvas = document.createElement('canvas');
                        masterCanvas.width = 1024; masterCanvas.height = 1024;
                        const ctx = masterCanvas.getContext('2d');

                        ctx.fillStyle = "#ffffff"; ctx.fillRect(0, 0, 1024, 1024);
                        ctx.strokeStyle = "#00f3ff"; ctx.lineWidth = 10; ctx.strokeRect(20, 20, 984, 984);
                        ctx.imageSmoothingEnabled = false; ctx.drawImage(imgElement, 152, 90, 720, 720);

                        ctx.fillStyle = "#08121c"; ctx.beginPath();
                        if (ctx.roundRect) ctx.roundRect(112, 860, 800, 84, 42);
                        else ctx.rect(112, 860, 800, 84);
                        ctx.fill();
                        ctx.strokeStyle = "#00f3ff"; ctx.lineWidth = 4; ctx.stroke();

                        const humanLabel = getHumanReadablePillLabel(fullRawValue);
                        ctx.fillStyle = "#ffffff";
                        ctx.font = "700 24px -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif";
                        ctx.textAlign = "center";
                        ctx.fillText(humanLabel.length > 38 ? humanLabel.substring(0, 35) + '...' : humanLabel, 512, 912);

                        const downloadUri = masterCanvas.toDataURL("image/png", 1.0);
                        const dlLink = document.createElement('a');
                        dlLink.href = downloadUri; dlLink.download = `MK_ULTRA_HD_QR_${Date.now()}.png`;
                        document.body.appendChild(dlLink); dlLink.click(); document.body.removeChild(dlLink);
                        document.body.removeChild(offscreenDiv);

                        showToast("Ultra-HD Image Downloaded!");
                        setTimeout(() => { restoreFormStateNormal(); }, 300);
                    };

                    if (sourceCanvas) processExport(sourceCanvas);
                    else if (imgSource && imgSource.complete) processExport(imgSource);
                    else if (imgSource) imgSource.onload = () => processExport(imgSource);
                    else { document.body.removeChild(offscreenDiv); showToast("Rendering failed"); }
                }, 120);
            }

            window.copyResultText = function() {
                initAudio();
                const rawTxt = window.activeScannedRawText;
                if (!rawTxt) return;
                if (navigator.clipboard && navigator.clipboard.writeText) {
                    navigator.clipboard.writeText(rawTxt).then(() => showToast("Copied to clipboard!"));
                } else {
                    const tempInput = document.createElement('textarea');
                    tempInput.value = rawTxt;
                    document.body.appendChild(tempInput);
                    tempInput.select(); document.execCommand('copy');
                    document.body.removeChild(tempInput);
                    showToast("Copied to clipboard!");
                }
            };

            function showToast(msg) {
                const toast = document.getElementById('toastPopup');
                if (!toast) return;
                toast.innerText = msg;
                toast.style.display = 'block';
                setTimeout(() => { toast.style.display = 'none'; }, 2200);
            }

            window.addEventListener('visibilitychange', function() { if (document.hidden) hardResetScannerEngine(); });
            window.addEventListener('blur', function() { hardResetScannerEngine(); });

            window.addEventListener('popstate', function(e) {
                const settingsModal = document.getElementById('settings-modal');
                const rewardedModal = document.getElementById('rewardedAdModal');
                const ratingModal = document.getElementById('ratingModal');
                const categoryOverlay = document.getElementById('category-page-overlay');
                const createTab = document.getElementById('create-tab');
                const detectedControls = document.getElementById('detectedControls');

                if (categoryOverlay && categoryOverlay.style.display === 'flex') { categoryOverlay.style.display = 'none'; return; }
                if (settingsModal && settingsModal.style.display === 'flex') { settingsModal.style.display = 'none'; return; }
                if (rewardedModal && rewardedModal.style.display === 'flex') { rewardedModal.style.display = 'none'; return; }
                if (ratingModal && ratingModal.style.display === 'flex') { ratingModal.style.display = 'none'; return; }
                if (detectedControls && detectedControls.style.display === 'block') { hardResetScannerEngine(); return; }

                if (window.isQrGeneratedState) {
                    restoreFormStateNormal();
                    return;
                }

                if (createTab && createTab.classList.contains('active')) {
                    switchTab('scan', document.getElementById('tab-scan-btn'));
                    return;
                }

                const now = Date.now();
                if (now - lastBackPressTime < 2000) {
                    if (navigator.app && navigator.app.exitApp) navigator.app.exitApp();
                    else window.close();
                } else {
                    lastBackPressTime = now;
                    showToast("Press back again to exit");
                    history.pushState(null, "");
                }
            });
            history.pushState(null, "");

            window.addEventListener('DOMContentLoaded', function() {
                loadSettings();
                renderCategoryList();
                buildDynamicForm('url');
                initScanner();
            });
        })();
    </script>
</body>
</html>
