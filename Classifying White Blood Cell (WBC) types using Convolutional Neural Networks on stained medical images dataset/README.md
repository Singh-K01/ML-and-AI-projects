# Project

## Description
Classifying White Blood Cell (WBC) types using Convolutional Neural Networks on stained medical images dataset.

## Business use-case
The time required to complete end-to-end blood testing (i.e. patient blood extraction to
delivering lab test results) can range from a few hours to over a week, depending on the purpose
for the required patient blood work (e.g. sexually transmitted infection (STI) tests, pregnancy
tests, thyroid tests, cancer tests). A common type of blood test is the Complete Blood Count
(CBC) blood test, which provides a full survey on the number of cells from the different cell
types found in patient blood (Canadian Cancer Society, 2018). Specifically, the WBC count
component of the blood test, also called the WBC differential, has been applied to the process of
“[detecting] hidden infections within [the] body and [to] alert doctors to undiagnosed medical
conditions, such as autoimmune diseases, immune deficiencies, and blood disorders... this test
[can] also help doctors monitor the effectiveness of chemotherapy or radiation treatment in
people with cancer” (Healthline Media, 2018). Until recently, the standard approach to
producing a WBC differential involved experienced operators manually counting and observing
cells under a microscope, which is considered a tedious and slow process (Su, Cheng & Wang,
2014). Some new techniques have been introduced to count the blood cells automatically, based
on chemical reactions using reagents. Initial testing of these techniques show promising results
for some - but not all - techniques (Meintker et al, 2013; MacQueen et al, 2016). Image
processing techniques could offer substantial improvements and simpler workflows.
WBC type | Approximate proportion of all WBCs
Neutrophil | 65%
Basophil | 1%
Eosinophil | 4%
Lymphocyte | 25%
Monocyte | 6%

## Project scope
This project was a proof-of-concept for utilizing CNNs for detection of WBC cell types using image input data.

## The dataset
White blood cells each belong to one of five sub-types: Basophil, Eosinophil, Lymphocyte, Monocyte, Neutrophil. The dataset is a labelled dataset with a supervised learning problem. There are approximately 410 original (non-augmented) images for each of 5 different cell types - Eosinophil, Lymphocyte, Monocyte, Basophil and Neutrophil. It can be found on Kaggle: https://www.kaggle.com/paultimothymooney/blood-cells
We scoped out BAsophils and that reduced our dataset to a total of 349 images representing four types of WBC (88 Eosinophils, 33 Lymphocytes, 207 Neutrophils, 21 Monocytes). This is a much smaller dataset than is standard in using neural networks for image classification, but our method could be extended easily, likely with stronger results, when more data is acquired.

## Note about the POC limitations
The original images are 640x480 pixels with three colour channels (RGB), but are imported into the training algorithms as resized 160x120 images to reduce the computational cost of the algorithm. This is because we had access to limited resources at the time of the project.

## Contributions
Would like to recognize the efforts of Team Osgoode at MMAI, Smith School of Business, which contributed with ideas, other code implementations, and final report. The author has only uploaded the code he worked on.
