# Module 6 Lab Guide (part 2)

## Activity 2 - MonitoringStation (Required)
### Problem Description
The USGS maintains a large number of monitoring stations on rivers around the country. These monitoring stations collect sample data on a wide range of metrics, including flow rate. In this activity we will create a class to represent a monitoring station. Each MonitoringStation class will include a StationID, a Description and a collection of  Observations. These observations will be stored internally as an ArrayList of FlowSample objects and a single station may contain thousands or 10s of thousands of individual FlowSample observations.

A number of text files containing tab-delimited USGS water flow data collected at the Glenwood Bridge on the Boise River have been provided. The comments and header rows have been removed to make processing these files easier.  The program should prompt the user to enter a Station ID, Station Description and a File Name.  It will then create a new Monitoring Station object and populate it with data from the provided text file.  Finally, it will display in the console the Monitoring Station information, including the number of samples loaded. For debugging purposes, it will also print each of the FlowSample objects by calling their respective toString() methods. Your program should behave as shown in the examples below:

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-1.tsv

...
```

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-3.tsv

...
```

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-day.tsv

...
```

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-week.tsv

...
```

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-month.tsv

...
```

#### Expected Program Output (with sample user input)
```
Please enter the station id: 13206000	
Please enter the station description: Glenwood Bridge on Boise River
Please enter the filename: glenwood-boise-year.tsv

...
```

### Implementation Guide
1. Expand the folder named A2-Kennel and create two new files named Dog.java and Kennel.java respectively
2. Design a program to satisfy the requirements in the Problem Description and enter the program code in Dog.java and the driver code in Kennel.java
3. Test the program using the run link above the main method. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Activity 2 is completed.
5. Push the changes from your local repository to the github classroom repository.

## Activity 3 - Bookshelf
### Problem Description
Design and implement a class called *Book* that contains instance data for the title, author, publisher, and copyright date. Define the *Book* constructor to accept and initialize these data. Include setter and getter methods for all instance data. Include a *toString* method that returns a nicely formatted, multiline description of the book. Create a driver class called *Bookshelf*, whose *main* method instantiates and updates several *Book* objects.

### Implementation Guide
1. Expand the folder named A3-Bookshelf and create two new files named Book.java and Bookshelf.java respectively
2. Design a program to satisfy the requirements in the Problem Description and enter the program code in Book.java and the driver code in Bookshelf.java
3. Test the program using the run link above the main method. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Activity 3 is completed.
5. Push the changes from your local repository to the github classroom repository


## Activity 4 - SnakeEyes
### Problem Description
Using the *Die* class from the SnakeEyes folder in the Module 6 examples, design and implement a class called *PairOfDice*, composed of two *Die* objects. Include methods to set and get the individual die values, a method to roll the dice, and a method that returns the current sum of the two die values. Rewrite the *SnakeEyes* program using a *PairOfDice* object.

### Implementation Guide
1. Open the Module 6 code examples and copy Die.java and SnakeEyes.java from the SnakeEyes folder into the A4-SnakeEyes folder.
2. Design a program to satisfy the requirements in the Problem Description and implement it in a file named PairOfDice.java
3. Test the program using the modified version of the SnakeEyes program. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Activity 4 is completed.
5. Push the changes from your local repository to the github classroom repository

## Activity 5 - GameOfPig
### Problem Description
Using the *PairOfDice* class from Activity 4, design and implement a class to play a game called Pig. In this game, the user competes against the computer. On each turn, the current player rolls a pair of dice and accumulates points. The goal is to reach 100 points before your opponent does. If, on any turn, the player rolls a 1 (on either die), all points accumulated for that round are forfeited, and control of the dice moves to the other player.  

If the player rolls two 1's in one turn, the player loses all points accumulated thus far in the game and loses control of the dice. Therefore, the player must decide either to roll again (be a pig) and risk losing points or to relinquish control of the dice, possibly allowing the other player to win. Implement the computer player such that it always relinquishes the dice after accumulating 20 or more points in any given round.

### Implementation Guide
1. Copy Die.java and PairOfDice.java from A4-SnakeEyes into the A5-GameOfPig folder.
2. Design a program to satisfy the requirements in the Problem Description and implement it in a file named GameOfPig.java
3. Test the program using the GameOfPig driver program. Carefully think about each of the different cases you'll need to test for to verify that the application is functioning properly.
4. Commit the changes to your local repository with a message stating that Activity 5 is completed.
5. Push the changes from your local repository to the github classroom repository
