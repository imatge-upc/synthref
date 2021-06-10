# SynthRef: Generation of Synthetic Referring Expressions for Object Segmentation

### Updates

- [X] Upload SynthRef-YouTube-VIS dataset
- [X] Upload pre-trained scene graph generation model which is able to detect object attributes
- [ ] TODO: Upload code for generating SynthRef-YouTube-VIS dataset
- [ ] TODO: Provide PyTorch dataloader for running [RefVOS model] with SynthRef-YouTube-VIS dataset 
- [ ] TODO: Provide weights of best models trained with SynthRef-YouTube-VIS dataset

[RefVOS model]: https://github.com/miriambellver/refvos

## Datasets

### 1. YouTube-VIS

In this work we used SynthRef method to generate synthetic referring expressions
for the training set of YouTube-VIS dataset [[1]](#1). We have used the 2019 version
of YouTube-VIS.

YouTube-VIS dataset (2019 version) can be downloaded [here].

[here]: https://youtube-vos.org/dataset/vis/


## SynthRef

![alt text](images/SynthRef_Overview.png "SynthRef Overview")

SynthRef generates synthetic referring expressions for objects by using the 
ground-truth annotations (object classes and bounding boxes) of objects in an 
image/video dataset as well as detected attributes of target objects.

Attributes for target objects are 
predicted by the model of [Unbiased Scene Graph Generation from Biased Training] [[3]](#3), a
scence graph generation model base on Faster R-CNN. 

Similarly to our work, where we used this model for predicting attributes for the objects in YouTube-VIS, this model 
can be used to predict attributes on any image/video dataset. Please refer to these [guidelines] on how to 
detect scene graphs (including attributes of objects) for your dataset.

We provide the pre-trained scene graph generation model with attribute detection head which you
can use in order to detect attributes for your dataset, following the [guidelines] mentioned above.

[guidelines]: https://github.com/KaihuaTang/Scene-Graph-Benchmark.pytorch#SGDet-on-custom-images

In our paper we only take advantage of the detected attributes but we encourage the community to explore also
the scene graph relationships for the generation of referring expressions.

## SynthRef-YouTube-VIS Dataset

Our dataset with synthetic referring expressions for YouTube-VIS training set is called SynthRef-YouTube-VIS.
It can be found in the **data/** folder in .csv format.

The video_id and annotation_id columns of the dataset correspond to the video and annotation IDs of the
"train_meta.json" file of the YouTube-VIS dataset, which you have to download from
the link provided [here].



[Unbiased Scene Graph Generation from Biased Training]: https://github.com/KaihuaTang/Scene-Graph-Benchmark.pytorch

## Experiments

The model used in our experiments is [RefVOS] [[2]](#2) 

We will provide the PyTorch Dataloader file which can be used in order to train RefVOS 
with SynthRef-YouTube-VIS dataset.

We will also upload the weights of the best RefVOS models trained with SynthRef-YouTube-VIS.

[RefVOS]: https://arxiv.org/abs/2010.00263
## References
<a id="1">[1]</a> 
Video instance segmentation (2019).
Linjie Yang, Yuchen Fan, and Ning Xu.
In Proceedings of the IEEE International Conference on Computer Vision, pages 5188–5197.

<a id="2">[2]</a>
Refvos: A closer look at referring expressions for video object segmentation (2020).
Miriam Bellver, Carles Ventura, Carina Silberer, Ioannis Kazakos, Jordi Torres, and Xavier Giro-i Nieto.
arXiv preprint arXiv:2010.00263

<a id="3">[3]</a>
Unbiased Scene Graph Generation from Biased Training (2020).
Kaihua Tang, Yulei Niu, Jianqiang Huang, Jiaxin Shi, Hanwang Zhang.
In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition,
pages 3716–3725.