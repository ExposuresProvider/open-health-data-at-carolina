# Open Health Data @ Carolina

The intent of this repo is to support our work with NC TraCS to establish an instance of [COHD (Columbia Open Health Data)](http://cohd.io/about.html) at UNC Health. Open Health Data will expose patient counts and prevalence estimates for patient demographics, diagnoses, medications, and procedures, and the co-occurrences between them. The EHR results will be derived from UNC Health's OMOP database and include data on ~6M patients over years 2018 through 2022.

Here is a list of required resources and/or helpful information:

   - Casey Ta's COHD repo: https://github.com/CaseyTa/ehr_prevalence/tree/master (note that the co-occurrence calculations required about 100GB RAM)

   - OMOP script: https://github.com/CaseyTa/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql (also here https://github.com/WengLab-InformaticsResearch/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql)

   - Sample files: https://github.com/CaseyTa/ehr_prevalence/tree/master/synthetic_example_files

   - Output/download files:https://figshare.com/collections/Columbia_Open_Health_Data_a_database_of_EHR_prevalence_and_co-occurrence_of_conditions_drugs_and_procedures/4151252

   - Additional notes: original COHD datasets were a total of 5GBs of csv files (uncompressed) and 1.3GB when compressed

   - [COHD CSV output files -> KGX script](https://drive.google.com/drive/folders/1AT_-7OUsovDxwt1O5MepLILfgTXnWu56?usp=drive_link)

   - KGX file: Two files: concept_pair_counts_2018-2022_randomized_mincount-11_N-2306126_hierarchical_20240826-1228.txt file [282M concept co-occurrences] and concept_pair_counts_yearly_randomized_mincount-11_20240901-055303.txt [30M concept co-occurrences]. First file is for the total five-year sample; second file is for each year of the five-year sample. First file is for KGX file generation.

   - Exposures Provider's OHD@Carolina repo: https://github.com/ExposuresProvider/ehr_prevalence 

     _Notes from Casey:
   The yearly file gives you the co-occurrence counts on a yearly basis (e.g., in 2018, in 2019, in 2020, etc). It is intended more as a data quality check to see if the counts are relatively consistent from year to year (this was created in response to a reviewer for the COHD paper). For the most part, you won't need the yearly file, unless you plan to do something interesting about how relationships change over time. If you're wondering why there's much fewer concept pairs in this file, it's probably because a lot of the rarer concepts drop down below the mincount threshold when only including 1 year's worth of data._

- Biolink mappings for KGX file: 26019 OMOP concept ids in the OHD@Carolina dataset that are not included in Casey's omop_id-to-biolink-id mapping file. Based on the comments below, there are 13K missing mappings (likely due to highly granular OMOP concepts) and 13K (26K-13K) missing mappings due to institutional differences

  _Note from Casey:
   I just checked our database, and we have 74,555 distinct concepts with count data. Of those 61,360 have mappings, and 13,195 don't. We only created mappings for concepts for which we have data, so your 26k number will include some caused by institutional differences, but there are still a large number of concepts that don't get mapped for us._

- Nested attributes: https://github.com/WengLab-InformaticsResearch/cohd_api/tree/master/kgx

NC TraCS and CDWH Oversight Committee: 

- Project comprises two phases: (1) Phase I is instantiation of COHD @ UNC Health (approved to move forward); (2) Phase II is extension of COHD to incorporate exposures data (approval pending expert determination of privacy risks).

   - Phase I estimate is 50 hours @ $115/hour, per Kellie Walters on 3/28/2024.
   - James Champion tranferred files to Goldfish on 9/3/2024, with an additional file added 9/5/2024.

   _Notes:
I am using concept_pair_counts_2018-2022_randomized_mincount-11_N-2306126_hierarchical_20240826-1228.txt file to create kg which includes about 282M concept co-occurrences. There is another file concept_pair_counts_yearly_randomized_mincount-11_20240901-055303.txt which includes about 30M concept co-occurrences along with year and frequency._
