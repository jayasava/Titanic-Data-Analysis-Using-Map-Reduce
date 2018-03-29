# Data-Analysis-Using-Map-Reduce
Titanic-Data-Analysis-Using-Map-Reduce

# Data Set Description

Passenger ID|
Status (survived=0 & died=1)|
Passenger class|
Name|
Sex|
Age|
Dispatch|
Parch|
Ticket|
Amount|
CabinNumber|
EmbarkNumber

Input file is Comma separated file.
## Case 1 :Finding Average age of people with gender who died.
Total Number of columns in the Dataset is 12 and minimum 6 columns should be present to be considered for the analysis
### Mapper Logic:
#### Output Key : Gender | Output Value : Age |
1. Input Key to the Mapper would be LongWritable(file offset) and Input Value would be text (row of file)
2. Output key of the Mapper would be Gender(Text Format) and output value would be Average age (IntWritable)
3. Converting entire Mapper Input Value into string and splitting with delimiter as "Comma"
4. If length of total number of columns is greater than 6 and if person died , then Gender is sent as Key and Age as Value

### Reducer Logic:
#### Input Key : Gender | Input Value : Age | Output Key : Gender | Output Value : Average Age |

Calculating the sum of ages for each entry and dividing it by total number of entries


## Case 2 :Finding total number of Survived people by class and gender
Total Number of columns in the Dataset is 12 and minimum 6 columns should be present to be considered for the analysis
### Mapper Logic:
#### Output Key : Gender and Class(Composite Key) | Output Value : 1 |
1. Input Key to the Mapper would be LongWritable(file offset) and Input Value would be text (row of file)
2. Output key of the Mapper would be Gender and class together as a Composite Key (Text Format) and output value would be 1 (IntWritable)
3. Converting entire Mapper Input Value into string and splitting with delimiter as "Comma"
4. If length of total number of columns is greater than 6 and if person survived, counting it as one entry by sending "Gender + class" as key and 1 as value

### Reducer Logic:
#### Input Key : Gender + Class| Input Value : 1 | Output Key : Gender + Class | Output Value : Count of survived |

Calculating the sum of entries for each unique class and Gender and returning the count of Total survived people.
