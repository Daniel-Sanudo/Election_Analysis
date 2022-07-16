# Election Results
This project will analyze the dataset for the results of the elections for Charles Gasper Stockham, Diana DeGette and Raymon Anthony Doane in the counties of Jefferson, Denver and Arapahoe.

## Overview of Project
![Results](/Resources/Images/Text_File_Output.png)

The information from the provided election results is broken down in this image to show the results for each candidate and county. The total vote count is shown a the beggining of the image to show the election commission how we calculated the percentage in the following results.

Denver is the county with the largest turnout, having 306,055 votes from the 369,711 total, rounding to a 82.8% of the votes.

Diana DeGette won the elections with 272,892 votes out of 369,711, rounding to 73.8% of the total votes, nearly three quartes of the citizens supported her.

### Purpose
Using this program, we aim to help the election commission have a fast and clear answer regarding how each county and candidate performed using a script that can handle datasets with an unlimited amount of candidates and counties.

By using grouping the information into candidates and counties, the commission can have a clear insight about which counties were vital to the final results, as well as the popularity of the different candidates. 

The relative amount of votes (percentage) is added to provide a clearer sense of the magnitude this value has, as well as to make the information much faster to process.

## Analysis and Challenges
This script has to be useable on different operating systems since our client is not a single person but a whole commission, thus we had to make sure that it would work regarldess of the Operative System each person has, so the following solution was employed:

![OS_Dependencies](/Resources/Images/Multi_platform_file_path.png)

By using the OS dependencies on python, the file path would automatically add the required symbols to work on Windows, masOS or others. This ensures that the commission will be able to use our script on any device.


While our dataset only included 3 candidates and 3 counties, we had to make sure that the script was scalable since the commission is likely to look into more counties and candidates. For this purpose we opted for the following methodology:

![CSV_entry_loop](/Resources/Images/Loop_for_any_amount_of_entries.png)

This loop will tally the total votes in the dataset with the total_votes + 1 line. This way we'll be able to have a precise calculation of the percentages each county and candidate obtain. 
The candidate_options and county_options will respectively create a list of all the candidates and counties found in the dataset, while the candidate_votes and county_votes will store the total votes for each candidate and county respectively. 

By storing the votes each candidate and county obtained on separate dictionaries, we'll be able to work in a more organized manner and prevent data from being corrupted.

![County_report_script](/Resources/Images/County_Calculation.png)

The results report for the counties is done by iterating through all the extracted county names from the dataset and their respective vote amount. The current entry is then compared with the previous entry to know if it had a larger turnout; if it did, the current entry and its votes are stored as the largest turnout county. After this conditional is evaluated then the script moves to the following entry.

![Candidate_report_script](/Resources/Images/Candidate_Calculation.png)

The results for the candidate are calculated in a similar fashion as those from the counties. Our script iterated through the list of candidates and the votes that each of them obtained; by comparing the each entry with the previous one until all entries are used we're able to find who won the elections, as well as their total votes and their vote percentage.

### Limitations

![CSV_Header_Format](/Resources/Images/Required_CSV_Format.png)

This script required that the CSV dataset is named as election_results.csv and to place the file inside the Resources folder. Morover, the CSV must contain the County name in its second column, as well as the candidate name in its third column since our code looks for that data in those specific columns.

## Results

Regarding the counties, Arapahoe had 24,801 voters (6.7%) while Jefferson had 38,855 (10.5%) of the voters. Denver however, holds 306.055 voters (82.8%), which means that Denver is vital county for determining a winner. Arapahoe and Jefferson do not have a voterbase that's big enough to turn over the election results as their combined votes only amount to 17.2% of the total voterbase. Which means that the candidates whould focus on winning as many votes as they can in Denver.

Regarding the candidates, the winner is Diana DeGette. She obtained 272,892 (73.8%) of the votes, making it a landslide compared to her runner up Charles Casper Stockham who won 85,213 (23%) of the votes. Raymon Anthony Doane had a small voterbase with only 11,606 (3.1%).

Even if Charles Casper had completely won over Arapahoe and Jefferson, it wouldn't have been possible to obtain a victory without holding a significant amount of Denver's voterbase.

This script can be used with any other election process as long as the CSV follows the structe mentioned in the limitations; it could be used with all 64 counties of colorado for state elections since there's no hard limit to how many counties and candidates the script can process. It could also be used with another state's counties since, as mentioned previously, our script look through all the information in the dataset. 

By using our script, the election commission can obtain a quick and clear answer to the results of any other election that's split up by counties, be it at Colorado or another state.