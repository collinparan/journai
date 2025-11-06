# JournAI

> Intelligent journey planning and dispatch system with H3 geospatial indexing

JournAI is a technician dispatch and navigation system designed for field service operations. It enables dispatchers to assign jobs to W2 or 1099 technicians and provides technicians with detailed job information, routes, and ETA calculations.

## 🎯 Features

- **Backend Dispatch Interface** - Assign jobs to W2 or 1099 contractors
- **Automatic Location Detection** - Captures technician's current location on page load
- **Job Acceptance Flow** - Technicians review job details before accepting
- **Smart Routing** - Calculates optimal route and ETA using OSRM
- **H3 Geospatial Indexing** - Precise location tracking with Uber's H3 system
- **Real-Time Location Tracking** - Logs technician location every 5 minutes during job
- **Audio Recording & Transcription** - Records customer interactions with optional Whisper AI transcription
- **Comprehensive Data Export** - Downloads complete job data (location points, audio, transcription)
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
7. Click "Arrived at Customer Location" to start audio recording
8. Complete the service call
9. Click "Job Complete" to stop tracking and download data

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
- **Audio Recording**: MediaRecorder API (WebM/MP4)
- **Transcription**: OpenAI Whisper API (optional)
- **Storage**: Browser localStorage + file downloads
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

## 🎙️ Audio Transcription Setup (Optional)

To enable automatic transcription of customer interactions:

1. Get an OpenAI API key from https://platform.openai.com/api-keys
2. Open `index.html` and find line 418:
   ```javascript
   const OPENAI_API_KEY = ''; // Set your OpenAI API key here
   ```
3. Add your API key:
   ```javascript
   const OPENAI_API_KEY = 'sk-...your-key-here...';
   ```
4. Save the file

**How it works:**
- When a technician clicks "Arrived at Customer Location", audio recording starts
- When they click "Job Complete", the audio is sent to OpenAI Whisper API for transcription
- The transcription is included in the downloaded `data.json` file
- If no API key is set, audio is still recorded but not transcribed

**Cost:** OpenAI Whisper API costs $0.006 per minute of audio (as of 2024)

**Privacy Note:** Audio is sent to OpenAI's servers for transcription. Ensure compliance with local recording and privacy laws.

## 📦 Data Export Format

When a job is completed, JournAI downloads two files:

**1. data.json** - Complete job tracking data:
```json
{
  "job_id": "JOB-1699123456789",
  "technician_id": "TECH-001",
  "job_details": "Washing machine not draining",
  "destination": "123 Main St, Chicago, IL",
  "start_time": "2024-11-05T14:30:00.000Z",
  "arrived_time": "2024-11-05T15:15:00.000Z",
  "end_time": "2024-11-05T16:45:00.000Z",
  "duration_minutes": 135,
  "status": "completed",
  "audio_file": "audio_TECH-001_JOB-1699123456789.webm",
  "transcription": "Full text transcription of customer interaction...",
  "total_locations": 18,
  "locations": [
    {
      "timestamp": "2024-11-05T14:30:00.000Z",
      "latitude": 41.8781,
      "longitude": -87.6298,
      "h3_index": "8c2a1072b59ffff",
      "accuracy_meters": 10,
      "speed_mps": 15.2,
      "heading_degrees": 180,
      "note": null
    }
  ]
}
```

**2. Audio file** (WebM or MP4 format):
- Filename: `audio_[TECH-ID]_[JOB-ID].webm`
- Contains full recording from arrival to completion
- Quality: 44.1kHz with echo cancellation and noise suppression

## 🔐 Privacy & Security

- Location data is processed client-side only
- Job data stored in browser localStorage until download
- No backend server required for basic operation
- Audio recordings optional and require explicit user action
- External API calls: OSRM (routing), Nominatim (geocoding), OpenAI Whisper (transcription - optional)
- Uses standard browser geolocation and MediaRecorder APIs with user permission

## 🌐 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires:
- Geolocation API support
- MediaRecorder API support (for audio recording)
- Modern JavaScript (ES6+)
- HTTPS or localhost for geolocation and audio recording

## 📄 License

[Specify license]

## 🤝 Contributing

This is a Sears Home Services internal tool. For issues or feature requests, contact the development team.

---

**Built with**: Vanilla JavaScript • Leaflet • H3 • OSRM • CartoDB • OpenAI Whisper

**Powered by**: Intelligent dispatch, H3 geospatial indexing, Real-time routing, Audio transcription
