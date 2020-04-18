---
layout: article
title: Spark OCR release notes
permalink: /docs/en/ocr_release_notes
key: docs-ocr-release-notes
modify_date: "2020-04-08"
---


# 1.2.0

Release date: 08-04-2020


#### Overview

Improved support Databricks and processing selectable pdfs.

#### Enhancements

* Adapted Spark OCR for run on Databricks.
* Added rewriting positions in [TesseractOCR](ocr_pipeline_components#tesseractocr) when run together with PdfToText.
* Added 'positionsCol' param to [TesseractOCR](ocr_pipeline_components#tesseractocr).
* Improved support Spark NLP. Changed [start](/ocr_install#using-start-function) function.

#### New Features

* Added [showImage](ocr_structures#showimages) implicit to Dataframe for display images in Scala Databricks notebooks.
* Added [display_images](ocr_structures#display_images) function for display images in Python Databricks notebooks.
* Added [create_init_script_for_tesseract](ocr_structures#create_init_script_for_tesseract) for install Tesseract to Databricks cluster.
* Added propagation selectable pdf file in [TextToPdf](ocr_pipeline_components#texttopdf). Added 'inputContent' param to 'TextToPdf'.


# 1.1.2

Release date: 09-03-2020

#### Overview

Minor improvements and fixes

#### Enhancements

* Improved messages during license validation

#### Bugfixes

* Fixed dependencies issue


# 1.1.1

Release date: 06-03-2020

#### Overview

Integration with license server.

#### Enhancements

* Added license validation. License can be set in following waysq:
  - Environment variable. Set variable 'JSL_OCR_LICENSE'.
  - System property. Set property 'jsl.sparkocr.settings.license'.
  - Application.conf file. Set property 'jsl.sparkocr.settings.license'.
* Added auto renew license using jsl license server.


# 1.1.0

Release date: 03-03-2020

#### Overview

This release contains improvements for preprocessing image before run OCR and
added possibility to store results to PDF for keep original formatting.


#### New Features

* Added auto calculation maximum size of objects for removing in `ImageRemoveObjects`.
  This improvement avoids to remove `.` and affect symbols with dots (`i`, `!`, `?`).
  Added `minSizeFont` param to `ImageRemoveObjects` transformer for
  activate this functional.
* Added `tesseractParams` parameter to `TesseractOcr` transformer for set any
  tesseract params.
* Added extraction font size in `TesseractOcr`
* Added `TextToPdf` transformer for render text with positions to pdf file.


#### Enhancements

* Added setting resolution in `TesseractOcr`. And added `ignoreResolution` param with
  default `true` value to `TesseractOcr` transformer for back compatibility.
* Added parsing resolution from image metadata in `BinaryToImage` transformer.
* Added storing resolution in `PrfToImage` transformer.
* Added resolution field to Image schema.
* Updated 'start' function for set 'PYSPARK_PYTHON' env variable.
* Improve auto-scaling/skew correction:
   - improved access to images values
   - removing unnecessary copies of images
   - adding more test cases
   - improving auto-correlation in auto-scaling.


# 1.0.0

Release date: 12-02-2020

#### Overview

Spark NLP OCR functionality was reimplemented as set of Spark ML transformers and
moved to separate Spark OCR library.


#### New Features

* Added extraction coordinates of each symbol in TesseractOCR
* Added ImageDrawRegions transformer
* Added ImageToPdf transformer
* Added ImageMorphologyOpening transformer
* Added ImageRemoveObjects transformer
* Added ImageAdaptiveThresholding transformer


#### Enhancements

* Reimplement main functionality as Spark ML transformers
* Moved DrawRectangle functionality to PdfDrawRegions transformer
* Added 'start' function with support SparkMonitor initialization
* Moved PositionFinder to Spark OCR


#### Bugfixes

* Fixed bug with transforming complex pdf to image