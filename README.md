# Pokedex

An OpenCV application that classifies any Pokemon.


## Usage

### search_pokemon.py
This script will search and save the pokemon images for you. It uses Microsoft Bing Image Search API

Sample usage:
```
python -m search_pokemon -q "bulbasaur" -o "datasets\bulbasaur"
```

Arguments:
* -q | --query		Search query to search Bing Image Search API for
* -o | --output		Path to output directory of images

It is cleaner if your Pokemon images were grouped in separate folders.
For better results, you may increase the MAX_RESULTS parameter of this script.
If Bing Search API is not working, replace the API_KEY parameter with your API key on [this link](https://azure.microsoft.com/en-us/try/cognitive-services/?api=bing-image-search-api)


### train.py
This script will train the gathered image datasets. It uses Smaller VGGNet algorithm to create a model that can be used for prediction.

Sample usage:
```
python -m train -d "datasets" -m pokedex.model -l lb.pickle -p plot.png
```

Arguments:
* -d | --dataset	Path to input dataset (i.e., directory of images)
* -m | --model		Path to output model
* -l | --labelbin	Path to output label binarizer
* -p | --plot		Path to output accuracy/loss plot. Default is plot.png

For better results, you may increase the number of epochs in EPOCHS parameter.


### classify.py
This script will classify the Pokemon, given the test image you will be using.

Sample usage:
```
python -m classify -m pokedex.model -l lb.pickle -i "examples\1.jpg"
```

Arguments:
* -m | --model		Path to trained model
* -l | --labelbin	Path to label binarizer
* -i | --image		Path to input image


## Acknowledgements
* [PyImageSearch](https://www.pyimagesearch.com) for providing nice tutorials on OpenCV applications