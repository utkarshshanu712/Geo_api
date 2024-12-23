   # This same api but hosted on cloudflare for more saftey and fast work https://geo.geocodingapi.workers.dev/
   # it is best to use 
# Geolocation API

This repository contains a geolocation API built using Node.js and Express. The API provides endpoints to:
1. Find the closest state, district, or country based on latitude and longitude.
2. Find geographic coordinates (latitude and longitude) based on a place name.

---

## Overview

🌈 The Geocoding API provides a simple way to retrieve detailed geographical information, such as the state, district, and country, based on latitude and longitude coordinates. It also supports finding geographic coordinates for a given place name.

---

## Endpoints

### 1. **Find State Based on Latitude and Longitude**
   **GET** `/find-state , /find-coordinates`

   #### Query Parameters:
   - `lat` (required): Latitude of the location.
   - `long` (required): Longitude of the location.

   #### Example Request:
   ```sh
   curl 'https://geo.geocodingapi.workers.dev/find-state?lat=28.6139&long=77.2090'
   ```

   #### Example Response:
   ```json
   {
     "location": "Delhi, India",
     "distance": "0.00"
   }
   ```

### 2. **Find Coordinates Based on Place Name**
   **GET** `/find-coordinates`

   #### Query Parameters:
   - `place` (required): Name of the place (country, state, or district).

   #### Example Request:
   ```sh
   curl 'https://geo.geocodingapi.workers.dev/find-coordinates?place=new-york'
   ```

   #### Example Response:
   ```json
   {
     "place": "New York",
     "latitude": 40.7128,
     "longitude": -74.0060
   }
   ```

   #### Response:
   - **Success:**
     ```json
     {
       "place": "[Place Name]",
       "latitude": [Latitude],
       "longitude": [Longitude]
     }
     ```
   - **Error:**
     ```json
     {
       "error": "Place name not found."
     }
     ```

### 3. **Health Check**
   **GET** `/`

   #### Response:
   ```text
   Server is running
   ```

---

## Example Projects

### 🌏 [Geocoding-API Website](https://github.com/utkarshshanu712/GeoEncodingApi-using-website)
A web-based interface for the Geocoding API.

### 🕑 [Digital Clock](https://github.com/utkarshshanu712/Digital-clock)
An example project demonstrating related features.

---

## Integration

### How to Use the API in Your Project

To integrate this API into your project, follow these steps:

1. **Fetch Data from the API**: Use any HTTP client (like Axios, Fetch API, etc.) to make requests to the API. Here’s an example using JavaScript's Fetch API:

   ```javascript
   async function getLocation(lat, long) {
     const response = await fetch(`https://geo.geocodingapi.workers.dev/find-state?lat=${lat}&long=${long}`);
     const data = await response.json();
     console.log(data.location);
   }

   // Example usage:
   getLocation(28.6139, 77.2090);
   ```

2. **Using Axios**: If you prefer using Axios, first install it in your project:

   ```sh
   npm install axios
   ```

   Then use it to fetch data from the API:

   ```javascript
   const axios = require('axios');

   async function getLocation(lat, long) {
     try {
       const response = await axios.get(`https://geo-api-61zy.onrender.com/find-state`, {
         params: {
           lat: lat,
           long: long
         }
       });
       console.log(response.data.location);
     } catch (error) {
       console.error(error);
     }
   }

   // Example usage:
   getLocation(28.6139, 77.2090);
   ```

3. **Handle the Response**: Once you receive the response from the API, you can integrate it into your application logic as needed.

   ```javascript
   const latitude = 28.6139;
   const longitude = 77.2090;

   getLocation(latitude, longitude).then(location => {
     // Do something with the location data
     console.log(`The location is: ${location}`);
   });
   ```

---

## Code Example

Here’s a snippet of how to handle the API response:

```javascript
if (response.ok) {
  const data = await response.json();
  const location = data.location || "Unknown Location";
  // Update the UI or handle the location data as needed
}
```

---

## How It Works

### Distance Calculation
- The Haversine formula is used to compute the great-circle distance between two points on Earth.

### Data Matching
- Place names are normalized by converting to lowercase and removing non-alphanumeric characters.
- Searches prioritize the smallest geographic unit (district > state > country).

---

## How to Run the Server

### Prerequisites
- [Node.js](https://nodejs.org/) installed.

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the server:
   ```bash
   node app.js
   ```
4. Access the server at:
   ```
   https://geo.geocodingapi.workers.dev/
   <!-- if not work next -->
   https://geo-api-61zy.onrender.com
   ```

---

## Configuration
- Add your geographic data to the `Coordinates` object in the code.
- Ensure the data follows the structure:
  ```json
  {
    "Country_Name": {
      "latitude": 0,
      "longitude": 0,
      "subDistricts": {
        "State_Name": {
          "latitude": 0,
          "longitude": 0,
          "subDistricts": {
            "District_Name": {
              "latitude": 0,
              "longitude": 0
            }
          }
        }
      }
    }
  }
  ```

---

## Contributing
🚀 Feel free to fork this repository and contribute by submitting a pull request. Any improvements, bug fixes, or new features are welcome!

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.
