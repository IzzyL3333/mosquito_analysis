# Data Analysis on Mosquito Data 🦟
This exercise aimed to provide valuable, data-derived insights into mosquito data as they largely spread West Nile Virus (WNV). As a Data Scientist, I performed basic EDA, data wrangling, and data analysis using real mosquito data. The following work and results are a sample of the analysis conducted with my technical skills.

## Table of Contents
- [Data](#data)
- [Work](#work)
- [Results](#results)
- [Future Considerations](#future-considerations)

---

<a id="data"></a>
### Data :books:
The data was originally sourced from the open data portal at the <a href="https://www.chicago.gov/city/en/depts/cdph/supp_info/infectious/west_nile_virus_surveillancereports.html" target="_blank">City of Chicago</a>. 

The data consisted of one table of mosquito populations and WNV prevalence using a series of traps. 

**Table: mosquito**
|Column Name| Description|
|---|---|
|`Year`|Year that the WNV test is performed|
|`Week`|Week that the WNV test is performed|
|`Address Block`|Address of the location of the trap.|
|`Block`|Block number of address|
|`Trap`|Id of the trap|
|`Trap type`|Type of trap|
|`Date`|Date and time that the WNV test is performed|
|`Mosquito number`|Number of mosquitoes caught in this trap|
|`Mosquito ID`|Id for Mosquito species|
|`WNV Present`|Whether West Nile Virus was present in these mosquitos|
|`Species`|Mosquito species|
|`Lat`|Latitude of trap|
|`Lon`|Longitude of trap|

---

<a id="work"></a>
### Work :bar_chart:

Using Python, the following sample questions were answered.

**Cleaning and Exploratory Data Analysis**

<ins>Part 1 - Basic Data Wrangling</ins>
1. What is the shape of the dataframe?
2. Pick two numeric and two categorical columns: What data they are storing? How are they distributed?
3. Are there any columns that contain duplicate information? If so, remove the redundant columns.
4. Are there any null values in the dataframe? If so, deal with them appropriately.
   
<ins>Part 2 Exploratory Data Analysis</ins>
1.  Using an appropriate visual, or visuals, explore the relationship between **mosquito number and date**.
2.  Using an appropriate visual, explore the relationship between **mosquito species and WNV prevalence**.

**Statistical Analysis**

Which columns are positively correlated with the number of mosquitoes caught? Which columns are negatively correlated? Are these correlations statistically significant?

---

<a id="results"></a>
### Results :eyes:

**Cleaning and Exploratory Data Analysis**

<ins>Part 1 - Basic Data Wrangling</ins>
1. The shape of the mosquito dataframe is **18,495 rows** and **13 columns**.
2. Distributions for 2 Numeric Columns and 2 Categorical Columns

![image](https://github.com/user-attachments/assets/7d880b95-6276-48cf-b354-1d6e3d5cecf2)

The following numeric columns are being analyzed to determine what data is being stored and how it is distributed: 
- The **mosquito number** is storing the number of mosquitoes caught in a trap represented by an **int64** data type.
    - The most frequent number of mosquitos being caught is skewed towards the right side of the statistical distribution, specifically **ranging between 1 to 20**. 
    - Despite the distribution being right skewed, the calculated **mean was greater than the median**. This skew can impact what kind of outliers and trends can be identified when catching mosquitos.    
- The **Block** is storing the Block number of address represented by an **int64** data type.
    - The most frequent block number of address trapping mosquitos is on or **close to 100**. 
    - There are **omitted blocks** in this dataframe, ranging within **block 80 and 140**. Additional information and/or research would be recommended to determine why certain block are missing in the dataframe.   
    - The data is **not skewed** towards a certain direction, establishing a challenge to identify anomalies and trends for further analysis. This distribution would be considered **symmetric**. 
    - This symmetric distribution would result in the calculated **mean, median, and mode close to block 50**.
      
![image](https://github.com/user-attachments/assets/a37c60c5-4b0d-4e53-a5b3-318dca48d91e)

The following categorical columns are being analyzed to determine what data is being stored and how it is distributed:

- The **Trap type** is storing the Type of trap represented by an **object** data type.
    - There are 4 unique categories: GRAVID, SENTINAL, CDC, OVI
    - **GRAVID** is the most common trap type used on mosquitos between 2008 and 2019.
    - Future relationship analysis with Trap Type will have GRAVID as the largest sample to compare against other data. 
- The **Species** is storing Mosquito species represented by an **object** data type.
    - There are 4 unique categories: CULEX RESTUANS, CULEX TERRITANS, CULEX SALINARIUS, CULEX PIPIENS
    - **CULEX RESTUANS** is the most common mosquito species caught between 2008 and 2019.
    - Future relationship analysis with Mosquito species will have CULEX RESTUANS as the largest sample to compare against other data.

3. The Mosquito ID and Species columns in mosquitoData store duplicate values. The **Mosquito ID** column was dropped to remove redundancy. The Block and Address Block columns in mosquitoData store duplicate values. The **Address Block** column was removed to remove redundancy.
4. The Nan values appeared in the **Lat** and **Lon** columns. The Nan values were **replaced with the average** of the respective columns.

<ins>Part 2 Exploratory Data Analysis</ins>
1. Relationship between Mosquito Number and Date
![image](https://github.com/user-attachments/assets/8098f465-dded-4df5-a68a-c13ce3c9a582)
![image](https://github.com/user-attachments/assets/d213e2af-e3cd-42ed-8f66-c79a13828d98)
![image](https://github.com/user-attachments/assets/7a1f93b5-e4cd-4f46-9a09-bc327016fd61)

From 2007 to 2019, the most number of mosquitos caught was **over 36,000** in the year **2016**. Broken down further, the month of **August** greatly contributed to the total sum of mosquitos caughts in 2016 with **over 16,000**. The number of mosquitos caught from 2009 to 2012 was steadily increasing. From 2013 to 2019 the trend of mosquitos being caught had significant sudden increases and decreases, notably 2016. A note regarding the data collection is that only months between June and September had mosquitos caught and documented. Further research is recommended to determine why August 2016 caught the most mosquitos between 2007 to 2019.

2. Relationship between Mosquito Species and WNV Prevalence
![image](https://github.com/user-attachments/assets/12ce5e4e-b0a7-41a8-90a9-f7e3d0ead65f)

The chances of West Nile Virus appearing in the Culex Restuans and Culex Pipiens species was over doubled compared to the Culex Territan and Culex Salinarius species. A note regarding the data collection is that once a trap had one moquito tested positive for West Nile Virus, the whole batch is considered positive. Many mosquitos caught could have been tested negative in a batch where only one mosquito was tested positive. Further research should be conducted to determine why the Culex Restuans and Culex Pipiens species is more likely to contain the West Nile Virus than the Culex Territan and Culex Salinarius species.

**Statistical Analysis**

_Which columns are positively/negatively correlated with the number of mosquitoes caught?_

![image](https://github.com/user-attachments/assets/955f1239-ce09-48a1-8959-87d8b5724555)

Columns with positive correlations to mosquitos caught: Year, WNV Present, Lat, Trap_type_CDC, Trap_type_SENTINEL 
- **largest positive** correlation coefficients to mosquitos caught is **WNV Present** with 0.41  
    
Columns with negative correlations to mosquitos caught: Week, Lon, Month, Trap_type_OVI, Trap_type_GRAVID 
- **largest negative** correlation coefficients to mosquitos caught is **Lon** with -0.15

_Are these correlations statistically significant?_ 

- Null Hypothesis: Mosquitos mosquitos has no significant correlation to the column in column_list.
- Alternative Hypothesis: Mosquitos mosquitos has a significant correlation to the column in column_list.

![image](https://github.com/user-attachments/assets/1913d0b7-ccf0-4480-bd18-d69ad06bec8f)

From calculating the p-values of all columns in column_list shown above against Moquito numbers, we can reject all null hypothesis except Trap_type_OVI. 

_Final Findings_

There is a significant positive correlation between Moquito numbers and the following columns: Year, WNV Present, Lat, Trap_type_CDC, Trap_type_SENTINEL. There is a significant negative correlation between Moquito numbers and the following columns: Week, Lon, Month, Trap_type_GRAVID. The pearsonr is inconclusive to determine the significant negative correlation between Moquito numbers and Trap_type_OVI.

--- 

<a id="future-considerations"></a>
**Future Considerations**
- Explore significant differences between the different mosquito species when looking at the occurrence of West Nile Virus.
- Run a linear regression to determine how the independent variables affect the number of mosquitoes caught. 

Thanks for reading! 🦟
