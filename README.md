# Election_Analysis

#### Project Overview

This is an election audit for a congressional election performed for the Colorado Board of Elections.  The scope of this audit includes the tasks listed below.

1. Total number of votes cast in this election.
2. A complete list of candidates.
3. The total number of votes that each candidate received.
4. The percentage of votes that each candidate received.
5. Summary of the winning candidates results.
6. A  complete list of counties where voters came from.
7. The total number of votes that came from each county.
8. The percentage of votes that came from each county.
9. The county with largest number of voters that participated in this election.

#### Resources

* Data Source: election_results.csv
  * This file contains the follow fields (Ballot_ID, County, Candidate)
  * There are 369711 records in this file.
* Software: Python 3.8, Visual Studio Code 1.48.0

#### Election Results

#####Total Votes: 369,711

-------------------------

#####Percentage and Count of Votes by County:
Jefferson: 10.5% (38,855)
Denver: 82.8% (306,055)
Arapahoe: 6.7% (24,801)

-------------------------

#####Largest County Turnout:

Denver

-------------------------

##### Percentage and Count of Votes by Candidate:

Charles Casper Stockham: 23.0% (85,213)
Diana DeGette: 73.8% (272,892)
Raymon Anthony Doane: 3.1% (11,606)

-------------------------

##### Winner

**Diana DeGette**
Winning Vote Count: 272,892
Winning Percentage: 73.8%

#### Audit Summary

The code used to perform this audit was written in such a way that can be easily modified to be used in other elections.  All the data reported comes from the data source, so with very few changes this code could be used to audit the results from almost any type of election.  The following code shows how we are able to read the data from the CSV file.   This we used a variable to load the data file, the code could be modified to request user input for the data source.

```python
with open(file_to_load) as election_data:

  reader = csv.reader(election_data)
```

 What the code does is loop over the data source and collect information and process it.  The code sample below collects unique Candidate and County names and tallies how many votes for each unique Candidate and County.  This could be modified the collect in additional information if the data is contained within the data source.

```python
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1
        # Get the candidate name from each row.
        candidate_name = row[2]
        # Extract the county name from each row.
        county_name = row[1]
        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:
            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)
            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0
        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1
        # Write a decision statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_options:
            # Add the existing county to the list of counties.
            county_options.append(county_name)
            # Begin tracking the county's vote count.
            county_votes[county_name] = 0
        # Add a vote to that county's vote count.
        county_votes[county_name] += 1
```

