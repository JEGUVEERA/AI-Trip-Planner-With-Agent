# AI Trip Planner

## Overview
AI Trip Planner is a smart, AI-powered travel planning application designed to simplify the process of organizing trips. It combines the power of AI, mapping, and user-friendly design to provide an efficient, seamless, and personalized travel planning experience.

## Key Features
- **AI-Powered Trip Planning**: Get personalized travel suggestions based on user preferences.
- **User Authentication**: Securely store and manage user data using Firebase.
- **Interactive Mapping**: Visualize your trip with mapped locations for better decision-making.
- **Responsive Design**: Built with TailwindCSS for an intuitive experience across devices.
- **User-Friendly Interface**: Easy to use and customize, making it ideal for developers.
- **Real-Time Feedback**: Ensures users provide complete trip details for the best itinerary generation.
- **Personalized Itinerary Generation**: AI processes user inputs to create structured, detailed daily plans.

## How It Works
1. **Input Your Trip Details**: Enter destination, duration, budget, preferences, accommodation type, and travel mode.
2. **Refine Your Itinerary**: Customize further with specific requests or additional details.
3. **Generate Itinerary**: Click the "Generate Itinerary" button to receive a tailored travel plan.
4. **View Your Itinerary**: See your complete itinerary with recommended activities, locations, and more.

## Tech Stack
- **Frontend**: React, TailwindCSS
- **Backend**: Firebase, Streamlit
- **AI**: Gemini AI for itinerary generation
- **Mapping**: Google Maps API

## Dependencies
- **React**: For building the user interface.
- **TailwindCSS**: For responsive styling.
- **Firebase**: For user authentication and database.
- **Streamlit**: For AI-driven itinerary generation.
- **Gemini AI**: Generates personalized travel itineraries based on user input.
- **Google Maps API**: Displays trip locations interactively.

## Project Structure
```
AI-Trip-Planner/
│── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TripForm.js
│   │   │   ├── Itinerary.js
│   │   │   ├── Map.js
│   │   ├── pages/
│   │   │   ├── Home.js
│   │   │   ├── Login.js
│   │   ├── App.js
│   │   ├── index.js
│   ├── public/
│   ├── package.json
│── backend/
│   ├── api/
│   │   ├── itinerary_generator.py
│   │   ├── firebase_auth.py
│   ├── server.py
│   ├── requirements.txt
│── README.md
```

## Code Implementation

### **Frontend (React + TailwindCSS)**
#### **TripForm.js** (Collects user inputs for trip planning)
```javascript
import React, { useState } from 'react';

const TripForm = ({ onSubmit }) => {
  const [tripDetails, setTripDetails] = useState({
    destination: '',
    duration: '',
    budget: '',
    preferences: ''
  });

  const handleChange = (e) => {
    setTripDetails({ ...tripDetails, [e.target.name]: e.target.value });
  };

  return (
    <form onSubmit={(e) => { e.preventDefault(); onSubmit(tripDetails); }}>
      <input type="text" name="destination" placeholder="Destination" onChange={handleChange} required />
      <input type="number" name="duration" placeholder="Duration (days)" onChange={handleChange} required />
      <input type="text" name="budget" placeholder="Budget" onChange={handleChange} required />
      <textarea name="preferences" placeholder="Preferences" onChange={handleChange}></textarea>
      <button type="submit">Generate Itinerary</button>
    </form>
  );
};

export default TripForm;
```

#### **Map.js** (Displays trip locations)
```javascript
import React from 'react';
import { GoogleMap, LoadScript, Marker } from '@react-google-maps/api';

const Map = ({ locations }) => {
  return (
    <LoadScript googleMapsApiKey="YOUR_GOOGLE_MAPS_API_KEY">
      <GoogleMap mapContainerStyle={{ height: "400px", width: "100%" }} center={locations[0]} zoom={10}>
        {locations.map((loc, index) => (
          <Marker key={index} position={loc} />
        ))}
      </GoogleMap>
    </LoadScript>
  );
};

export default Map;
```

### **Backend (Streamlit + Firebase)**
#### **itinerary_generator.py** (AI itinerary generation using Gemini AI)
```python
import openai

def generate_itinerary(destination, duration, budget, preferences):
    prompt = f"Plan a {duration}-day trip to {destination} with a budget of {budget}. Preferences: {preferences}."
    response = openai.Completion.create(
        model="gemini-ai",
        prompt=prompt,
        max_tokens=500
    )
    return response.choices[0].text
```

#### **firebase_auth.py** (Firebase authentication setup)
```python
import firebase_admin
from firebase_admin import auth, credentials

cred = credentials.Certificate("path/to/your/firebase_credentials.json")
firebase_admin.initialize_app(cred)

def create_user(email, password):
    user = auth.create_user(email=email, password=password)
    return user.uid
```

## Contributing Repositories
Explore the source code and contribute to the project through the following repositories:
- [AI Trip Planner by mannye3](http://github.com/mannye3/AI-Trip-Planner?utm_source=chatgpt.com)
- [LLM Travel Advisor by vinayaktiwari](https://github.com/vinayaktiwari/LLM-Travel-Advisor)
- [AI Travel Planner by jgalt0311](https://github.com/jgalt0311/ai-travel-planner?utm_source=chatgpt.com)
- [AI-Powered Travel Planner by Vvl1232](https://github.com/Vvl1232/AI-powered-travel-planner)

## Deployment Guide
### **Frontend Deployment (Vercel)**
1. Install Vercel CLI:
   ```bash
   npm install -g vercel
   ```
2. Deploy React frontend:
   ```bash
   vercel --prod
   ```

### **Backend Deployment (Firebase/Streamlit)**
1. Deploy Firebase Authentication and Database.
2. Host AI itinerary generator on **Streamlit Sharing** or **Google Cloud**.
3. Expose AI model endpoint for frontend access.

## Conclusion
The AI Trip Planner simplifies travel planning by leveraging AI to create customized itineraries with minimal effort. Whether you're a traveler seeking convenience or a developer looking to contribute, this project provides a perfect balance of innovation and functionality.

#   A I - T r i p - P l a n n e r - W i t h - A g e n t  
 