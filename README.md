# WeRateDog-Tweets-Data-Analysis
This was my second project in the Udacity Data Analytics Nano Degree program sponsored by ALX. Here, three different datasets were gathered, cleaned, merged into a single master dataset and finally insights drawn and visualizations generated from it.
Data Gathering
To start, the three sets of data were appropriately gathered and read to data frames. Data set one being already in a csv format was read directly using pd.read_csv command. To read dataset 2, the request command was used to assess the given url, a response created from the url and after which the content was written to a file named image_prediction and finally the third dataset was extracted line by line from the tweet_json.txt file into a pandas DatatFrame with tweet_id, retweet_count and favorite_count as it's columns.

__Assessing__

All three datasets were assessed programmatically and visually in jupyter notebook and further using Microsoft Excel. To assess programmatically, functions such as df.info(), ```df.describe()``` and df.isnull() among others were used. The assessment revealed some cleanliness issues with the three(3) datasets. These included eight quality issues and four(4) tidyness issues. These are outline below:

__Quality issues__

Retweeted entries in dataset (ids in retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp) in twitter_archive dataframe

Null values in in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp, and expanded urls columns in twitter_archive datafreame.

Upper case ending a name (DayZ) in twitter_archive dataframe

Null entries represented as 'None' in stages and name columns and other lower case text in names column (e.g. 'a', 'an', 'the') in twitter_archive dataframe.

Same name represented differently in twitter_archive dataframe (i.e. Frank, Frönq, Frankie, Gordon and Gòrdón)

Erroneous data types in all three datasets : tweet_id all datasets and timestamp in twitter_archive dataset

Inconsistent column name of id column of tweet_json dataset compared to twitter_archive and image_predictions datasets

Inconsistent value format in columns 'p1', 'p2' and 'p3' of image_predictions dataframe


__Tidiness issues__
Multiple and duplicated urls in expanded urls column in twitter_archive dataset

Comment, ratings and image urls in same column (text) in twitter_archive dataset

doggo , floofer, pupper and puppo columns are all categories of a dog's stage in twitter_archive dataset. These should be one column

The three datasets should be a single dataset


__Cleaning Process__
Each identify cleanliness issue was resolved using the define-code-tes approach. Here, each issue was clearly defined and a set of actions outlined to appropriately rective the issue. These action items (pseudo codes) were converetd into actual python codes whihc were ran and afterwards effected changes confirmed with another code.

__Resolving Quality Issues__
These cleanliness issues were addressed to make the datset(s) ready for generating insights. Firstly, all instances of retweets with images were dropped, then, the in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp columns were dropped as well becuase they all have over 50 % of their entries missing.

Then, the 58 rows (less 5% of 2356) of the expanded_urls column with null values were dropped followed by changing the name "DayZ" which starts and ends with an upper case leter to an appropriate format whihc was "Dayz".

Moroever, all "None" in the name column of the twitter_archive dataset were replaced with nulls using np.nan and all instances of name represented differently in twitter_archive dataframe (i.e. Frank, Frönq, Frankie, Gordon and Gòrdón) appropriately replaced with a single instance of that name. Frankie and Frönq were replace with Frane and Gòrdón replaced with Gordon.

Furthermore, appropriate datatypes were assigned where necessary followed by renaming the id column in tweets_json dataset to conform with that in twitter_archiv and image_predictions datasets to ensure uniformity and enable easy merging where necessary with the tweet_id column is the key.

Finally, the inconsistent value format in columns 'p1', 'p2' and 'p3' columns of the image_predictions dataframe were corrected by changing all entries in these columns to lower case after which thirty(30) samples of each columns entries were viewed to confirm the change had be effected.


__Resolving Tidyness Issues__
Using the split command, the expanded_urls column was split based on the comma delimeter and only the firt column from the split named expanded_urls retained and all the other four(4) unwanted columns a, b, c, d dropped.

In the twitter_archive dataset, a new column named comments containing only comments extracted using regex from the expanded_urls column values was created and a csv file created from the reulting datatset to aid visual assessment of the this new column to confirm the extraction was successfull. The text column was dropped afterwards.

Moreover,the four dog stage columns; doggo , floofer, pupper and puppo were assessed for their unique entries then all four concatenated to form one column named _dog_stage with a space introduced before each column's entry. The appropriate regex was then used to extract the named dog stage in the resulting column and afterwards all the four(4) original dog stage columns were dropped.

Finally, all the three(3) datasets were merged into a single master dataset called twitter_archive_master.csv using pd.merge.


__Conclusion__
The data now was ready for generating the required insights and visualization to make data-driven decision
