# CSU-RSISC10-DATASET

## Updata Info.
More natural catogeries are added to CSU-RSISC. Now all patches are classified into 15 typical urban and natural scenes categories, including road, commercial area, industrial area, residential area, redeveloped area, institutional organization, harbor, open space, airport, ocean, inland water, mountain, barren, forest, and field. 
## dataset link:
Baidu disk: https://pan.baidu.com/s/12-DgF3ZiuSi0dnfg-xM7iw

Google drive: https://drive.google.com/open?id=1qU2s0HIZanF9OqwkwX0zy6wruCIr127A
(New data will be updated in the near future)

## Introduction
This dataset is for urban scene classification and built by Chao Tao, Weipeng Lu, Ji Qi and Hao Wang of Central South University. This dataset is composed by two levels: sample and patch.
The size of a sample is 2000×2000 and the size of a patch is 100×100. When you use this dataset, please cite this project.
![Two-level Construction](fig.png)
## Categories
The categories and number of data in train and test dataset.

| Scene Class   | Sub-class components                                                                     | Count | Label # |
| ------------- | ---------------------------------------------------------------------------------------- | ----- | ------- |
| Road          | Railway, highway, overpass, intersection and general road                                | 21886 | 0       |
| Commercial    | Commercial services with complex buildings, and parking lots around commercial buildings | 7071  | 1       |
| Industrial    | Factory, warehouse                                                                       | 2094  | 2       |
| Residential   | Residential houses, terraces and small road in them                                      | 48253 | 3       |
| Redeveloped   | Bare soil, scattered vegetation, reconstructions                                         | 1905  | 4       |
| Institutional | Education, church, scientific research, office                                           | 2543  | 5       |
| Harbor        | Sea shore, dock, ship                                                                    | 5975  | 6       |
| Open Space    | Park, sports field, leisure square, beach and parking lots nearby them                   | 14460 | 7       |
| Airport       | Airport, runway, and building grass and road in airport                                  | 3503  | 8       |
| Ocean         | Sea                                                                                      | 12307 | 9       |
| Inland Water  | Rivers and channels on land                                                              | 2081  | 10      |
| Mountain      | A land mass that projects well above its surroundings                                    | 13681 | 11      |
| Barren        | land with on vegetation or unused                                                        | 4758  | 12      |
| Forest        | Natural woodland                                                                         | 20834 | 13      |
| Field         | Agricultural land and its auxiliary facilities                                           | 52249 | 14      |
## How to use
The following code (Python) shows an example to get a patch's label by its file name:
```python
import cv2


lbl = {
    1: cv2.imread('root/LA-1-LBL_PATCH.tif', 0),
    2: cv2.imread('root/LA-2-LBL_PATCH.tif', 0),
    3: cv2.imread('root/LA-3-LBL_PATCH.tif', 0),
    4: cv2.imread('root/LA-4-LBL_PATCH.tif', 0),
    5: cv2.imread('root/LA-5-LBL_PATCH.tif', 0),
    6: cv2.imread('root/LA-6-LBL_PATCH.tif', 0)
} # load labels

file_name = 'LA_3_002003_002017.tif'
'''
LA_3_002003_002017.tif is the file name.
LA_3 means the region code.
002003 means this patch is from a sample whose row and colunm in LA_3 is 2 and 3.
002007 means this row 2 and column 7 of this patch in the sample that it belongs to.
'''

region = int(file_name.split('_')[1])
sample_region = patch_name.split('_')[2]
patch_region = patch_name.split('_')[3][:-4]
sample_row, sample_cul = int(sample_region[:3]), int(sample_region[3:])
patch_row, patch_cul = int(patch_region[:3]), int(patch_region[3:])
pixel_row = sample_row * 20 + patch_row
pixel_cul = sample_cul * 20 + patch_cul

label_of_file = lbl[region][pixel_row, pixel_cul]
```
