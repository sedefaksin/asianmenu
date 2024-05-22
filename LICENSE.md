<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asian Kitchen's Menu</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Asian Kitchen's Menu</h1>
        <div class="btn-container">
            <button class="btn" id="all">All</button>
            <button class="btn" id="korean">Korean</button>
            <button class="btn" id="chinese">Chinese</button>
            <button class="btn" id="japanese">Japanese</button>
            <button class="btn" id="thai">Thai</button>
        </div>
    </header>
    <section class="section-center">
        <div id="menu-items"></div>
    </section>
    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f0f0f0;
}

header {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 20px 0;
}

.btn-container {
    margin-top: 20px;
}

.btn {
    background-color: #555;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 0 5px;
    cursor: pointer;
}

.btn:hover {
    background-color: #777;
}

.section-center {
    width: 90vw;
    margin: auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 50px 0;
}

.menu-item {
    background-color: #fff;
    border-radius: 5px;
    padding: 20px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.menu-item img {
    width: 100%;
    border-radius: 5px;
    margin-bottom: 15px;
}

.menu-item h3 {
    font-size: 20px;
    margin-bottom: 10px;
}

.menu-item p {
    font-size: 16px;
    color: #555;
}


// Menü öğeleri
const menu = [
    {
        id: 1,
        title: "Bibimbap",
        category: "korean",
        price: 12.99,
        img: "images/bibimbap.jpg",
        desc: "Traditional Korean mixed rice with assorted vegetables and meat."
    },
    {
        id: 2,
        title: "Sweet and Sour Chicken",
        category: "chinese",
        price: 9.99,
        img: "images/sweet-and-sour-chicken.jpg",
        desc: "Crispy fried chicken pieces coated in a tangy sweet and sour sauce."
    },
    {
        id: 3,
        title: "Sushi Platter",
        category: "japanese",
        price: 16.99,
        img: "images/sushi-platter.jpg",
        desc: "Assorted sushi rolls with fresh seafood and vegetables."
    },
    {
        id: 4,
        title: "Pad Thai",
        category: "thai",
        price: 11.99,
        img: "images/pad-thai.jpg",
        desc: "Classic Thai stir-fried noodles with shrimp, tofu, peanuts, and bean sprouts."
    },
    {
        id: 5,
        title: "Kimchi Fried Rice",
        category: "korean",
        price: 10.99,
        img: "images/kimchi-fried-rice.jpg",
        desc: "Spicy fried rice with kimchi, pork, and vegetables."
    },
    {
        id: 6,
        title: "General Tso's Chicken",
        category: "chinese",
        price: 11.99,
        img: "images/general-tsos-chicken.jpg",
        desc: "Crispy chicken pieces tossed in a sweet and spicy sauce."
    },
    {
        id: 7,
        title: "Sashimi",
        category: "japanese",
        price: 18.99,
        img: "images/sashimi.jpg",
        desc: "Fresh slices of raw fish served with soy sauce and wasabi."
    },
    {
        id: 8,
        title: "Tom Yum Soup",
        category: "thai",
        price: 8.99,
        img: "images/tom-yum-soup.jpg",
        desc: "Spicy and sour Thai soup with shrimp, mushrooms, and lemongrass."
    },
];

// Tüm menü öğelerini göster
window.addEventListener("DOMContentLoaded", function () {
    displayMenuItems(menu);
});

// Butonları seç
const btns = document.querySelectorAll(".btn");

// Butonlara click event listener ekle
btns.forEach(function (btn) {
    btn.addEventListener("click", function (e) {
        const category = e.currentTarget.id;
        const menuCategory = menu.filter(function (menuItem) {
            if (menuItem.category === category || category === "all") {
                return menuItem;
            }
        });
        displayMenuItems(menuCategory);
    });
});

// Menü öğelerini ekrana yazdır
function displayMenuItems(menuItems) {
    const menuSection = document.getElementById("menu-items");
    let displayMenu = menuItems.map(function (item) {
        return `<article class="menu-item">
                    <img src="${item.img}" alt="${item.title}" class="photo">
                    <div class="item-info">
                        <header>
                            <h3>${item.title}</h3>
                            <h4>$${item.price.toFixed(2)}</h4>
                        </header>
                        <p class="item-text">${item.desc}</p>
                    </div>
                </article>`;
    });
    displayMenu = displayMenu.join("");
    menuSection.innerHTML = displayMenu;
}
