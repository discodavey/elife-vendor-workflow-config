# eLife production workflow proposal June 2015

See <https://github.com/elifesciences/elife-vendor-workflow-config/blob/master/elife_file_naming_proposal_2015-05-28.md>
for file naming requirements.

######General note on turnaround times:
The vendor works until 3.30pm UK time.
Therefore, where their turnaround times are specified in hours, this excludes the period of from 3.30pm UK time to 3.30am UK time the following day.
Indian Bank holidays - a list of which will be supplied.


##Export process

###PoA
ExeterPremedia complete export checks on EJP for PoA content before export from the "Post Acceptance Check" queue on EJP. This involves ensuring all the data held in the submissions screens is correct and that all the asset files are correctly named.
This is required for the PoA workflow that eLife manages via Amazon Web Services (AWS) - the data from the submission screens is exported as CSV files, which are read to create PoA XML.
The charge for this process is £5 per article.

###VoR
If an article skips PoA and goes traight to the "Export System" eLife staff will export without any checks and all checks will occur at pre-editing.
There is no additional charge.


## Pre-editing

####Input:

Export from submission system:

1. XML metadata file
2. author Word/LaTex file
3. PDF representation of that Word/LaTex file and figure asset files
4. asset files

Asset files can be any combination of the following: 

- figure 
- figure supplement 
- supplementary file 
- media (includes videos, audio and animation) 
- source code 
- source data 
- reporting standards 
- appendix asset file, for example figure
- author response asset file, for example figure

####Expectations:
At the start of this process the Word/LaTex file is converted to an HTML file, and overlaid on the XML metadata output to cross check. 

Any conflicts in the information result in an output file to the production team to check, but the Word/LaTex source file is considered the source of truth for author and affiliation information.

The XML metadata is the source of truth for other metadata outputs, eg Funding information, copyright, conflict of interest, contribution.

This task is completed using the ECS tool.

For more detailed description of the pre-editing process see **ExeterPremedia please provide**.

####Output:

- HTML file - follow file naming convention with .html suffix
- All asset files are converted/sized/renamed as appropriate
- At the end of this process all components are zipped up and delivered to an eLife AWS bucket: elife-production-preedited
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
- SOAP message to PaW to move article to next stage

####Turnaround time:
It is expected this process will take 15 minutes of operator time.
The allowed time for the vendor is 24 hours to complete this step.

####Volume:
It is anticipated that at current publishing volumes up to 5 articles coupld be accepted on one day. However, there are peaks and troughs and we have seen periods of days without acceptances and instances of bunching up where 7-8 have been accepted in one day.

## Copy editing

####Expectations:

Please see EJP processing instructions in the XML metadata output to determine which level of copy editing is required:

<custom-meta><meta-name>Copy editing requirement</meta-name><meta-value>2</meta-value></custom-meta<custom-meta>
Values 0 and 1 require pre-editing only
Value 2 is an exeterpremedia copy edit
value 3 is an eLife UK freelance copy edit

- Copy editor edits on ECS, and all components of the article are available when editing
- If any changes to assest(s) are required, copy editor will either download, edit and reload, or add  Author Queries (AQs), asking author to resupply during the author proofing process 
- All copy editing changes are tracked and are available to the author and production to view when checking the proof.

####Output:
At the end of the copy editing process all components are zipped up and delivered to an eLife AWS bucket: elife-production-copyedited

- HTML file - follow file naming convention with .html suffix
- All asset files are converted/sized/renamed as appropriate
- At the end of this process all components are zipped up and delivered to an eLife AWS bucket: elife-production-preedited
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
 - SOAP message to PaW to move article to next stage

####Turnaround time:

- The allowed time for the vendor/freelance copy editor is 2 days to complete this step.

####Volume:

It is anticipated:

- 60% of content will require copy editing by the vendor
- 30% will not require a copy edit
- 10% will be copy edited onshore by eLife UK freelancers.

##Waiting steps

####Decision letter and response
These items are not ready at the point of export. The turnaorund time for them to be produced is 3-5 days. On completion, they will be uploaded to an FTP site, using a specific file-naming criteria and will be processed into the article by the vendor.

Note, there can be figures/tables/videos in the author response.
We anticipate this step will require input at the vednor end.

####Digest
This is the final expected item for an article before it can be delivered to the author. It is a standard piece of simple content.
Can this be dropped into a placeholder in the article on ECS and checked by eLife production staff before pressing the button to deliver the author email? **TBC**


##Proof to author

####Expectations:
- It is anticipated that unless the article has any specific requirements or difficulties, it will process straight to the next stage following on from copy editing or pre-editing.
- This task is completed using the ECS tool.
- Do we need another bucket to track the output of this stage? Or should there be no changes, making this unnecessary? **TBC**

####Output:
 email to author containing link to their article on ECS
- Do we need another bucket to track the output of this stage? Or should there be no changes, making this unnecessary? **TBC**

####Turnaround time:
NA, unless there is any particular difficulty with the file, in which case it would be 12 hours.


####Volume:
All content will go thorugh this process


##Author corrections


####Expectations:
Author will edit their content, move components around on the PDF representation view, and potentially upload new versions of figures.
It is anticipated that most changes will be done automatically, but in rare circumstances the author will not be able to directly input their changes and regenerate their proof.

####Output:
At the end of the author correction process all components are zipped up and delivered to an eLife AWS bucket **TBC**

- Zip file name: elife-12345-r1.zip
- If reprocessed r1 suffix will be replaced with r2 suffix (zipped file). The naming convention for all actual files remains unchanged, even if the files themsleves changed.

####Turnaround time:
Authors are given 2 days to complete this process, however, they often take longer.
We'd like automatic chasing mechanisms to be inplemented. Details of which **TBC**

####Volume:
All content will go through this process.

##eLife production staff QC


####Expectations:
eLife production staff vet all changes and where authors have added a comment rather than an edit, which can be easily changed, eLife staff will do this in order to keep automation optimised. 

####Output:
At the end of the eLife production QC process all components are zipped up and delivered to an eLife AWS bucket **TBC**

- Zip file name: elife-12345-r1.zip
- If reprocessed r1 suffix will be replaced with r2 suffix (zipped file). The naming convention for all actual files remains unchanged, even if the files themsleves changed.

####Turnaround time:
eLife staff aim to do this task on the day the author submits their corrections.

####Volume:
All content will go through this process.


##final delivery of files


####Expectations:
Unless there are changes that cannot be automated in the above two steps, there will be no need to see a revision and eLife staff should be able to automate delivery of final content at the end of their process.
If not, they will require another version using the ECS tool to be delivered to them, and this will or will not be shared with the author.


####Output:
All components are zipped up and delivered to an eLife AWS bucket **TBC**

- Zip file name: elife-12345-r1.zip
- If reprocessed r1 suffix will be replaced with r2 suffix (zipped file). The naming convention for all actual files remains unchanged, even if the files themsleves changed.


####Turnaround time:
If revision cycles occur, expected redelivery of content throguh ECS to Production staff within 12 hours.
If on final sign off manual intervention is required by vendor before delivery to the online platform, 6 hours is allowed for this process.

####Volume:
All content will go through this process.

##final delivery of files - process
There needs to be a mechanism of either informing the publishing platform to pick up the files from the revisions bucket OR for the final sign off from production to be the indication that final files should be delivered somewhere different, to kick off the publishing process.
The production system knows to strip/ignore the revision number from the zip file, this is only used for production tracking of content.

##Non research article content
The key components of non-research content are:
Commissioned and process is managed by an in house team called the "Features Team"
Submission system is used to a limited extend in the tracking of this content.

Currently the features team are shoehorning content into the submission system author screens in order to generate XML metadata output. It would be the preference that they follow a template Word file and only input the content into the submission system to generate a DOI. Therefore the XML metadata could be thrown away with the exception of recording the DOI and the Word file would be the source of all content and metadata.

####Insights
These are commissioned commentaries on particularly interesting research articles. They are commissioned on acceptance of the original research article and thus can delay the publication of that article as they are published together and linked. Therefore, once in the prodcution system these items need to be processed as quickly as possible.
With the exception of a few differences in the XML, and the besoke nature of the display fo the author affiliation details, this content is very simple and non-complex.

####Feature 1
These are commissioned opinion pieces. With the exception of a few differences in the XML, and the besoke nature of the display fo the author affiliation details, this content is very simple and non-complex.

####Feature 2
These are commissioned research pieces. They follow the template of a research article, with some minor differences.
The metadata from the Submission system would be used in this case.

####Editorials
These are commissioned editoral pieces. With the exception of a few differences in the XML, and the besoke nature of the display fo the author affiliation details, this content is very simple and non-complex.

##Press content
