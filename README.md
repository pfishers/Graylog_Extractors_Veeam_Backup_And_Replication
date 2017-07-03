# Graylog_Extractors_Veeam_Backup_And_Replication
Graylog Extractors for Veeam Backup and Replication Logs

My simple set of Veeam Backup and Replication extractors

The extractor works by using an input receiving content from Graylog Collector Sidecar (Using NXlog to read data from the Windows Event Log). the Windows Event Log EventIDs used by the extractor can be broken down into two categories, Jobs and Tasks, Jobs are Veeam Backup and Replication Jobs which can contain multiple vms, Tasks are the individual vm backup process. below is a list of the Event IDs:

    Event ID 110 - Job Started
    Event ID 190 - Job Finished
    Event ID 210 - Restore Session Started
    Event ID 290 - Restore Session Finished
    
    Event ID 150 - Task Finished
    Event ID 250 - Restore Task Finished
    
Veeam Backup and Replication creates many more logs under additional event ids than the ones i have chosn for this extractor, for a full list please see here: https://www.veeam.com/pdf/guide/veeam_backup_9_0_events_en.pdf

Below is a breakdown of what is extracted from the logs

    Event ID 110 - Job Started
                   Extract Job_Name From Message
                   Extract Job_Type From Message
                   
    Event ID 190 - Job Finished
                   Extract Job_Name From Message
                   Extract State_Name From Message
                   
    Event ID 210 - Restore Session Started
                   Extract Username From Message
                   
    Event ID 290 - Restore Session Finished
                   Extract State_Name From Message
                   
    Event ID 150 - Task Finished
                   Extract State_Name From Message
                   Extract Object_Name From Message
                   
    Event ID 250 - Restore Task Finished
                   Extract Object_Name From Message
                   Extract State_Name From Message
                   
This is by no means a complete extractor for all fields/logs created by Veeam, but was created for a specific need with the intent of keeping logs to the minimum, I posted this in the hope this may useful to others.

To install this extractor, simply paste the content of the JSON file into the 'Import Extractor' dialog, on the desired Input.
  
Thanks.
  
