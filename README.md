# ARE: Accessability, Readability, and Explainability



# Requirement
1. YoloV4 (Bochkovskiy et al., 2020)
```bash
git clone https://github.com/AlexeyAB/darknet.git
```
For Yolo wegihts and configuration file, please download from https://drive.google.com/drive/folders/1u-phD02XehL7fl1aZ4vt6_nMVv2jNZ17?usp=sharing

2. Tensorflow
Please download the legend neediness model from https://drive.google.com/drive/folders/1u-phD02XehL7fl1aZ4vt6_nMVv2jNZ17?usp=sharing

# Method
- Image preprocessing:
	- Compound figure classification and compound figure separation. (Please refer to https://github.com/sciosci/graph_check)

- Accessability:

- Readability:

- Explainability:
	1. Legend detection on suplots: We fine-tuned YOLOv4 (pre-trained on MS COCO dataset) with around 1400 charts to detect legend in graph .
	2. Legend detection on compound figures: We also detect on compound figures to check if legend exists.
	3. Legend neediness classification: We fine-tuned ResNet152v2 (pre-trained on ImageNet) with arond 1500 charts. If a charts has more than one lines and symbols, we annotated as needed.
	4. Legend descriptive words in caption: We analyze and count descriptive words in corresponding caption. (e.g. color words(red, blue, etc.), dashed line, solid line, triangle, square) 

# Method Flowchart
<img src="https://github.com/sciosci/ARE-analysis/blob/main/images/flowchart.png" alt="drawing" width="600"/>

# License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a> \
(c) Han Zhuang, Tzu-Yang Huang, and Daniel Acuna 2021 - 2022 Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)  \
[Science of Science + Computational Discovery Lab](https://scienceofscience.org/) in the School of Information Studies at Syracuse Univeristy.
