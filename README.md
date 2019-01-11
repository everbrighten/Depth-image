# A dataset of Snow-road

The images in this dataset are of actual road scenes captured while unmanned vehicle driving.

If this dataset is provided for research purposes, please see License section below.


## Files
Currently the dataset contains 6000 [infrared images](infrared_images), visible light images and ground-truth depth maps.

```
-----------------------------------------------------
infrared images         | 6000 | 7.40M tokens
visible light images    | 6000 |  396K tokens
ground-truth depth maps | 6000 | 1.11M tokens
-----------------------------------------------------
```

## Format
The raw images in Snow-road dataset are the resolution of 768×576.
We crop the infrared images, visible light images and depth maps to the resolution of 256×512 for depth estimation. Next, the depth map that display on `Example` are generated by classifying the raw depth map into 32 levels in the logarithmic space.We use the generated depth maps as training and testing labels


## Example

### infrared images 

![infrared_image](/example/infrared_image.png)

### visible light images

![visible light image](/example/visible_light_image.png)

### depth maps

![depth_map](/example/depth_map.png)


## Usage

Start with importing `package`:
```python
import h5py
import matplotlib.pyplot as plt
```
- To load a dataset:
```python
def read_hdf5(file_name):
    with h5py.File(file_name, 'r') as f:
        images = np.asarray(f['images'])
        depths = np.asarray(f['depths'])
        infrareds = np.asarray(f['infrareds'])
    return images,depths,infrareds
images,depths,infrareds=read_hdf5('test_snow_data.h5')
```
- To display the image of a dataset:
```python
i, j = 0,4
imageTest = images[i:j]
plt.imshow(imageTest[0],cmap='jet')
```


## License
I provide this dataset for research purposes and make no ownership claim on any part of it. The question of copyright in the case of jokes is unclear and I recommend not using the dataset commercially.

For removal of copyrighted content, please contact me on GitHub.


## Citing
If you use this dataset in academic work, please cite as follows:

```bibtex
@misc{pungas,
        title={A dataset of English plaintext jokes.},
        url={https://github.com/taivop/joke-dataset},
        author={Pungas, Taivo},
        year={2017},
        publisher = {GitHub},
        journal = {GitHub repository}
}
```
