# Migration

Notes on PolusAI migration of docker containers

## Plugins Status

| Name                                 | Builds | Repo | Pushed | PR  | Contact | bfio  |
| ------------------------------------ | ------ | ---- | ------ | --- | ------- | ----- |
| feature-subsetting-plugin            | yes    | no   | no     | no  |         | 2.1.9 |
| hdbscan-clustering-plugin            | yes    | no   | no     | no  |         | 2.1.9 |
| k-means-clustering-plugin            |        |      |        | yes | Nina    | 2.1.9 |
| outlier-removal-plugin               | yes    | no   | no     | no  |         | 2.1.9 |
| csv-statistics-plugin                |        |      |        | yes | Ben     | 2.1.9 |
| feature-eval-plugin                  | yes    | yes  | yes    | no  |         | 2.1.9 |
| feature-extraction-plugin            | yes    | no   | no     | no  |         | 2.0.4 |
| imagenet-model-featurization-plugin  | yes    | no   | no     | no  |         | 2.0.0 |
| object-spectral-featurization-plugin | yes    | no   | no     | no  |         | 2.1.6 |
| czi-extract-plugin                   | yes    | no   | no     | no  |         | 2.1.9 |
| feather-to-tabular-plugin            | yes    | yes  | no     | no  |         | 2.1.9 |
| imaris-parser-plugin                 | yes    | no   | no     | no  |         | 2.1.9 |
| multichannel-tiff-plugin             | yes    | no   | no     | no  |         | 1.3.6 |
| ome-zarr-converter-plugin            | yes    | yes  | no     | no  |         | 2.1.9 |
| tabular-to-feather-plugin            | yes    | yes  | no     | no  |         | 2.1.9 |
| tiledtiff-converter-plugin           | nope!  | yes  | no     | no  | Nick    | 2.1.9 |
| vector-converter-plugins             | yes    | no   | no     | no  |         | 2.1.9 |
| binary-ops-plugin                    | yes    | no   | no     | no  |         | 2.1.9 |
| basic-flatfield-correction-plugin    | yes    | yes  | yes    | no  |         | 2.1.9 |
| bleed-through-estimation-plugin      | yes    | yes  | no     | no  |         | 2.1.9 |
| aics-classic-seg-plugin              | no     | no   | no     | no  |         | 1.3.6 |
| cell-nuclei-segmentation-plugin      | yes    | no   | no     | no  |         | 1.0.7 |
| zo1-segmentation-plugin              | yes    | yes  | yes    | no  |         | 2.1.9 |
| apply-flatfield-plugin               | yes    | yes  | no     | yes | Najib   | 2.1.9 |
| autocropping-plugin                  | yes    | no   | no     | no  |         | 2.1.9 |

## Definitely need testing:

* imaris-parser-plugin

## Notes

The `cell-nuclei-segmentation-plugin` used to have a requirement:
```
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow_cpu-2.1.0-cp37-cp37m-manylinux2010_x86_64.whl ; sys_platform == 'linux'
```
