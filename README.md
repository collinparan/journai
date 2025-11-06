# JournAI

> Intelligent journey planning and dispatch system with H3 geospatial indexing

JournAI is a technician dispatch and navigation system designed for field service operations. It enables dispatchers to assign jobs to W2 or 1099 technicians and provides technicians with detailed job information, routes, and ETA calculations.

## 🎯 Features

- **Backend Dispatch Interface** - Assign jobs to W2 or 1099 contractors
- **Automatic Location Detection** - Captures technician's current location on page load
- **Job Acceptance Flow** - Technicians review job details before accepting
- **Smart Routing** - Calculates optimal route and ETA using OSRM
- **H3 Geospatial Indexing** - Precise location tracking with Uber's H3 system
- **Mobile-First Design** - Optimized for technicians using smartphones
- **Clean Google Maps-style Interface** - CartoDB Voyager tiles for familiar UX

## 🚀 Quick Start

### For Dispatchers

1. Open `backend.html` in your browser
2. Enter customer address and job details (e.g., "Washing machine not draining")
3. Select a technician (W2 employee or 1099 contractor)
4. Click "Generate URL"
5. Send the URL via SMS or copy to clipboard

### For Technicians

1. Receive dispatch URL via SMS
2. Click link to open job assignment
3. Allow location access when prompted
4. Review job details, distance, and ETA
5. Click "OK" to accept job and view route
6. Navigate to customer using the map

## 📱 URL Format

Dispatch URLs include all necessary parameters:

```
index.html?lat=41.8781&lng=-87.6298&address=123%20Main%20St&tech=TECH-003&job=Broken%20Washer
```

Parameters:
- `lat` / `lng` - Customer coordinates
- `address` - Customer address
- `tech` - Technician ID
- `job` - Job description

## 🏗️ Tech Stack

- **Frontend**: Vanilla JavaScript (no frameworks)
- **Mapping**: Leaflet.js with CartoDB Voyager tiles
- **Routing**: OSRM (Open Source Routing Machine)
- **Geospatial**: H3 hexagonal indexing (Uber H3)
- **Geocoding**: Nominatim (OpenStreetMap)
- **Design**: Sears Home Services brand colors and typography

## 📂 Project Structure

```
journai/
├── index.html              # Technician interface
├── backend.html            # Dispatcher interface
├── SEARS_DESIGN.md        # Design system documentation
└── README.md              # This file
```

## 🎨 Design System

JournAI follows the Sears Home Services design language:
- **Primary Color**: Sears Blue (#0048bb)
- **Accent Color**: Sears Green (#66ff99)
- **Typography**: IBM Plex Mono (headings) + Outfit (body)
- **Color Distribution**: 60-30-10 rule (white/brand/accent)

See `SEARS_DESIGN.md` for complete design specifications.

## 🧪 Sample Technicians

The backend includes 6 sample technicians:
- **Alice Johnson** (W2) - HVAC, Electrical - ⭐ 4.9
- **Bob Martinez** (1099) - Appliance Repair, Plumbing - ⭐ 4.7
- **Carol Davis** (W2) - Washer/Dryer, Dishwasher - ⭐ 4.8
- **David Chen** (1099) - HVAC, Refrigeration - ⭐ 4.6
- **Emma Wilson** (W2) - Electrical, Appliance Repair - ⭐ 4.9
- **Frank Thompson** (1099) - Plumbing, Water Heater - ⭐ 4.5

## 📍 H3 Geospatial Indexing

JournAI uses Uber's H3 hexagonal hierarchical geospatial indexing system at resolution 12 (~9m edge length) for precise location tracking and analysis.

## 🔐 Privacy & Security

- Location data is processed client-side only
- No data is stored or transmitted to external servers (except routing/geocoding APIs)
- Uses standard browser geolocation API with user permission

## 🌐 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires:
- Geolocation API support
- Modern JavaScript (ES6+)
- HTTPS or localhost for geolocation

## 📄 License

[Specify license]

## 🤝 Contributing

This is a Sears Home Services internal tool. For issues or feature requests, contact the development team.

---

**Built with**: Vanilla JavaScript • Leaflet • H3 • OSRM • CartoDB

**Powered by**: Intelligent dispatch, H3 geospatial indexing, Real-time routing
