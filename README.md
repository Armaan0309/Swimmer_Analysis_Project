# Swimmer Performance Analyzer
## Project Overview


Welcome to the Swimmer Performance Analyzer! This project provides a web-based application to analyze swimmer performance data, visualize key metrics, and offer personalized recommendations for improvement. By processing raw lap time data, our system helps swimmers, coaches, and enthusiasts gain insights into performance trends, pacing consistency, and even predicts future race times.

## Features
* Data Processing: Automatically extracts swimmer data (name, age, distance, stroke, lap times) from text files.

* Performance Metrics: Calculates essential metrics such as total race time, average lap time, velocity, and estimated heart rate during races.

* Interactive Visualizations: Generates insightful plots including:

    * Total Race Times: Tracks a swimmer's performance across multiple races.

    * Average Lap Times by Distance and Stroke: Breaks down lap times based on different distances and strokes, helping identify strengths and areas for improvement.

* Performance Prediction: Utilizes linear regression to predict a swimmer's total time for their next race.

* Personalized Recommendations: Provides actionable advice based on lap time consistency, velocity, heart rate analysis, and predicted performance changes.

* Web Interface: A user-friendly Flask web application to display analysis results and visualizations.

## How It Works
The application is built using Flask for the web framework, Pandas for data manipulation, and Matplotlib and NumPy for data visualization and numerical operations. Scikit-learn is used for the linear regression model.

1 Data Ingestion: The process_files() function scans a specified directory for .txt files. Each file is expected to be named in the format SwimmerName-Age-DistanceStroke.txt (e.g., JohnDoe-18-100mFreestyle.txt) and contain comma-separated lap times in minutes:seconds format.

2 Data Analysis:

   - parse_time() converts lap time strings into total seconds.

   - calculate_velocity() determines the swimmer's speed.

   - analyze_swimmer() is the core function that:

   - Filters data for a specific swimmer.

   - Calculates average lap times and other key metrics.

   - Generates two plots: total race times over races and average lap times by distance and stroke.

   - Performs linear regression on total race times to predict future performance.

   - Estimates heart rate based on age and distance.

   - Formulates general and metric-specific recommendations.

3 Web Presentation:

   - The Flask application serves an index.html template (which would be in your templates folder).

   - When a swimmer's data is requested via the /swimmer/<name> route, the analyze_swimmer function is called, and the results (including base64 encoded plot images, metrics, and recommendations) are returned as a JSON response.

## Getting Started
   - To run this application, follow these steps:

## Prerequisites
Make sure you have Python installed (Python 3.7+ is recommended).

You'll need the following Python libraries. You can install them using pip:

```Bash

pip install Flask pandas matplotlib scikit-learn numpy
```
## Repository Structure
Your repository should ideally have a structure similar to this:

```bash
largeFiles/
├── .gitattributes
├── README.md
├── swimmer_data.zip
├── app.py          # Your main application code
└── templates/
    └── index.html  # Your HTML template for the web interface
```
Note: The swimmer_data.zip file is expected to contain .txt files with swimmer data as described in the "Data Ingestion" section above. After downloading and extracting swimmer_data.zip, the .txt files should be accessible by the app.py script.

## Running the Application
1 Download and Extract Data: Download the swimmer_data.zip file from this repository and extract its contents into the same directory as your app.py file. These extracted .txt files are crucial for the application to function.

2 Navigate to the Project Directory:

```Bash
cd Swimmer_Analysis_Project
```
3 Run the Flask Application:

```Bash
python app.py
```

4 Access the Application: Once the application is running (you'll see a message like * Running on http://127.0.0.1:5000/), open your web browser and go to:

   - http://127.0.0.1:5000/ to access the main page (assuming you have index.html).

   - To see specific swimmer data, you can append the swimmer's name (e.g., http://127.0.0.1:5000/swimmer/JohnDoe if "JohnDoe" is a swimmer in your data).

## How to Interact
Once the application is running, you can interact with it by entering the swimmer's name into the appropriate field on the web interface (if index.html provides one) or directly accessing the /swimmer/<name> endpoint in your browser or through tools like Postman.

The application will then display:

   - Performance Plots: Visual graphs of total race times and average lap times.

   - Key Metrics: Numerical values for total time, average lap time, velocity, distance, predicted time, and heart rate.

   - Recommendations: Personalized advice to help the swimmer improve their performance.
