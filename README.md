# Dance_Form_Classifier
The repository contains 2 CNN codes for Hacker Earth's challenge : ***Dance Classification***. The first technique makes use of the classical transfer learning approach & the second technique makes use of the qunatum transfer learning approach. Both the techniques invovled the basic use of csv files that contained image name and the respective target. Basic pandas looping was used & approporiate images were placed in directory named after the class structure(This type of ordering is used by Tensorflow FlowfromDirectory to generate appropriate target labels for i/p data).
1. The classical approach made use of the InceptionV3 model. The Inception model makes use of network in network architecture & also performs convolution operation at different dimensions in an Inception block. The advantage of this is that seperate brances are created in an inception block that learn spatial & channel wise features. The strategy used for training the model was as follows
    > Initially the performance was unknown therefore ImageDataGenerator was used with no augmentations in order to see the performance of a base model.
    
    > The ImageNet weights were used & the model was frozen, also a randomly formed FullyConnected layer was created to get a final layer with 8 nodes (8 classes soft max classification).
    
    > Once the model was trained & a sufficient model accuracy was achieved, the weights were unfrozen & the model was tweaked to perform better on the specific dataset.(fine tuning)
    
    > Heat Maps were used in Tflow2.0 to see what portions of image to led predictions. Majority of the kathakali dance images were classified correctly beacuse they had a prominent green face in it. Based on the intution gained from heat maps the ImageDataGenerator was reloaded with new augmentations added that made sense in reality & also allowed to increase the dataset distribution for better performance. This also led to better & generalized fitting.
    
    > To reduce overfitting & get better score on validation set the FullyConnected layer nodes were decreased. The final setting used included GlobalAveragePooling for node reduction from base net i.e InceptionV3 & also dropout was added with a high value of 0.6. This model was overfitting because it had a lot of trainable parameters with less images. MobilenetV2 model was used for testing purpose to see wether it better generalizes but that model led to underfitting therefore it was dropped from the final submission.
    
    > Image resoulution change was also explored to see better performance but the model did not perform better just increased its training time.

2. Also quantum transfer learning approach was explored even though it was not in the submission file. The code was in pytorch and the following points were used in the approach 

    >The Quantum convolutional filter (variational circuit) involved the use of Hadamard & Rotation gates for embedding, CNOT gate for entangling based processing & Pauli’s Transforms   were utilized for collapsing the wave function based on the Copenhagen interpretation.
    
    > The images were preprocessed and augmented using pytorch's data transform methods. 
    


