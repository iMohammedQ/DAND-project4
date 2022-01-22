
Wrangle report

The dataset that used in this project is WeRateDogs and this is account from twitter @dog_rates. In this project a split the wrangle section into three main section:

    Data Gathering
    Data assessing
    Data Cleaning

First in the in data gathering section I gather 3 data from different resourse. First data was twitter-archive-enhanced.csv and is in this link https://d17h27t6h515a5.cloudfront.net/topher/2017/August/59a4e958_twitter-archive-enhanced/twitter-archive-enhanced.csv and save it in df. then I download Download Image Prediction Data from https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv and name it pred. Afterthat, I used the twitter_json.txt that provided in support material I couldn't have access to twitter and save the tweets_api in df2.

In the data assessing section, after I do some test in the df,pred and df2 I found these issues:
quality issue

1.Remove columns 'in_reply_to_status_id' , in_reply_to_user_id , retweeted_status_id , retweeted_status_user_id and retweeted_status_timestamp has alot of missing data and not need in our analysis in df.

2.Source Data not clear and long make it shorter and

3.timestamp has data not necessary +0000

4.name column have (None,a,all,an,the,by,old,this,my...) value need to change to null

5.any value not equal 10 in rating_denominator remove it in df.

6.rating_numerator most the number between 0 to 15 considering maximum value 15 and any number bigger than that it will be 15.

7.Change data type for many columns.

8.Remove columns jpg_url and img_num from pred is not needed for our analysis.

9.Remove rows that contains data in retweeted_status_id , retweeted_status_user_id and retweeted_status_timestamp
tidiness issue

1.df (Twitter Archive), pred (Image Prediction Data) and df2 (retweet and Davourite Data) must be in one dataframe

2.doggo,floofer,pupper and puppo in df needs to be in one column

In the cleaning section, I start copying all dataframe in new copy to start changing in these copies. After that, the first thing I do was merge all dataframe to one dataframe to make it easier to change in one dataframe. When I do it I solve another issue was some data would have missing data in some columns. Then I start removing all the value that not null in retweeted_status_id , retweeted_status_user_id and retweeted_status_timestamp. Then I start droping columns that have unused and have alot of missing data. Then I make source shorter and easier to read. Then I delete the unnecessarily data in timestamp (+0000) all these in all rows because this data will not effect in our analysis. Then I start cleaning the name because they contain alot of dirty data that need to clean like (a,all,old,by...). Then I start cleaning the rating_denominator. Some rows not equal to 10 and that effect to our analysis so I delete these rows. For rating_numerator, I make this between 0 to 15 and other that if it more than 15 change it to 15 because these data are very few. Then I clean thes columns doggo,floofer,pupper and puppo and make it in one column call it dog_type. finally after structure of dataframe is cleaned, I change the data type for some columns to make our analysis more accurate. During the Cleaning section, I divide for each issue into three section: define, code and test. In define section I explain the issue and do some code to show the issue. in code section I solving the issue and finally in the test section I show the result. After the cleaning section, I store the dataframe as twitter_archive_master.csv
