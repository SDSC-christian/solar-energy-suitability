# Project description

Aerial images are an ideal data source to complement the missing info in the Swiss database of photovoltaic (PV) installations. Detecting and delineating solar panels from aerial images is complex as color, size, shape, and lightning vary.
The project uses Convolutional Neural Networks (U-Net or others) to automatically detect and segment solar panels from 10cm resolution images available at Swisstopo. Before that, the students are expected to explore existing labeling methods to train the CNN in a supervised way, as well as data augmentation techniques.


## Getting started

 1. Clone the repository.
 2. Install the libraries in [`requirements.txt`](./requirements.txt).
 2. Download and unpack to data/solkat  [`SOLDACH_KAT.pdgk`](https://data.geo.admin.ch/ch.bfe.solarenergie-eignung-daecher/solarenergie-eignung-daecher/solarenergie-eignung-daecher_2056.gpkg.zip
).
 3. Run [`fetch_uniform.ipynb`](./notebooks/fetch_uniform.ipynb) to download a few pictures where there are rooftops. Feel free to adjust the parameters.
 4. Run [`prepare_images.ipynb`](./notebooks/prepare_images.ipynb) to slice images into smaller chunks and ignore regions without rooftops, for convenience.
 5. Optional: Run [`prepare_masks.ipynb`](./notebooks/prepare_masks.ipynb) to get the masks where the rooftops are.


## Labelling

You can use the tool that you prefer. Here are some options:

 * Simply take any image editing tool (like Paint), pick a color (like magenta) and paint the solar panels in that color. When you read the image take the pixels with this color as the label "solar panel" and everything else as "other".
 * https://github.com/NaturalIntelligence/imglab
 * https://github.com/abreheret/PixelAnnotationTool


## Exploration notebooks

There are three exploration notebooks as starters to work with images and if you wish to add Sonnendach into your model:

 * [`explore_swissimage.ipynb`](./notebooks/explore_swissimage.ipynb): How to work with swissimage satellite image.
 * [`explore_solkat.ipynb`](./notebooks/explore_solkat.ipynb): How to work with Sonnendach polygons .
 * [`explore_overlap.ipynb`](./notebooks/explore_overlap.ipynb): How map Sonnendach to the satellite images.
 * [`fetch_uniform.ipynb`](./notebooks/fetch_uniform.ipynb): Download a few random tiles, which are guaranteed to have some rooftops.
 * [`prepare_images.ipynb`](./notebooks/prepare_images.ipynb): Extract sub-tiles (100x100 meters) as JPEG from downloaded tiles, focusing on rooftops.
 * [`prepare_masks.ipynb`](./notebooks/prepare_masks.ipynb): Generate rooftop masks, for each prepared sample.
