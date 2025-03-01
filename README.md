# JG_Module_3_CNN_Cancer_Detection_

This repository is a partial submission for my Coursera Deep Learning Assignment. 

The dataset used for this project is from https://www.kaggle.com/c/histopathologic-cancer-detection/overview. It contains 277,483 96x96 pixel pathology images with a binary label: positive if at least one pixel in the center 32x32 pixels of the image contains tumor tissue, 0 otherwise. The data is split into 220025 image-label pairs for model implementation (i.e. split into training and validation), with 57458 image-label pairs to assess the dataset on. The goal is to train a model to classify the pathology images with the maximum area under the ROC curve between predicted probability and observed target.

At this point the data itself is very clean with all labels are 0 or 1 and all images are the same size. All images are 96x96x3, with the 3rd dimension being RGB channels. I additionally checked that all images were 96x96x3, which 

There are an unequal # of positive and negative labels, so the accuracy must exceed 0.6 to show learning (guess all labels as 0 would produce an accuracy of 0.6). Due to the large # of cases, it can be assumed that there will be a similar proportion of positive and negative cases when split into training and testing.

I plan on doing transfer learning on VGG19, as this model has been shown to produce good results with medical image classification (Comparison of Machine Learning and Deep Learning for View Identification from Cardiac Magnetic Resonance Images Chauhan D et al https://pmc.ncbi.nlm.nih.gov/articles/PMC8849564/). Since the dataset is large, utilizing a pre-trained network is acceptable. I will test epochs from 1-10, select an epoch based on maximum accuracy value predicting the validation datasets. I will then reduce the batch size from 256 to 128 to see if the accuracy increases at a trade-off with training time. The best validation accuracy of the different batch sizes will be used for final dataset prediction. I will use a SGD optimizer and a loss function of binaary cross entropy.

Due to the constraints of Kaggle, I was limited to 3 epochs, which appears to be sufficient as validation accuracy increased much less from epoch 2 to 3 than from 1 to 2. I have printed a screenshot of the training in the notebook. I will attempt to lower the batch size to 128 to see if I can increase accuracy at the expense of increasing training time.

As we can see from the validation accuracy, using a batch size of 128 increased the accuracy of the validation predictions, from 0.8153 to 0.8194. The trade-off was that training time went from ~8.5 hours to ~10.5. My private score when submitted predictions using the model was 0.7894.

I learned through this that while VGG19 is a very good model for image classification, it takes a long time to transfer learn. In the future, I will avoid using VGG19 without a GPU accelerator.
