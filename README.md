# Data-Analysis-Using-Map-Reduce
Titanic-Data-Analysis-Using-Map-Reduce

# 1. Data Set Description

Passenger ID
Status (survived=0 & died=1)
Passenger class
Name
Sex
Age
Dispatch
Parch
Ticket
Amount
CabinNumber
EmbarkNumber

Input file is Comma separated file.
# 2. Finding Average age of people with gender who died.
Total Number of columns in the Dataset is 12 and minimum 6 columns should be present to be considered for the analysis
## Mapper Logic:
### Output Key : Gender | Output Value : Age
1. Input Key to the Mapper would be LongWritable(file offset) and Input Value would be text (row of file)
2. Output key of the Mapper would be Gender(Text Format) and output value would be Average age (IntWritable/FloatWritable)
3. Converting entire Mapper Input Value into string and splitting with delimiter as "Comma"
4. If length of total number of columns is greater than 6 and if "Age" is numeric , then Gender is sent as Key and Age as Value

