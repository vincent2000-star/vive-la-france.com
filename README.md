<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vive la France RP - Vente de Véhicules</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; background: #f4f4f9; }
        nav { margin-bottom: 20px; background: #333; padding: 10px; border-radius: 5px; }
        nav a { margin: 10px; text-decoration: none; font-size: 20px; color: white; font-weight: bold; }
        section { max-width: 800px; margin: auto; padding: 20px; border: 1px solid #ccc; border-radius: 10px; background: #fff; box-shadow: 2px 2px 10px rgba(0,0,0,0.1); }
        h1 { color: #333; }
        .vehicle { border-bottom: 1px solid #ddd; padding: 15px; }
        .vehicle img { width: 100%; max-width: 400px; border-radius: 10px; }
        .pagination { margin-top: 20px; display: flex; justify-content: center; gap: 10px; }
        button { background: #f5f7fa; border: none; padding: 10px; border-radius: 50%; cursor: pointer; }
        button:disabled { opacity: 0.5; cursor: not-allowed; }
        #page-number { background: #0e3a66; color: white; padding: 10px 15px; border-radius: 10px; }
    </style>
</head>
<body>
    <h1>Bienvenue sur Vive la France RP - Vente de Véhicules</h1>
    <nav>
        <a href="#accueil">Accueil</a>
        <a href="#vehicules">Véhicules</a>
        <a href="#discord">Discord</a>
    </nav>
    
    <section id="vehicules">
        <h2>Nos Véhicules</h2>
        <div class="vehicles-container" id="vehicles-list"></div>
    </section>
    
    <section id="discord">
        <h2>Discord</h2>
        <p>Rejoignez notre serveur Discord pour plus d'informations :</p>
        <a href="https://discord.gg/FyjNdNDy" target="_blank">Notre Discord</a>
    </section>
    
    <div class="pagination">
        <button id="prev" disabled>&#x276E;</button> 
        <span id="page-number">1</span>
        <button id="next">&#x276F;</button>
    </div>
    
    <script>
        const vehicles = [
            { name: "Cupra Formentor 2021", img: "https://img.gta5-mods.com/q95/images/2021-cupra-formentor-replace-fivem-kowalski_pau/c9896b-1.png", price: "20€" },
            { name: "Audi RS3 2020 ABT", img: "https://img.gta5-mods.com/q85-w800/images/audi-rs3-2020-addon-fivem-animated-tuning-abt/f78b73-1.jpg", price: "20€" },
            { name: "Mercedes-Benz AMG GT63 2018", img: "https://i0.wp.com/gtaland.net/wp-content/uploads/2019/10/1572108405_amggt1_GTALand.net.jpg?fit=800%2C450&ssl=1", price: "20€" },
            { name: "Mercedes-Benz Classe A45 AMG", img: "https://img.gta5-mods.com/q85-w800/images/mercedes-classe-a-45-amg-edition-1-add-on-replace/4bf77e-1.jpg", price: "20€" },
            { name: "BMW M3 G81 Competition Touring", img: "https://www.motorstore-france.com/public/img/medium/51jpg_6633a36a502ca6.42277254.jpg", price: "20€" }
        ];
        
        const itemsPerPage = 4;
        let currentPage = 1;
        
        const vehiclesList = document.getElementById("vehicles-list");
        const pageNumber = document.getElementById("page-number");
        const prevButton = document.getElementById("prev");
        const nextButton = document.getElementById("next");
        
        function renderVehicles() {
            vehiclesList.innerHTML = "";
            const start = (currentPage - 1) * itemsPerPage;
            const end = start + itemsPerPage;
            const visibleVehicles = vehicles.slice(start, end);
            
            visibleVehicles.forEach(vehicle => {
                const div = document.createElement("div");
                div.classList.add("vehicle");
                div.innerHTML = `
                    <h3>${vehicle.name}</h3>
                    <img src="${vehicle.img}" alt="${vehicle.name}">
                    <p>Prix: ${vehicle.price}</p>
                `;
                vehiclesList.appendChild(div);
            });
        }
        
        function updatePagination() {
            pageNumber.textContent = currentPage;
            prevButton.disabled = currentPage === 1;
            nextButton.disabled = currentPage === Math.ceil(vehicles.length / itemsPerPage);
        }
        
        prevButton.addEventListener("click", () => {
            if (currentPage > 1) {
                currentPage--;
                renderVehicles();
                updatePagination();
            }
        });
        
        nextButton.addEventListener("click", () => {
            if (currentPage < Math.ceil(vehicles.length / itemsPerPage)) {
                currentPage++;
                renderVehicles();
                updatePagination();
            }
        });
        
        renderVehicles();
        updatePagination();
    </script>
</body>
</html>

    
