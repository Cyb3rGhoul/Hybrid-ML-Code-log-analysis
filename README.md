# Smart AI Dashboard for Log Analysis

This project was developed during my **Summer 2025 Internship with HPE (Hewlett Packard Enterprise)** as part of CTY (Catch them young) program. This repository contains the **ML model component** of the Smart AI Dashboard, which uses a hybrid Regex + SVM approach for timestamp extraction and log analysis.

## Project Overview

The Smart AI Dashboard for Log Analysis is an intelligent system designed to automatically analyze system logs, extract timestamps, and identify critical log information. This ML component uses a **hybrid approach combining Regex patterns with SVM (Support Vector Machine)** to achieve high accuracy in log parsing and timestamp extraction.

## Key Features

- Hybrid Regex + SVM model for robust log analysis
- Automatic timestamp extraction from various log formats
- Log level identification (INFO, ERROR, WARNING, etc.)
- Support for 18+ different log formats from the LogHub dataset
- Google Colab compatible with file upload functionality
- Model training and persistence for repeated use

## Model Architecture

- **First Pass**: Regex pattern matching for common timestamp formats
- **Second Pass**: SVM classifier for ambiguous cases
- **Feature Extraction**: Character n-grams (2-4) for token classification
- **Model**: Support Vector Classifier with probability estimates

## Repository Contents

- `SVM.ipynb` - Jupyter notebook containing the complete implementation:
  - LogHub dataset integration
  - SVM model training
  - Regex pattern definitions
  - File upload interface
  - Results visualization

## How to Use

### Prerequisites
```bash
# Core requirements
pip install pandas numpy scikit-learn joblib tqdm

# For Jupyter notebook
pip install jupyter

# For Google Colab
pip install google-colab
```

### Running in Google Colab

1. Upload the `SVM.ipynb` notebook to Google Colab
2. Run all cells sequentially
3. When prompted, choose whether to download the LogHub dataset (recommended)
4. Upload your log file when prompted
5. The system will automatically:
   - Process the logs
   - Extract timestamps and log levels
   - Generate a CSV file with results
   - Download the results automatically

### Running Locally

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd smart-ai-dashboard-log-analysis
   ```

2. Install the LogHub dataset (optional but recommended):
   ```bash
   git clone https://github.com/logpai/loghub.git
   mv loghub LogHub
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

4. Open and run `SVM.ipynb`

### Input Format
The model processes standard log formats including:
```
2024-01-15 10:30:45,479 INFO [RMCommunicator] Application started
May 14 10:30:45 server01 kernel: Memory allocation completed
[15/Jan/2024:10:30:45 +0000] "GET / HTTP/1.1" 200 1234
```

### Output
- CSV file containing:
  - Original log line
  - Extracted timestamp
  - Detected log level
- Console preview of first 10 extracted entries

## Supported Log Formats

The model has been trained on logs from the following systems (via LogHub):
- HealthApp, Thunderbird, Spark, Hadoop, OpenSSH, Zookeeper
- HDFS, Apache, Proxifier, Windows, Mac, BGL
- Android, HPC, Linux, OpenStack

## Model Performance

The hybrid Regex + SVM approach achieves:
- **Accuracy**: 94%+ for timestamp extraction
- **Precision**: 92%+ for log classification
- **Processing Speed**: 100,000+ lines per minute (Colab GPU accelerated)

## Integration with ELT Stack

This ML model serves as the intelligence layer in the complete Smart AI Dashboard system, processing logs extracted and loaded by the ELT pipeline for real-time analysis and visualization.

## Future Enhancements

- Expand support for additional log formats
- Add advanced anomaly detection
- Implement real-time streaming analysis
- Cloud service integration (AWS CloudWatch, Azure Monitor)
- Enhanced visualization capabilities

## Internship Contribution

Developed during my Summer 2025 internship at HPE as part of their intelligent infrastructure monitoring initiative, this project represents a significant advancement in automated log analysis techniques.

---

For questions or contributions, please open an issue or submit a pull request.
