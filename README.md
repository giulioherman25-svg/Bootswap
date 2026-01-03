<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BootSwap - Buy & Sell Football Boots</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Roboto', sans-serif; margin:0; padding:0; background:#f4f4f4; color:#333; }
    header { background:#0a74da; color:white; padding:20px 0; text-align:center; }
    header h1 { margin:0; font-size:2rem; }
    nav { margin-top:10px; }
    nav a { color:white; margin:0 15px; text-decoration:none; font-weight:700; }
    .container { max-width: 1000px; margin: 20px auto; padding:0 20px; }
    h2 { color:#0a74da; }
    .boots-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(250px,1fr)); gap:20px; }
    .boot-card { background:white; padding:15px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.1); }
    .boot-card img { width:100%; border-radius:10px; }
    .boot-card h3 { margin:10px 0 5px; }
    .boot-card p { margin:5px 0; }
    .form-section { background:white; padding:20px; border-radius:10px; box-shadow:0 2px 6px rgba(0,0,0,0.1); margin-top:40px; }
    label { display:block; margin:10px 0 5px; font-weight:700; }
    input, textarea { width:100%; padding:10px; border-radius:5px; border:1px solid #ccc; }
    button { background:#0a74da; color:white; padding:10px 20px; border:none; border-radius:5px; cursor:pointer; margin-top:15px; }
    button:hover { background:#065bb5; }
    footer { text-align:center; padding:20px; margin-top:40px; background:#333; color:white; }
  </style>
</head>
<body>

  <header>
    <h1>BootSwap</h1>
    <nav>
      <a href="#buy">Buy Boots</a>
      <a href="#sell">Sell Your Boots</a>
    </nav>
  </header>

  <div class="container">

    <!-- Boots For Sale Section -->
    <section id="buy">
      <h2>Available Football Boots</h2>
      <div class="boots-grid" id="boots-list">
        <!-- Example boot card -->
        <div class="boot-card">
          <img src="https://via.placeholder.com/250x150" alt="Nike Mercurial">
          <h3>Nike Mercurial</h3>
          <p>Size: 9 UK</p>
          <p>Condition: Match-Ready</p>
          <p>Price: £50</p>
          <button onclick="alert('Checkout coming soon!')">Buy Now</button>
        </div>
      </div>
    </section>

    <!-- Sell Your Boots Form -->
    <section id="sell" class="form-section">
      <h2>Sell Your Boots</h2>
      <form id="sellForm">
        <label for="name">Your Name</label>
        <input type="text" id="name" name="name" required>

        <label for="email">Email</label>
        <input type="email" id="email" name="email" required>

        <label for="brand">Boot Brand & Model</label>
        <input type="text" id="brand" name="brand" required>

        <label for="size">Size</label>
        <input type="text" id="size" name="size" required>

        <label for="condition">Condition Description</label>
        <textarea id="condition" name="condition" rows="3" required></textarea>

        <label for="photos">Photo URLs (separate by commas)</label>
        <textarea id="photos" name="photos" rows="2" placeholder="https://example.com/boot1.jpg, https://example.com/boot2.jpg"></textarea>

        <button type="submit">Submit Boots for Inspection</button>
      </form>
      <p id="formMessage" style="margin-top:10px;color:green;"></p>
    </section>

  </div>

  <footer>
    &copy; 2026 BootSwap - Player-Verified Football Boots
  </footer>

  <script>
    const sellForm = document.getElementById('sellForm');
    const formMessage = document.getElementById('formMessage');
    const bootsList = document.getElementById('boots-list');

    // Handle boot submissions (for MVP, it just shows an alert / adds to page)
    sellForm.addEventListener('submit', (e) => {
      e.preventDefault();

      const name = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      const brand = document.getElementById('brand').value;
      const size = document.getElementById('size').value;
      const condition = document.getElementById('condition').value;
      const photos = document.getElementById('photos').value.split(',');

      // Show confirmation message
      formMessage.textContent = "Thank you! Your boots have been submitted for inspection.";

      // For MVP, add the first photo to available boots list (simulating approval)
      if(photos[0]){
        const card = document.createElement('div');
        card.className = 'boot-card';
        card.innerHTML = `
          <img src="${photos[0].trim()}" alt="${brand}">
          <h3>${brand}</h3>
          <p>Size: ${size}</p>
          <p>Condition: ${condition}</p>
          <p>Price: TBD</p>
          <button onclick="alert('Checkout coming soon!')">Buy Now</button>
        `;
        bootsList.appendChild(card);
      }

      // Clear form
      sellForm.reset();
    });
  </script>

</body>
</html>
