#  heritmapsite
The site code of heritmap
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Heritmap</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Inter', sans-serif;
      background: #f9f9f9;
      color: #333;
    }
    header {
      padding: 2rem;
      text-align: center;
      background-color: #fff;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
    }
    h1 {
      margin: 0;
      font-size: 2.5rem;
    }
    #map {
      width: 100%;
      height: 80vh;
    }
    .popup {
      font-size: 14px;
    }
  </style>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
</head>
<body>
  <header>
    <h1>Heritmap: Discover China's Cultural Heritage</h1>
  </header>

  <div id="map"></div>

  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
  <script>
    const map = L.map('map').setView([34.2, 108.9], 5); // Center on China

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    const sites = [
      {
        name: "Terracotta Army",
        coords: [34.3846, 109.2732],
        description: "A famous archaeological site in Xi'an, Shaanxi Province."
      },
      {
        name: "The Forbidden City",
        coords: [39.9163, 116.3971],
        description: "The former Chinese imperial palace from the Ming to the Qing dynasty."
      },
      {
        name: "Mogao Caves",
        coords: [40.0459, 94.8091],
        description: "Also known as the Thousand Buddha Grottoes, located in Dunhuang."
      }
    ];

    sites.forEach(site => {
      L.marker(site.coords).addTo(map)
        .bindPopup(`<div class='popup'><strong>${site.name}</strong><br>${site.description}</div>`);
    });
  </script>
</body>
</html>
