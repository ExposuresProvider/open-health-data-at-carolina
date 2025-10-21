# Open Health Data @ Carolina

The intent of this repo is to support our work with NC TraCS to establish an instance of [COHD (Columbia Open Health Data)](http://cohd.io/about.html) at UNC Health. Open Health Data will expose patient counts and prevalence estimates for patient demographics, diagnoses, medications, and procedures, and the co-occurrences between them. The EHR results will be derived from UNC Health's OMOP database and include data on ~2M patients over years 2018 through 2022. **Update:** Total number of patients in final cohort = 2,344,578.

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

     _Notes: Uses concept_pair_counts_2018-2022_randomized_mincount-11_N-2306126_hierarchical_20240826-1228.txt file to create kg which includes about 282M concept co-occurrences. There is another file concept_pair_counts_yearly_randomized_mincount-11_20240901-055303.txt which includes about 30M concept co-occurrences along with year and frequency._

- Nested attributes: https://github.com/WengLab-InformaticsResearch/cohd_api/tree/master/kgx

NC TraCS and CDWH Oversight Committee: 

- Project comprises two phases: (1) Phase I is instantiation of COHD @ UNC Health (approved to move forward); (2) Phase II is extension of COHD to incorporate exposures data (approval pending expert determination of privacy risks).
   - Phase I estimate is 50 hours @ $115/hour, per Kellie Walters on 3/28/2024.
   - James Champion tranferred files to Goldfish on 9/3/2024, with an additional file added 9/5/2024.
 
**Update from November 2024:**

_Evan, Max, Casey, Kara exchange_

1. Evan deployed COHD to: https://automat-dev.apps.renci.org/cohd/ (openapi here https://automat-dev.apps.renci.org/#/cohd)
2. A number of node CURIES did not normalize in Node Normalizer.
3. biolink:categories should be changed to biolink:category.
4. infores:automat-cohd (and infores:auotmat-open-health-data-carolina) need to be added to the InfoRes catalog. DONE
5. supporting_data_source is not yet handled correctly.
6. Nested attributes remain an issue, although they won't be after we move away from Neo4J.

```RXCUI:1860133
CPT:99213
SNOMEDCT:44749005
CPT:77013
RXCUI:797835
CPT:71010
CPT:76937
CPT:31231
CPT:73610
CPT:47610
CPT:36620
RXCUI:1729198
SNOMEDCT:110466009
CPT:88305
CPT:50592
RXCUI:900963
RXCUI:1860240
RXCUI:1735004
RXCUI:1860464
CPT:76817
CPT:88311
CPT:42410
RXCUI:797836
RXCUI:1740468
CPT:99223
CPT:61782
CPT:93306
CPT:99214
CPT:99254
CPT:27705
CPT:26785
CPT:11641
CPT:73590
CPT:99469
RXCUI:665002
CPT:00102
SNOMEDCT:243787009
SNOMEDCT:709479007
CPT:30465
CPT:73140
RXCUI:1794431
RXCUI:847624
CPT:99233
CPT:36825
RXCUI:1812184
CPT:20912
RXCUI:1740918
RXCUI:1795345
CPT:34151
CPT:27513
SNOMEDCT:710955000
CPT:31575
RXCUI:1795608
CPT:73540
RXCUI:1860237
SNOMEDCT:41587001
CPT:74000
CPT:99232
RXCUI:1732015
CPT:00100
SNOMEDCT:60108003
CPT:77001
CPT:36450
CPT:73030
CPT:11470
CPT:31292
CPT:73560
SNOMEDCT:199165004
CPT:76816
RXCUI:328317
RXCUI:1737234
CPT:44135
CPT:88307
CPT:00548
RXCUI:1928300
RXCUI:1861733
CPT:99291
CPT:88304

