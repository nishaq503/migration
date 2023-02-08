# Migration

Notes on PolusAI migration of docker containers

## General Notes

* Add bump2version to every single plugin to manage plugin version numbers.
* If at all possible, we need to remove exact pins of version numbers of packages for every python plugin. In general, use [semver notation](https://devhints.io/semver) for all requirements.
* If a plugin requires `preadator`, it needs to be updated when the newer version of `preadator` comes out with bug fixes.
* If a plugin relies on `filepattern`, we should restrict version numbers to `<2.0` in anticipation of the new release of `filepattern`. Once the update to `filepattern` lands, we can go back over our plugins and make the required updates.
* If a plugin relies on a pre-1.0 version of a package, figure out how to properly handle versions of all involved packages to prevent breaks from updates in other packages like `bfio`.
 
## binary-ops-plugin

* Open PR to remove the duplicate of this plugin.
* This plugin relies on `filepattern`.

## Problematic Plugins

* features
  * feature-evaluation
    * Update `requirements.txt`. Particularly, `scikit-learn` from `0.24.2` to `1.x`
  * feature-extraction
    * update `bfio` from `2.0.4` to `2.1.9`.
  * object-spectral-featurization
    * This used to rely on `scikit-image==0.17.2` but I needed to change it to `scikit-image>=0.17.2`. Test the plugin to make sure that nothing broke.
* formats
  * czi-extract
    * This relies on `preadator`.
  * imaris-parser
    * I had to update all packages in `requirements.txt` and to this should be tested for correctness.
    * The main update will be with `pandas` going from `0.24.2` to `1.x`.
    * We should also take a look at the dependency on `XlsxWriter`.
  * multichannel-tiff
    * This used to use `bfio==1.3.6` and will have bugs from breaking changes in `2.1.9`.
  * ome-converter
    * This relies on `preadator`
  * tabular-to-feather
    * This relies on `fcsparser==0.2.2` and `blake3==0.2.1`.
  * tiledtiff-converter
    * Container fails to build.
    * This is a java plugin. Is this an obsolete plugin with `bfio` in the picture?
* regression
  * basic-flatfield-correction
    * Test this plugin because it was updated to use `basicpy` and needs to be able to run on a GPU.
    * Tests are underway (Najib)
  * bleed-through-estimation
    * Container fails to build. Investigate why. Probably because of inclusion of `bfio` in `requirements.txt`.
    * Update the plugin with new features from the Theia paper and associated code.
* segmentation
  * aics-classic-seg
    * Container fails to build. Probably because of the reliance, in `requirements.txt`, on a git commit hash from [the discontinued repo](https://github.com/AllenInstitute/aics-segmentation) from the Allen Institute.
    * This used to use `bfio==1.3.6` and will have bugs from breaking changes in `2.1.9`.
  * cell-nuclei-segmentation
    * folder needs renaming to have the `plugin` postfix.
    * This used to use `bfio==1.0.7` and will have bugs from breaking changes in `2.1.9`.
    * This used to rely on a tensorflow wheel from a [google repo](https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow_cpu-2.1.0-cp37-cp37m-manylinux2010_x86_64.whl). Test this plugin in the `bfio:2.1.9-tensorflow` container.
  * smp-training
    * Tests are underway.
    * Tests are underway (Najib)
  * zo1-segmentation
    * Get update from Ben about plugin status
* transforms/images
  * autocropping
    * This plugin relies on `filepattern`.
  * ftl-label
    * Optimization is underway (Najib)
  * image-registration
    * The old container base image was `labshare/polus-bfio-util:2.4.2-slim-buster`. Test the plugin with the new `bfio` base container.
    * This plugin relies on `filepattern`.
  * intensity-projection
    * This used to use `bfio==2.0.5` and will have probably bugs from breaking changes in `2.1.9`.
  * roi-relabel
    * This plugin needs a `VERSION` file.
  * stack-z-slice
    * This used to use `bfio==2.0.5` and will have probably bugs from breaking changes in `2.1.9`.
    * This plugin relies on `filepattern`.
* transforms/tabular
  * csv-merger
    * This plugin relies on `filepattern`.
    * This relies on `blake3==0.2.1`.
* utils
  * filepattern-generator
    * folder needs renaming to have the `polus` prefix.
  * generic-to-image-collection
    * This plugin relies on `filepattern`.
  * imagej-macro
    * Testing is underway (Ben)
  * notebook
    * Container fails to build
  * subset-data
    * This plugin relies on `filepattern`.
* visualization
  * color-pyramid-builder
    * The old container base image was `labshare/polus-bfio-util:2.4.4-slim-buster`. Test the plugin with the new `bfio` base container.
  * feature-heatmap-pyramid
    * This used to use `bfio==1.3.6` and will have bugs from breaking changes in `2.1.9`.
  * graph-pyramid-builder
    * This plugin relied on `pandas==0.25.1` and the current version is `1.x`.
  * precompute-slide
    * This relies on `preadator` and `filepattern`.
  * precompute-volume
    * There are lots of issues with the requirements listed.
