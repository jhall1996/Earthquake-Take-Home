# Earthquake-Take-Home

Environment Setup: 

You can load the Jupyter Notebook file into a suitable environment, such as a local Jupyter Notebook locally or any other Python IDE that supports Jupyter. I used Google Colab to develop the solution. 
Within Colab, the Python libraries are pre-installed. If you are using a different solution you may need to run a pip install.
'pip install pandas matplotlib spacy numpy'  


Data:

The data I used was collected on Friday 9th August from the USGS website via the following link:
https://earthquake.usgs.gov/earthquakes/search/
I selected the data from the past 30 days, saved the results as a CSV file, and loaded them into this GitHub repository.


Step 1: Identify the country/territory with the most earthquakes in the last 30 days.

I loaded the data into my notebook and displayed it as a Pandas data frame. I noticed that the 'place' column, which describes the earthquake location, lacked a consistent naming convention for countries/territories. Many entries described a distance from a specific location, while others named only the country (e.g., "Fiji region").

I decided to explore using Natural Language Processing to simplify the countries into a consistent format. After researching the Python libraries available, I decided to use the Spacy NLP model. This model analysed the text and could extract a Geopolitical Entity (GPE). 

However, the results were inconsistent, with some entries being region-specific (e.g., "Pāhala, Hawaii") and others naming only the country. To address this, I removed text before the final comma, leaving just the country or state name.


This allowed me to identify a country/territory with the highest number of earthquakes, which in the case of the data I used was Hawaii. Were I to run through this process again, I would want to explore a way of standardising the data to more specific regions as my solution doesn't account for the variability of regions that make up a country/territory. One of the options I looked at was, Geopy a Python Reverse Geocoding library. However, initial research suggested that this solution would be subject to API keys/service limitations so I opted to go with NLP as a first solution. 


Step 2: Step 2: Find the top 3 locations with the highest magnitude earthquakes in the last 30 days, sorted by timestamp (descending).

This was straightforward. I sorted the original 'place' column by magnitude and timestamp (in descending order) to identify the top three locations with the highest magnitude earthquakes.


Step 3: Investigate the data to determine which criteria to use in the evaluation of countries which are the highest risk to insure. We will continue to work with the filtered data frame.

I conducted exploratory analysis to better understand the data, including creating a histogram of earthquake magnitudes and a scatter plot of earthquake depth vs. magnitude. The scatter plot revealed no correlation between magnitude and depth.

Step 4: 

I made the judgement that the frequency of earthquakes would be a critical factor for which locations would be the riskiest to insure. I filtered out the top 10 locations that experienced the highest number of earthquakes (using the locations grouped via Spacy). The magnitude and depth of the earthquakes they experienced would also be an important consideration, therefore I identified the average depth and magnitude of the top 10 locations. 

To visualise the data, I plotted a scatter graph with average depth represented by marker size. The results clearly showed that the riskiest locations to insure are Fiji, the Philippines, and Indonesia/Japan. I further validated this by applying a basic weighting system to calculate a risk score, giving more weight to average magnitude and depth. This confirmed Fiji, the Philippines, and Indonesia as the three riskiest locations to insure.


Considerations for Further Analysis

Depth of Earthquakes:

Depth is an important factor when evaluating earthquake risk. Earthquakes can be categorised as shallow (0–70 km deep), intermediate (70–300 km deep), or deep (300–700 km deep). Shallow earthquakes, in particular, can cause significant damage due to their proximity to the Earth's surface.
In future analyses, I would consider filtering out extremely shallow earthquakes as they could inflate the number of earthquakes in high-frequency areas without contributing significantly to risk. Small, shallow earthquakes might occur frequently but may not be as damaging as deeper, stronger ones.

Magnitude Considerations:

Not all earthquakes are necessarily likely to cause damage. Lower-magnitude earthquakes might be less of a concern from an insurance risk perspective.
A potential refinement could involve setting a magnitude threshold to exclude lower-magnitude earthquakes that are unlikely to cause significant damage, thereby focusing the analysis on more impactful events.

There is also inconsistency in the magnitude type across the data which could affect the accuracy of the analysis. Standardising these magnitude types or exploring converting them to a common scale could help make more reliable comparisons. However, this inconsistency did not affect the results in Step 2 for the three areas with the highest magnitude recorded, as they all demonstrated the same magnitude type. 

Socioeconomic Factors:

The potential damage from an earthquake is not only a function of its magnitude and depth but also of the infrastructure, population density, and preparedness of the affected area.
Further investigation into these factors could enhance the risk assessment, providing a more comprehensive view of which locations are truly the riskiest to insure, though this is beyond the scope of the dataset supplied from USGS. 

