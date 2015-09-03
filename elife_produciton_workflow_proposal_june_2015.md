# eLife production workflow proposal June 2015

See <https://github.com/elifesciences/elife-vendor-workflow-config/blob/master/elife_file_naming_proposal_2015-05-28.md>
for file naming requirements.

Until eLife's own platform is live, we'll require delivery of files for HighWire to go to HighWire direct, as well as to the eLife bucket elife-articles-hw.

######General note on turnaround times:
The vendor works until 3.30pm UK time.
Therefore, where their turnaround times are specified in hours, this excludes the period of from 3.30pm UK time to 3.30am UK time the following day.
Indian Bank holidays - a list of which will be supplied.
**ExeterPremedia please supply**

######General note on new procedure (for production):
Production now export from the "Export System" as soon as an article enters this stage (no QC checks)
No manual movement on PaW between the stages - all movement is done on ECS and that is messaged back to PaW
The ECS stages will mirror PaW stages.


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
- appendix asset file, for example, figure
- author response asset file, for example, figure

####Expectations:
At the start of this process the Word/LaTex file is converted to an HTML file, and overlaid on the XML metadata. Any conflicts in the affiliations and author names: the Word/LaTex file is seen as the source of truth and overwrite the EJP output. The EJP output is seen as the source of truth for:
- article type and article info/publisher info
- Reviewing editor details
- Related article links
- Keywords/Major research area/research organism
- Funding
- Author contributions
- Conflicts of interest
- Copy right details
- Datasets


Track changes - only italicisation from pre-editing needs to be available for author to view, with copy edited changes. **This is an enhancement - release date TBD**

For more detailed description of the pre-editing process see: **ExeterPremedia please provide rules document**.

####Output:
At the end of the pre-editing process all components are zipped up and delivered to an eLife AWS bucket: elife-production-preedited

A SOAP message is delivered to PaW to push the article onto the next stage
This message will also include additional metadata details: MS pages and word count.

- Main XML file
- XML file of EJP XML converted: file naming: elife-00000-EJP.xml
- All asset files are converted/sized/renamed as appropriate
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
- SOAP message to PaW to move article to next stage: 

Please see EJP processing instructions in the XML metadata output to determine which level of copy editing is required (<https://github.com/elifesciences/elife-vendor-workflow-config/blob/master/eLife%20JATS%20processing%20instructions%20xml.xlsx>):

`<custom-meta><meta-name>Copy editing requirement</meta-name><meta-value>2</meta-value></custom-meta<custom-meta>`
Values 0 and 1 require pre-editing only
Value 2 is an ExeterPremedia copy edit
value 3 is an eLife UK freelance copy edit

Note: The SOAP message to PaW depends on what level of copy editing is required.

If NO copy editing required the article should be moved to: Publisher: Check content
If ExeterPremedia copy editing required, should be moved to: Copyeditor: Copy edit
If external freelance copyediting required, should be moved to: Publisher: Assign copy editor

####Turnaround time:
It is expected this process will take 15 minutes of operator time.
The allowed time for the vendor is 24 hours to complete this step.

####Volume:
It is anticipated that at current publishing volumes up to 5 articles coupld be accepted on one day. However, there are peaks and troughs and we have seen periods of days without acceptances and instances of bunching up where 7-8 have been accepted in one day.


####PaW workflow exceptions:
No feature content is copy edited or expects Decision Letter/Response or Digest.
Therefore, for all feature content move on PaW/ECS from Content processor: Pre-edit file to Publisher: OK proof to author.


## Copy editing

####Expectations:

- Copy editor edits on ECS, and all components of the article are available when editing
- If any changes to assest(s) are required, copy editor will either download, edit and reload, or add  Author Queries (AQs), asking author to resupply during the author proofing process 
- All copy editing changes are tracked and are available to the author and production to view when checking the proof.

If level 3 copy editing required the article will enter Publisher: Assign copy editor, on PaW and ECS. ECS will deliver an email to production to log into ECS and assign to a copy editor. Once this is done, ECS will send the email to the chosen copy editor with a link.

**eLife to provide list of freelance copy editors and their email addresses, as well as template email text for the message**


####Output:
At the end of the copy editing process all components are zipped up and delivered to an eLife AWS bucket: elife-production-copyedited

- XML 
- All asset files
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
 - SOAP message to PaW to move article to next stage: Publisher: Check content
 

####Turnaround time:

- The allowed time for the vendor/freelance copy editor is 2 days to complete this step.

####Volume:

It is anticipated:

- 60% of content will require copy editing by the vendor
- 30% will not require a copy edit
- 10% will be copy edited onshore by eLife UK freelancers.


####Publisher: Check content
Once content is copy edited it is moved to this queue by ExeterPremedia.
eLife production staff will review the content and then move to the next stage on ECS.
We anticipate this stage is a transition stage only and will be removed once everything is bedded in.


####Output:
 - SOAP message to PaW to move article to next stage



##Decision letter and response

####Expectations:
These items are not ready at the point of export. The turnaround time for them to be produced is 3-5 days. On completion, they will be delivered by email using a template email.
When these are delivered they should be moved to Publisher: Deliver letters on PaW

Note, there can be figures/tables/videos in the author response.
We anticipate this step will require input at the vendor end.
There is a slim chance that these items are delivered before the content reaches Publisher: check content.

**Questions to ExeterPremedia: How should we deal with this in SOAP messages?**


####Output:
Once a decision letter and response and assets (if any) are delivered by email to ExeterPremedia they should be processed and made available on ECS.

Decision letter and response components are zipped up and delivered to an eLife AWS bucket: elife-production-letters

- HTML file - follow file naming convention with .html suffix
- Asset files of the author response component are converted/sized/renamed as appropriate
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
- SOAP message to PaW to move article to next stage: Publisher: Deliver digest
 
**Questions to ExeterPremedia: Is it easier to deliver just the decision letter/response/assets to the AWS bucket or ALL the items?**

####Turnaround time:

- If there are no problems, this should process automaticallly. If there are complications we request a 12 h turnaround time.

**Questions to ExeterPremedia: Is that TAT OK?**

####Volume:

Most research content has a decision letter and response, but occassionally an article is published without both or one of these components.

**Questions to ExeterPremedia: How should we indicate to you if either/both these items are not going to be published and can you automatically skip the Publisher: Deliver lettersContent processor: Process letters stages on PaW?**

##Digest
####Expectations:
This is the final expected item for a research article before it can be delivered to the author. It is a standard piece of simple content.

It will be delivered by email using a template email.
When delivered it should process automatically into the article and the article moved to the next stage.

####Output:

- Deliver Word file of Digest to eLife AWS bucket: elife-production-digest
- SOAP message to PaW to move article to next stage: Publisher: OK proof to author

####Turnaround time:

- If there are no problems, this should process automaticallly. If there are complications we request a 6 h turnaround time.

**Questions to ExeterPremedia: Is that TAT OK?**

####Volume:
All research articles have a Digest.


##Proof to author

####Expectations:
There is a temporary stage after all content is ready "Publisher: OK proof to author" - this is potentially transition stage and will be removed once processes are bedded in.

eLife production staff will review the content and then move to the next stage on ECS. Tis will generate the change on PaW.


**Questions to ExeterPremedia: Can the Figures PDF be incorporated into the author proof stage on ECS?**

####Output:
- email to author containing link to their article on ECS
- all components are zipped up and delivered to an eLife AWS bucket: elife-production-authorproof
- XML file 
- PDF file
- PDF figures fix
- Asset files of the author response component are converted/sized/renamed as appropriate
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
- SOAP message to PaW to move article to next stage: Publisher: OK proof to author


####Turnaround time:
NA


####Volume:
All content will go thorugh this process


##Author corrections

####Expectations:
Author will edit their content, move components around on the PDF representation view, and potentially upload new versions of figures, videos etc.
It is anticipated that most changes will be done automatically, but in rare circumstances the author will not be able to directly input their changes and regenerate their proof.

**Could we add an SLA that 90% will not require additional intervention by ExeterPremedia? Later - after 4 months live**

####Output:
At the end of the author correction process all components are zipped up and delivered to an eLife AWS bucket: elife-production-authorcorrected
- XML file 
- PDF file
- PDF figures fix
- Asset files of the author response component are converted/sized/renamed as appropriate
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed
- SOAP message to PaW to move article to next stage: Publisher: Check author changes

####Turnaround time:
Authors are given 2 days to complete this process, however, they often take longer.
We'd like automatic chasing mechanisms to be inplemented. Details of which **Built into system - need to send EP the details - ie times and who and email text**

####Volume:
All content will go through this process.



##eLife production staff QC

####Expectations:
eLife production staff vet all changes and where authors have added a comment rather than an edit, which can be easily changed, eLife staff will do this in order to keep automation optimised. 

####Output:
At the end of the eLife production QC process all components are zipped up and delivered to an eLife AWS bucket: elife-production-productionchecked

- Zip file name: elife-12345-r1.zip
- If reprocessed r1 suffix will be replaced with r2 suffix (zipped file). The naming convention for all actual files remains unchanged, even if the files themsleves changed.

####Turnaround time:
eLife staff aim to do this task on the day the author submits their corrections.

####Volume:
All content will go through this process.

####PaW workflow exceptions:
Feature content goes through an additional step before the content is returned to the production staff: Publisher: Feature staff check author changes. The output from this stage is also required to be sent to it's onw AWS bucket: elife-production-featurechecked

**Questions to ExeterPremedia: Will you add this step on ECS for feature content only? YES**


##final delivery of files

####Expectations:
Unless there are changes that cannot be automated in the above step, there will be no need to see a revision and eLife staff should be able to automate delivery of final content at the end of their process.
If not, they will require another version using the ECS tool to be delivered to them, and this will or will not be shared with the author.

If another version is required the results of the author/production QC steps should move the content to Content processor: Deliver revised ECS view in PaW via a SOAP feed.
Once available to production again they should be moved on PaW to Publisher: Check final version.
The output from this stage is also required to be sent to it's onw AWS bucket: elife-production-revised
Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actual files remain unchanged in naming convention, even if changed

If another version is NOT required  the results of the authour/production QC process move to:  Publisher: Ready to load online in PaW via a SOAP feed.

There is another stage that indicated delivery of final files to the final AWS bucket:
The production staff need to move the content to Content processor: Upload online.

Once this is moved, the output is finalised and publication ready. All components are zipped up and delivered to an eLife AWS bucket: elife-production-final

This will basically be a repeat of the most recent version that was delivered to elife-production-revised, but the delivery to AWS bucket: elife-production-final will be the trigger to the eLife production system to start the publication process.


####Turnaround time:
If revision cycles occur, expected redelivery of content throguh ECS to Production staff within 12 hours.
If on final sign off manual intervention is required by vendor before delivery to the online platform, 6 hours is allowed for this process.

####Volume:
Expectation is that less than 10% of content will go through this process.

##Non research article content


##Press content


##Correction procedure

