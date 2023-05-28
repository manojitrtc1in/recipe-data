# RECIPE Data
Benchmark Dataset created for the Paper "RECIPE: A Vehicle RECall Incident PrEdiction Method"

CarComplaints.com is an online automotive complaint platform that shows automotive defect patterns, based on complaints submitted by consumers. The complaints are organized into groups with associated metadata such as vehicle, vehicle component, and specific problem.
% we develop our benchmarking consumer car complaints dataset from this website in the following two steps. 

## Data Crawler
We create a data crawler on carcomplaints.com using python framework. The following method is used to parse the website to collect data.
- Collect all names of car manufacturers, i.e., MAKE from the website. (e.g. TOYOTA)
- For each MAKE, extract all MODEL names. (e.g. TOYOTA CAMRY)
- For each MODEL name, collect all the YEAR in which the that particular model is manufactured. (e.g. TOYOTA CAMRY 2005)
- Now, for each (MAKE, MODEL, YEAR) of a vehicle, collect all the COMPONENT names for which a complaint has been registered. (e.g. ENGINE)
- For each COMPONENT name, extract the types of PROBLEM CLASS of registered complaints. (e.g. SMOKING ENGINE)
- Using the information extracted above, for each instance of (MAKE, MODEL, YEAR, COMPONENT, PROBLEM CLASS), collect all complaint texts and their respective dates.

## Data Processing

Crawled data from carcomplaints.com is processed as a list of data instances, where each instance is prepared using the structure [MAKE, MODEL, YEAR, COMPONENT, PROBLEM CLASS, COMPLAINT TEXT, YEAR]. Below is an example of data instance from the benchmarking dataset.

- Make : Volvo
- Model : 240
- Year : 1992
- Component : exhaust_system
- Problem Class : /Volvo/240/1992/exhaust_system/whining_sound
- Complaint Text : I paid \$475.00 so far for catalytic converter replacement, but still have the same whining sound upon acceleration, especially uphill. Any advice?
- Year : Nov 122003(reported on)

## Dataset Usage

Unzip the file "RECIPE-data.zip" to find the pickle file "RECIPE-data.pkl".
Use the following code to read the dataset. 
```
import pickle
f=open("RECIPE-data.pkl","rb")
data=pickle.load(f)
```
Data will be a list of lists, where each list will be [MAKE, MODEL, YEAR, COMPONENT, PROBLEM CLASS, COMPLAINT TEXT, YEAR]
