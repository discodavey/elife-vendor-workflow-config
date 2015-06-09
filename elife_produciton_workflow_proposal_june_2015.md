# eLife produciton workflow proposal June 2015

See <https://github.com/elifesciences/elife-vendor-workflow-config/blob/master/elife_file_naming_proposal_2015-05-28.md>
for file naming requirements.


## Pre-editing

Export from submission system is a package of XML, the author Word file, a PDF representation fo that word file and any associated asset files eg: 


)Generation of file that contains all metadata output from editorial system, cross links the references and other items such as tables and figures, basic automatable house style completed and references styled.

## Copy editing


##Proof to author

##Author corrections

##eLife production staff QC

##final delivery of files



###### `<f-id>`

This is the file id and is the numerical digit that is used to make up part of the DOI for an article (`<article-id pub-id-type="doi">`). For example an eLife article with the following DOI `/10.7554/eLife.06659` will have an f-id of `06659`.


###### `<asset>`

This refers to an asset file related to an article, ie a figure (fig), source code (code), source data (data), media (includes videos, audio and animation) (media), supplementary file (supp), (figures) the figures pdf, reporting standards (repstand).

Should these asset files be present in an appendix or author response, they will take the suffix A or R, respectively before the number, ie: figA or mediaR.

###### `<a-id>`

The `a-id` is the asset id, and indicates the order of an asset in the article. For example an
article with three figures will have the following asset files:

- elife-00012-fig1.tiff
- elife-00012-fig2.tiff
- elife-00012-fig3.tiff

###### `<sub-asset>`

Some assets will have sub-assets, eg figure supplements (figsupp), source data (data), or source code (code). These are indicated by the sub-asset component.

###### `<sa-id>`

Some assets have sub-asset ids, for example, an article with three main figures, where one
figure has three figure supplements, and one figure has two figure supplements will have the following:

- elife-00012-fig1.tiff
- elife-00012-fig1-figsupp1.tiff
- elife-00012-fig1-figsupp2.tiff
- elife-00012-fig1-figsupp3.tiff
- elife-00012-fig2.tiff
- elife-00012-fig3.tiff
- elife-00012-fig3-figsupp1.tiff
- elife-00012-fig3-figsupp2.tiff

###### data

Sometimes there is source data at a parent level, but sometimes assets will have source data files associated with them. These data files are indicated by the presence of a `data` in the filename.

###### `<d-id>`

Assets can have multiple source data files associated with them, and these are distinguished with the
data id.

For example, an article with three main figures, where one figure has three figure supplements, and one figure has two figure supplements, and all have associated data, with some of them having multiple data files, could have the following:

- elife-00012-fig1.tiff
- elife-00012-fig1-data1.csv
- elife-00012-fig1-data2.csv
- elife-00012-fig1-figsupp1.tiff
- elife-00012-fig1-figsupp1-data1.csv
- elife-00012-fig1-figsupp2.tiff
- elife-00012-fig1-figsupp2-data1.csv
- elife-00012-fig1-figsupp3.tiff
- elife-00012-fig1-figsupp3-data1.mol
- elife-00012-fig2.tiff
- elife-00012-fig2-data1.txt
- elife-00012-fig3.tiff
- elife-00012-fig3-data.csv
- elife-00012-fig3-figsupp1.tiff
- elife-00012-fig3-figsupp1-data1.csv
- elife-00012-fig3-figsupp1-data2.csv
- elife-00012-fig3-figsupp1-data3.csv
- elife-00012-fig3-figsupp2.tiff
- elife-00012-fig3-figsupp2-data1.csv
- elife-00012-fig3-figsupp3.tiff
- elife-00012-fig3-figsupp3-data1.csv


###### code

Sometimes there is source code at a parent level, but sometimes assets will have source code files associated with them. These source code files are indicated by the presence of a `code` in the filename.

###### `<c-id>`

Assets can have multiple source code files associated with them, and these are distinguished with the
code id.

For example, an article with a top level source code, two main figures, where one figure has source code, and one figure has one figure supplement with source code:

- elife-00012-fig1.tiff
- elife-00012-fig1-code1.csv
- elife-00012-fig2.tiff
- elife-00012-fig2-figsupp1.tiff
- elife-00012-fig2-figsupp1-code1.csv
- elife-00012-code1.csv


## Zip file naming pattern

###### `<status>`

This is either `poa` (publish on accept) or `vor` (version of record).

##### r`<revision>`

#####Example
- elife-00012-vor-r4.zip contains
- elife-00012.xml
- elife-00012.pdf
- elife-00012-figures.pdf
- elife-00012-fig1.tiff
- elife-00012-fig1-data1.csv
- elife-00012-fig1-data2.csv
- elife-00012-fig1-figsupp1.tiff
- elife-00012-fig1-figsupp1-data1.csv
- elife-00012-fig1-figsupp2.tiff
- elife-00012-fig1-figsupp2-data1.csv
- elife-00012-fig1-figsupp3.tiff
- elife-00012-fig1-figsupp3-data1.mol
- elife-00012-fig2.tiff
- elife-00012-fig2-data1.txt
- elife-00012-fig3.tiff
- elife-00012-fig3-data.csv
- elife-00012-fig3-figsupp1.tiff
- elife-00012-fig3-figsupp1-data1.csv
- elife-00012-fig3-figsupp1-data2.csv
- elife-00012-fig3-figsupp1-data3.csv
- elife-00012-fig3-figsupp2.tiff
- elife-00012-fig3-figsupp2-data1.csv
- elife-00012-fig3-figsupp3.tiff
- elife-00012-fig3-figsupp3-data1.csv


