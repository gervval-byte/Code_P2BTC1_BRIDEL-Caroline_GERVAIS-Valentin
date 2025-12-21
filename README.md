Authors: Gervais Valentin & Bridel Caroline
Group: Pré Ing 2 BTC groupe 1

This Python application automates the processing of biological data regarding the effect of antibiotics (ABX) on gut microbiota in mice. The script processes raw CSV data to generate:
1.  Formatted CSV files containing only relevant data for analysis.
2.  Graph showing the evolution of fecal bacteria over time.
3.  Violin plots comparing bacterial load in cecal and ileal contents between ABX and Placebo groups.
The application automatically organizes the output into a structured project folder.

Prerequisites
To run this application, you need Python 3 installed on your machine.
You also need the `matplotlib` library for data visualization.

How to use 
1. Launch the script : Run the Python file from your terminal or IDE.
2. Select the Source File : A file dialog window will open. Select the raw CSV data file 
3. Select the Destination Folder : A second dialog window will open. Choose the folder where you want the project directory to be created
4. Processing : The script will create a folder named Projet_Gervais_Valentin_Bridel_Caroline. A progress indicator will appear in the console showing the estimated time remaining based on the number of mice
5. Results : Once finished, navigate to the created folder to find:
              input : A copy of your original CSV file
              output : Three CSV files (fecal, cecal, ileal) with extracted and formatted data necessary to draw graphs
              images : Generated plots (outfecal.png, outcecal.png, outileal.png)

Functional Scope & Limitations
1. Implemented Features
Dynamic Folder Creation : Automatically creates the required directory structure (input, output, images).
Data Extraction : Correctly isolates Mouse_ID, Treatment, Area, X (Time/Group), and Y (Log10 of bacteria).
Visualization : Line plots for Fecal data (Time course).
                Violin plots with scattered data points for Cecal and Ileal data
User Interface: Uses tkinter for easy file selection instead of manually written paths
2. Limitations and Known Issues
The application fulfills the project requirements, but the following limitations exist:
Performance Optimization (Time Complexity): The current algorithm iterates through the entire source file for each mouse ID identified and does not save information in a dictionnary
                                            For small datasets, the execution time is acceptable. However, for very large datasets, the processing time would increase significantly and exponentially
Input File Rigidity: The script strictly expects the CSV columns to be in a specific order and won't work if the input CSV structure changes (the script will extract incorrect data or eventually crash)
                     The script also don't work for any other mouth name that would'nt start with ABX and if the treatment is not placebo and ABX
                     Lack of Error Handling for Data Types: Inside data_extraction, the script directly cast values: vx=int(data[7]) and vy=math.log10(float(data[8])) and if a cell in the CSV contains text instead of a number, the script will crash immediately
Statistical Analysis: The application generates visual comparisons but does not perform mathematical statistical tests for the user to confirm if the differences between ABX and placebo
Image Saving Strategy: Currently, the fecal plot image is saved at the very end of the process to optimize performance. Real-time visualization during processing is disabled to save resources and time











