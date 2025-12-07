<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Course Categories</title>
    
    <!-- Icons Libraries -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css">

    <style>
        :root {
            --card-border: #ff675f;
            --card-text: #ff675f;
            --bg-color: #ffffff;
            --header-dev: #ea5252;
            --header-design: #f68b1e;
            --header-network: #007791;
            --header-other: #2d2f31;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f7f9fa;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            padding: 20px;
            border-radius: 4px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.08);
        }

        /* Accordion Section */
        .category-section {
            margin-bottom: 20px;
            border-bottom: 1px solid #e0e0e0;
        }

        .category-section:last-child {
            border-bottom: none;
        }

        /* Headers */
        .category-header {
            font-size: 1.1rem;
            font-weight: 700;
            padding: 15px 0;
            cursor: pointer;
            user-select: none;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        /* Specific Header Colors based on screenshots */
        .header-Development { color: var(--header-dev); }
        .header-Graphic.Design { color: var(--header-design); }
        .header-Network.\&.System { color: var(--header-network); }
        .header-Other { color: var(--header-other); }

        /* Accordion Icon */
        .category-header::after {
            content: '\f078'; /* FontAwesome Chevron Down */
            font-family: "Font Awesome 6 Free";
            font-weight: 900;
            font-size: 0.8rem;
            color: #666;
            transition: transform 0.3s ease;
        }

        .category-header.active::after {
            transform: rotate(180deg);
        }

        /* Subcategories Container */
        .subcategory-container {
            display: none; /* Hidden by default */
            flex-wrap: wrap;
            gap: 15px;
            padding-bottom: 20px;
        }

        .subcategory-container.show {
            display: flex;
            animation: fadeIn 0.3s ease-in-out;
        }

        /* Card Style */
        .card {
            display: flex;
            align-items: center;
            border: 1px solid var(--card-border);
            padding: 10px 15px;
            border-radius: 4px; /* Rounded rectangle */
            background-color: white;
            color: var(--card-text);
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
            min-width: 120px;
        }

        .card:hover {
            background-color: #fff0f0;
        }

        .card:active {
            transform: scale(0.98);
        }

        /* Icon Styling inside Card */
        .card i {
            font-size: 1.2rem;
            margin-right: 10px;
            display: inline-block;
            width: 20px;
            text-align: center;
        }

        /* Icon Colors (Generic mapping to maintain the colorful look) */
        .card i.colored {
            /* Devicon handles colors automatically for 'colored' class, 
               but we can force overrides if needed. 
               The screenshot shows mostly uniform color icons, 
               but some (like AWS, Linux) have their own colors. 
            */
        }
        
        /* Helper to fix specific icon colors if they aren't loading correctly */
        .devicon-android-plain { color: #3DDC84; }
        .devicon-angularjs-plain { color: #E23237; }
        .devicon-bootstrap-plain { color: #7952B3; }
        /* ... can add more specific brand colors here, 
           or rely on the 'colored' class from devicon 
        */

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .card {
                flex: 1 1 calc(50% - 15px);
            }
        }
        @media (max-width: 480px) {
            .card {
                flex: 1 1 100%;
            }
        }
    </style>
</head>
<body>

<div class="container" id="app">
    <!-- JS will populate content here -->
</div>

<script>
    // 1. Data Structure
    const categories = [
        {
            name: "Development",
            items: [
                "android", "angularjs", "bootstrap", "c", "cpp", "csharp", "css", 
                "data-structure", "debug-test", "development-tools", "django", "drupal", 
                "e-commerce", "ethical-hacking", "game-development", "git", "hardware", 
                "html", "ios", "java", "javascript", "jquery", "json", "machine-learning", 
                "matlab", "mobile-development-other", "mysql", "nodejs", "nosql", "php", 
                "programming-other", "python", "r-programming", "react-redux", "robotics", 
                "ruby", "seo", "software", "sql", "system-programming", "ux", 
                "web-development-other", "wordpress", "vue"
            ]
        },
        {
            name: "Graphic Design",
            items: [
                "3d-model", "after-effects", "animation", "graphic-design", "photography", 
                "photoshop", "premiere-pro", "video-design"
            ]
        },
        {
            name: "Network & System",
            items: [
                "aws", "hosting", "linux", "mac", "network-security", "windows", "windows-server"
            ]
        },
        {
            name: "Other",
            items: [
                "academic", "blockchain", "business", "certification", "health-fitness", 
                "languages", "lifestyle", "marketing", "music", "office-productivity", 
                "personal-development", "social-media"
            ]
        }
    ];

    // 2. Icon Mapping Helper
    // Maps item names to specific FontAwesome (fa-) or Devicon (devicon-) classes
    function getIconClass(item) {
        const map = {
            // Development
            'android': 'devicon-android-plain colored',
            'angularjs': 'devicon-angularjs-plain colored',
            'bootstrap': 'devicon-bootstrap-plain colored',
            'c': 'devicon-c-plain colored',
            'cpp': 'devicon-cplusplus-plain colored',
            'csharp': 'devicon-csharp-plain colored',
            'css': 'devicon-css3-plain colored',
            'data-structure': 'fas fa-layer-group',
            'debug-test': 'fas fa-bug',
            'development-tools': 'fas fa-tools',
            'django': 'devicon-django-plain colored',
            'drupal': 'devicon-drupal-plain colored',
            'e-commerce': 'fas fa-shopping-cart',
            'ethical-hacking': 'fas fa-user-secret',
            'game-development': 'fas fa-gamepad',
            'git': 'devicon-git-plain colored',
            'hardware': 'fas fa-microchip',
            'html': 'devicon-html5-plain colored',
            'ios': 'devicon-apple-original colored', // using apple for ios
            'java': 'devicon-java-plain colored',
            'javascript': 'devicon-javascript-plain colored',
            'jquery': 'devicon-jquery-plain colored',
            'json': 'devicon-json-plain colored',
            'machine-learning': 'fas fa-brain',
            'matlab': 'devicon-matlab-plain colored',
            'mobile-development-other': 'fas fa-mobile-alt',
            'mysql': 'devicon-mysql-plain colored',
            'nodejs': 'devicon-nodejs-plain colored',
            'nosql': 'fas fa-database',
            'php': 'devicon-php-plain colored',
            'programming-other': 'fas fa-code',
            'python': 'devicon-python-plain colored',
            'r-programming': 'devicon-r-plain colored',
            'react-redux': 'devicon-react-original colored',
            'robotics': 'fas fa-robot',
            'ruby': 'devicon-ruby-plain colored',
            'seo': 'fas fa-search',
            'software': 'fas fa-compact-disc',
            'sql': 'fas fa-database',
            'system-programming': 'fas fa-terminal',
            'ux': 'fab fa-figma', // approximating UX
            'web-development-other': 'fas fa-globe',
            'wordpress': 'devicon-wordpress-plain colored',
            'vue': 'devicon-vuejs-plain colored',

            // Graphic Design
            '3d-model': 'fas fa-cube',
            'after-effects': 'devicon-aftereffects-plain colored',
            'animation': 'fas fa-film',
            'graphic-design': 'fas fa-palette',
            'photography': 'fas fa-camera',
            'photoshop': 'devicon-photoshop-plain colored',
            'premiere-pro': 'devicon-premierepro-plain colored',
            'video-design': 'fas fa-video',

            // Network & System
            'aws': 'devicon-amazonwebservices-original colored',
            'hosting': 'fas fa-server',
            'linux': 'devicon-linux-plain colored',
            'mac': 'devicon-apple-original colored',
            'network-security': 'fas fa-shield-alt',
            'windows': 'devicon-windows8-original colored',
            'windows-server': 'fas fa-network-wired',

            // Other
            'academic': 'fas fa-graduation-cap',
            'blockchain': 'fas fa-link',
            'business': 'fas fa-briefcase',
            'certification': 'fas fa-certificate',
            'health-fitness': 'fas fa-heartbeat',
            'languages': 'fas fa-language',
            'lifestyle': 'fas fa-spa',
            'marketing': 'fas fa-bullhorn',
            'music': 'fas fa-music',
            'office-productivity': 'fas fa-paperclip',
            'personal-development': 'fas fa-user-plus',
            'social-media': 'fas fa-share-alt'
        };

        return map[item] || 'fas fa-tag'; // Default icon
    }

    // 3. Render Function
    function renderCategories() {
        const app = document.getElementById('app');
        
        categories.forEach(cat => {
            // Create Section
            const section = document.createElement('div');
            section.className = 'category-section';

            // Create Header
            const header = document.createElement('div');
            header.className = `category-header header-${cat.name.replace(/\s|&/g, '.')}`;
            header.innerHTML = `<span>${cat.name}</span>`;
            
            // Create Content Container
            const content = document.createElement('div');
            content.className = 'subcategory-container';

            // Populate Cards
            cat.items.forEach(item => {
                const card = document.createElement('div');
                card.className = 'card';
                
                // Determine icon class
                const iconClass = getIconClass(item);
                
                card.innerHTML = `<i class="${iconClass}"></i><span>${item}</span>`;
                content.appendChild(card);
            });

            // Add Click Event for Accordion
            header.addEventListener('click', () => {
                const isVisible = content.classList.contains('show');
                
                // Optional: Close others (uncomment if you want only one open at a time)
                // document.querySelectorAll('.subcategory-container').forEach(el => el.classList.remove('show'));
                // document.querySelectorAll('.category-header').forEach(el => el.classList.remove('active'));

                if (!isVisible) {
                    content.classList.add('show');
                    header.classList.add('active');
                } else {
                    content.classList.remove('show');
                    header.classList.remove('active');
                }
            });

            // Removed the code block that opened 'Development' by default
            // to make it consistent with other sections.

            section.appendChild(header);
            section.appendChild(content);
            app.appendChild(section);
        });
    }

    // Initialize
    renderCategories();

</script>

</body>
</html>
