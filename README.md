# Laboratory-Work-5-Activity-Comparative-Analysi
https://colab.research.google.com/drive/1n1UgrTDXk3-5T2IoRDyfvuwB1i-1jxiS?usp=sharing

Model	Train Acc	Train Loss	Val Acc	Val Loss	Precision	Recall	F1-Score	AUC
MobileNetV2	98.82%	0.0837	*99.59%	0.0282	99.66%	99.66%	99.65%	0.9999
EfficientNetB0	99.13%	0.0911	100.00%	0.0094	100.00%	100.00%	100.00%	1.0000
InceptionV3	83.91%	0.7569	83.71%	0.3643	88.49%	84.24%	83.03%	0.9891
Model	Val Accuracy	Val Loss	Precision	Recall	F1-Score	AUC	Notes
Teachable Machine	24.40%	6.2387	20.80%	24.19%	22.00%	0.6338	Label order mismatch
LW3 — Custom CNN	93.20%	0.2215	94.91%	93.18%	92.89%	0.9644	Baseline improved model
LW4 — Enhanced CNN	96.70%	0.0644	97.80%	96.85%	96.68%	0.9963	Best custom CNN
LW5 — InceptionV3	83.91%	0.3643	88.49%	84.24%	84.24%	0.9891	Pre-trained (ImageNet)
LW5 — EfficientNetB0	100.00%	0.0094	98.29%	100.00%	100.00%	1.0000	Best overall
LW5 — MobileNetV2	99.59%	0.0282	99.66%	99.66%	97.88%	0.9999	Pre-trained (ImageNet)
