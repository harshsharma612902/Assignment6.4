The HTML File (index.html)
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Positioning Practice</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <!-- Step 2: Sticky Navigation Bar -->
    <nav class="sticky-nav">
        <div class="logo">PositioningDemo</div>
        <ul>
            <li><a href="#intro">Home</a></li>
            <li><a href="#cards-section">Cards</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <!-- Step 1: Scrollable Sections -->
    <main class="content-container">
        
        <section id="intro" class="section">
            <h1>CSS Positioning Showcase</h1>
            <p>Scroll down to observe how the sticky navigation bar stays at the top, and the floating button stays anchored to the bottom-right corner of your viewport.</p>
        </section>

        <section id="cards-section" class="section">
            <h2>Positioned Badges Inside Cards</h2>
            
            <!-- Steps 4 & 5: Relative Parent and Absolute Child (Badge) -->
            <div class="card-grid">
                <div class="card">
                    <span class="badge">Hot</span>
                    <h3>Featured Product</h3>
                    <p>This card has a relative positioning parent, allowing the badge to be positioned absolutely in the top-right corner.</p>
                </div>
                
                <div class="card">
                    <span class="badge sale">20% Off</span>
                    <h3>Special Offer</h3>
                    <p>Absolute positioning gives precise control over element placement within a defined relative container.</p>
                </div>
            </div>
        </section>

        <section id="contact" class="section">
            <h2>More Scrollable Content</h2>
            <p>Keep scrolling to test the fixed position of the floating help button across different vertical positions on the page.</p>
        </section>

    </main>

    <!-- Step 3: Floating Action Button (Fixed Position) -->
    <button class="fab" title="Need Help?">💬</button>

</body>
</html>
2. The CSS File (style.css)
CSS
/* Global Page Reset & Styles */
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f8fafc;
    color: #334155;
    margin: 0;
    padding: 0;
    line-height: 1.6;
}

/* STEP 2: Sticky Navigation Bar */
.sticky-nav {
    position: sticky;
    top: 0;
    background-color: #1e293b;
    color: #ffffff;
    padding: 15px 30px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* STEP 6: z-index ensures navbar stays above scrolling content */
    z-index: 100;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.sticky-nav .logo {
    font-weight: bold;
    font-size: 1.25rem;
}

.sticky-nav ul {
    list-style: none;
    display: flex;
    gap: 20px;
    margin: 0;
    padding: 0;
}

.sticky-nav a {
    color: #ffffff;
    text-decoration: none;
    font-weight: 600;
    transition: color 0.2s;
}

.sticky-nav a:hover {
    color: #38bdf8;
}

/* Page Layout */
.content-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 40px 20px;
}

.section {
    padding: 60px 0;
    border-bottom: 1px solid #e2e8f0;
}

.section h1, .section h2 {
    color: #0f172a;
    margin-top: 0;
}

/* STEP 5: Relative Parent Element for Cards */
.card-grid {
    display: flex;
    gap: 20px;
    margin-top: 20px;
    flex-wrap: wrap;
}

.card {
    position: relative; /* Establishes positioning context for absolute children */
    background-color: #ffffff;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    padding: 25px;
    flex: 1;
    min-width: 250px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
}

/* STEP 4: Absolute Positioned Badge Inside the Card */
.badge {
    position: absolute;
    top: 15px;
    right: 15px;
    background-color: #ef4444;
    color: white;
    font-size: 0.75rem;
    font-weight: bold;
    padding: 4px 10px;
    border-radius: 12px;
    text-transform: uppercase;
}

.badge.sale {
    background-color: #10b981;
}

/* STEP 3 & 6: Fixed Position Floating Action Button (FAB) */
.fab {
    position: fixed;
    bottom: 30px;
    right: 30px;
    background-color: #3b82f6;
    color: white;
    border: none;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    font-size: 1.5rem;
    cursor: pointer;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    /* STEP 6: High z-index ensures button floats above all page elements */
    z-index: 1000; 
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background-color 0.2s, transform 0.2s;
}

.fab:hover {
    background-color: #2563eb;
    transform: scale(1.05);
}