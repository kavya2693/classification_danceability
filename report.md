Data Collection and Upload to BigQuery
The following steps outline the process of collecting a dataset containing track features and uploading it to BigQuery:
Project Creation: 
To facilitate the analysis, I initiated the project with the ID "root-matrix-400415" in Google Cloud Platform. This project served as the primary environment for all subsequent data handling, storage, and analysis tasks in BigQuery and Google Cloud Storage.
Dataset Acquisition:
Sourced a dataset comprising features essential for the classification task: 'tempo', 'energy', 'valence', 'loudness', 'speechiness', and 'acousticness' and other features. The dataset was in CSV format with 18000 songs, suitable for processing and analysis.
Cloud Storage Upload:
Uploaded the CSV file to a cloud storage solution. For this task, Google Cloud Storage was used as it integrates seamlessly with BigQuery. Ensured data integrity during the upload by verifying the file size and content post-upload against the original file. Created a new bucket in the Google Cloud Console, selecting the appropriate storage class and location to optimize for access speed and cost. The bucket's settings were configured to ensure data privacy and security.
 
Uploading Data to the Bucket:
Uploaded the CSV file containing the track features to the designated Google Cloud Storage bucket. 
Linking the Bucket with BigQuery:
Imported the data from the CSV file in Google Cloud Storage into the BigQuery dataset and table. This process involved specifying the data source (the CSV file in Cloud Storage), the destination table (the newly created table in BigQuery), and the schema.Ensured that the import process correctly mapped CSV columns to the BigQuery table columns and checked for any errors or warnings during the import. Schema is set to detect automatically and ensure jagged rows option is selected to arrange the data.
Within the project "root-matrix-400415", the dataset "spotifydatakj" was created, and within this dataset, the specific table "kj26" was used to store and manage the track features data essential for our analysis.
 
Data Verification:
Check Data Integrity:
After the data was loaded into BigQuery, ran a few basic queries to verify the integrity and correctness of the data. This included checking row counts, viewing sample records, and ensuring that no data corruption occurred during the transfer.

-- Count the total number of rows in the table
SELECT COUNT(*) AS total_row_count
FROM `root-matrix-400415.spotifydatakj.kj26`;

-- Preview the first 10 records from the table
SELECT *
FROM `root-matrix-400415.spotifydatakj.kj26`
LIMIT 10;
SELECT COUNT(*) AS total_rows
FROM `root-matrix-400415.spotifydatakj.kj26`;
SELECT COUNT(*) AS total_columns
FROM `root-matrix-400415`.spotifydatakj.INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'kj26';

 
 
 
Missing Values
Check for missing values if any : Based on the results of the below query, there are no missing values.
SELECT
  COUNTIF(valence IS NULL) AS missing_valence,
  COUNTIF(year IS NULL) AS missing_year,
  COUNTIF(acousticness IS NULL) AS missing_acousticness,
  COUNTIF(artists IS NULL) AS missing_artists,
  COUNTIF(danceability IS NULL) AS missing_danceability,
  COUNTIF(duration_ms IS NULL) AS missing_duration_ms,
  COUNTIF(energy IS NULL) AS missing_energy,
  COUNTIF(explicit IS NULL) AS missing_explicit,
  COUNTIF(id IS NULL) AS missing_id,
  COUNTIF(instrumentalness IS NULL) AS missing_instrumentalness,
  COUNTIF(key IS NULL) AS missing_key,
  COUNTIF(liveness IS NULL) AS missing_liveness,
  COUNTIF(loudness IS NULL) AS missing_loudness,
  COUNTIF(mode IS NULL) AS missing_mode,
  COUNTIF(name IS NULL) AS missing_name,
  COUNTIF(popularity IS NULL) AS missing_popularity,
  COUNTIF(release_date IS NULL) AS missing_release_date,
  COUNTIF(speechiness IS NULL) AS missing_speechiness,
  COUNTIF(tempo IS NULL) AS missing_tempo
FROM `root-matrix-400415.spotifydatakj.kj26`;

Checking Datatypes:

Check the datatypes of each column 
Row	column_name	data_type	

1	valence	FLOAT64	
2	year	INT64	
3	acousticness	FLOAT64	
4	artists	STRING	
5	danceability	FLOAT64	
6	duration_ms	INT64	
7	energy	FLOAT64	
8	explicit	INT64	
9	id	STRING	
10	instrumentalness	FLOAT64	
11	key	INT64	
12	liveness	FLOAT64	
13	loudness	FLOAT64	
14	mode	INT64	
15	name	STRING	
16	popularity	INT64	
17	release_date	STRING	
18	speechiness	FLOAT64	
19	tempo	FLOAT64	
Unique values:
Check the unique values for the columns

SELECT
  COUNT(DISTINCT valence) AS unique_valence,
  COUNT(DISTINCT year) AS unique_year,
  COUNT(DISTINCT acousticness) AS unique_acousticness,
  COUNT(DISTINCT artists) AS unique_artists,
  COUNT(DISTINCT danceability) AS unique_danceability,
  COUNT(DISTINCT duration_ms) AS unique_duration_ms,
  COUNT(DISTINCT energy) AS unique_energy,
  COUNT(DISTINCT explicit) AS unique_explicit,
  COUNT(DISTINCT id) AS unique_id,
  COUNT(DISTINCT instrumentalness) AS unique_instrumentalness,
  COUNT(DISTINCT key) AS unique_key,
  COUNT(DISTINCT liveness) AS unique_liveness,
  COUNT(DISTINCT loudness) AS unique_loudness,
  COUNT(DISTINCT mode) AS unique_mode,
  COUNT(DISTINCT name) AS unique_name,
  COUNT(DISTINCT popularity) AS unique_popularity,
  COUNT(DISTINCT release_date) AS unique_release_date,
  COUNT(DISTINCT speechiness) AS unique_speechiness,
  COUNT(DISTINCT tempo) AS unique_tempo
FROM `root-matrix-400415.spotifydatakj.kj26`;


 



![image](https://github.com/kavya2693/classification_danceability/assets/127579722/f3b52b59-8557-41e0-a6e4-f72de38b444a)
