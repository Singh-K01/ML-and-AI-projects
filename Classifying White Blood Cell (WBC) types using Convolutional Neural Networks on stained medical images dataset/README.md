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

## The dataset
White blood cells each belong to one of five sub-types: Basophil, Eosinophil, Lymphocyte, Monocyte, Neutrophil. The dataset is a labelled dataset with a supervised learning problem. There are approximately 3,000 images for each of 4 different cell types - Eosinophil, Lymphocyte, Monocyte, and Neutrophil. It can be found on Kaggle: https://www.kaggle.com/paultimothymooney/blood-cells

## Project scope
This project was a proof-of-concept for utilizing CNNs for detection of WBC cell types using image input data.
