**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:      |  23   |
| -------------- | --- |
| Student Names: |  Mustafa Muhammad   |
|                |  Samuel Tomecek    |
|                |  Umair Tariq   |
|                |  Gian Luke Adug   |

# 1 Introduction

In the third lab of Seng 438 we are given the source code for the JAR files we used in the previous lab. The focus of this lab is to use white box unit testing techniques alongside automated coverage tools to increase the quality of our test suite. By having the source code alongside using the eclemma coverage tool we were able to pinpoint areas of the code which our tests did not cover and use whitebox testing tools like DU pairs and condition coverage. We had to ensure a certain level of coverage through this lab, through adding tests for different methods and bolstering previous tests. Overall this was an eye opening experience as it was our first time applying whitebox testing for a java program.

# 2 Manual data-flow coverage calculations for X and Y methods

All work for this step can be seen here: [Our google docs](https://docs.google.com/document/d/1w9w3shtEDF1kt6CYPM6HF1dMxdtMAN7oD4YIKzeK4bA/edit?usp=sharing)






# 3 A detailed description of the testing strategy for the new unit test

Who will create which tests for new methods:

Mustafa: calculateColumnTotal(), calculateRowTotal(), calculateColumnTotal(validRows), calculateRowTotal(validCols)

Sam: clone(), equals(), getCumulativePercentages()

Gian: combine(), combineIgnoringNaN(), expand(), expandToInclude(), shift(Range, double), shift(Range, double, boolean), max(), min() 

Umair: getCentralValue(), intersects(), equals(), constrain(), hashCode(), scale(), isNaNRange()

How we plan to develop tests to achieve the adequacy criteria:

How we plan to develop these tests goes back to the white-box testing principles involving line and branch coverage that successively follows the testing ideology in a progressive manner. Our tests are to be designed with the goal of trying to at least reach 60% method coverage, 70% branch coverage and 90% line/statement coverage. To achieve these goals we will be prioritizing statement and branch coverage as much as possible within our test cases. We will be executing every branch that we can see within the code of every specified method found within each respective class. This includes determining how we will be analyzing the loop structure of every method. Next we will be using procedure nodes and predicate nodes to determine where branches were created and this allows us to structurize the plan model to adapt accordingly to what is needed for branch coverage. Just like data flow graphs but in real-time and in a faster and successive manner we will be analyzing the sequences of statements, determining where if-conditions are placed, where if-then-else branching is occurring, while-loops and other repeat-loops take place and prioritizing the code coverage in that order. As a result our test cases will be in a similar manner (however, it is possible for them to order themselves in different ways than as written as a byproduct of consecutive error and passing testing). That leads into a last-resort testing strategy where if the method is using outside resources that is unreachable then try various test cases in different orders if needed. The condition coverage can also have a Modified Condition-Decision Criterion metrics where we attribute true/false values to the overall condition letting us examine the outcome of decision changes better. As a reminder all of this is encompassing the various edges that will be present within each method of the code and if we are stuck then as per our strategy we will re-attempt a new test case until we see progress and move forward from there. We are assuming that with the adequate level of coverage to both branch and statement coverage we will also meet the goal of 60% method coverage as a byproduct of prioritization over statement and branch coverage.

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

public void getCumulativePercentages_Null()
After reviewing the coverage from assignment 2, it could be seen that there was a branch that was not tested. Inside the first for loop of getCumulativePercentages(), we never had a test case that covered the else part of if(v!=null). We never had a test with the keyed value data == null. By adding this test case, the function would then skip the if statement and test another branch. The branch coverage was increased to 75%, just missing an infinite for loop in the function.
 
public boolean intersects(double b0, double b1):
It should be first quickly noted that b0 is the lower bound and b1 is the upper bound. This is an important method in the Range class that determines if there is an intersection or overlap within the specified ranges of the lower and upper bound inside a range. Initially we did not cover this during black-box testing but added seven methods now within the white-box testing stage. All of the methods tested the branch instructions for this method and a return statement. This involved determining when the lower input was less than or equal to the actual returned portion of the lower range and to return accordingly. A simple test case for intersects we did was test_intersects_Regular() which tested whether a range from 5 to 10 has an intersection from 2 to 8. After adding this the branch coverage for the specified test method was increased by 50%. This is true as 8 is inside 10 so the test case passes the branch conditions and gives us coverage in the overall class. The test cases for the intersects() method added 8.6% more to the overall total branch coverage, 3.4% more to the overall total line/statement coverage and 8.7% more to the overall total method/condition coverage. This total coverage was added to the Range class. As demonstrated the method is more heavy on branch coverage and focuses more on testing the intricacies of branch flow and the test cases were designed to characterize and analyze all possible scenarios to cover the various ways in which branch flow is constituted.

public double constrain(double value):
This is another important method found within the Range class that is analyzing a range and is to return us to the value that is the closest to our specified value. This was implemented during white-box testing design and we added three methods during the white-box testing stage. This involved methods that would test primarily the branch and statement coverage of the selected method. The method determines whether a value is contained within a specified range and if it isn’t then to return the upper/lower bound closest to the value. A simple test case for constraint we did was test_constrain_InvalidNumberHigher() where we tested a range from -10 to 30 and had the constrained value as 31. This should return 30 being the closest value in the range and the test passes and covers the branch and statements accordingly. This increased both branch and statement coverage by 50% and 25% respectively for the specified test method. The test cases for the constrain() method added 6.1% more to the overall total branch coverage, 6.8% more to the overall line/statement coverage, and 4.4% more to the overall method/condition coverage. This total coverage was added to the Range class. The test cases provide a sizable coverage to the total branch and statement coverage.

public void testCombine_TwoNullRanges() 
This is an important Range test for combine() that was not covered during black-box testing. It was mainly used to test the output of the method if both ranges are null. The expected output should be a null Range. The test gave 0.9% more overall line coverage, 1.2% more overall branch coverage, and no change to overall condition coverage. As shown, the tests were more focused on the statement and branch coverages.

public void testCalculateColumnTotal_NullValuesInColumn()
This is an important DataUtilities test for the function CalculateColumn Total as the previous test suite for lab 2 never tested if the values inside the column were null. Given the source code we were able to see that this missed an if statement, if(n != null), on line 167. Since the coverage tool exposed this missing branch for us, we were able to create this test case and cover both branches of the above if statement. Overall increasing the branch coverage of the file by 1.6%. 


# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

Text…

# 6 Pros and Cons of coverage tools used and Metrics you report

We used EclEmma as our coverage tool for this lab. The first pro is that it was very easy to set up and get running, because it is integrated in Eclipse. It is easy to run and get quick results for our coverage. Due to the large amount of libraries, it could be frustrating to navigate to the results of the one method you were testing each time, but that is not a large issue. The larger issue that we encountered in this lab was the lack of condition coverage. This forced us to change one of our goals to test method coverage instead. Other than that, EclEmma made it clear on the percentages of the coverage, and it was easy to go through the function in question and it would highlight what lines were never reached in the test cases. This made it clear what additional test(s) would be needed to achieve proper code coverage.

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Text…

# 8 A discussion on how the team work/effort was divided and managed

The first step taken in the lab was to review the lab document together and run through any setup. Then once we reached section 3.2 we divided up the two methods we had to analyze between two subgroups between the team, where 

Sam+Mustafa worked on DataUtilities

Umair+Gian worked on Range

Afterwards when moving to step 3.3, the work was further divided where each member focused on writing tests for specific functions

Sam: clone(), equals(), getCumulativePercentages(), calculateColumnTotal()

Mustafa: calculateColumnTotal(validRows), calculateRowTotal(validCols), calculateColumnTotal(), calculateRowTotal

Umair: getCentralValue(), intersects(), equals(), constrain(), hashCode(), scale(), isNaNRange()

Gian: combine(), combineIgnoringNaN(), expand(), expandToInclude(), shift(Range, double), shift(Range, double, boolean)

Overall it was an equal split with everyone having been involved in every step of the process. 


# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

Overall, the lab went smoothly. The one issue that came up for a few of the tests in DataUtilities is that some functions have for loops that are impossible to get out of once you’re in it. These were unable to be tested properly, as by including them in our coverage in the test suite, it wouldn’t allow the other tests results to finish. We had to ignore these lines/branches and make up the coverage elsewhere. Otherwise this lab was a great first hand experience in working with coverage tools, it helped us as a group to realize the power and usefulness of automated coverage tools and how they can easily expose areas of your code which isn't tested thoroughly. 

# 10 Comments/feedback on the lab itself

Overall the lab was a wonderful and exciting opportunity to explore and venture into the various aspects and designs regarding white-box testing. We were able to learn a lot about how the internal structure of code designs allow us to manipulate and determine ideal and feasible ways to create test cases relating to the code. It would have been great if any tutorial information was provided on other code coverage tools and exactly what libraries we needed to import for this lab.
