# eLife produciton workflow proposal June 2015

See <https://github.com/elifesciences/elife-vendor-workflow-config/blob/master/elife_file_naming_proposal_2015-05-28.md>
for file naming requirements.


## Pre-editing

####Input:

Export from submission system:

1. XML metadata file
2. author Word file
3. PDF representation of that Word file and figure asset files
4. Asset files

Asset files can be any combination of the following: 

- figure 
- figuresupplement 
- supplementary file 
- media (includes videos, audio and animation) 
- source code 
- source data 
- reporting standards 
- appendix asset file, for example figure
- author response asset file, for example figure

####Expectations:
During pre-editing the Word file is converted to an HTML file, and overlaid the XML metadata output to cross check. Any confilicting metadata is added as a query for eLife staff or author. **TBD whether eLife staff see proofs before delivery to author** - anticipate initially we'll have this step in the workflow.

For more detailed description of the pre-editing process see **XXX**.

####Output:

- The HTML file can output publishable eLife JATS XML any time once this process is complete
- All asset files are converted/sized/renamed as appropriate
- At the end of this process all components are zipped up and delivered to an eLife AWS bucket **TBC**
- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actural files remain unchanged in naming convention, even if changed.

####Turnaround time:
It is expected this process will take 15 minutes of operator time. **TBC**
The allowed time for the vendor is 24 hours to complete this step.

####Volume:
It is anticipated that at current publishing volumes up to 5 articles coupld be accepted on one day. However, there are peaks and troughs and we have seen periods of days without acceptances and bunching of up to 7-8 in one day.

## Copy editing

####Expectations:

- Copy editor edits using the tool, and all components of the article are available when editing
- If any changes  to assest(s) required, copy editor will either download, edit and reload, or add  AQs, asking author to resupply during the author proofing process **(TBD)**

####Output:
At the end of the copy editing process all components are zipped up and delivered to an eLife AWS bucket **TBC**

- Zip file name: elife-12345-r1.zip
- Rare, but if reprocessed r1 suffix will be replaced with r2 suffix (zipped file). All actural files remain unchanged in naming convention, even if changed.

####Turnaround time:

- The allowed time for the vendor is 2 days to complete this step.

####Volume:

It is anticipated:

- 50% of content will require copy editing by the vendor
- 40% will not require a copy edit
- 10% will be copy edited onshore by eLife UK freelancers.

##Proof to author



##Author corrections

##eLife production staff QC

##final delivery of files

