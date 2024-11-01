
# LandVista Backend

Welcome to the LandVista backend project! This Django application is designed to manage and provide flood risk data for various locations.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [Predict Flood Risk](#predict-flood-risk)
  - [Get Flood Risk](#get-flood-risk)
- [Models](#models)
- [Serialization](#serialization)
- [Contributing](#contributing)
- [License](#license)

## Features

- Store and retrieve flood risk data including location, risk percentage, soil type, elevation, and geographical information.
- Automatically fetch geographical data using the Google Maps API.
- Categorize flood risk based on pre-defined thresholds.

## Installation

To set up the LandVista backend, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd landvista-backend
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`


pip install -r requirements.txt

GOOGLE_MAPS_API_KEY=your_api_key_here

python manage.py migrate


python manage.py runserver


Usage
This backend service can be accessed via the provided API endpoints. You can use tools like Postman or curl to test the endpoints.

API Endpoints
Predict Flood Risk
URL: /predict-flood-risk/
Method: POST


Request Body:

{
  "location": "Location Name",
  "risk_percentage": 50.0,
  "soil_type": "Clay",
  "elevation": 30.0
}



Response:
On success (201 Created):

{
  "message": "Flood risk data created successfully",
  "flood_risk": { /* flood risk details */ }
}

On error (400 Bad Request):

{
  "error": "All fields are required."
}



Get Flood Risk
URL: /flood-risk/<location>/
Method: GET
Response:

On success (200 OK):

{
  "location": "Location Name",
  "risk_percentage": 50.0,
  "soil_type": "Clay",
  "elevation": 30.0,
  "geometry": { /* geometry data */ },
  "risk_category": "Moderate",
  "additional_information": "Additional info here.",
  "map_url": "https://www.google.com/maps/search/?api=1&query=Location%20Name"
}

On error (404 Not Found):

{
  "error": "Location not found"
}



Models
FloodRisk
The FloodRisk model stores information about flood risks associated with different locations. It includes fields for:

location: Name of the location (unique)
risk_percentage: The associated flood risk percentage
soil_type: Type of soil in the location
elevation: Elevation of the location
geometry: Geographical coordinates in JSON format
Serialization
The FloodRiskSerializer class is used to convert FloodRisk model instances into JSON format for API responses.

Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.





