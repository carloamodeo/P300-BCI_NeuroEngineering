# P300 Speller Project

This project was undertaken as part of the Neuroengineering course at Politecnico di Milano. The data used in this project is sourced from the BCI Competition III, Dataset II, involving two subjects (http://www.bci2000.org) and is provided in .mat format. The primary goal of this project was to investigate whether a subset of electrodes could maintain acceptable accuracy in detecting P300 events.

## Abstract

In the initial preprocessing phase, we segmented the signal into windows of 667ms, applied an 8th order bandpass Butterworth filter with cutoff frequencies set at 0.1 and 20, and subsequently extracted the average P300 and non-P300 epochs for pattern visualization.

The model implemented for this project is inspired by Liu et al., featuring a 6-layer CNN known as the Batch Normalization Neural Network (BN3). Batch normalization layers were used to mitigate internal covariate shift during neural network training, and the first layer reduced the channel dimensionality from 64 to 16 via 1D convolution.

In addition to Liu's neural network, we experimented with a Long Short-Term Memory/CNN network and a distinct CNN architecture. However, our observations revealed that BN3 consistently delivered the best overall performance. The model achieved an accuracy of 0.77 for subject B and 0.7 for subject A. We also confirmed Liu's observation that the model tends to overfit after 6 epochs using early stopping.

For character recognition within the speller, which involves accumulating P300 signal detections and determining the intent character by identifying the row and column with the most detections, we achieved an accuracy of 92% for both subjects.

Our group's specific task, the electrode subset analysis, significantly reduced computational and setup time. The spatial activation graph displayed a clear distinction between P300 and non-P300 events, with P300 events occurring 300-400ms after the intensification of the row/column where the desired letter is located. To assess electrode importance, we employed the Leave One Feature Out method, which iteratively removed a channel and calculated its importance based on accuracy. Our findings aligned with existing literature, confirming that the parietal zone, especially the occipital and parietal electrodes, exhibited the highest activation levels.

## Original paper:
Liu, Mingfei & Wu, Wei & Gu, Zhenghui & Yu, Zhuliang & Qi, FeiFei & Li, Yuanqing. (2017). Deep Learning Based on Batch Normalization for P300 Signal Detection. Neurocomputing. 275. 10.1016/j.neucom.2017.08.039.