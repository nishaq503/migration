# Migration

Notes on PolusAI migration of docker containers

## Plugins Status

| Name                                      | Builds | Repo | Pushed | PR  | Contact | bfio  |
| ----------------------------------------- | ------ | ---- | ------ | --- | ------- | ----- |
| feature-subsetting-plugin                 | yes    | no   | no     | no  |         | 2.1.9 |
| hdbscan-clustering-plugin                 | yes    | no   | no     | no  |         | 2.1.9 |
| k-means-clustering-plugin                 |        | no   |        | yes | Nina    | 2.1.9 |
| outlier-removal-plugin                    | yes    | no   | no     | no  |         | 2.1.9 |
| csv-statistics-plugin                     |        | yes  |        | yes | Ben     | 2.1.9 |
| feature-eval-plugin                       | yes    | yes  | yes    | no  |         | 2.1.9 |
| feature-extraction-plugin                 | yes    | no   | no     | no  |         | 2.0.4 |
| imagenet-model-featurization-plugin       | yes    | no   | no     | no  |         | 2.0.0 |
| object-spectral-featurization-plugin      | yes    | no   | no     | no  |         | 2.1.6 |
| czi-extract-plugin                        | yes    | no   | no     | no  |         | 2.1.9 |
| feather-to-tabular-plugin                 | yes    | yes  | no     | no  |         | 2.1.9 |
| imaris-parser-plugin                      | yes    | no   | no     | no  |         | 2.1.9 |
| multichannel-tiff-plugin                  | yes    | no   | no     | no  |         | 1.3.6 |
| ome-zarr-converter-plugin                 | yes    | yes  | no     | no  |         | 2.1.9 |
| tabular-to-feather-plugin                 | yes    | yes  | no     | no  |         | 2.1.9 |
| tiledtiff-converter-plugin                | nope!  | yes  | no     | no  | Nick    | 2.1.9 |
| binary-ops-plugin                         | yes    | yes  | yes    | no  |         | 2.1.9 |
| basic-flatfield-correction-plugin         | yes    | yes  | yes    | no  |         | 2.1.9 |
| bleed-through-estimation-plugin           | yes    | yes  | no     | no  |         | 2.1.9 |
| aics-classic-seg-plugin                   | no     | no   | no     | no  |         | 1.3.6 |
| cell-nuclei-segmentation-plugin           | yes    | no   | no     | no  |         | 1.0.7 |
| zo1-segmentation-plugin                   | yes    | yes  | yes    | no  |         | 2.1.9 |
| apply-flatfield-plugin                    | yes    | yes  | no     | yes | Najib   | 2.1.9 |
| autocropping-plugin                       | yes    | no   | no     | no  |         | 2.1.9 |
| ftl-label-plugin                          |        | yes  |        |     |         | 2.1.9 |
| image-assembler-plugin                    |        | yes  |        |     |         |       |
| image-calculator-plugin                   |        | yes  |        |     |         |       |
| image-registration-plugin                 |        | NoÍ  |        |     |         |       |
| intensity-projection-plugin               |        | No   |        |     |         |       |
| montage-plugin                            |        | No   |        |     |         |       |
| rolling-ball-plugin                       |        | No   |        |     |         |       |
| stack-z-slice-plugin                      |        | No   |        |     |         |       |
| recycle-vector-plugin                     |        | No   |        |     |         |       |
| csv-merger-plugin                         |        | yes  |        |     |         |       |
| generalized-linear-model-plugin           |        | no   |        |     |         |       |
| tabular-thresholding-plugin               |        | yes  |        |     |         |       |
| filepattern-generator-plugin              |        | yes  |        |     |         |       |
| generic-to-image-collection-plugin        |        | no   |        |     |         |       |
| notebook-plugin                           |        | no   |        |     |         |       |
| stitching-vector-merger-plugin            |        | no   |        |     |         |       |
| subset-data-plugin                        |        | no   |        |     |         |       |
| color-pyramid-builder-plugin              |        | no   |        |     |         |       |
| feature-heatmap-pyramid-plugin            |        | no   |        |     |         |       |
| graph-pyramid-builder-plugin              |        | no   |        |     |         |       |
| image-cluster-annotation-plugin           |        | no   |        |     |         |       |
| precompute-slide-plugin                   |        | yes  |        |     |         |       |
| precompute-volume-plugin                  |        | no   |        |     |         |       |
| imagej-threshold-apply-plugin             |        | yes  |        |     |         |       |
| imagej-threshold-huang-plugin             |        | yes  |        |     |         |       |
| imagej-threshold-ij1-plugin               |        | yes  |        |     |         |       |
| imagej-threshold-intermodes-plugin        |        | yes  |        |     |         |       |
| imagej-threshold-isodata-plugin           |        | yes  |        |     |         |       |
| imagej-threshold-li-plugin                |        | yes  |        |     |         |       |
| imagej-threshold-maxentropy-plugin        |        | yes  |        |     |         |       |
| imagej-threshold-maxlikelihood-plugin     |        | yes  |        |     |         |       |
| imagej-threshold-mean-plugin              |        | yes  |        |     |         |       |
| imagej-threshold-minerror-plugin          |        | yes  |        |     |         |       |
| imagej-threshold-minimum-plugin           |        | yes  |        |     |         |       |
| imagej-threshold-moments-plugin           |        | yes  |        |     |         |       |
| imagej-threshold-otsu-plugin              |        | yes  |        |     |         |       |
| imagej-threshold-percentile-plugin        |        | yes  |        |     |         |       |
| imagej-threshold-renyientropy-plugin      |        | yes  |        |     |         |       |
| imagej-threshold-rosin-plugin             |        | yes  |        |     |         |       |
| imagej-threshold-shanbhag-plugin          |        | yes  |        |     |         |       |
| imagej-threshold-triangle-plugin          |        | yes  |        |     |         |       |
| imagej-threshold-yen-plugin               |        | yes  |        |     |         |       |
| imagej-macro-plugin                       |        | yes  |        |     |         |       |
| imagej-deconvolve-richardsonlucy-plugin   |        | yes  |        |     |         |       |
| imagej-deconvolve-richardsonlucytv-plugin |        | yes  |        |     |         |       |
| imagej-filter-addpoissonnoise-plugin      |        | yes  |        |     |         |       |
| imagej-filter-convolve-plugin             |        | yes  |        |     |         |       |
| imagej-filter-correlate-plugin            |        | yes  |        |     |         |       |
| imagej-filter-derivativegauss-plugin      |        | yes  |        |     |         |       |
| imagej-filter-dog-plugin                  |        | yes  |        |     |         |       |
| imagej-filter-frangivesselness-plugin     |        | yes  |        |     |         |       |
| imagej-filter-gauss-plugin                |        | yes  |        |     |         |       |
| imagej-filter-partialderivative-plugin    |        | yes  |        |     |         |       |
| imagej-filter-tubeness-plugin             |        | yes  |        |     |         |       |
| imagej-image-integral-plugin              |        | yes  |        |     |         |       |
| imagej-filter-sobel-plugin                |        | no   |        |     |         |       |
| label-to-vector-plugin                    | yes    | no   | no     | no  |         | 2.1.9 |
| vector-to-label-plugin                    | yes    | no   | no     | no  |         | 2.1.9 |

## Permissions:

polusai/feature-eval-plugin:0.2.2

## Definitely need testing:

* imaris-parser-plugin

## Notes

The `cell-nuclei-segmentation-plugin` used to have a requirement:
```
https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow_cpu-2.1.0-cp37-cp37m-manylinux2010_x86_64.whl ; sys_platform == 'linux'
```
