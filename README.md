[+]deploy-CNN-google-cloud-platform-GCP
Implementing and Deploying a Deep Convolutional Neural Network with Google Cloud App Engine

## Deploy a CNN on Google Cloud with Keras and Flask

This repository provides a step-by-step guide and code example to deploy a pre-trained InceptionResNetV2 convolutional neural network (CNN) on Google Cloud Platform (GCP) using Flask for serving the model.

### Prerequisites

Before getting started, please check, you have the following:

- **Google Cloud Platform Account:**  You'll need an active GCP account. If you don't have one, you can sign up for a free trial [here](https://cloud.google.com/free).
- **Google Cloud SDK:** Download and install the Google Cloud SDK for your operating system from [here](https://cloud.google.com/sdk/install).  This will provide you with the `gcloud` command-line tool.
- **Python 3.6 (Recommended):**  While other versions may work, this guide uses Python 3.6. Create a virtual environment for this project:

   ```bash
   pip install virtualenv
   virtualenv web_app 
   source web_app/bin/activate 
   ```

### Project Setup

1. **Clone the Repository:**
   ```bash
   git clone this_repo_Git
   cd Deploy-CNN-on-google-cloud
   ```

2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt 
   ```

3. **Download the Pre-trained Model:**
   ```bash
   python download_model.py
   ```
   This script downloads the InceptionResNetV2 model weights.

### Local Testing

1. **Start the Flask Development Server:**
   ```bash
   gunicorn -b :8889 app:app -t 120 --graceful-timeout 60
   ```

2. **Open the Web Interface:**
   Open your web browser and navigate to `http://localhost:8889/`. You should now be able to interact with the deployed CNN model.

### Deploying to Google Cloud

1. **Initialize the Google Cloud SDK:**
   ```bash
   gcloud init
   ```
   Follow the prompts to select your project and default zone.

2. **Deploy the Application:**
   ```bash
   gcloud app deploy 
   ```

3. **Access the Deployed App:**
   ```bash
   gcloud app browse
   ```
   This command will open your deployed web application in your default browser.

### Project Structure

- **app.py:** Contains the Flask application logic for handling requests and predictions.
- **download_model.py:** Downloads the pre-trained InceptionResNetV2 model weights.
- **requirements.txt:** Lists the required Python packages for the project.
- **templates/index.html:**  The HTML template for the web interface.

### Notes

- **Customization:** You can modify the code to use different CNN architectures or adjust the web interface to your needs.
- **Security:**  In a production environment, implement appropriate security measures like HTTPS and authentication.
- **Error Handling:** Implement robust error handling in the Flask application for a smoother user experience.
