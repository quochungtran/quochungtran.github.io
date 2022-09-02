---
noteId: "4356ef400cb811ed9a159b1ba6a039b6"
tags: []
layout: "post"
title: "<Weeks 10,11,12> Cleaning code and demo application"
categories: "junk"
date: "2022-08-30 16:41:53 +0200"
author:
  - "TRAN Quoc Hung"
meta: "Springfield"

---


# Resuming  

In my final weeks of the Google Summer of Code 2022, I spend my time polishing code and writing and documenting all parts of my code for the final Submission for final integration into the branch master.


I discussed with my mentor throughout these weeks that these tasks mainly focus on : 

- Add a license header on the top of each source file.
- Drop extra space by using the bash script : https://invent.kde.org/graphics/digikam/-/blob/master/project/scripts/dropextraspaces.sh.
- Use **cppcheck** (Cppcheck is an analysis tool for C/C++ code). It provides unique code analysis to detect bugs and focuses on seeing undefined behavior and danger).
- Reduce the text size of each item in QcomboBox, add notes in context for translators to limit translation sizes, and use a tooltip to host a long string description for each item.
- Limit digiKam and Qt headers to export the minimum dependencies outside digiKam.

To summarize, I would like to demo the functionalities of the Digikam OCR tool what I have done:


1. The user can process OCR in multiple documented images by selecting them; if not, a pop-up will appear. 

2. There are four options that users can choose from based on 4 Tesseract basic options. 

3. When the User clicks the button "Start OCR," The batch process will begin, it finishes 100% in the progress bar, and all results details are displayed in the Text Editor by double click on the item. 

4. With the support of the spell-checking engine, users can adjust the text and store it in separate text files or XMP metadata by clicking on the "Save" button. 

5. The text stored in XMP can translate to another language if stored in another place.


You can view the demo of the plugin here : 


[demo](https://drive.google.com/file/d/1wyiHLaJbHDna1QLUZ5wS6vrrKwiyPkts/view?usp=sharing) 


# Improvement 


As mentioned in week 1 and 2, the accuracy of OCR need to be enhanced, so a dialog concluding the pre-processing methods is necessary. This feature will be helpful in the future.    