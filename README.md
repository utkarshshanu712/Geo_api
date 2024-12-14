🌍 **Geocoding API** 🌍

This API provides geographical information based on latitude and longitude coordinates. It returns the closest state, district, and country for the provided coordinates.

## Overview

🌈 The Geocoding API allows users to find geographical locations worldwide based on latitude and longitude. It can return detailed location information, including the state, district, and country.

## Endpoint

- **URL**: `/find-state`
- **Method**: `GET`

## Query Parameters

- `lat` (required): Latitude of the location.
- `long` (required): Longitude of the location.

## Example Request

```sh
curl 'https://geo-api-61zy.onrender.com/find-state?lat=28.6139&long=77.2090'
https://geo-api-61zy.onrender.com/find-state?lat=28.6139&long=77.2090
```

## Example Response

```json
{
  "location": "Delhi, India",
  "distance": "0.00"
}
```

## Integration

### How to Use the API in Your Project

To integrate this API into your project, follow these steps:

1. **Fetch Data from the API**: Use any HTTP client (like Axios, Fetch API, etc.) to make requests to the API. Here’s an example using JavaScript's Fetch API:

   ```javascript
   async function getLocation(lat, long) {
     const response = await fetch(`https://geo-api-61zy.onrender.com/find-state?lat=${lat}&long=${long}`);
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

## Code Example

Here’s a snippet of how to handle the API response:

```javascript
if (response.ok) {
  const data = await response.json();
  const location = data.location || "Unknown Location";
  // Update the UI or handle the location data as needed
}
```

## Contributing

🚀 Feel free to fork this repository and contribute by submitting a pull request. Any improvements, bug fixes, or new features are welcome!

## License

📜 This project is licensed under the MIT License. See the LICENSE file for details.