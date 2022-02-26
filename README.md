# DataWrangling_Project

Visual and programming assessment showed that these data are untidy and messy. Cleanning ought to be performed before data analysis and visualization.

Firstly, the file twitter-archive-enhanced consists of 2356 entries and 10 columns. There were problems with the data type of twitter-archive-enhanced: tweet_id should be converted to string from int; the data type of timestamp, retweeted_status_timestamp should be datetime; in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id and retweeted_status_user_id should be string instead of float because these features should not be able to be calculated. Also, tweet_id in image-predictions and in tweet-json should be changed into string from int. After went through the data, there were numerators which were not int, so the date type should be changed into float.

Furthermore, not only in expanded_urls but also null values were found in features including in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp. Among them, since there were too few valid values, these columns could be considered to be dropped. About expanded_urls, the contents were confusing for analysis, and therefore, this column could be dropped as well.

Additionally, there was mixed use of lowercase and uppercase for dogs' names, and thus, it would be better if all of them changed into uppercase. To be noted, there whose many dogs' names were None, which should be changed to NaN to perform statistics.

Besides, uncommon values found in rating_numerator and rating_denominator such as large numbers, float numerators or 0. Actually, a denominator will never be zero. To fix value problems, it could be better to check the values from the texts. To make sure about the validity of these two features, a new column named score was added, of which the value equals the rating_numerator divided by rating_denominator. There was still a value inf in row 313, and this one could be dropped for analysis.

Beyond all the above, since three tables share the same tweet_id, which means that these tables decribe different features of the same targets, and therefore, they can be merged into one table. In the merged dataframe, four columns doggo, floofer, pupper and puppo are all dog types, and thus, this information can be recorded with a single column dog_types.

Lastly, data was saved to twitter_archive_master. More effort was devote to checking whether data saved is clean enough. Column 'Unnamed' appeared in the dataframe, and then it was removed by coding.

In the end, although many issues have been fixed, more effort still can be done, such as in certain entries, the text described more than one dog. These tweets can be isolated from the tweets about single dogs for analysis.
