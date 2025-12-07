<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Course Categories</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: #fafafa;
        margin: 0;
        padding: 30px;
    }

    h2 {
        margin: 20px 0;
        cursor: pointer;
        color: #d35400;
        font-size: 26px;
        transition: 0.2s ease;
    }
    h2:hover {
        opacity: 0.7;
    }

    .category-section {
        margin-bottom: 40px;
    }

    .subcategories {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
        gap: 15px;
        overflow: hidden;
        max-height: 0;
        transition: max-height 0.4s ease;
    }

    .subcategory-card {
        border: 2px solid #ff6b6b;
        padding: 12px 15px;
        text-align: center;
        border-radius: 10px;
        background: #fff;
        color: #d64541;
        font-weight: bold;
        cursor: default;
        user-select: none;
    }

    .expanded {
        max-height: 2000px; /* large enough to show all items */
    }

</style>

</head>
<body>

<!---------------------------------------------------------
   CATEGORY TEMPLATE
---------------------------------------------------------->

<div class="category-section">
    <h2 onclick="toggleCategory('dev')">Development</h2>
    <div id="dev" class="subcategories">
        <!-- Development sub-categories -->
        <div class="subcategory-card">android</div>
        <div class="subcategory-card">angularjs</div>
        <div class="subcategory-card">bootstrap</div>
        <div class="subcategory-card">c</div>
        <div class="subcategory-card">cpp</div>
        <div class="subcategory-card">csharp</div>
        <div class="subcategory-card">css</div>
        <div class="subcategory-card">data-structure</div>
        <div class="subcategory-card">debug-test</div>
        <div class="subcategory-card">development-tools</div>
        <div class="subcategory-card">django</div>
        <div class="subcategory-card">drupal</div>
        <div class="subcategory-card">e-commerce</div>
        <div class="subcategory-card">ethical-hacking</div>
        <div class="subcategory-card">game-development</div>
        <div class="subcategory-card">git</div>
        <div class="subcategory-card">hardware</div>
        <div class="subcategory-card">html</div>
        <div class="subcategory-card">ios</div>
        <div class="subcategory-card">java</div>
        <div class="subcategory-card">javascript</div>
        <div class="subcategory-card">jquery</div>
        <div class="subcategory-card">json</div>
        <div class="subcategory-card">machine-learning</div>
        <div class="subcategory-card">matlab</div>
        <div class="subcategory-card">mobile-development-other</div>
        <div class="subcategory-card">mysql</div>
        <div class="subcategory-card">nodejs</div>
        <div class="subcategory-card">nosql</div>
        <div class="subcategory-card">php</div>
        <div class="subcategory-card">programming-other</div>
        <div class="subcategory-card">python</div>
        <div class="subcategory-card">r-programming</div>
        <div class="subcategory-card">react-redux</div>
        <div class="subcategory-card">robotics</div>
        <div class="subcategory-card">ruby</div>
        <div class="subcategory-card">seo</div>
        <div class="subcategory-card">software</div>
        <div class="subcategory-card">sql</div>
        <div class="subcategory-card">system-programming</div>
        <div class="subcategory-card">ux</div>
        <div class="subcategory-card">web-development-other</div>
        <div class="subcategory-card">wordpress</div>
        <div class="subcategory-card">vue</div>
    </div>
</div>

<div class="category-section">
    <h2 onclick="toggleCategory('graphic')">Graphic Design</h2>
    <div id="graphic" class="subcategories">
        <div class="subcategory-card">3d-model</div>
        <div class="subcategory-card">after-effects</div>
        <div class="subcategory-card">animation</div>
        <div class="subcategory-card">graphic-design</div>
        <div class="subcategory-card">photography</div>
        <div class="subcategory-card">photoshop</div>
        <div class="subcategory-card">premiere-pro</div>
        <div class="subcategory-card">video-design</div>
    </div>
</div>

<div class="category-section">
    <h2 onclick="toggleCategory('network')">Network & System</h2>
    <div id="network" class="subcategories">
        <div class="subcategory-card">aws</div>
        <div class="subcategory-card">hosting</div>
        <div class="subcategory-card">linux</div>
        <div class="subcategory-card">mac</div>
        <div class="subcategory-card">network-security</div>
        <div class="subcategory-card">windows</div>
        <div class="subcategory-card">windows-server</div>
    </div>
</div>

<div class="category-section">
    <h2 onclick="toggleCategory('other')">Other</h2>
    <div id="other" class="subcategories">
        <div class="subcategory-card">academic</div>
        <div class="subcategory-card">blockchain</div>
        <div class="subcategory-card">business</div>
        <div class="subcategory-card">certification</div>
        <div class="subcategory-card">health-fitness</div>
        <div class="subcategory-card">languages</div>
        <div class="subcategory-card">lifestyle</div>
        <div class="subcategory-card">marketing</div>
        <div class="subcategory-card">music</div>
        <div class="subcategory-card">office-productivity</div>
        <div class="subcategory-card">personal-development</div>
        <div class="subcategory-card">social-media</div>
    </div>
</div>

<script>
function toggleCategory(id) {
    const area = document.getElementById(id);
    area.classList.toggle('expanded');
}
</script>

</body>
</html>
