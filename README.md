<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vive la France RP - Vente de Véhicules</title>
    <meta name="description" content="Achetez des véhicules de luxe sur Vive la France RP. Découvrez notre sélection exclusive !">
    <style>
        body { 
            font-family: Arial, sans-serif; 
            text-align: center; 
            padding: 20px; 
            background: #000000; 
            color: white; 
            transition: background 0.3s, color 0.3s;
        }
        .light-mode {
            background: white;
            color: black;
        }
        nav { 
            margin-bottom: 20px; 
            background: #333; 
            padding: 10px; 
            border-radius: 5px; 
        }
        nav a { 
            margin: 10px; 
            text-decoration: none; 
            font-size: 20px; 
            color: white; 
            font-weight: bold; 
        }
        nav a:hover {
            text-decoration: underline;
        }
        section { 
            max-width: 800px; 
            margin: auto; 
            padding: 20px; 
            border: 1px solid #ccc; 
            border-radius: 10px; 
            background: #2c2c2c; 
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
            transition: background 0.3s;
        }
        .light-mode section {
            background: #f0f0f0;
        }
        h1, h2 { 
            color: white;
        }
        .light-mode h1, .light-mode h2 {
            color: black;
        }
        .vehicle { 
            border-bottom: 1px solid #444; 
            padding: 15px; 
            opacity: 0;
            transform: translateY(20px);
            animation: fadeIn 0.5s forwards;
        }
        @keyframes fadeIn {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .vehicle:hover {
            transform: scale(1.05);
            transition: transform 0.3s;
        }
        #theme-toggle {
            background: #0e3a66;
            color: white;
            padding: 10px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        #sort-select {
            margin-bottom: 20px;
            padding: 10px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <button id="theme-toggle">Mode Clair / Sombre</button>
    <h1>Bienvenue sur Vive la France RP - Vente de Véhicules</h1>
    <nav>
        <a href="#accueil">Accueil</a>
        <a href="#vehicules">Véhicules</a>
        <a href="#discord">Discord</a>
    </nav>
    
    <section id="vehicules">
        <h2>Nos Véhicules</h2>
        <select id="sort-select">
            <option value="default">Trier par</option>
            <option value="name-asc">Nom (A-Z)</option>
            <option value="name-desc">Nom (Z-A)</option>
            <option value="price-asc">Prix croissant</option>
            <option value="price-desc">Prix décroissant</option>
        </select>
        <div class="vehicles-container" id="vehicles-list"></div>
    </section>
    
    <section id="discord">
        <h2>Discord</h2>
        <p>Rejoignez notre serveur Discord pour plus d'informations :</p>
        <a href="https://discord.gg/FyjNdNDy" target="_blank">Notre Discord</a>
    </section>
    
    <script>
        const vehicles = [
            { name: "Cupra Formentor 2021", img: "https://img.gta5-mods.com/q95/images/2021-cupra-formentor-replace-fivem-kowalski_pau/c9896b-1.png", price: 20 },
            { name: "Audi RS3 2020 ABT", img: "https://img.gta5-mods.com/q85-w800/images/audi-rs3-2020-addon-fivem-animated-tuning-abt/f78b73-1.jpg", price: 20 },
            { name: "Mercedes-Benz AMG GT63 2018", img: "https://i0.wp.com/gtaland.net/wp-content/uploads/2019/10/1572108405_amggt1_GTALand.net.jpg?fit=800%2C450&ssl=1", price: 20 },
            { name: "Mercedes-Benz Classe A45 AMG", img: "https://img.gta5-mods.com/q85-w800/images/mercedes-classe-a-45-amg-edition-1-add-on-replace/4bf77e-1.jpg", price: 20 },
            { name: "BMW M3 G81 Competition Touring", img: "https://www.motorstore-france.com/public/img/medium/51jpg_6633a36a502ca6.42277254.jpg", price: 20 }
        ];
        
        function renderVehicles() {
            const vehiclesList = document.getElementById("vehicles-list");
            vehiclesList.innerHTML = "";
            vehicles.forEach(vehicle => {
                const div = document.createElement("div");
                div.classList.add("vehicle");
                div.innerHTML = `
                    <h3>${vehicle.name}</h3>
                    <img src="${vehicle.img}" alt="${vehicle.name}">
                    <p><strong>Prix: ${vehicle.price}€</strong></p>
                `;
                vehiclesList.appendChild(div);
            });
        }
        
        document.getElementById("theme-toggle").addEventListener("click", () => {
            document.body.classList.toggle("light-mode");
        });
        
        document.getElementById("sort-select").addEventListener("change", (e) => {
            const value = e.target.value;
            if (value === "name-asc") vehicles.sort((a, b) => a.name.localeCompare(b.name));
            else if (value === "name-desc") vehicles.sort((a, b) => b.name.localeCompare(a.name));
            else if (value === "price-asc") vehicles.sort((a, b) => a.price - b.price);
            else if (value === "price-desc") vehicles.sort((a, b) => b.price - a.price);
            renderVehicles();
        });
        
        renderVehicles();
    </script>
</body>
</html>
