<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mapa Interativo com Leaflet.js</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
  <style>
    #map {
      height: 500px;
      width: 100%;
    }
  </style>
</head>
<body>

  <h1>Mapa Interativo com Leaflet.js</h1>
  <div id="map"></div>

  <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
  <script>
    // Inicializa o mapa
    var map = L.map('map').setView([-1.455, -48.490], 12); // Coordenadas de Belém, PA

    // Adiciona camada de tile do OpenStreetMap
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Adiciona marcador com pop-up
    var marker = L.marker([-1.455, -48.490]).addTo(map);
    marker.bindPopup('<b>Belém, PA</b><br>Capital do Pará').openPopup();

    // Adiciona círculo com estilo
    var circle = L.circle([-1.455, -48.490], {
      color: 'blue',
      fillColor: '#30a7d7',
      fillOpacity: 0.5,
      radius: 500
    }).addTo(map);
    circle.bindPopup('Área de interesse');

    // Adiciona polígono com estilo
    var polygon = L.polygon([
      [-1.460, -48.495],
      [-1.450, -48.495],
      [-1.450, -48.485]
    ], {
      color: 'green',
      weight: 3,
      opacity: 0.5,
      fillColor: '#32cd32',
      fillOpacity: 0.2
    }).addTo(map);
    polygon.bindPopup('Área delimitada');

    // Adiciona controle de zoom
    L.control.zoom({
      position: 'topright'
    }).addTo(map);
  </script>

</body>
</html>
