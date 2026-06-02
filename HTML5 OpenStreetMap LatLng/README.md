

`index.html`
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>OpenStreetMap + Leaflet — Lat/Lng Example</title>

  
  <!-- Leaflet CSS -->
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
    integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
    crossorigin=""
    />

  <style>
    html, body, #map { height: 100%; margin: 0; padding: 0; }
    body { font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; }
    .controls {
      position: absolute;
      z-index: 1000;
      left: 12px;
      top: 12px;
      background: rgba(255,255,255,0.95);
      border-radius: 8px;
      padding: 10px;
      box-shadow: 0 4px 14px rgba(0,0,0,0.15);
      min-width: 220px;
    }
    .coords { font-weight: 600; margin-top: 6px; }
    .btn { display:inline-block; padding:6px 10px; border-radius:6px; border:1px solid #ddd; cursor:pointer; margin-top:6px; background:#f7f7f7; }
    .btn:hover { background:#eee; }
    small { color:#666; display:block; margin-top:4px; }
  </style>
</head>
<body>
  <div id="map"></div>

  <div class="controls" id="controls">
    <div>
      <strong>OpenStreetMap (Leaflet)</strong>
      <small>Click on map to place marker and read lat/lng</small>
    </div>

    <div style="margin-top:8px;">
      <button id="locateBtn" class="btn">Use my location</button>
      <button id="clearBtn" class="btn">Clear marker</button>
    </div>

    <div class="coords" id="coords">Lat: — , Lng: —</div>
    <div id="accuracy" style="font-size:12px;color:#666;"></div>
  </div>

  <!-- Leaflet JS -->
  <script
    src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
    integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
    crossorigin=""
  ></script>

  <script>
    // --- Initialize map ---
    const map = L.map('map', {
      center: [20.5937, 78.9629], // default center (India)
      zoom: 5,
      zoomControl: true,
    });

    // OpenStreetMap tile layer
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 19,
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    // UI elements
    const coordsEl = document.getElementById('coords');
    const accuracyEl = document.getElementById('accuracy');
    const locateBtn = document.getElementById('locateBtn');
    const clearBtn = document.getElementById('clearBtn');

    let clickMarker = null;
    let userMarker = null;
    let userCircle = null;

    // Format lat/lng to fixed decimals
    function fmt(n) { return n === null ? '—' : Number(n).toFixed(6); }

    // Update coords display
    function updateCoordsDisplay(lat, lng, accuracy=null) {
      coordsEl.textContent = `Lat: ${fmt(lat)} , Lng: ${fmt(lng)}`;
      if (accuracy !== null) {
        accuracyEl.textContent = `Accuracy: ±${Number(accuracy).toFixed(1)} meters`;
      } else {
        accuracyEl.textContent = '';
      }
    }

    // Add marker on map click & show coords
    map.on('click', (e) => {
      const { lat, lng } = e.latlng;

      // remove previous click marker
      if (clickMarker) map.removeLayer(clickMarker);

      clickMarker = L.marker([lat, lng], { draggable: true }).addTo(map)
        .bindPopup(`Clicked at<br>Lat: ${fmt(lat)}<br>Lng: ${fmt(lng)}`)
        .openPopup();

      updateCoordsDisplay(lat, lng);

      // when marker is dragged update coords
      clickMarker.on('dragend', (ev) => {
        const p = ev.target.getLatLng();
        ev.target.setPopupContent(`Marker at<br>Lat: ${fmt(p.lat)}<br>Lng: ${fmt(p.lng)}`);
        updateCoordsDisplay(p.lat, p.lng);
      });
    });

    // Clear marker
    clearBtn.addEventListener('click', () => {
      if (clickMarker) { map.removeLayer(clickMarker); clickMarker = null; }
      updateCoordsDisplay(null, null);
    });

    // Use HTML5 Geolocation (one-shot)
    locateBtn.addEventListener('click', () => {
      if (!navigator.geolocation) {
        alert('Geolocation is not supported by your browser');
        return;
      }

      locateBtn.textContent = 'Locating…';
      navigator.geolocation.getCurrentPosition((position) => {
        const lat = position.coords.latitude;
        const lng = position.coords.longitude;
        const accuracy = position.coords.accuracy;

        // remove old user marker/circle
        if (userMarker) map.removeLayer(userMarker);
        if (userCircle) map.removeLayer(userCircle);

        userMarker = L.marker([lat, lng]).addTo(map)
          .bindPopup(`You are here<br>Lat: ${fmt(lat)}<br>Lng: ${fmt(lng)}`)
          .openPopup();

        userCircle = L.circle([lat, lng], { radius: accuracy }).addTo(map);

        map.setView([lat, lng], 15);
        updateCoordsDisplay(lat, lng, accuracy);

        locateBtn.textContent = 'Use my location';
      }, (err) => {
        alert('Geolocation error: ' + err.message);
        locateBtn.textContent = 'Use my location';
      }, {
        enableHighAccuracy: true,
        timeout: 10000,
        maximumAge: 0
      });
    });

    // OPTIONAL: continuously follow user (watch), commented out for safety
    // let watchId = null;
    // function startWatching() {
    //   if (!navigator.geolocation) return;
    //   watchId = navigator.geolocation.watchPosition((pos) => {
    //     const lat = pos.coords.latitude, lng = pos.coords.longitude, acc = pos.coords.accuracy;
    //     if (userMarker) map.removeLayer(userMarker);
    //     if (userCircle) map.removeLayer(userCircle);
    //     userMarker = L.marker([lat, lng]).addTo(map);
    //     userCircle = L.circle([lat, lng], { radius: acc }).addTo(map);
    //     updateCoordsDisplay(lat, lng, acc);
    //   }, (err) => console.warn(err), { enableHighAccuracy: true });
    // }

    // Initial display
    updateCoordsDisplay(null, null);
  </script>
</body>
</html>
```