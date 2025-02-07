# deity-imagee-classification
# DeityVision

## Overview
**DeityVision** is a deep learning-based system designed to identify and classify deity images using Convolutional Neural Networks (CNNs). The project leverages machine learning techniques, web scraping, and Flask to create an automated pipeline for recognizing Buddhist deities based on iconographic attributes.

## Features
- **Multi-Class Classification**: Uses CNN-based models alongside Logistic Regression and Random Forest for deity identification.
- **Custom Dataset Creation**: Developed **ImageScape**, a web scraping tool built with Scrapy and Selenium, to automate the extraction of 50,000+ deity images and metadata.
- **High Accuracy**: Achieved **85% classification accuracy** through model optimization.
- **Hyperparameter Tuning**: Applied **RandomizedSearchCV** to optimize model performance, improving generalization by **15%**.
- **Cross-Validation & Evaluation**: Used **accuracy, precision, and cross-validation techniques** to ensure robust model performance.

## Technology Stack
- **Python, Flask** (Backend API)
- **TensorFlow, Keras** (Deep Learning Frameworks)
- **Scrapy, Selenium** (Web Scraping & Dataset Collection)
- **RandomizedSearchCV** (Hyperparameter Tuning)
- **Random Forest, Logistic Regression** (Alternative Classification Models)

## Installation & Setup
### Prerequisites
Ensure you have the following installed:
- Python 3.8+
- TensorFlow, Keras
- Flask
- Scrapy, Selenium
- NumPy, Pandas, Matplotlib

### Steps to Run
1. **Clone the repository**  
   ```bash
   git clone https://github.com/yourusername/deityvision.git
   cd deityvision
   ```
2. **Create a virtual environment & install dependencies**  
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. **Run the Flask server**  
   ```bash
   python app.py
   ```
4. **Scrape new images (if required)**  
   ```bash
   python scraper.py
   ```

## API Endpoints
### Image Classification
```
POST /predict
```
- **Request**: Multipart/form-data with an image file
- **Response**:
  ```json
  {
    "deity": "Avalokiteshvara",
    "confidence": 0.85,
    "attributes": {
      "heads": 4,
      "arms": 8,
      "symbol": "lotus"
    }
  }
  ```

## Contributing
1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-branch
   ```
3. Commit and push changes:
   ```bash
   git commit -m "Added new classification feature"
   git push origin feature-branch
   ```
4. Open a pull request.

## License
This project is licensed under the MIT License.

