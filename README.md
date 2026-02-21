<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Miswar - Toko Sepatu Online</title>
    <style>
        /* --- CSS (Style) --- */
        :root {
            --primary: #ff6600; /* Warna Oranye Khas */
            --dark: #222;
            --light: #f4f4f4;
            --text-gray: #666;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--light);
            color: var(--dark);
        }

        /* Navbar */
        nav {
            background-color: var(--dark);
            color: white;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            margin-left: 20px;
            font-weight: 500;
            transition: 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            background-color: var(--primary);
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 12px;
            position: absolute;
            top: -10px;
            right: -10px;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1556906781-9a412961c28c?q=80&w=1000&auto=format&fit=crop');
            background-size: cover;
            background-position: center;
            height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 10px;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 20px;
        }

        .btn {
            padding: 10px 25px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            text-decoration: none;
            transition: 0.3s;
        }

        .btn:hover {
            background-color: #e55c00;
        }

        /* Products Section */
        .container {
            max-width: 1200px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
            font-size: 2rem;
            color: var(--dark);
        }

        .section-title span {
            color: var(--primary);
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .product-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            background-color: #ddd;
        }

        .product-info {
            padding: 20px;
        }

        .product-title {
            font-size: 1.1rem;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .product-price {
            color: var(--primary);
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .btn-block {
            width: 100%;
            display: block;
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 50px;
        }

        /* Responsive Mobile */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2rem; }
            nav { flex-direction: column; gap: 10px; }
            .nav-links { margin-top: 10px; }
        }
    </style>
</head>
<body>

    <!-- Navbar -->
    <nav>
        <div class="logo">MISWAR</div>
        <div class="nav-links">
            <a href="#home">Home</a>
            <a href="#produk">Produk</a>
            <a href="#kontak">Kontak</a>
        </div>
        <div class="cart-icon" onclick="alert('Keranjang belanja Anda: ' + count)">
            🛒 <span class="cart-count" id="count">0</span>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="hero" id="home">
        <h1>Selamat Datang di Miswar</h1>
        <p>Koleksi sepatu sneakers, running, dan casual terbaik dengan harga terjangkau.</p>
        <a href="#produk" class="btn">Belanja Sekarang</a>
    </header>

    <!-- Produk Section -->
    <section class="container" id="produk">
        <h2 class="section-title">Koleksi <span>Sepatu Terbaru</span></h2>
        
        <!-- Area Produk (Di-generate oleh JS) -->
        <div class="product-grid" id="product-list">
            <!-- Produk akan muncul di sini -->
        </div>
    </section>

    <!-- Footer -->
    <footer id="kontak">
        <p>&copy; 2023 Toko Miswar. All rights reserved.</p>
        <p>Jl. Sudirman No. 123, Jakarta Selatan | WA: 0812-3456-7890</p>
    </footer>

    <script>
        /* --- JavaScript (Logika) --- */
        
        // 1. Data Produk (Database Simulasi)
        const products = [
            {
                id: 1,
                name: "Miswar Sneakers Red",
                price: 350000,
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=500&q=80"
            },
            {
                id: 2,
                name: "Miswar Running Blue",
                price: 420000,
                image: "https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?auto=format&fit=crop&w=500&q=80"
            },
            {
                id: 3,
                name: "Miswar Casual White",
                price: 280000,
                image: "https://images.unsplash.com/photo-1525966222134-fcfa99b8ae77?auto=format&fit=crop&w=500&q=80"
            },
            {
                id: 4,
                name: "Miswar Boots Leather",
                price: 550000,
                image: "https://images.unsplash.com/photo-1608231387042-66d471307172?auto=format&fit=crop&w=500&q=80"
            },
            {
                id: 5,
                name: "Miswar Sport Black",
                price: 390000,
                image: "https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?auto=format&fit=crop&w=500&q=80"
            },
            {
                id: 6,
                name: "Miswar Canvas Old School",
                price: 250000,
                image: "https://images.unsplash.com/photo-1524805444758-089113d48a6d?auto=format&fit=crop&w=500&q=80"
            }
        ];

        // 2. Variabel Keranjang
        let
