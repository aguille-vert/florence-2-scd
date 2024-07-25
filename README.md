# Stacked Carton Dataset: Experiments with Various Models
### this repository is work-in-progress  

[SCD: A Stacked Carton Dataset for Detection and Segmentation](https://arxiv.org/abs/2102.12808)  


Even the most advanced Warehouse Management Systems (WMS) depend on humans, and humans make errors. One of such erros which leads to operational costs is misplacements of pallets. Misplaced pallet is a lost pallet. WMS shows its location, but it's not there. To find lost pallets, warehouses  have to perform periodic inventory counting, which - if done manually, is costly and slow.  

Manual counting of pallets can be replaced with AI/ML. The following steps are needed to implement automated AI-assisted pallet counting/identification:  

- object detection model needs to be trained/fine-tuned on a custom dataset of pallets
- bar codes and text need to be recognized in each detected segment
- a combination of recognized barcodes and text need to be matched to an index of product titles/bar codes/other textual information/
- an image of each incoming pallet can be made when a pallet enters a warehouse facility; in that case bar codes/textual information can be enhenced with images  

The system described above can be connected to a drone, which performs autonomous/semi-autonomous flightrs inside a warehouse and sends video stream or images to a server, which does object detection/recognition/matching. 

This repository contains notebooks and code to fine-tune and deploy several models. We are using Stacked Carton Dataset to fine-tune the model to recognize segments of carton boxes stacked on pallets in warehouses. 

The two images below show an example of an image from SCD dataset: 
* without annotated segments
* with annotated segments

our goal is to fine-tune Florence-2 model so that it annotates carton segments on an image with maximum accuracy.  


<p align="center">
    <a href="https://github.com/aguille-vert/stacked-carton-recognition/blob/main/images/carton_00.png" target="_blank">
        <figure>
            <img src="https://github.com/aguille-vert/stacked-carton-recognition/blob/main/images/carton_00.png" alt="Example of unlabeled image of stacked cartons" width="100"/>
            <figcaption>Image of unannotated stacked cartons</figcaption>
        </figure>
    </a>
</p>

<p align="center">
    <a href="https://github.com/aguille-vert/stacked-carton-recognition/blob/main/images/carton_01.png" target="_blank">
        <figure>
            <img src="https://github.com/aguille-vert/stacked-carton-recognition/blob/main/images/carton_01.png" alt="Example of labeled image of stacked cartons" width="100"/>
            <figcaption>Image of annotated stacked cartons</figcaption>
        </figure>
    </a>
</p>


# Brief description of the Notebooks
notebooks will be added as the project progresses

[0_SCD_download_explore.ipynb](https://github.com/aguille-vert/florence-2-scd/blob/main/notebooks/0_SCD_download_explore.ipynb)  

In this notebook we download Stacked Carton Dataset and explore its contents 


[1_SCD_create_dataset_ft_detr.ipynb](https://github.com/aguille-vert/stacked-carton-recognition/blob/main/notebooks/1_SCD_create_dataset_ft_detr.ipynb)  

In this notebook we make the necessary tarnsformations and create the following 3 datasets:
* train_df
* val_df
* test_df  

[3_florence_2_zero_shot.ipynb](https://github.com/aguille-vert/florence-2-scd/blob/main/notebooks/3_florence_2_zero_shot.ipynb)  

In this notebook we test zero-shot Florence-2 performance on a selection of images from val_df. We can see that the model shows quite a reasonable accuracy and thus is a good candidate for fine-tuning.  

[4_fine_tune_rt_detr.ipynb](https://github.com/aguille-vert/stacked-carton-recognition/blob/main/notebooks/4_fine_tune_rt_detr.ipynb)  

In this notebook we fine-tune [RT-DETR](https://huggingface.co/PekingU/rtdetr_r50vd_coco_o365) model. Unfortunately, we have failed to achieve good enough results with this model.