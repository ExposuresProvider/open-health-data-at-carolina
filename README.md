# Open Health Data @ Carolina

The intent of this repo is to support our work with NC TraCS to establish an instance of [COHD (Columbia Open Health Data)](http://cohd.io/about.html) at UNC Health. Open Health Data will expose patient counts and prevalence estimates for patient demographics, diagnoses, medications, and procedures, and the co-occurrences between them. The EHR results will be derived from UNC Health's OMOP database and include data on ~6M patients over years 2018 through 2022.

Here is a list of required resources and/or helpful information:

   - Casey Ta's COHD repo: https://github.com/CaseyTa/ehr_prevalence/tree/master (note that the co-occurrence calculations required about 100GB RAM)

   - OMOP script: https://github.com/CaseyTa/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql (also here https://github.com/WengLab-InformaticsResearch/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql)

   - Sample files: https://github.com/CaseyTa/ehr_prevalence/tree/master/synthetic_example_files

   - Output/download files:https://figshare.com/collections/Columbia_Open_Health_Data_a_database_of_EHR_prevalence_and_co-occurrence_of_conditions_drugs_and_procedures/4151252

   - Additional notes: original COHD datasets were a total of 5GBs of csv files (uncompressed) and 1.3GB when compressed

NC TraCS and CDWH Oversight Committee: 

- Project comprises two phases: (1) Phase I is instantiation of COHD @ UNC Health (approved to move forward); (2) Phase II is extension of COHD to incorporate exposures data (approval pending expert determination of privacy risks).

-   Phase I estimate is 50 hours @ $115/hour, per Kellie Walters on 3/28/2024.
