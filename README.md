Plant Disease Detection based on CNN and ResNet-18. 

 Project Overview  

In this project, deep learning techniques are explored for the classification of plant diseases based on leaf images. The baseline model is a custom Convolutional Neural Network (CNN) and a pretrained ResNet-18 model is used to evaluate the benefits of transfer learning. The project involves a comparison of CNN and ResNet-18 performance and a study of the impact of data augmentation on the classification accuracy of ResNet-18 on the PlantVillage dataset. 

 Problem Statement: The goal is to categorize the plant leaf images into the different disease categories present in the data set, and compare the performance of various deep learning methods. The experiments are conducted on overall classification performance, the effect of data augmentation, and the classification of the disease categories that are still hard to classify.  

Dataset: PlantVillage This is a dataset from Hugging Face — PlantVillage. Number of images: 54,305 Number of classes: 38 The data set is split by the official training set size.The official training split size is used for the data set. This is the official test split of 10,709 images. The official training split was split into training and validation subsets via stratified sampling, with a random seed of 42. 

Subset 

Number of images 

Training 

39,236 

Validation 

4,360 

Held-out test 

10,709 

Images are resized to 224 × 224 pixels and normalized using ImageNet mean and standard deviation. Training-time augmentation uses random horizontal flips and rotations of up to 15 degrees. Evaluation data is processed without random augmentation. 

Models and Experiments : 

Three setups were tested: CNN baseline: A custom CNN consisting of four convolutional blocks, dropout and final classification layer. ResNet-18 (augmentation): Fine-tuned ResNet-18 using augmentation during training on the 38 plant disease classes from ImageNet. ResNet-18 with augmentation: The same pretrained architecture and training configuration, but with random augmentation during training. The experiments are performed with cross-entropy loss, Adam optimizer, learning rate 0.001 and three training epochs. The batch size is 8. 

Evaluation Metrics 

The models are evaluated using: 

Accuracy 

Macro precision 

Macro recall 

Macro F1-score 

Confusion matrices 

Analysis of misclassified images 

The held-out test set is used to evaluate the final selected model checkpoints. 

Results 

The following table summarizes the held-out test results. 

Model 

Accuracy 

Macro Precision 

Macro Recall 

Macro F1-score 

CNN baseline 

90.03% 

88.84% 

87.62% 

87.83% 

ResNet-18 with augmentation 

96.67% 

96.05% 

96.03% 

95.84% 

ResNet-18 without augmentation 

95.98% 

95.41% 

94.29% 

94.58% 

 

Failure Analysis 

Although ResNet-18 achieved strong overall performance, some disease categories remained challenging. 

Examples from the evaluation include: 

Tomato Early Blight: Recall of 58% and F1-score of 0.72 for the augmented ResNet-18 model. 

Corn Gray Leaf Spot: Recall of 74% and F1-score of 0.79. 

Peach Healthy: Recall of 100% and precision of 81%. 

Reproducibility : 

The project is developed in Python with PyTorch and torchvision, evaluated with scikit-learn and processed the results with pandas. Google Colab was used with a Tesla T4 GPU for the experiments. The notebook records the process of data preparation, pre-processing, training, validation, held-out testing, inferences and the generation of results. 

 

 

Project Structure 

. 
├── notebooks/ 
│   └── plant_disease_detection.ipynb 
├── models/ 
├── results/ 
├── README.md 
└── requirements.txt 

 

The primary notebook is: 

notebooks/plant_disease_detection.ipynb 

 

Conclusion 

 The experiments demonstrate that ResNet-18 achieved superior performance over the baseline CNN trained with the custom dataset on the held-out test set of PlantVillage. The augmentation experiment also revealed a relatively small performance boost for the tested ResNet-18 model. The class level evaluation identified areas of weakness that are not evident from the overall
