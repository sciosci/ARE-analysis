# ARE: Accessability, Readability, and Explainability
Figures are an essential part of scientific communication. Yet limited is understood about how accessible (e.g., color-blind safe), readable (e.g., good contrast), and explainable (e.g., contain captions and legends) they are--i.e., ARE issues. We develop computational techniques to measure these features and analyze a large sample from open access publications. Our method combines principles from computer and human vision research, achieving high accuracy. Overall, we found that around 5% of all figures contain some issue. We found that readability and accessibility are lower for lower-ranked journals and smaller author’s h-index . We release our analysis as a dataset and method for further examination by the scientific community.

# Requirement
1. YoloV4 (Bochkovskiy et al., 2020)
```bash
git clone https://github.com/AlexeyAB/darknet.git
```
For Yolo wegihts and configuration file, please download from [ARE_explainability](https://drive.google.com/drive/folders/1u-phD02XehL7fl1aZ4vt6_nMVv2jNZ17?usp=sharing)

2. Tensorflow
Please download the legend neediness model from [ARE_explainability](https://drive.google.com/drive/folders/1u-phD02XehL7fl1aZ4vt6_nMVv2jNZ17?usp=sharing)

# Method
- Image preprocessing:
	- Compound figure classification and compound figure separation. (Please refer https://github.com/sciosci/graph_check)

- Accessability: Inaccessible to color-blind readers
	1. Obtain figures in color-blind vision systems through a simulation method (Machado et al., 2009)
	2. Colorblind unsafe: examine if a figures contains red and green areas at the same time and if the red area disappears in the simulated figure.
	
- Readability: 
	1. Low light image classification: Fined-tuned a convolutional neural network to classify.
	2. Computed RMS constrast and spatial frequency.
	3. Image with issues: the proportion of high spatial frequcney > 0.5 in low contrast and low light images.

- Explainability: Contain legends and appropriate captions in line charts.
	1. Image classification: Fine-tuned YOLOv4 to classify charts into different categories (line charts, bar charts, ...). (Please refer https://github.com/sciosci/graph_check)
	2. Legend detection on suplots: Fine-tuned YOLOv4 (pre-trained on MS COCO dataset) with around 1400 charts to detect legend in graph. We also detect corresponding compound figures to check if legend exists.
	3. Legend neediness classification: Fine-tuned ResNet152v2 (pre-trained on ImageNet) with arond 1500 charts. If a charts has more than one lines and symbols, we annotated as needed.
	4. Legend descriptive words in caption: Analyzed and counted descriptive words in corresponding caption. (e.g. color words(red, blue, etc.), dashed line, solid line, triangle, square) 

# Method Flowchart
<img src="https://github.com/sciosci/ARE-analysis/blob/main/images/flowchart.png" alt="drawing" width="600"/>

# License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a> \
(c) Han Zhuang, Tzu-Yang Huang, and Daniel Acuna 2021 - 2022 Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)  \
[Science of Science + Computational Discovery Lab](https://scienceofscience.org/) in the School of Information Studies at Syracuse Univeristy.

# Reference
- Bochkovskiy, A., Wang, C.-Y., & Liao, H.-Y. M. (2020). YOLOv4: Optimal Speed and Accuracy of Object Detection. ArXiv:2004.10934 [Cs, Eess]. http://arxiv.org/abs/2004.10934
- Jambor, H., Antonietti, A., Alicea, B., Audisio, T. L., Auer, S., Bhardwaj, V., Burgess, S. J., Ferling, I., Gazda, M. A., & Hoeppner, L. H. (2021). Creating clear and informative image-based figures for scientific publications. PLoS Biology, 19(3), e3001161.
