# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked 'enter' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Access to the Server / Directory to store PDF report of Analysis
3. Maximum and Minimum threshold limits to classify as breach
4. Notification / Email Service to notify receiver when new report is available

(add more if needed)

### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | No            | External application not in scope
Counting the breaches       | Yes           | This is part of the software being developed
Detecting trends            | Yes           | This is part of the software being developed
Notification utility        | No            | External application not in scope

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
1. Write "Invalid input" to the PDF when the csv doesn't contain expected data
1. Write "No Breaches" to PDF when there is no breach
1. Write "Invalid File Format" when input file format is wrong
1. Write "File not found" when input csv file is not found
1. Write "No breaches found" when there is no breach in battery telemetry data
1. Write "Increasing Breach Trend" when increasing continuously for 30 minutes
1. Check "Total breaches Count"
1. Check PDF generated or not and in weekly frequency
1. Check notification sent after every PDF generated 

(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | pdf file     | email sent/not sent         | Fake the notification
Report inaccessible server | csv file     | no access / access denied   | Fake the call to server
Find minimum and maximum   | csv data     | return min and max list     | None - it's a pure function
Detect trend               | csv data     | normal/abnormal trend       | None - it's a pure function
Write to PDF               | csv data     | PDF file                    | Fake the call to PDF Converter
