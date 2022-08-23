---
noteId: "e8ab7120fc6c11eca76fbdf1109b752b"
tags: []
layout: "post"
title: "New digiKam Plugin to Process  Optical Character Recognition(OCR)"
date: "2022-06-19 16:41:53 +0200"
categories: "junk"
author:
  - "TRAN Quoc Hung"

---

## **Problem description** 

DigiKam is an advanced open-source digital photo management application that runs on Linux, Windows, and MacOS. The application provides a comprehensive set of tools for importing, managing, editing, and sharing photos and raw files.

However, many digikam users can take a lot of types of document pictures containing the text in them, which is needed to extract for specific reasons. Therefore, it would be practical to generate tags, add a description or a caption automatically.  

Implementing Optical Character Recognition (OCR) technology is a proposed solution for automating and extracting data. Printed or written text from a scanned document or image file can be converted to text in a machine-readable form and can be used for data processing, such as editing or searching. 

The goal of this project is to implement a new generic DPlugin to process images in batch with Tesseract. Tesseract is an-open-source OCR engine. Even though it can be painful to implement and modify sometimes, only a few of free and powerful OCR alternatives are available on the current market. Tesseract is compatible with many programming languages and frameworks through wrappers that can be found here. Tesseract can be used with the existing layout analysis to recognize text within a large document, or it can be used in conjunction with an external text detector to recognize text from an image of a single text line. 

Thanks to the help of the OCR plugin in digikam. The users will be able to select optional parameters to improve the quality of record detected text in image metadata. The output text will be saved in XML files, recorded in the exif of jfif or the user was asked to store output text under the text file in the locale where they want. Furthemore, digikam users will be able to review them and correct (spell checking) any OCR errors .  

In this document, I will first represent in detail my planned implementation and finally, my provisional schedule for each step.


## **Plan** 


The project consists of tree components:

### **_Make a new base for evaluating algorithms_**

Firstly, I will construct the test set for evaluation. Images can be collected from some websites with samples of popular cameras like Nikon, Sony, etc. Then unit tests will be implemented using the current function interface. They will re-evaluate the performance of the OCR plugin. This evaluation will give a more evident status and perspective. These tests could also be used to benchmark the accuracy of the algorithm and the execution time and to improve the performance of the plugin later. 


### **_Implement pipeline to evaluate good pre/post preprocessing algorithm in general OCR cases_**

Optical Character Recognition remains a challenging problem when text occurs in unconstrained environments, due to brightness, natural scenes, geometrical distortions, complex backgrounds, and/or diverse fonts. According to the document [2], Tesseract does various image processing operations internally before doing OCR actually.
 
Therefore, each type of document image needs to be preprocessed or segmented before text converting provided by Tesseract. During the implementation of each algorithm, we are able to choose some parts of these processes that will be duplicated for each case of the test data set. Each algorithm of OCR implementation needs a preprocessing of an image before analyzing. The purpose of this phase is to optimize the time of preprocessing and to increase the accuracy of OCR processing before analyzing. 


Post-processing is the next step to detect and correct linguistic misspellings in the OCR output text after the input image has been scanned and completely processed.  

And finally output text will be recorded in XML files or saved as a form of a text file.

I will plan some of the most basic and important pre-processing and post-processing techniques for OCR .

### **_Plugin implementation_** 

The idea of OCR processing plugin in digikam is inspired by a conversion from the RAW to DNG version. For most of the generic  plugins of digikam, their components were inherited from the abstract based class implemented exclusively, that provides its own independent implementation through the same interface.  The following sections are the proposal of general conceptions of text converter plugin to process OCR. The general architecture of the plugin will be introduced in this part. The details of this plugin will be determined explicitly after having a well tested working version for validating the pre/post preprocessing algorithm. 
