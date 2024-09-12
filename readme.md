### Business Understanding

Business objective 
1. what factors make a car more or less expensive
2. what consumers value in a used car

Data Task:
1. Feature or List of Features influencing the price of a car
2. Attributes that consumers prioritize when purchasing a used car

As per the problem statement, we can have to two high level objectives, First one create a model which will list attributes which contribute to the price of the car and second one which is not very clear from the data is cutomers prioritization, as the current data does not capture sale information like which cars got sold, what was bench time and what was customer ratings post purchase. We can combine both the objectives and create model assuming higher the price higher the customer priority when purchasing the used cars 


### Data Understanding
1. Plot  bar graph to check count of null values for each attribute 
2. VIN should be unique for each car, drop duplicate vin records
3. Plot mean price of each car make hue by year
4. Check values of each field and their counts
5. Boxplot to check how the data is distributed

The years are spread out from around 1960 to 2020.
There are several outliers before 1960, indicating that these years are significantly different from the rest of the data.

For car sales from 1900 t0 1960, we can do separate analysis as vintage car sales. We can get set of different attributes which may impact vintage car prices compare the regular cars

This is from internet, want to check what information does VIN can help us with
https://www.autocheatsheet.com/used-car/vin-decoder.html

A Vehicle Identification Number (VIN) is a unique 17-digit code assigned to every motor vehicle when it’s manufactured. This code serves as the car’s fingerprint, providing a wealth of information about the vehicle. Here’s a breakdown of what a VIN can tell you:

Country of Origin: The first digit indicates where the car was manufactured.
Manufacturer: The next few digits identify the manufacturer and the vehicle type.
Vehicle Details: Subsequent digits provide information about the vehicle’s model, body type, engine type, and more.
Check Digit: This digit is used to verify the accuracy of the VIN.
Model Year: Indicates the year the vehicle was manufactured.
Assembly Plant: Shows where the vehicle was assembled.
Serial Number: The last few digits are the vehicle’s unique serial number

We can use the above data to fill some of the missing data, for example Year has around 1.2K missing entries. 
We can extract the Model year from the above and fill, as the missing values are very less compare to overall data.

### Data Preparation

1. All the ids are unique there is no duplicates -- Drop Id's
2. Drop duplicate VIN 
3. Drop cars which are manufactured before 1960, price not in 1000,240000
4. Try to fill the missing fields using VIN 
    a. convert Year to interger and fill missing values with 0
    b. use vininfo package and fill year
    c. use vininfo package and fill manufacturer 
5. Drop rows which has null values 
6. categorical attributes which can be converted numerical
    a. Use label encoding where there is ordinal relationship
    b. Use one-hotcode encoding for the rest
6. drop row with nulls
    year, transmission,fuel,odometer,model,title_Status and manufacturer
7. Drop column size vin
   cylinders, drive , condition paint color -- has arond 120K missing records 
   if we have time, we can take only this data and create models including 

We have categorical attributes which can be converted numerical 
type, paint_color, drive,VIN,condition,cylinders,size 
Regions are very vast, we can map to standard regions 
There and null values, we can plot graph and see null counts for each attribute
We see cylinders, has number and text, we can remove the text and keep only number or label encoding
ordinal relationship between the categories we can use label encoding 
Condition 



### Evaluation

With some modeling accomplished, we aim to reflect on what we identify as a high quality model and what we are able to learn from this.  We should review our business objective and explore how well we can provide meaningful insight on drivers of used car prices.  Your goal now is to distill your findings and determine whether the earlier phases need revisitation and adjustment or if you have information of value to bring back to your client.

Linear Regression model has performed the best as the comparision for different modeling algorithms. 


### Deployment

Now that we've settled on our models and findings, it is time to deliver the information to the client.  You should organize your work as a basic report that details your primary findings.  Keep in mind that your audience is a group of used car dealers interested in fine tuning their inventory.

Feature  Importance       Std
0                 year    0.329748  0.002694
2            cylinders    0.226934  0.001949
4             odometer    0.166633  0.002019
7                 type    0.109966  0.001502
6                drive    0.026850  0.000482
3                 fuel    0.019414  0.000487
9           region_map    0.012623  0.000348
5         transmission    0.005876  0.000357
10  manufacturer_freqs    0.003991  0.000253
8          paint_color    0.002565  0.000156
1            condition    0.000698  0.000120


 