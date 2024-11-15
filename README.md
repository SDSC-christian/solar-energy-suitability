# Project description
Aerial images are an ideal data source to complement the missing info in the Swiss database of photovoltaic (PV) installations. Detecting and delineating solar panels from aerial images is complex as color, size, shape, and lightning vary.
The project uses Convolutional Neural Networks (U-Net or others) to automatically detect and segment solar panels from 10cm resolution images available at Swisstopo. Before that, the students are expected to explore existing labeling methods to train the CNN in a supervised way, as well as data augmentation techniques.


## Getting started
1. Clone the repo
2. Install [gdal](https://gdal.org/en/latest/)
2. Install the libraries in [requirements.txt](requirements.txt)
3. Run [fetch_data.ipynb](solar-energy-suitability/notebooks/fetch_data.ipynb) ~20min ~10GB. This will download the tiff satelite images from swissimage and split them in png of size 1000x1000px (adjustable) into this [folder](data/swissimage/ch.swisstopo.swissimage-dop10-8K9OTrP9/tiles).

## Labelling
You can use the tool that you prefer. Here are some options:
* Simply take any image editting tool (like paint), pick a color (like magenta) and paint the solar panels in that color. When you read the image take the pixels with this color as the label "solar panel" and everything else as "other".
* https://github.com/NaturalIntelligence/imglab
* https://github.com/abreheret/PixelAnnotationTool

## Add more data
You can download csvs containing links to the tiff from [swissimage](https://www.swisstopo.admin.ch/de/orthobilder-swissimage-10-cm) and run fetch_data. 

## Exploration notebooks
There are three exploration notebooks as starters to work with images and if you wish to add Sonnendach into your model:
* explore_swissimage.ipynb: How to work with swissimage satelite image
* explore_solkat.ipynb: How to work with Sonnendach polycons
* explore_overlap.ipynb: How map Sonnendach to the satelite images