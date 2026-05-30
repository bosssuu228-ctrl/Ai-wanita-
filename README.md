# Ai-wanita-
Website planger
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Affiliate Prompt Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            color: #ffffff;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* HEADER */
        header {
            background: rgba(15, 12, 41, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 28px;
            font-weight: 700;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-links a {
            color: #ffffff;
            text-decoration: none;
            font-size: 14px;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        /* MAIN CONTAINER */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        /* HERO SECTION */
        .hero {
            text-align: center;
            margin-bottom: 60px;
            animation: fadeInDown 0.8s ease-out;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero p {
            font-size: 18px;
            color: #b8b8d1;
            margin-bottom: 30px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        /* MAIN FORM */
        .form-container {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 40px;
            animation: fadeInUp 0.8s ease-out;
        }

        .form-section {
            margin-bottom: 40px;
            display: none;
        }

        .form-section.active {
            display: block;
            animation: fadeIn 0.5s ease-out;
        }

        .section-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 30px;
            color: #667eea;
        }

        .section-subtitle {
            font-size: 14px;
            color: #b8b8d1;
            margin-bottom: 20px;
        }

        /* FILE UPLOAD */
        .upload-area {
            border: 2px dashed rgba(102, 126, 234, 0.4);
            border-radius: 15px;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            background: rgba(102, 126, 234, 0.05);
        }

        .upload-area:hover {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        .upload-area.dragover {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.15);
        }

        .upload-icon {
            font-size: 48px;
            margin-bottom: 15px;
        }

        .upload-text {
            font-size: 16px;
            margin-bottom: 10px;
        }

        .upload-subtext {
            font-size: 12px;
            color: #b8b8d1;
        }

        #fileInput, #productImageInput {
            display: none;
        }

        .image-preview {
            margin-top: 20px;
            text-align: center;
        }

        .image-preview img {
            max-width: 200px;
            max-height: 200px;
            border-radius: 10px;
            border: 1px solid rgba(102, 126, 234, 0.3);
        }

        /* PRODUCT GRID */
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .product-card {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .product-card:hover {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
            transform: translateY(-5px);
        }

        .product-card.selected {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.2);
        }

        .product-emoji {
            font-size: 36px;
            margin-bottom: 10px;
        }

        .product-name {
            font-size: 14px;
            font-weight: 600;
        }

        /* QUESTIONS SECTION */
        .question-group {
            margin-bottom: 30px;
        }

        .question-label {
            font-size: 14px;
            font-weight: 600;
            margin-bottom: 15px;
            display: block;
            color: #b8b8d1;
        }

        .option-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 10px;
            margin-bottom: 15px;
        }

        .option-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #ffffff;
            padding: 12px 16px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 13px;
            transition: all 0.3s;
        }

        .option-btn:hover {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        .option-btn.active {
            background: #667eea;
            border-color: #667eea;
            color: #ffffff;
        }

        textarea {
            width: 100%;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #ffffff;
            padding: 12px;
            border-radius: 8px;
            font-size: 14px;
            font-family: inherit;
            resize: vertical;
            min-height: 80px;
        }

        textarea::placeholder {
            color: #b8b8d1;
        }

        /* BUTTONS */
        .button-group {
            display: flex;
            gap: 15px;
            justify-content: space-between;
            margin-top: 30px;
        }

        .btn {
            padding: 14px 32px;
            border: none;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #ffffff;
            flex: 1;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }

        .btn-primary:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.15);
        }

        /* RESULTS */
        .results-container {
            display: none;
            animation: fadeIn 0.5s ease-out;
        }

        .results-container.show {
            display: block;
        }

        .poses-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .pose-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 20px;
            transition: all 0.3s;
        }

        .pose-card:hover {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        .pose-number {
            font-size: 12px;
            color: #667eea;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .pose-title {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 12px;
        }

        .pose-description {
            font-size: 13px;
            color: #b8b8d1;
            line-height: 1.6;
            margin-bottom: 15px;
        }

        .copy-btn {
            background: rgba(102, 126, 234, 0.2);
            border: 1px solid #667eea;
            color: #667eea;
            padding: 8px 16px;
            border-radius: 6px;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .copy-btn:hover {
            background: #667eea;
            color: #ffffff;
        }

        .prompts-section {
            margin-top: 40px;
        }

        .prompt-box {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
        }

        .prompt-type {
            font-size: 12px;
            color: #667eea;
            font-weight: 700;
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .prompt-content {
            font-size: 14px;
            line-height: 1.8;
            color: #ffffff;
            margin-bottom: 15px;
            padding: 15px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 8px;
            word-break: break-word;
        }

        .loading {
            text-align: center;
            padding: 40px;
        }

        .loader {
            border: 4px solid rgba(255, 255, 255, 0.1);
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 32px;
            }

            .form-container {
                padding: 20px;
            }

            .option-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .button-group {
                flex-direction: column;
            }

            .poses-grid {
                grid-template-columns: 1fr;
            }
        }

        /* TOAST NOTIFICATION */
        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #667eea;
            color: white;
            padding: 16px 24px;
            border-radius: 8px;
            z-index: 1000;
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <!-- HEADER -->
    <header>
        <div class="header-container">
            <div class="logo">✨ AI Affiliate Generator</div>
            <ul class="nav-links">
                <li><a href="#features">Features</a></li>
                <li><a href="#pricing">Pricing</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
    </header>

    <!-- MAIN CONTAINER -->
    <div class="container">
        <!-- HERO SECTION -->
        <div class="hero">
            <h1>🎬 AI Affiliate Prompt Generator</h1>
            <p>Buat prompt konten afiliasi profesional dengan AI. Upload foto, pilih produk, dan hasilkan prompt siap pakai untuk gambar & video AI dalam hitungan detik.</p>
        </div>

        <!-- FORM -->
        <div class="form-container">
            <!-- STEP 1: UPLOAD KARAKTER -->
            <div class="form-section active" data-step="1">
                <h2 class="section-title">📸 Step 1: Upload Foto Karakter</h2>
                <p class="section-subtitle">Upload foto wajah, half body, atau full body Anda</p>

                <div class="upload-area" id="uploadArea">
                    <div class="upload-icon">📷</div>
                    <div class="upload-text">Klik atau drag foto di sini</div>
                    <div class="upload-subtext">JPG, PNG, WebP (Max 10MB)</div>
                    <input type="file" id="fileInput" accept="image/*">
                </div>

                <div class="image-preview" id="imagePreview" style="display: none;">
                    <img id="previewImage" src="" alt="Preview">
                </div>

                <div class="question-group" style="margin-top: 25px;">
                    <label class="question-label">Mode Referensi:</label>
                    <div class="option-grid">
                        <button class="option-btn active" data-option="soft" onclick="selectReferenceMode(this)">
                            🎨 Soft Reference
                        </button>
                        <button class="option-btn" data-option="medium" onclick="selectReferenceMode(this)">
                            📸 Medium Reference
                        </button>
                        <button class="option-btn" data-option="strong" onclick="selectReferenceMode(this)">
                            ✅ Strong Reference
                        </button>
                    </div>
                </div>

                <div class="button-group">
                    <button class="btn btn-secondary" onclick="skipCharacter()">Skip (No Reference)</button>
                    <button class="btn btn-primary" onclick="nextStep()">Lanjut →</button>
                </div>
            </div>

            <!-- STEP 2: PILIH KATEGORI PRODUK -->
            <div class="form-section" data-step="2">
                <h2 class="section-title">🛍️ Step 2: Pilih Kategori Produk</h2>
                <p class="section-subtitle">Pilih jenis produk yang ingin Anda promosikan</p>

                <div class="product-grid">
                    <div class="product-card" data-product="fashion" onclick="selectProduct(this)">
                        <div class="product-emoji">👕</div>
                        <div class="product-name">Fashion / Baju</div>
                    </div>
                    <div class="product-card" data-product="shoes" onclick="selectProduct(this)">
                        <div class="product-emoji">👟</div>
                        <div class="product-name">Sepatu</div>
                    </div>
                    <div class="product-card" data-product="hijab" onclick="selectProduct(this)">
                        <div class="product-emoji">🧕</div>
                        <div class="product-name">Jilbab / Hijab</div>
                    </div>
                    <div class="product-card" data-product="food" onclick="selectProduct(this)">
                        <div class="product-emoji">🍔</div>
                        <div class="product-name">Makanan / Minuman</div>
                    </div>
                    <div class="product-card" data-product="beauty" onclick="selectProduct(this)">
                        <div class="product-emoji">💄</div>
                        <div class="product-name">Produk Kecantikan</div>
                    </div>
                    <div class="product-card" data-product="accessories" onclick="selectProduct(this)">
                        <div class="product-emoji">👜</div>
                        <div class="product-name">Aksesoris</div>
                    </div>
                    <div class="product-card" data-product="gadget" onclick="selectProduct(this)">
                        <div class="product-emoji">📱</div>
                        <div class="product-name">Gadget / Tech</div>
                    </div>
                    <div class="product-card" data-product="furniture" onclick="selectProduct(this)">
                        <div class="product-emoji">🛋️</div>
                        <div class="product-name">Furniture</div>
                    </div>
                </div>

                <div class="button-group">
                    <button class="btn btn-secondary" onclick="prevStep()">← Kembali</button>
                    <button class="btn btn-primary" onclick="nextStep()" id="nextBtn2" disabled>Lanjut →</button>
                </div>
            </div>

            <!-- STEP 3: UPLOAD FOTO PRODUK (OPTIONAL) -->
            <div class="form-section" data-step="3">
                <h2 class="section-title">📦 Step 3: Upload Foto Produk (Opsional)</h2>
                <p class="section-subtitle">Upload foto produk untuk analisis lebih detail</p>

                <div class="upload-area" id="uploadArea2">
                    <div class="upload-icon">📦</div>
                    <div class="upload-text">Klik atau drag foto produk di sini</div>
                    <div class="upload-subtext">JPG, PNG, WebP (Max 10MB)</div>
                    <input type="file" id="productImageInput" accept="image/*">
                </div>

                <div class="image-preview" id="imagePreview2" style="display: none;">
                    <img id="previewImage2" src="" alt="Preview">
                </div>

                <div class="button-group">
                    <button class="btn btn-secondary" onclick="prevStep()">← Kembali</button>
                    <button class="btn btn-primary" onclick="nextStep()">Lanjut →</button>
                </div>
            </div>

            <!-- STEP 4: KLARIFIKASI -->
            <div class="form-section" data-step="4">
                <h2 class="section-title">⚙️ Step 4: Klarifikasi Detail</h2>
                <p class="section-subtitle">Tentukan setting, vibe, dan gaya visual</p>

                <!-- SETTING -->
                <div class="question-group">
                    <label class="question-label">🎭 Setting / Lokasi:</label>
                    <div class="option-grid">
                        <button class="option-btn" data-setting="studio" onclick="selectOption(this, 'setting')">Studio</button>
                        <button class="optio