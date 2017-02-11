---
layout: post
title: What I learned from analyzing jobs at naukri.com
---

So, one day I was skimming through naukri.com just looking at the requirements of **data scientists** jobs in India, work experience, qualification, salary etc. As I was going through more and more pages, it was becoming difficult for me to keep track of all the things seen.

So, I thought of doing analysis of jobs posted at naukri.com with the search keyword Data Scientist. At that time I did not know where to start. What I did know was that the first step was scraping the data.

## Scraping and storing the data

So, I just googled web scraping with python and then a number of resources came up. The most useful I found for me was [this](https://www.dataquest.io/blog/web-scraping-tutorial-python/). I used requests library for getting the data from the page and then Beautiful soup, which is another python library for puling data out of HTML and XML files. Beautiful soup was used to extract the text from the HTML tags. 

I went to the page of each of the job and extracted the relevant details, and then moved to next job. This work was repeated for 4 pages. In the end I had 183 jobs information. I did not extract more because the job postings were repeating themselves. 
 The things I scraped were -:
- Job Description
- Job Requirements
- Work Experience required.
- Job Location
- Salary

Then I stored the data in MongoDB, which is a database with JSON like documents. It is called a NoSQL database. Data storage is necessary else we need to run the script every time we need the data.

## Data Cleanup

The data whenever needed was loaded into a pandas data frame.
Some steps also needed to be performed for the cleanup. The format of the experience was **5 - 10 yrs**. So, I converted the data in list of the form [5,10]. Now for analysis, I found the average of these experiences and converted them into ranges of the form 0-2, 2-5 etc. Now for the cities, the frequency of jobs in each city was found and the chart was plotted.
For requirements also, the above task was done.

## Data Analysis

Matplotlib was used for the plotting of the plots.

So, the first is the visualization of the job-experience required in relation to the number of jobs.

![an image alt text]({{site.baseurl}}/images/Selection_001.png)

So we can see that the average age experience required is 2-5 years in most cases followed by 5-8 years.

The next is the visualization of job location related to the number of jobs.

![an image alt text]({{site.baseurl}}/images/Selection_002.png)

So, Silicon valley of India, that is Bangalore provides most of the jobs to data scientists.


The next is the visualization of skills required relating to the number of jobs. 

![an image alt text]({{site.baseurl}}/images/Selection_002.png)

So, Machine Learning is the most popular sought after skill followed by python. 

We could not plot salary because in most of the cases salary was not disclosed by the recruiters. 
All the code for this analysis along with the ipython notebook can be found at [this link](https://github.com/abhinavbh08/naukri-analysis)
