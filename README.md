# Open Health Data @ Carolina

The intent of this repo is to support our work with NC TraCS to establish an instance of [COHD (Columbia Open Health Data])(http://cohd.io/about.html) at UNC Health.

Here is a list of required resources and/or helpful information:

   - Casey Ta's COHD repo: https://github.com/CaseyTa/ehr_prevalence/tree/master (note that the co-occurrence calculations required about 100GB RAM)

   - OMOP script: https://github.com/CaseyTa/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql (also here https://github.com/WengLab-InformaticsResearch/ehr_prevalence/blob/master/cohd_omop_export_sql_server.sql)

   - Sample files: https://github.com/CaseyTa/ehr_prevalence/tree/master/synthetic_example_files

   - Output/download files:https://figshare.com/collections/Columbia_Open_Health_Data_a_database_of_EHR_prevalence_and_co-occurrence_of_conditions_drugs_and_procedures/4151252

   - Additional notes: original COHD datasets were a total of 5GBs of csv files (uncompressed) and 1.3GB when compressed

## Tips from Casey Ta re integration with the Translator ecosystem

From the output files of the ehr_prevalence scripts, we load those data into a MySQL database using scripts here: https://github.com/WengLab-InformaticsResearch/cohd_api/tree/master/db/sql

The data are stored primarily as co-occurrence counts and some pre-computed stats on MySQL. Concepts are still referenced in OMOP.

We create all KG edges on the fly when we receive TRAPI calls. Most of that work captured in here: https://github.com/WengLab-InformaticsResearch/cohd_api/blob/master/cohd/cohd_trapi_15.py

For mappings from OMOP to Biolink, we essentially try to create mappings between the OMOP concepts we have in our data to Biolink with the help of Node Norm. We store these mappings in the MySQL database and have scheduled events to update once/month. https://github.com/WengLab-InformaticsResearch/cohd_api/blob/master/cohd/biolink_mapper.py. These mappings are stored with the normalized Biolink CURIEs, so whenever a TRAPI call comes in, we first call Node Norm to make sure QNode curies are normalized, then find those mappings from Biolink to OMOP in our tables, get the query results in OMOP, then convert as many of those results back to Biolink as we can via our tables. Even if your setup is different from ours, you could potentially steal code from the build_mappings function to help with your mappings from OMOP to Biolink, if you wish.
