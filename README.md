# Lab3
Summary of lab3:

The dataset was imported from Azure Data Lake Storage, specifically from the curated_reviews folder inside my Fabric Lakehouse. Once the data was loaded, several cleaning and transformation steps were applied using Power Query to make it consistent, accurate, and analysis ready.

The first step was changing column types to make sure all IDs and numerical fields were stored properly. The book_id, author_id, and user_id columns were converted into text to prevent type mismatches, while numeric fields like book_avg_rating and book_ratings_count were explicitly set as integers. This helped avoid data type errors in later steps and made sorting and aggregations work correctly.

After fixing data types, I focused on removing empty and invalid records. Three consecutive “Remove Blank Rows” transformations were applied to catch and delete any rows that contained missing or null values across any column. This step was important because many rows in the original dataset had missing author names, review text, or rating fields, which would have distorted the results in the aggregation phase.

Next, I created a new column called review_length, which calculates the number of characters in each review. This was done using the Text.Length() function. I then filtered the dataset to keep only reviews that had at least 10 characters, removing very short or meaningless reviews. This ensured that only proper user reviews were kept for later analysis.

To handle missing values in the language column, I applied two replacements. Any null value was replaced with the word “Unknown”, and any blank or empty string was replaced with “unknown” (in lowercase). This made sure the language column was clean and consistent while still preserving the information that the language wasn’t specified.

Text cleanup came next. I used multiple Trim transformations to remove extra spaces from the beginning and end of the text in columns like title, name, and review_text. This was followed by a Capitalize Each Word transformation on the title column, so all book titles now follow a consistent capitalization style. These steps improved readability and standardization across text data.

Finally, I added a new column called word_count, which counts how many words each review contains. This was calculated by counting the number of spaces in the trimmed review text and adding one. This feature helps measure how detailed or long each review is, which could be useful for later sentiment or text-based analysis.

In summary, the cleaning process focused on fixing data types, removing blanks, replacing missing values, and formatting text fields. The dataset is now standardized, consistent, and enriched with two new features: review_length and word_count. These steps prepared the data for the next phase of aggregations and publishing, ensuring a high-quality final dataset named curated_reviews.
