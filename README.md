# ICME2019_SPL_pub

The implement of ICME2019-accepted paper “SPL: EXPLOITING UNLABELED DATA FOR MULTI-LABEL IMAGE CLASSIFICATION”, the code is implemented under caffe and tensorflow while 
caffe is for classification and tensorflow is for data augmentation.

This paper focus on a special data augmentation with GANs and exploit the influence of generated data in training. All codes related to this paper can be found in github.
![](https://github.com/caskcsg/SPL/blob/main/img/ICME19-framework.png)

1. Data Augmentation

One of the candidate solutions of obtaining the additional unlabeled data is employing generative adversarial network. In this paper,  We adopt W-GAN and DC-GAN as the methods 
to generate additional data.

Repository are listed below：\
https://github.com/carpedm20/DCGAN-tensorflow/ \
https://github.com/LynnHo/DCGAN-LSGAN-WGAN-WGAN-GPTensorflow/

Please follow the two repositories to generate your own data. In this paper, we just regard all the training data as the input and got as many as images we want.

![Data enhancement diagram](https://github.com/caskcsg/SPL/blob/main/img/ICME2019-data_aug.png)

2. Assign suitable labels to unlabeled data

In this paper, we propose a flexible label mechanism called soft pseudo labeling (SPL), which assigns the virtual and appropriate multi-label for each generated unlabeled data.
First, we train a basic model with resnet-101 with its fc replaced. Specially, we adopt SRN code 'https://github.com/zhufengx/SRN_multilabel' as the classification code. Then we pass the generated data through the trained models and get its confidence. In the end, we use softmax
function to amend the confidence to get the final labels for the generated images.\
x=softmax(x)

![Label assignment](https://github.com/caskcsg/SPL/blob/main/img/ICME2019-label_assign.png)

3. Train the models with additional labeled data

We train the models again with the labeled unlabeled data with resnet-101 structure.
