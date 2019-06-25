Data Science Final Project - Wine Classifier

This file goes over how the program works. One remark to be made is that I am relatively new to python, and so, some of the blocks of code or operations will not be optimal. I tried putting many comments to explain what I was doing when I wrote those lines. I also would like to acknowledge Gilman Callsen for having helped me debug some of the scraping code. 

Aside from this README file, the Final Report also contains more detailed information on this project. Additionally, a requirements.txt was created using pip freeze. There is a chance that some packages might be missing, since pip freeze only copies versions of the packages that have a pip install command. 

BEGINNING OF THE CODE:

- Importing Packages: 

The first block of code imports all the necessary packages used in the project. Their uses are separated by comment lines. The kernel uses Python 3, Python 3.6.8 :: Anaconda, Inc.

I also used the markdown mode in the jupyter notebooks to make observations/remarks about the project and the important aspects of the information being used in this program. For example, the wine technical data sheet image is an illustration of what the PDF documents that were scraped look like. However, this data was not used in the project.

- Scraping Data: 

The main website used for data collection had protection against scraping, which is why the Request package was used - creating an agent and using Mozilla as the access browser. Once that was implemented, there were no apparent errors running the scraper portion of the code. However, different computers/operational systems, may create problems. In the case that errors occur, the Final Report contains the results and some screenshots of the data frames produced during the project. 

The link to the website used for scraping can also be accessed through this link:
http://minerwines.com/trade-and-media/data-sheets/

- Downloading/Reading Files:

In order to extract data from PDF's, the files are download and saved to the current directory. One of the features of the download_file function is that it always saves the file as "document.pdf", which means that only the last PDF file remains saved in the directory. Once the code if done compiling, the document can be moved to trash, since the data is already saved in the data frames.

One downside of the download_file function was that I was unable to include cache tools that would allow the data to be stored in memory - making running the code a second time much faster. 

Some files failed the download, which is why I included a try/except loop that adds the faulty files to a list called del_list. All data files are kept in a list called wine_list. Once the faulty files were identified, I deleted their respective links from the main wine_list.

- Obtaining Data:

Using text string slicing, a function was created to obtain the alcohol content, the pH and the TA values from the PDF files. The parameters used for this function refer to the number of characters. Feature len means the number of characters required to write the feature plus a space. Data len means the number of characters required to write the numerical data plus the period for decimal values. On the Final Report, this function is further explained with a respective summary of the parameters and the numbers used for the program. 

- Data Exploration:
 
In order to handle missing data, the pandas package was used to address NaN - not a number - values. Two functions were considered: dropna() and fillna(method=ffil). For the first one, NaN cells are removed from the data frame, therefore reducing the number of data points. The ffill method uses the last numerical value to fill NaN cells, maintaining the same amount of data points as the original data frame. New data frames were created for each method so that further data investigation could be conducted.

- Machine Learning (ML) Models:

For the ML models, scikit learn was used to facilitate setting the classifiers, separating test and train data, fitting the model and predicting the outputs. From the scikit learn cheat sheet for choosing a model, Linear SVC and KNN were selected for this program. The results were stored in lists and plotted for visualization. For the Linear SVC there was a warning message about the number of iterations being used. The model expected the number of iteration to be quite high. The initial number of iterations selected for the program was 10.000 iterations.

- Database:

For the database integration at the end of the code, sql_lite was used, which is a simplified version of the SQL database. The sql_lite holds information at memory. For this project, the number of data points is very small. Therefore, using sql_lite is not a problem and causes no errors. 





