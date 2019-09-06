# Polus CZI Extraction Plugin

This WIPP plugin will import individual fields of view from a CZI file (will only import one scene or collection of images).

The need for this plugin is due to the bioformats mechanism of importing CZI images. If the image in the CZI file is mosaiced (stitched based off image positions in Zen), then bioformats imports the mosaiced image. However, preprocessing may want to be performed prior to mosaicing, or correlation based image stitching may want to be performed to improve the quality/accuracy of the stitching. Correlation based image stitching may be desired since small errors in the microscope stage may lead to minor offsets/defects in the mosaic based off of stage position alone.

For more information on WIPP, visit the [official WIPP page](https://isg.nist.gov/deepzoomweb/software/wipp).

**This plugin is an alpha version and subject to substantial changes.**

## Building

To build the Docker image for the conversion plugin, run
`./build-docker.sh`.

## Install WIPP Plugin

If WIPP is running, navigate to the plugins page and add a new plugin. Paste the contents of `plugin.json` into the pop-up window and submit.

There is currently no publicly available docker image, so a docker image will need to be built and sent to the kubernetes cluster WIPP is running on.

## Options

This plugin takes one input argument and one output argument:
1. Path to czi file folder

## Run the plugin

### Run the Docker Container

```bash
docker run -v /path/to/data:/data polus-czi-extract-plugin \
  --inpDir /data/input \
  --outDir /data/output
```
