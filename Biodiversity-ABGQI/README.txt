Project: Biodiversity-ABGQI Classification
Authors: Kathy Y., Justin B., and Darien L.
Date: 12/15/2023
Class: CS 479 Computer Vision
Instructor: Dr. Gill

--- ABOUT ---

The files contained within this folder are intended to be used to demonstrate 
and replicate the data gathered in the attached PowerPoint Presentation. There
are some required setup in order to ensure that these files can work together.
Provided below are some instructions that may help/allow for a reader to have a
better understanding of how to work with the code provided.

--- Files/Folders Provided ---

- "1min_predictions" is a folder containing all of the CSVs output by the 
original model containing predictions on each of the 5 classes.
- "1min_spectrograms" is a folder contianing all of the spectrogram images of 
the 1 minute wav files.
- "code" is a folder containing all the code used to run this project.
- "ABGQI-CNN" is a folder containing the CNN model of Colin's code.

- "ABGQI_prediction.ipynb" is a Jupyter Notebook that is used to generate CSV
files that contain predictions for each melspectrogram provided.
- "Histogram_and_Confusion_Matrix_Creation.ipynb" contains the python code that
is used to create histograms for comparing each 1 minute prediction against its
corresponding label as well as a confusion matrix for each class.
- "melspec_functions.py" is a python script that contains the functions for
generating melspectrograms in melspec_generation.ipynb.
- "melspec_generation.ipynb" is a Jupyter Notebook that is used to generate
melspectrograms for provided WAV files at either the full length of the WAV
file or at 2 second intervals.
- "SVM_predictions.ipynb" is a Jupyter Notebook that uses Colin's CNN model as
a feature extractor to train the ABGI SVMs.

- "arbimon_soundscape_composition_date_sorted.xlsx" is the date sorted CSV file
that is used to create the labels needed for SVM generation.
- "labeled_data.csv" is the CSV containing all of the labeled data on each of 
the 1 minute wav files.


--- Help with Comparison Histograms/Confusion Matrices Code ---

Using the file, "Histogram_and_Confusion_Matrix_Creation.ipynb" requires that 
you connect your google drive if you are using Google Colab. If you are instead
utilizing Jupyter Notebook to view and run the code, ensure that the second 
cell is commented out (as to not access a google drive) and that the third code
cell at the beginning contains the correct directory path to where you have 
locally stored the CSVs containing the model predictions. If you are using 
google colab and thus the files are stored in your google drive, the path will
still need to be corrected to where in your drive they are located. The 
"/content/drive/" accesses the local data in the colab program, inside the 
drive folder, after having mounted your drive with the second code cell, is 
where you can add the path to where you have the CSVs stored. Further more, in
both the cases of using Google Colab and Jupyter Notebook, you need to update 
the directory names for the following variables: 
- "csv_dirs" which gathers the prediction CSVs output by the CNN model. 
- "labeled_csv_dir" which is the location of the CSV containing the labeled 
data on all of the CSV data. 
- "results_csvs_dir" is the location where the histograms will be output to. 
This location can be whereever you wish to output them.
- "result_confusion_dir" is the location of where the Confusion Matrices are 
output to. This location can be whereever you wish to output them.
- "spec_dir" is the location of the spectrogram images to be used in 
conjunction with the histograms.

Note: Ensure that the result directories are already created before running 
the code.

--- Help with SVM Model Code ---

The SVM model code will take the melspecs that you provide it in data_path
and use those with the respective labels in a CSV file column that you
specify to train the SVM from the extracted features of Colin's CNN model.
There are four SVMs, anthropophony, biophony, geophony, and interference.
The data is split into 60% train and 40% test data for each SVM and the
resulting confusion matrices are outputted. The accuracy percentages are
also displayed at the bottom of the notebook.


--- Help with YAMNet Model Code ---

Using the YAMNet code is quite simple, in fact it can run as is without the 
need to change anything. The only point of note is if you wish to use noise
reduction. The noise reduction allows for slightly better results as it 
preprocesses the data by cutting out excess noise that is not meant to be part
of the main audio. More specifically, heavy background noise can often be 
missclassified by the YAMNet model and thus it is recommended to be used, 
however, it is by no means required to run the model and thus can be removed 
should that be desired.
