<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Vault - Thrift Streetwear</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&family=Montserrat:wght@400;600&display=swap" rel="stylesheet">
    <style>
        * { margin:0; padding:0; box-sizing:border-box; }
        html { scroll-behavior:smooth; }
        body { font-family:'Poppins',sans-serif; line-height:1.6; color:#333; background-color:#fafafa; overflow-x:hidden; }
        header { background-color: rgba(0,0,0,0.9); color:#fff; padding:1rem 0; position:fixed; width:100%; top:0; z-index:1000; backdrop-filter: blur(10px);}
        nav { display:flex; justify-content:space-between; align-items:center; max-width:1200px; margin:0 auto; padding:0 1rem;}
        .logo { font-family:'Montserrat',sans-serif; font-size:1.8rem; font-weight:700; color:#ffd700;}
        .nav-links { list-style:none; display:flex;}
        .nav-links li { margin-left:2rem;}
        .nav-links a { color:#fff; text-decoration:none; font-weight:600; transition:all 0.3s ease; position:relative;}
        .nav-links a::after { content:''; position:absolute; width:0; height:2px; bottom:-5px; left:0; background-color:#ffd700; transition:width 0.3s ease;}
        .nav-links a:hover::after { width:100%;}
        .menu-toggle { display:none; flex-direction:column; cursor:pointer;}
        .menu-toggle span { width:25px; height:3px; background-color:#fff; margin:3px 0; transition:0.3s;}
        section { padding:4rem 1rem; max-width:1200px; margin:0 auto; min-height:100vh;}
        #home { background: linear-gradient(135deg,#000 0%,#333 100%); color:#fff; text-align:center; display:flex; flex-direction:column; justify-content:center; align-items:center; position:relative; overflow:hidden;}
        #home::before { content:''; position:absolute; top:0; left:0; width:100%; height:100%; background:url('https://via.placeholder.com/1920x1080/000/fff?text=Thrift+Streetwear') no-repeat center center/cover; opacity:0.3; z-index:-1;}
        #home h1 { font-family:'Montserrat',sans-serif; font-size:4rem; margin-bottom:1rem; animation:fadeInUp 1s ease-out; }
        #home p { font-size:1.5rem; margin-bottom:2rem; animation:fadeInUp 1.2s ease-out; }
        .cta-btn { background-color:#ffd700; color:#000; padding:1rem 2rem; text-decoration:none; font-weight:700; border-radius:50px; transition:all 0.3s ease; animation:fadeInUp 1.4s ease-out; box-shadow:0 4px 15px rgba(255,215,0,0.3);}
        .cta-btn:hover { transform:translateY(-5px); box-shadow:0 8px 25px rgba(255,215,0,0.5);}
        @keyframes fadeInUp { from {opacity:0; transform:translateY(30px);} to {opacity:1; transform:translateY(0);} }
        #shop { background-color:#fafafa; perspective:1000px;}
        #shop h2 { text-align:center; margin-bottom:3rem; font-size:2.5rem; font-family:'Montserrat',sans-serif;}
        .product-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(300px,1fr)); gap:2rem; }
        .product-card { background-color:#f4f4f4; border-radius:15px; overflow:hidden; box-shadow:0 8px 20px rgba(0,0,0,0.1); transition:all 0.3s ease; transform-style: preserve-3d;}
        .product-card:hover { transform: rotateX(5deg) rotateY(5deg); box-shadow:0 20px 40px rgba(0,0,0,0.2);}
        .product-image { width:100%; height:250px; background-color:#ddd; display:flex; align-items:center; justify-content:center; color:#666; font-size:1.2rem;}
        .product-info { padding:1.5rem; text-align:center;}
        .product-name { font-size:1.3rem; font-weight:600; margin-bottom:0.5rem;}
        .product-price { font-size:1.2rem; color:#ffd700; margin-bottom:1rem;}
        .product-description { margin-bottom:1.5rem; color:#666;}
        .buy-btn { background-color:#000; color:#fff; padding:0.75rem 1.5rem; text-decoration:none; border-radius:50px; display:inline-block; transition:all 0.3s ease; box-shadow:0 4px 15px rgba(0,0,0,0.2);}
        .buy-btn:hover { transform:translateY(-3px); box-shadow:0 8px 25px rgba(0,0,0,0.3);}
        #about { background-color:#fafafa; text-align:center; position:relative;}
        #about::before { content:''; position:absolute; top:20%; left:10%; width:80px; height:80px; background-color:#ffd700; border-radius:50%; opacity:0.1; animation:float 3s ease-in-out infinite;}
        #about h2 { margin-bottom:2rem; font-size:2.5rem; font-family:'Montserrat',sans-serif;}
        #about p { max-width:800px; margin:0 auto; font-size:1.1rem; animation:fadeIn 1s ease-out;}
        @keyframes float { 0%,100%{transform:translateY(0px);} 50%{transform:translateY(-20px);} }
        @keyframes fadeIn { from {opacity:0;} to {opacity:1;} }
        #contact { background-color:#fff;}
        #contact h2 { text-align:center; margin-bottom:3rem; font-size:2.5rem; font-family:'Montserrat',sans-serif;}
        .contact-info { display:flex; flex-wrap:wrap; justify-content:space-around; margin-bottom:3rem;}
        .contact-item { text-align:center; margin:1rem;}
        .contact-item a { color:#333; text-decoration:none; transition:color 0.3s;}
        .contact-item a:hover { color:#ffd700;}
        .contact-form { max-width:600px; margin:0 auto;}
        .form-group { margin-bottom:1.5rem;}
        label { display:block; margin-bottom:0.5rem; font-weight:600;}
        input, textarea { width:100%; padding:1rem; border:2px solid #ddd; border-radius:10px; font-family:inherit; transition:border-color 0.3s;}
        input:focus, textarea:focus { border-color:#ffd700; outline:none;}
        button { background-color:#000; color:#fff; padding:1rem 2rem; border:none; border-radius:50px; cursor:pointer; font-weight:600; transition:all 0.3s ease; box-shadow:0 4px 15px rgba(0,0,0,0.2);}
        button:hover { transform:translateY(-3px); box-shadow:0 8px 25px rgba(0,0,0,0.3);}
        footer { background-color:#000; color:#fff; text-align:center; padding:2rem 1rem;}
        .social-icons { display:flex; justify-content:center; margin-bottom:1rem;}
        .social-icons a { margin:0 1rem; color:#fff; font-size:1.5rem; transition:color 0.3s;}
        .social-icons a:hover { color:#ffd700;}
        @media (max-width:768px){ .nav-links { display:none; flex-direction:column; position:absolute; top:100%; left:0; width:100%; background-color:rgba(0,0,0,0.9); padding:1rem 0;} .nav-links.active { display:flex;} .menu-toggle { display:flex;} #home h1 { font-size:2.5rem;} #home p { font-size:1.2rem;} .product-grid { grid-template-columns:1fr;} }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">The Vault</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#shop">Shop</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="menu-toggle" onclick="toggleMenu()">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </nav>
    </header>

    <section id="home">
        <h1>The Vault</h1>
        <p>Discover Unique Thrift Finds – Streetwear With Character</p>
        <a href="https://www.instagram.com/the_vault_____?igsh=NGoxZHVnMTZwNzB3" class="cta-btn">Follow Us on Instagram</a>
    </section>

    <section id="shop">
        <h2>Shop Our Thrift Collection</h2>
        <div class="product-grid">
            <!-- Product 1 -->
            <div class="product-card">
                <div class="product-image">Vintage Hoodie</div>
                <div class="product-info">
                    <div class="product-name">Retro Hoodie</div>
                    <div class="product-price">$49.99</div>
                    <div class="product-description">Gently pre-loved item with unique style. One-of-a-kind streetwear piece.</div>
                    <a href="https://wa.me/919220510556?text=Hi,%20I%20want%20to%20buy%20this%20Retro%20Hoodie%20from%20The%20Vault." class="buy-btn">Grab This Unique Piece</a>
                </div>
            </div>
            <!-- Product 2 -->
            <div class="product-card">
                <div class="product-image">Vintage Jacket</div>
                <div class="product-info">
                    <div class="product-name">Classic Denim Jacket</div>
                    <div class="product-price">$59.99</div>
                    <div class="product-description">Pre-loved denim with timeless retro vibes. Limited edition style.</div>
                    <a href="https://wa.me/919220510556?text=Hi,%20I%20want%20to%20buy%20this%20Classic%20Denim%20Jacket%20from%20The%20Vault." class="buy-btn">Claim This Vintage Gem</a>
                </div>
            </div>
            <!-- Product 3 -->
            <div class="product-card">
                <div class="product-image">Vintage Tee</div>
                <div class="product-info">
                    <div class="product-name">Graphic Street Tee</div>
                    <div class="product-price">$29.99</div>
                    <div class="product-description">Unique thrift find with retro graphics. Perfect for streetwear enthusiasts.</div>
                    <a href="https://wa.me/919220510556?text=Hi,%20I%20want%20to%20buy%20this%20Graphic%20Street%20Tee%20from%20The%20Vault." class="buy-btn">Grab This Vintage Gem</a>
                </div>
            </div>
        </div>
    </section>

    <section id="about">
        <h2>About The Vault</h2>
        <p>The Vault is a thrift streetwear brand offering one-of-a-kind, pre-loved clothing that brings character and style to your wardrobe. Every item has a story, making each piece truly unique for modern fashion enthusiasts.</p>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <div class="contact-info">
            <div class="contact-item">
                <p>Email: <a href="mailto:support@thevaultco.in">support@thevaultco.in</a></p>
            </div>
            <div class="contact-item">
                <p>WhatsApp: <a href="https://wa.me/919220510556">+919220510556</a></p>
            </div>
            <div class="contact-item">
                <p>Instagram: <a href="https://www.instagram.com/the_vault_____?igsh=NGoxZHVnMTZwNzB3">Follow Us</a></p>
            </div>
        </div>
        <form class="contact-form" onsubmit="submitForm(event)">
            <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" name="message" rows="5" required></textarea>
            </div>
            <button type="submit">Send Message</button>
        </form>
    </section>

    <footer>
        <div class="social-icons">
            <a href="mailto:support@thevaultco.in"><i class="fas fa-envelope"></i></a>
            <a href="https://wa.me/919220510556"><i class="fab fa-whatsapp"></i></a>
            <a href="https://www.instagram.com/the_vault_____?igsh=NGoxZHVnMTZwNzB3"><i class="fab fa-instagram"></i></a>
        </div>
        <div class="contact-info">
            <div class="contact-item">
                <p>Email: <a href="mailto:support@thevaultco.in">support@thevaultco.in</a></p>
            </div>
            <div class="contact-item">
                <p>WhatsApp: <a href="https://wa.me/919220510556">+919220510556</a></p>
            </div>
            <div class="contact-item">
                <p>Instagram: <a href="https://www.instagram.com/the_vault_____?igsh=NGoxZHVnMTZwNzB3">Follow Us</a></p>
            </div>
        </div>
        <p>&copy; 2023 The Vault. All rights reserved.</p>
    </footer>

    <script src="https://kit.fontawesome.com/a076d05399.js"></script>
    <script>
        function toggleMenu() { document.querySelector('.nav-links').classList.toggle('active'); }
        function submitForm(event) { event.preventDefault(); alert('Thank you for your message! We will get back to you soon.'); }
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const hero = document.querySelector('#home');
            hero.style.transform = `translateY(${scrolled * 0.5}px)`;
        });
    </script>
</body>
</html>
