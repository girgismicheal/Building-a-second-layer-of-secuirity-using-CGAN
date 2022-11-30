# Building-a-second-layer-of-secuirity-using-CGAN-and-WGAN

## Generate fake tasks then use the discriminator for classification

![Fake or real](https://drive.google.com/uc?export=view&id=1-PMAvx35fcqMgSatbjTQjxx7nGWJJTv-)

### This project uses and explain how to use GANs with tabular data not only with images

## Overview
Fake task attack is critical for Mobile Crowdsensing system (MCS) that aim to clog the sensing servers in the MCS platform and drain more energy from participants’ smart devices. Typically, fake tasks are created by empirical model such as CrowdSenSim tool. Recently, cyber criminals deploy more intelligent mechanisms to create attacks. Generative Adversarial Network (GAN) is one of the most powerful techniques to generate synthetic samples. GAN considers the entire data in the training dataset to create similar samples. This project aims to use GAN to create fake tasks and verify fake task detection performance.<br>


# The Project Methodology

![image](https://drive.google.com/uc?export=view&id=1DqTuRozMCieSHShD5_udzpP2MxR8MTFo)



# Project Steps:

1. Prepare the dataset For training
2. Implement classic classifiers (Adaboost and RF) and train them
3. Verify detection performance using test dataset and compare the results
4. Implement Conditional GAN with Wasserstein loss [2].
5. Train the CGAN on the training dataset
6. Generate synthetic fake tasks via Generator network in CGAN after the training procedure
7. Mix the generated fake tasks with the original test dataset to obtain a new test dataset
8. Obtain Adaboost and RF detection performance using the new test dataset and compare the results
9. Consider the Discriminator to as the first level classifier and RF/Adaboost as the second level classifier


## Important dependencies
```python
pip install numpy 
pip install tensorflow-gpu==2.9.1
pip install pandas 
pip install seaborn 
pip install matplotlib 
pip install sklearn
pip install imbalanced-learn
```

## Results

|    Original test set                                                                                               | Mixed without disc                                                                                  | Cascade framework                                                                                  |
|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| ![Original test set](https://drive.google.com/uc?export=view&id=1ZQSdpkSDZ-QCko7_9cE8iQDpWx7fYNnv) | ![Mixed without disc](https://drive.google.com/uc?export=view&id=10F31icaCioeeXcFox_4R9GkNMSm3KVmA) | ![Cascade framework](https://drive.google.com/uc?export=view&id=1ov0sRD1zQxonKinQjQOqzZsE4cvA-F06) |





# Conclusion
The generated tasks from the generator are robust and succussed to fault the classic ML algorithms because it is tried to generate tasks very close to the real one, so the models can’t determine it and the accuracies has been decreased from 0.92 to 0.575 in the Adaboost model and has been decreased from 0.993 to 0.590 in the Random Forest model.
In the cascade approach the discriminator helped the models because it can filter the fake tasks, so after the filtering it out the accuracies increased again to 0.926 in Adaboost and to 0.993 in the Random Forest model and this result is approximately one before mixing which means that the discriminator filtered.


# **Reference**
1. GAN implementation via keras https://keras.io/examples/generative/conditional_gan/
2. GAN implementation via tensorflow https://www.tensorflow.org/tutorials/generative/dcgan
3. GAN tutorial https://towardsdatascience.com/generative-adversarial-network-gan-for-dummies-a-step-bystep-tutorial-fdefff170391
4. Chen, Zhiyan, and Burak Kantarci. "Generative Adversarial Network-Driven Detection of AdversarialTasks in Mobile Crowdsensing."arXiv preprint arXiv:2202.07802 (2022).
5. Mirza, Mehdi, and Simon Osindero. "Conditional generative adversarial nets." arXiv preprint arXiv:1411.1784 (2014).
