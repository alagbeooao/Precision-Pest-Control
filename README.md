# Agricultural pest image classification

Classifies field photos of 12 agricultural pests (ants, bees, beetles, caterpillars, earthworms, earwigs, grasshoppers, moths, slugs, snails, wasps and weevils) using the Agricultural Pests Image Dataset: 5,494 images, split 64/16/20 into training, validation and test sets.

## Model

ResNet-50 pretrained on ImageNet, fine-tuned in two stages: first the new classifier head with the backbone frozen, then the top 30 layers unfrozen at a tenth of the learning rate.

On the 1,099 test images it reaches 90.4% accuracy and a macro F1 of 0.90. Earwigs are the weakest class, with a recall of 0.73.

The notebook also trains a small CNN from scratch as a baseline. It did not learn: early stopping restored its first-epoch weights, and it scored 7.9% on the test set, below the 8.3% chance level for 12 classes. It is kept as a record, not as a result.

## Running it

Open the notebook in Colab, upload `agricultural-pests-image-dataset.zip` to `/content`, run the unzip cell first, then run the rest in order. The best model is saved with its class mapping for single-image prediction.
