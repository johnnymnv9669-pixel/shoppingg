<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ร้านค้าของคุณ</title>
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      background-color: #304674;
      color: #ffffff;
    }

    h1 {
      text-align: center;
      padding: 1rem;
    }

    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
      gap: 1rem;
      padding: 1rem;
    }

    .product {
      background: rgba(255, 255, 255, 0.05);
      padding: 0.5rem;
      border-radius: 8px;
      text-align: center;
      color: #ffffff;
    }

    .product img {
      width: 100%;
      border-radius: 6px;
      aspect-ratio: 1 / 1;
      object-fit: cover;
    }

    .product-name {
      font-weight: bold;
      margin: 0.5rem 0 0.3rem;
      font-size: 0.9rem;
    }

    .product-price {
      color: #00ff88;
      font-size: 0.9rem;
      margin-bottom: 0.5rem;
    }

    .product a {
      display: inline-block;
      padding: 0.3rem 0.6rem;
      background-color: #ffffff33;
      color: #ffffff;
      text-decoration: none;
      font-size: 0.8rem;
      border-radius: 4px;
    }

    @media (min-width: 480px) {
      .product-grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }
  </style>
</head>
<body>
  <h1>ร้านค้าของคุณ</h1>
  <div class="product-grid" id="productGrid"></div>

  <script>
    const API_URL = "https://script.google.com/macros/s/AKfycbyYCo9_wN3_7Y52vDT5agBj24wLZgCFXx93rd73WGUajR8aoD5CXXVgUHyZI2Pws8ppBg/exec";

    async function loadProducts() {
      const res = await fetch(API_URL);
      const products = await res.json();

      const container = document.getElementById("productGrid");
      products.forEach(p => {
        const el = document.createElement("div");
        el.className = "product";
        el.innerHTML = `
          <img src="${p.Pictures}" loading="lazy" alt="${p.Name}">
          <div class="product-name">${p.Name}</div>
          <div class="product-price">${p.Price.toLocaleString()} ₭</div>
          <a href="#">สั่งซื้อ</a>
        `;
        container.appendChild(el);
      });
    }

    loadProducts();
  </script>
</body>
</html>
