# Lung Cancer Prediction App with FastAPI, Streamlit and Docker

[![Language](https://img.shields.io/badge/Python-darkblue.svg?style=flat&logo=python&logoColor=white)](https://www.python.org)
[![Framework](https://img.shields.io/badge/sklearn-darkorange.svg?style=flat&logo=scikit-learn&logoColor=white)](http://www.pytorch.org/news.html)
[![Framework](https://img.shields.io/badge/FastAPI-darkgreen.svg?style=flat&logo=fastapi&logoColor=white)](https://lung-cancer-api.herokuapp.com/docs)
[![Framework](https://img.shields.io/badge/Streamlit-red.svg?style=flat&logo=streamlit&logoColor=white)](https://share.streamlit.io/nneji123/lung-cancer-prediction/main)
![hosted](https://img.shields.io/badge/Heroku-430098?style=flat&logo=heroku&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-blue?style=flat&logo=docker&logoColor=white)
![build](https://img.shields.io/badge/build-passing-brightgreen.svg?style=flat)
![reposize](https://img.shields.io/github/repo-size/Nneji123/Lung-Cancer-Prediction)

A Machine Learning Project to predict if someone has Lung Cancer or not. Built with FastAPI, Streamlit and Docker.


## Problem Statement
Lung cancer is a type of cancer that begins in the lungs and most often occurs in people who smoke. Two major types of lung cancer are non-small cell lung cancer and small cell lung cancer. Causes of lung cancer include smoking, second-hand smoke, exposure to certain toxins and family history. Symptoms include a cough (often with blood), chest pain, wheezing and weight loss. These symptoms often don't appear until the cancer is advanced. Treatments vary but may include surgery, chemotherapy, radiation therapy, targeted drug therapy and immunotherapy.

The aim of this project was to build a **machine learning model** that can help in detecting/predicting lung cancer based on the following features: age, gender, blood pressure, smoke, coughing, allergies, fatigue etc and then create an API using **FastAPI** framework and also access the API through a frontend interface such as **Streamlit.**

The Streamlit App can be viewed [through this link](https://share.streamlit.io/nneji123/lung-cancer-prediction/main)


The API and its documentation can be viewed [here](https://lung-cancer-api.herokuapp.com/docs) or [here](https://lung-cancer-api.herokuapp.com/redoc)

## Data Preparation
The original dataset contains 16 columns and 310 rows with the "GENDER" and "LUNG_CANCER" columns containing object data types while the rest of the columns were integer datatypes.

The data was the clean and processed for modelling by changing the following:
- The values "M" and "F" in the "GENDER column were converted to 1 and 0 respectively.
- The values "YES" and "NO" in the "LUNG_CANCER" column were converted to 1 and 0 respectively.
- The values "2" and "1" in the rest of the columns were converted to 1 and 0 respectively.

The processed dataset was then saved as **processed_lung_cancer.csv**

[Original Dataset](https://github.com/Nneji123/Lung-Cancer-Prediction/blob/main/Datasets/lung_cancer.csv)

[Processed Dataset](https://github.com/Nneji123/Lung-Cancer-Prediction/blob/main/Datasets/processed_lung_cancer.csv)

### Modelling
In this project I tested 6 different classification algorithms namely:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- GradientBoostClassifier
- SupportVectorClassifier


The final model used for the API was the Gradient Boost Classifier model which had an accuracy score of 0.94.


## Preview

### API Demo
![fastapi](https://user-images.githubusercontent.com/101701760/173524600-961b66fc-da9f-4714-8240-52054e85d0b4.gif)

### Streamlit App Demo

![streamlit](https://user-images.githubusercontent.com/101701760/173524653-7706e13f-d3c6-46cc-abb3-ac9f79316e4b.gif)


## How to run API and Streamlit App on Google Colab:
### Running the API on Google Colab
To run a demo or carry out testing with the API it's best to do that with Google Colab. To run/test the API on Google Colab do the following:
1. Clone the repository.
2. Open a Google Colab instance and upload the **Lung Cancer Prediction.ipynb** file to that instance.
3. Run each cell until the last cell and you should be able to view the API with a link that has the name **ngrok** in it.

### Running the Streamlit App on Google Colab
The Streamlit App can also be viewed using Google Colab by doing the following:
1. Upload the "streamlit_app.py" and "requirements.txt" file to your instance on Google Colab
2. Install the requirements by running:
```
!pip install -r requirements.txt
```
3. Install Pyngrok in your instance:
```
!pip install pyngrok
```
4. Run the following code in your instance:
```
from pyngrok import ngrok 
public_url = ngrok.connect(port=’8501')
public_url
```
5. You can then view the streamlit app on your Google Colab instance by running:
```
!streamlit run /content/streamlit_app.py & npx localtunnel — port 8501
```

## Running on Local Machine
For testing a **docker-compose.yml** file has been included so as to run both the API and Streamlit app simultaneously as docker containers. To run the API and the Streamlit app on your local machine do the following:
1. Clone the repository to your local machine
2. Install docker and docker-compose if you haven't
3. Open a bash/cmd in the directory and run:
```docker
docker-compose build
docker-compose up
```
4. After the above steps have been carried out you can now view the documentation of the API and also the Streamlit app.

To visit the FastAPI documentation go to http://localhost:8000 with a web browser.

To visit the streamlit UI, visit http://localhost:8501.

Logs can be inspected via:
```
docker-compose logs
```
The **docker-compose** method can also be used to deploy the API and Streamlit app on Heroku(using Dockhero which is not free) or using cloud services such as Microsoft Azure, Amazon Web Services or Google Cloud Platform.
## Deployment
The API has been deployed using the dockerfile on heroku.

### Deploying the API
Assuming you have git and heroku cli installed just carry out the following steps:

1. Clone the repository

```
git clone https://github.com/Nneji123/Lung-Cancer-Prediction.git
```

2. Change the working directory

```
cd Lung-Cancer-Prediction
```

4. Create the heroku app

``` 
heroku create your-app-name 
```

Replace **your-app-name** with the name of your choosing.

4. Set the heroku cli git remote to that app

```
heroku git:remote your-app-name
```

5. Set the heroku stack setting to container
 
```
heroku stack:set container
```

6. Push to heroku
```
git push heroku main
```

### Deploying the Streamlit App to Streamlit Cloud
The Streamlit App was deployed using the streamlit cloud and accesses the API deployed on Heroku. To deploy the app using streamlit cloud share do the following:
1. Fork this repository to your Github account.
2. Create a Streamlit Account and then navigate to https://streamlit.io/cloud
3. Create a new app and then choose the repository you cloned and the **"streamlit_app.py"** and then click deploy.

After the app has been built on the cloud you should then be able to view your app right away!

