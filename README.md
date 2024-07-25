# Fine-tune Florence-2 Multi Modal LLM on Stacked Carton Dataset
### this repository is work-in-progress  

Even the most advanced Warehouse Management Systems depend on humans, and humans make errors. One of such erros which leads to operational costs is misplacements of pallets. Misplaced pallet is a lost pallet. WMS shows its location, but it's not there. To find lost pallets, warehouses  have to perform periodic inventory counting, which if done manually is costly and slow.  

This repository contains notebooks and code to fine-tune and deploy Florence-2 model. We are using Stacked Carton Dataset to fine-tune the model to recognize segments of carton boxes stacked on pallets in warehouses. Identifying box segments is the first step to match boxes to a product index from WMS. The second step is to OCR each segment to extract text written on the boxes. The third step is to identify barcodes on the cartons. The fourth step involves matching barcodes and text to the product index.  

The two images below show an example of an image from SCD dataset: 
* without annotated segments
* with annotated segments

our goal is to fine-tune Florence-2 model so that it annotates carton segments on an image with maximum accuracy.  


<p align="center">
    <a href="https://github.com/aguille-vert/florence-2-scd/blob/main/images/carton_00.png" target="_blank">
        <figure>
            <img src="https://github.com/aguille-vert/florence-2-scd/blob/main/images/carton_00.png" alt="Example of unlabeled image of stacked cartons" width="100"/>
            <figcaption>Image of unannotated stacked cartons</figcaption>
        </figure>
    </a>
</p>

<p align="center">
    <a href="https://github.com/aguille-vert/florence-2-scd/blob/main/images/carton_01.png" target="_blank">
        <figure>
            <img src="https://github.com/aguille-vert/florence-2-scd/blob/main/images/carton_01.png" alt="Example of labeled image of stacked cartons" width="100"/>
            <figcaption>Image of annotated stacked cartons</figcaption>
        </figure>
    </a>
</p>


# Brief description of the Notebooks
notebooks will be added as the project progresses

[0_SCD_download_explore.ipynb](https://github.com/aguille-vert/florence-2-scd/blob/main/notebooks/0_SCD_download_explore.ipynb)  

In this notebook we download Stacked Carton Dataset and explore its contents 


[1_SCD_create_train_val_ds.ipynb](https://github.com/aguille-vert/florence-2-scd/blob/main/notebooks/1_SCD_create_train_val_ds.ipynb)  

In this notebook we make the necessary tarnsformations and create the following 3 datasets:
* train_df
* val_df
* test_df  

[3_florence_2_zero_shot.ipynb](https://github.com/aguille-vert/florence-2-scd/blob/main/notebooks/3_florence_2_zero_shot.ipynb)  

In this notebook we test zero-shot Florence-2 performance on a selection of images from val_df. We can see that the model shows quite a reasonable accuracy and thus is a good candidate for fine-tuning.