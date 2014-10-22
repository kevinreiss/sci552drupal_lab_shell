# SILS 663 Drupal Demonstration Modules

## Description

A set of sample content types and taxonomy definitions corresponding to
the simple VRA demo presented in class. Also contains the a basic CSV
importer for the "Image" content type with a sample import file that can
be used. 

Append all the admin paths to the base URL of your drupal site to access
the menu options at that path. If your URL is http://mydrupalsite.com
the path the content types listings would be
http://mydrupalsite.com/admin/structure/types.

These examples are a very basic implementation of the VRA Core Schema
http://www.vraweb.org/projects/vracore4/. 


## Content Types, Importers, and Views Installed by Demo Modules

### Content Types at admin/structure/types

* Work
* Image
* Collection
* License


### Taxonomies at admin/structure/taxonomy

* Image Tags - Free Tags that can be assinged to "Image Content Types"
* Locations - Utilized by the "Work" content type
* Image Work Types - Work types that can be assigned to the "image"
content type.
* Work Types - Work types that can be assigned to the "work" content
type.

### Sample Importer at admin/structure/feeds

* Flickr Importer - Maps data pulled from flickr into the "Image Content
Type"
  
### Views Installed at admin/structure/views

* Basic Image Gallery find at http://mysite.com/gallery
* List of Images that have been associated with Works find at
  http://mysite.com/catalog

## To Install

1. Have a functioning Drupal instance
2. Install the following Drupal modules
   1. Feeds 
   2. Feeds Tamper
   3. Field Group
   4. Entity 
   5. Entity Reference
   6. Date
   7. Features
   8. Ctools
3. Download and unzip the code from github
   https://github.com/kevinreiss/sils663demo/zipball/master
5. The extracted directory should be named something like
   "kevinreiss-sils663demo-bff694d"  
6. Rename the directory to "custom" and copy the entire folder to the sites/all/modules directory of your Drupal installation
   directories
7. Activate these two modules under the "features" at admin/structure/features
8. Try adding some data. 


## Sample Data Import

A very brief sample CSV import file that can be used as the basis for a
batch import is also included. This file contains
data pulled from Flickr via the Flickr API. The example comes from
collections that are available in Flickr's "Commons"

Several sample csv files are provided. These contain images of various
New York City Bridges, Parks, and Landmarks. These can be found in the
"sample_images" directory.

### To Use

1. Visit the "Feeds" Import  at import/flickr_importer
2. Upload the file "commons_central_park_drupal.csv"
3. Go to admin/content and confirm content has been added properly

### Import images into Drupal

The column "url" in the spreadsheet contains the URL to the actual image
on Flickr. If a Drupal Field is defined as a "File" or "Image" (Image in
this case) the importer will go fetch the image at the URL and store it
within Drupal. See admin/structure/feeds/flickr_importer/mapping for the
individual field mappings, see
admin/structure/feeds/flickr_importer/settings/FeedsNodeProcessor for
the overall settings for the importer. 

### Mapping Tags into Taxonomies

The column "tags" is mapped to the the taxonomy "Image
Tags" in the "Image" content type. In order for Drupal to process a
field as tags a delimiter needs to be consistently used to seperate
these tags into discrete token. In this the two characters "//" are
used. Drupal's feeds tamper module can be used to pre-process values
before they are loaded into the system. I had one processor set-up to
split the tags columns at the "//" characters. See the "explode"
processor set up for tags at
admin/structure/feeds/tamper/list/flickr_importer.  

### Importing other taxonmies 

Some very basic taxomies for locations, work types and image work types are
provided. These are in the "sample_taxonmies" directory. This can be imported using the taxonomy CSV module,
http://drupal.org/project/taxonomy_csv. 


## Going Further With Flickr

If you'd like to try your hand at downloading batches of data from
flickr consult and modify this GIST at https://gist.github.com/3881807. This script
utilizes ruby and the "flickraw" gem to interact with the API and
download data from flickr.

## Questions
Contact Kevin Reiss at kevin.reiss [ at ] gmail dot com 
