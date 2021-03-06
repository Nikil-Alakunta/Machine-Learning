# Data
- **`kc_house_data.csv`** is the data used for modelling

# Model
- In this model, gradient boosting implementation from scikit-learn was used to predict house prices. To make the deployment easier, I reduced the number of input features.
- **`house_princing.ipynb`** Notebook was used to create function of **`prediction.py`**
- **`prediction.py`** is the final sklearn model used for prediction

# Flask
- Flask is a great python module to create API server using decorators to associate functions to URL routes.
- The documentation is nice and it is easy to get started with flask: http://flask.pocoo.org/
- **`server.py`** is the flask server
- **`server.py`** has the route named predict_price that receives json data and then applies the predict function and returns the prediction (also in json format).

# Docker
- **`Dockerfile`** is the magical instruction file that defines all that is needed to run the code.(installation of the container)
- The file **`requirements.txt`** contains all the python packages. You can generate your own requirements if you have additional dependencies using **`pip3 freeze`**

# Start Everything
- To start everything, you just need to be in the folder **`House_price_pred_Docker`** and execute : **`docker-compose up`**. After the installation that can take few minutes, you will see:
<img src = "assets/Screenshot 2020-11-13 at 23.21.46.png">


- This means that everything is fine and that the flask server is listening.
- You can use curl to connect to the server to verify that the service is available:
- use **`curl -X POST -H "Content-Type: application/json" -d @to_predict_json.json http://localhost:5000/predict_price`** 
- where **`to_predict.json`** contains: **`{"grade":10.0,"lat":47.5396,"long":-122.073,"sqft_living":4490.0,"waterfront":0.0,"yr_built":2006.0}`**
- this should return 

<img src ="assets/Screenshot 2020-11-13 at 23.22.00.png">
