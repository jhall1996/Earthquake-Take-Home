# Earthquake-Take-Home

Environment Setup: 

You can load the Jupyter Notebook file into a suitable environment, such as a local Jupyter Notebook locally or any other Python IDE that supports Jupyter. I used Google Colab to develop the solution. 
Within Colab, the Python libraries are pre-installed. However, if you are using a different solution you may need to run a pip install.
'pip install pandas matplotlib spacy numpy'  

Data:

The data I used was collected on Friday 9th August from the USGS website via the following link:
https://earthquake.usgs.gov/earthquakes/search/
I selected the data from the past 30 days, saved the results as a CSV and loaded them into this GitHub repository.

Step 1: Identify the country/territory with the most earthquakes in the last 30 days.

I loaded the data into my notebook and displayed it as a Pandas data frame. Within the results for the earthquake location (under the column 'place'), it was clear there was no consistent naming convention for the countries/territories. Most results described a km distance from a particular location, but some did not reference a km distance and others named only the country (for example 'Figi region'.

I decided to explore using Natural Language Processing to simplify the countries into a consistent format. After researching the Python libraries available, I decided to use the Spacy NLP model. This model analysed the text and could extract a Geopolitical Entity (GPE). 

I ran the data through the library and viewed the results. The NLP model again provided inconsistent results, in some cases being GPE region-specific (e.g. Pāhala, Hawaii), but in others giving just the GPE country (E.g. Hawaii only). I decided to standardise the data by removing text before the final comma, leaving just the country (or in the US case the state). 

This allowed me to identify a country/territory with the highest number of earthquakes, which in the case of the data I used was Hawaii. Were I to run through this process again, I would want to explore a way of standardising the data to more specific regions as my solution doesn't account for the variability of regions that make up a country/territory. One of the options I looked at was, Geopy a Python Reverse Geocoding library. However, initial requests suggested that this service would be subject to API keys/service limitations so I opted to go with NLP as a first solution. 

Step 2: Step 2: Find the top 3 locations with the highest magnitude earthquakes in the last 30 days, sorted by timestamp (descending).

This was a fairly straightforward solution. I opted to use the original 'place' column to allow for more specific locations within the results. 

Step 3: Investigate the data to determine which criteria to use in the evaluation of countries which are the highest risk to insure. We will continue to work with the filtered data frame.

I undertook some exploratory analysis to better understand the data. This included a histogram showing the frequency of the different earthquake magnitudes recorded, and a scatter graph of Earthquake Depth vs Magnitude. The scatter graph in particular showed no correlation between magnitude and depth.

