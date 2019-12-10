# A Simple Keras + deep learning REST API

The code from this project was inspired by this tutorial from the creators of keras [*Building a simple Keras + deep learning REST API*](https://blog.keras.io/building-a-simple-keras-deep-learning-rest-api.html), published on the Keras.io blog.

This api is simple and is meant to be a simple example of an API that serves a machine learning model. This architecture will not scale well and is not secure.

The we model used was created with the help of this Kaggle kernel, which is a part of a melanoma machine learning competetion and is using the HAM10000 dataset that contains 10,000 human labeled picture of 7 different types of skin lesions.

## Getting started

install dependancies

```sh
pip install flask gevent requests

pip install tensorflow

pip install keras
```

Next, clone the repo:

```sh
$ git clone https://github.com/jrosebr1/simple-keras-rest-api.git
```

## Starting the Keras server

Below you can see the image we wish to classify, some cancer, but more specifically a _beagle_:

![cancer](cancer.jpg)

The Flask + Keras server can be started by running:

```sh
$ python run_keras_server.py 
Using TensorFlow backend.
 * Loading Keras model and Flask starting server...please wait until server has fully started
...
 * Running on http://127.0.0.1:5000
```

You can now access the REST API via `http://127.0.0.1:5000`.

## Submitting requests to the Keras server

Requests can be submitted via cURL:

```sh
curl -X POST -F image=@cancer.jpg "http://localhost:5000/predict"
{"predictions":
[{"Melanocytic nevi":0.0},
{"Melanoma":0.0},
{"Benign keratosis-like lesions ":0.0},
{"Basal cell carcinoma":0.0},
{"Actinic keratoses":1.0},
{"Vascular lesions":0.0}],
"success":true}
```

