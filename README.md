# elife-vendor-workflow-config

Capturing requirements and niggles for setting up the elife production workflow.

This repo is for the discussion an development of the eLife production workflow between eLife Production/Development staff and ExeterPremedia.

###Export process
Currently ExeterPremedia complete export checks on EJP. This involves ensuring all the data held in the submissions screens is correct, and missing data is helpd in a red stucky note for export, and that all the asset files are correctly named.
This is required for the PoA wokrflow that eLife manages via AWS and also for the export of content to TNQ for full content processing.

Currently approx 23% of author names and affiliations are either changed on export or are not contained within the EJP databales and only stored as notes, so there is not really a requirement to maintain this data as cleanly as we do on EJP.

The proposal is that on acceptance, all content is exported straight to ExeterPremedia and they use the XML export and the author's Word file to build the html of the article, which commences the production workflow. Where there are differences in the data, this is resolved here.

######_Problems_
- FundRef database on EJP and that many funding details are changed during this process
- The PoA workflow is reliant on CSV output from EJP to puld the XML

######_Soultions_
- Link to FundRef during the production process?
- There is a 30 min window in the PoA wokrflow when the XML remains in an eLife AWS bucket, this is an opportunity to go in and overwrite it without affecting the POA to HW delivery and the production of the downstream deliveries, CrossRef and PubMed.



###Pre-editing process

###Copy editing process

###Author proofing and QC process

###Feature content

###File naming,  packaging, and delivery

###New requirements/workflow improvements




