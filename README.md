![CS121 Banner](images/CS121-BANNER.svg)
# Module 6 Lab Guide (part 2)
[Lab Introduction Video](https://boisestate.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=f55e35f5-97ca-4a07-b4bd-ae290012b26e&start=0)  

## Lab Activity 2 - MonitoringStation
### Problem Description
The USGS maintains a large number of monitoring stations on rivers around the country. These monitoring stations collect sample data on a wide range of metrics, including flow rate. In this activity we will create a class to represent a monitoring station. Each MonitoringStation class will include a StationID, a Description and a collection of  Observations. These observations will be stored internally as an ArrayList of FlowSample objects and a single station may contain thousands or 10s of thousands of individual FlowSample observations.

A number of text files containing tab-delimited USGS water flow data collected at the Glenwood Bridge on the Boise River have been provided. The comments and header rows have been removed to make processing these files easier.  The program should prompt the user to enter a Station ID, Station Description and a File Name.  It will then create a new Monitoring Station object and populate it with data from the provided text file.  Finally, it will display in the console the Monitoring Station information, including the number of samples loaded. For development purposes, it will also print each of the FlowSample objects by calling their respective toString() methods. 

### Program Design
Please copy FlowSample.java from the FlowSampleParser activity into the MonitoringStation folder. This will allow us to take advantage of the FlowSample functionality we implemented in the earlier activities.
#### Instance Variables
The MonitoringStation class should contain three private instance variables to represent the required data as shown below:
- **String:** stationID, description
- **ArrayList\<FlowSample\>:** observations
  
#### Constructor
When a new Monitoring Station object is created, the constructor should assign values to the stationID and description instance variables and it should instantiate a new (empty) ArrayList of observations. The constructor should have the following signature:

```
public MonitoringStation(String stationID, String description)
```

#### Other Methods
The MonitoringStation class should include a method called loadSampleData() that reads lines of TSV sample data from a specified file, creates FlowSample objects from each and addes them to the Observations ArrayList. The FileEcho example from the previous module is an excellent reference on how to read lines from a File. Use the javadoc comment below to implement the required functionity.  
```
/**
 * Read tab deliminated water flow data from specified TSV database file
 *    where each line in the file represents exactly one flow sample. 
 *    For each line, create a new FlowSample object and add it to the
 *    observations ArrayList. As each sample is added, increment a counter
 *    to track the total number of observations. When all flow samples
 *    have been processed, return the sample count.
 * 
 *    If a FileNotFoundException occurs when opening the database File
 *    with a Scanner object, display the following error in the console
 *    and return a sampleCount of zero.
 *
 * @param database File object containing TSV formatted water sample data
 * @return Number of samples processed
 */
public int loadSampleData(File database) {...}
```

The MonitoringStation class should include a method called displayObservations() that will loop through the FlowSample objects in the observations ArrayList, calling the toString() method on each and displaying the String value in the console. Use the javadoc comment below to implement the required functionity.  
```
/**
 * Display all of the FlowSample objects in the observations ArrayList 
 *     in the console, by calling toString() on each sample object 
 *     and displaying the resulting String value using println(). Count
 *     the number of items displayed and return this value to the caller.
 * 
 * @return Number of samples displayed
 */
public int displayObservations() {...}
```

The MonitoringStation class should include a toString() method that will return a String that contains a nicely formatted representation of the class information.  Use the javadoc comment below to implement the required functionity.  
```
/**
 * Return a String representation of the current MonitoringStation object
 *     using the following template:
 * 
 *     StationID: <stationID>
 *     Description: <description>
 *     Number of Observations: <number of observations>
 * 
 * @return String value representing this MonitoringStation object
 */
public String toString() 
```
#### Driver Class
In the main() method of the MonitoringStationDriver class, use a Scanner to prompt the user to enter a StationID, Description and Filename of text file contain tab-delimited sample data.  Check if the file exists (and is a file) and if it does not, display an error message and prompt the user again.

Use the user supplied StationID and Description to create a new MonitoringStation object.  Then call the loadSampleData() method to populated the MonitoringStation with data. Store the return value to a variable and display a message in the console stating that it successfully loaded N samples. Call the displayObservations() method on the MonitoringStation to display the sample data in the console.  Finally, call the toString() method on the MonitoringStation and display the returned String value in the console as a summary of the MonitoringStation. The examples below show the expected output for a couple different datasets.

NOTE:  You are welcome to copy LabUtility.java class we created in the previous module and use the LabUtility.getFile() static method we created in that lab. You wrote it and one of the priciples of object oriented programming is code reuse. :)

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-1.tsv
Successfully loaded 1 samples

------------------------
| Station Observations |
------------------------

### USGS - 13206000 ###
Timestamp: Thu 30 Dec 2021 09:30:00 PM UTC
Flow Rate: 226.0


---------------------
|  Station Summary  |
---------------------
StationID: 13206000
Description: Glenwood Bridge on Boise River
Number of Observations: 1
```

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-3.tsv            
Successfully loaded 3 samples

------------------------
| Station Observations |
------------------------

### USGS - 13206000 ###
Timestamp: Wed 05 Jan 2022 08:30:00 AM UTC
Flow Rate: 231.0


### USGS - 13206000 ###
Timestamp: Wed 05 Jan 2022 10:45:00 AM UTC
Flow Rate: 249.0


### USGS - 13206000 ###
Timestamp: Wed 05 Jan 2022 12:45:00 PM UTC
Flow Rate: 261.0


---------------------
|  Station Summary  |
---------------------
StationID: 13206000
Description: Glenwood Bridge on Boise River
Number of Observations: 3
```

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-day.tsv            
Successfully loaded 96 samples

------------------------
| Station Observations |
------------------------

<-- removed for clarity --->

---------------------
|  Station Summary  |
---------------------
StationID: 13206000
Description: Glenwood Bridge on Boise River
Number of Observations: 96
```

The following demonstrates the expected error handling behavor for missing for missing files.
#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: missing.tsv
Error: File does not exist.
Please enter the filename: GlenwoodBoise1.tsv
Error: File does not exist.
Please enter the filename: glenwood-boise-1.tsv
...
```

### Implementation Guide
1. Expand the folder named MonitoringStation, copy FlowSample.java from the FlowSampleParser activity and open MonitoringStation.java and MonitoringStationDriver.java
2. Design a program to satisfy the requirements in the Problem Description and Program Design sections
3. Test the program using the sample user input and compare against the expected output. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Lab Activity 2 is completed.
5. Push the changes from your local repository to the github classroom repository.
6. Take a break, you've earned it!  :)

## Lab Activity 3 - RiverFlowStats
### Problem Description
When we have a large collection of data it is often desirable to be able to generate statistical information about the data in aggregate. In this activing we are going to extend our MonitoringStation class to provide the following statistics over the observation data:
- Max Flow Rate
- Min Flow Rate
- Avg Flow Rate
- Number of Samples

There is obviously a lot more we could do with our collection of FlowSample data, but these should be sufficent for our purposes. :)  

### Program Design
Please copy FlowSample.java and MonitoringStation.java from the MonitoringStation folder into the RiverFlowStats folder. This will allow the reuse of these classes.  Use the javadoc comments below to implement four additional methods in the MonitoringStation class.

```
/**
 * Iterate through the ArrayList of FlowSample objects and maintain a reference to the
 *    FlowSample object with the highest flow rate value. If a FlowSample with a higher 
 *    flow rate is found, update the reference to point at the higher object. Once the
 *    the entire collection of observations has been processed, return the reference to 
 *    FlowSample object with the highest flow rate. 
 *
 *    If a FlowSample is found with the same flow rate as the current highest flow rate,
 *    do not update the reference.
 *    If the ArrayList of observations is empty, return null
 *
 *    @return Reference to FlowSample object containing the highest flow rate value
 */   
public FlowSample getMaxFlowRate() {...}
```

```
/**
 * Iterate through the ArrayList of FlowSample objects and maintain a reference to the
 *    FlowSample object with the lowest flow rate value. If a FlowSample with a lower 
 *    flow rate is found, update the reference to point at the lower object. Once the
 *    the entire collection of observations has been processed, return the reference to 
 *    FlowSample object with the lowest flow rate. 
 *
 *    If a FlowSample is found with the same flow rate as the current lowest flow rate,
 *    do not update the reference.
 *    If the ArrayList of observations is empty, return null
 *
 *    @return Reference to FlowSample object containing the lowest flow rate value
 */   
public FlowSample getMinFlowRate() {...}
```

```
/**
 * Iterate through the ArrayList of FlowSample objects to calculate the average flow rate
 *    for the set of observations.  Return this value as double to the caller
 *
 *    If the ArrayList of observations is empty, return 0.0
 *
 *    @return Average flow rate
 */   
public double getAvgFlowRate() {...}
```

```
/**
 * Return the total number of FlowSample observations
 *
 *    @return Total number of FlowSample observations for this Monitoringstations
 */   
public int getNumSamples() {...}
```

In the main() method of the RiverFlowStats class, use a Scanner to prompt the user to enter a StationID, Description and Filename of text file contain tab-delimited sample data.  Check if the file exists (and is a file) and if it does not, display an error message and prompt the user again.

Use the user supplied StationID and Description to create a new MonitoringStation object.  Then call the loadSampleData() method to populated the MonitoringStation with data. Store the return value to a variable and display a message in the console stating that it successfully loaded N samples. 

Use the getMaxFlowRate() and getMinFlowRate() methods to get references to FlowSample objects for the respective values. Then call the toString() method on each and display the resulting String data in the console.

Use the getAvgFlowRate() and getNumSamples() methods to get double and int values (respectively) and display them with appropriate label in the console. Use the DecimalFormat class to format the double value to 4 decimal places.

The examples below show the expected output for a the years 2000, 2010 and 2020.

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Boise River at Glenwood Bridge - 2000  
Please enter the filename: glenwood-boise-2000.tsv
Successfully loaded 32153 samples

---------------------
|  Max Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Wed 19 Apr 2000 10:30:00 AM UTC
Flow Rate: 3870.0

---------------------
|  Min Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Tue 08 Feb 2000 11:00:00 PM UTC
Flow Rate: 188.0

---------------------
|  Avg Flow Sample  |
---------------------
Average Flow: 818.5974

---------------------
| Number of Samples |
---------------------
Sample Count: 32153
```

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Boise River at Glenwood Bridge - 2010    
Please enter the filename: glenwood-boise-2010.tsv
Successfully loaded 34453 samples

---------------------
|  Max Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Sat 12 Jun 2010 01:30:00 AM UTC
Flow Rate: 6000.0

---------------------
|  Min Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Mon 29 Nov 2010 10:00:00 PM UTC
Flow Rate: 133.0

---------------------
|  Avg Flow Sample  |
---------------------
Average Flow: 729.3648

---------------------
| Number of Samples |
---------------------
Sample Count: 34453
```

#### Expected Program Output (with sample user input)
```
---------------------
|   Station Setup   |
---------------------
Please enter the station id: 13206000
Please enter the station description: Boise River at Glenwood Bridge - 2010
Please enter the filename: glenwood-boise-2020.tsv
Successfully loaded 35135 samples

---------------------
|  Max Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Thu 30 Apr 2020 04:45:00 PM UTC
Flow Rate: 1000.0

---------------------
|  Min Flow Sample  |
---------------------
### USGS - 13206000 ###
Timestamp: Fri 20 Mar 2020 08:00:00 PM UTC
Flow Rate: 168.0

---------------------
|  Avg Flow Sample  |
---------------------
Average Flow: 471.6461

---------------------
| Number of Samples |
---------------------
Sample Count: 35135
```

### Implementation Guide
1. Expand the folder named RiverFlowStats, copy FlowSample.java and MonitoringStation.java from the MonitoringStation folder, then open MonitoringStation.java and RiverFlowStats.java.
2. Design a program to satisfy the requirements in the Problem Description and Program Design sections
3. Test the program using the sample user input and compare against the expected output. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Lab Activity 3 is completed.
5. Push the changes from your local repository to the github classroom repository.
