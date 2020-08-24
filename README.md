# Deep Neural Networks Help Detect Defects in Semiconductors
For a company that produces millions of semiconductors each week, it is essential to design a model to automate the detection of defects in order to pick out the flawed products while not sacrificing too many good ones as well as liberate humans from menially checking the products themselves.

Our research applied two deep neural network models, ResNet18 and VGG19 with back normalization (we will call it VGG19 for simplicity from now on), and modified them to combine spatial transformer networks or attention networks (STN) to the defect detection task. We fed 31025 images to train plain ResNet18, VGG19, ResNet18 and VGG19 with STN inserted before, respectively, and ResNet18 with three attention layers inserted after the last three residual blocks, and tested the above-mentioned five models on another set of 3830 images and compared the results.

In order to measure the performance, we set defect images as positive, and passed ones negative. For each model, we compare the AUC and estimate the false positive rate (FPR) against true positive rate (TPR) being 99.1%, 99.3%, 99.5%, 99.7%, and 100%, respectively. We find that a plain ResNet18 model can detect defects pretty good, with FPR below 5% when TPR is boosted to 99.7%. No other models can vie with a plain ResNet18 when TPR is up to 99.7%. However, when TPR is set to be 100%, i.e., all defect images are correctly picked out, a VGG19 model with STN works best, with FPR below 25% when TPR=100% and below 8% when TPR<=99.7%.

Another interesting finding is that, looking into the images that are wrongly classified by most models, we confirm that many of the passed images with high defect scores are indeed flawed. Furthermore, the higher the defect score is, the more reassuring that an image has defects, while those with relatively lower defect scores are considered on the borderline between passed and flawed. It is understandable that the current labels we are using are decided by human beings and humans make mistakes. Nevertheless, these mistakes could harm the trustworthiness of the ground truth of the data, thereby affecting our models' performance. With difficulties to further improve the performance of current deep neural networks, which all already give AUC over 99.60%, the forthcoming task will be to estimate the probability that mislabelling occurs and to apply neural networks to correct the mistakes.
