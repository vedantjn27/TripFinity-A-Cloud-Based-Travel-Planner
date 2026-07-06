# Setup Guide for Tripfinity (Cloud-Based Travel Planner)

This guide provides step-by-step instructions to set up the Tripfinity application on your local machine.

## Prerequisites
1. **Python 3.8+**: Ensure Python is installed on your system.
2. **MySQL Server**: A running instance of MySQL Server.
3. **Firebase Account**: A Firebase project with Authentication (Email/Password) and Cloud Storage enabled.
4. **API Keys**:
   - OpenWeather API Key
   - Google Places/Maps API Key

## 1. Database Setup (MySQL)
1. Log in to your MySQL server as `root` (or another administrative user).
2. Create the database:
   ```sql
   CREATE DATABASE travel_planner;
   ```
3. Update `db_utils.py` with your MySQL credentials (username, password, host).
4. Run the appropriate SQL schemas to create tables for `users`, `trips`, `itineraries`, `expenses`, `travel_notes`, `packing_list_items`, etc. Ensure the tables match the query structures used in the python modules.

## 2. Firebase Configuration
1. Go to the Firebase Console and create a new project.
2. Enable **Authentication** (Email/Password provider).
3. Enable **Cloud Storage** and update the storage security rules to allow read/write access.
4. Generate a new Private Key from **Project Settings > Service Accounts** and download the resulting JSON file.
5. In `firebase_config.py`:
   - Update the path to your downloaded JSON credentials file in the `credentials.Certificate(...)` declaration.
   - Update the `firebase_config` dictionary with your project's web app configuration details (`apiKey`, `authDomain`, `databaseURL`, `projectId`, `storageBucket`, etc.).

## 3. External APIs Setup
1. Get a free API key from [OpenWeatherMap](https://openweathermap.org/api).
2. Get an API key from [Google Cloud Console](https://console.cloud.google.com/) (ensure you Enable the **Places API** and **Directions API**).
3. Open `api_integration.py` and replace the placeholder API keys:
   ```python
   OPENWEATHER_API_KEY = "your_openweather_api_key_here"
   PLACES_API_KEY = "your_google_api_key_here"
   ```

## 4. Installation
1. Navigate to the project directory in your terminal:
   ```bash
   cd path/to/cloud_based_travel_planner
   ```
2. (Optional but recommended) Create and activate a virtual environment:
   ```bash
   python -m venv venv
   
   # On Windows use:
   venv\Scripts\activate
   
   # On macOS/Linux use:
   source venv/bin/activate
   ```
3. Install the required Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## 5. Running the Application
1. Start the Streamlit application:
   ```bash
   streamlit run app.py
   ```
2. The application will launch and open in your default web browser (typically at `http://localhost:8501`).
