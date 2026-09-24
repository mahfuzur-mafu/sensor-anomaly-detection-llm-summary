# Anomaly Detection + LLM Situation Summary using DEFINE Foundry

## Overview

This project analyzes synthetic SAPIENT sensor messages generated using the DEFINE Foundry scenario-foundry repository.

The goal of this project is to:

1. Generate and inspect sensor data.
2. Detect anomalous or noteworthy events using a lightweight statistical method.
3. Use an LLM to generate a short situation summary for a human operator and evaluate the quality of the generated summary.


## Project Structure

Anomaly_Detection_LLM_Summary/

├── task_analysis.ipynb

├── requirements.txt

├── Reflection.pdf

├── Anomaly_Detection_LLM_Summary_ppt.pdf

└── scenario-foundry/

    └── data/

        └── generated_output/

            └── joensuu_messages.json


## Requirements

Python 3.10 or higher is recommended.

Install the required packages:

pip install -r requirements.txt


Main libraries used:

- pandas
- numpy
- matplotlib
- jupyter
- google-genai


## Running the Project

Clone the repository:

git clone <your-github-repository-link>


Go to the project directory:

cd Anomaly_Detection_LLM_Summary


Install dependencies:

pip install -r requirements.txt


Start Jupyter Notebook:

jupyter notebook


Open:

task_analysis.ipynb


Run the notebook cells in order.


## Scenario Foundry Setup

This project uses the DEFINE Foundry scenario-foundry repository to generate synthetic SAPIENT sensor messages.

Clone the scenario-foundry repository:

git clone https://github.com/define-ai-foundry/scenario-foundry.git


Place the repository inside the project folder:

Anomaly_Detection_LLM_Summary/

└── scenario-foundry/


The generated Joensuu scenario data is located at:

scenario-foundry/data/generated_output/joensuu_messages.json


# Task 1: Generate and Inspect SAPIENT Sensor Data

The Joensuu scenario from the DEFINE Foundry scenario-foundry repository was used to generate synthetic SAPIENT sensor messages.

The notebook performs:

- Loading generated SAPIENT messages.
- Inspecting message structure.
- Checking available sensors and objects.
- Analyzing altitude and confidence patterns.
- Creating sensor and object level statistics.


The analysis focuses on:

- timestamp
- sensor information
- object IDs
- altitude values
- confidence values
- detection patterns over time


# Task 2: Lightweight Anomaly Detection

A lightweight anomaly detection method was implemented using an Interquartile Range (IQR)-based statistical approach.

The method automatically calculates thresholds from the generated data.

Messages are flagged based on:

- Low confidence values.
- Long detection gaps.
- High altitude change rates.


The method does not require model training and keeps the reason for each detected anomaly.

Example detections:

- A sensor observation with unusually low confidence.
- A message received after a long detection gap.
- An object with a high altitude change rate.


The detected events should be considered noteworthy observations and not confirmed sensor failures.


# Task 3: LLM Situation Summary

A small batch of sensor detections was provided to an LLM to generate a short natural-language situation summary for a human operator.

The LLM was instructed to:

- Describe detected objects.
- Mention altitude changes.
- Report confidence information.
- Use only the provided sensor information.
- Avoid unsupported assumptions.


The generated summary was evaluated based on:

- Correct information extracted from the data.
- Incorrect assumptions.
- Possible hallucinations.


The evaluation showed that the LLM can create useful summaries, but the output still needs verification against the original sensor data.


# Gemini API Setup

The LLM summary generation uses the Gemini API.

To run Task 3, a Gemini API key is required.


## Getting Gemini API Key

1. Open Google AI Studio:

https://aistudio.google.com/app/apikey


2. Sign in with your Google account.

3. Select "Create API Key".

4. Copy the generated API key.




## Setting Gemini API Key


For macOS/Linux:

export GEMINI_API_KEY="YOUR_GEMINI_API_KEY_HERE"


For Windows:

set GEMINI_API_KEY="your_api_key_here"


The notebook reads the key using:

os.getenv("GEMINI_API_KEY")


# Results



SAPIENT Sensor Messages → Data Loading → Inspection → Sensor Pattern Analysis → IQR-based Anomaly Detection → Selected Anomalous Detections → Gemini LLM Situation Summary → Critical Evaluation


# Reflection

AI tools helped throughout the project by improving understanding of the sensor data, supporting coding and debugging, and generating a human-readable situation summary.

The results also showed that AI outputs need verification. The LLM was able to summarize important patterns, but it could also make assumptions that were not directly supported by the data.

For production use, additional validation, historical data, better tracking methods, domain knowledge, and human supervision would be required.


# Notes

- The anomaly detection method is intentionally lightweight and interpretable.
- The LLM summary is generated only from the provided sensor observations.
- API keys and sensitive information should not be included in the repository.
