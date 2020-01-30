# Marine Institute Data Catalogue - Content Types
# Data Documentation for the IFBA Archive

1. [Sample](#Sample)
   1. Sample ID
   1. Contained In
   1. Date Collected
   1. Date Mask
   1. Species
   1. Lab Number
   1. Developmental Stage
   1. Observed Maturity
   1. Approximate Sample Amount
   1. Fish Origin
   1. Geographic Feature
   1. Weight
   1. Length
   1. Fate
   1. Field Comments
   1. Archivist Comments
   1. Tag ID
   1. Tag Type
   1. Maturity
   1. Maturity Determination Method
   1. Sex
   1. Sex Determination Method

1. [Sample Set Container](#Container)
   1. Container ID
   1. Sample Set Container
   1. Sample Type
   1. Sample Set State
   1. Sample Set Compromised
   1. Sample Set Compromised Description
   1. Archive Location
   1. Contact Email
   1. Date Archived
   1. Programme
   1. Number of Samples in Container

   
1. [Archive Location](#archivelocation)
   1. Archive ID
   1. Name
   1. Description
   1. Type
   1. Parent Unit


## Sample
- Machine name: *sample*

The Sample content type is the base content type in the IFBA Archive within the Data Catalogue. It may combine many different parameters, collected at multiple times and locations. A sample is commonly either a fish otolith or scale, which is often held in a coin envelope. The sample data entered into the Data Catalouge is the data that is written on the physical sample. 

A Sample is linked to its storage and retention information and the classification, including licencing, associated with the sample under the Marine Institute's Data Policy.


| Label | Machine Name | Field Type | Required Field | Allowed Number of Values | Notes
| --- | --- | --- | --- | --- | --- |
| Sample ID |  field_sample_id | Integer | Yes | Unlimited | Primary key
| Contained In | field_contained_in | String | Yes | Unlimited | Forgein Key, this links to the Container table
| Species | field_species | Entitiy Reference | Yes | 1 | Reference to term(s) from the *World Register of Marine Species (WoRMS)* |
| Date Collected | field_date_collected | Date | Yes | 1 | The date the sample was collected | 
| Date Mask | field_date_mask | Date | Entitiy Reference | 1 | If month and day not known, put January 1 If month known, but day not, put the first of the month | 
| Lab Number | field_lab_no | String | No | 1 | The ID allocated to the sample by the resarcher who collected the sample | 
| Developmental Stage | field_life_stage | Entity Reference | Yes | 1 | Reference to *ICES Controlled vocab* for adult/juvenille |
| Approximate Sample Amount | field_approximate_sample_amount | Integer | Yes | 1 | The amount within the sample, for example 5 would indicate their are approximately 5 fish scales in the envelope | 
| Fish Origin | field_fish_origin | Entity Reference | No | 1 |  Reference to *ICES Controlled Vocab* for hatchery/wild | 
| Geographic Location Name | field_geographic_location_name | Entity Reference | No | 1 | The location the fish was sampled - Reference to Geographic Feature in the *MI Data Catalouge* | 
| Weight | field_weight | Integer | No | 1 | metric, grams | 
| Length | field_length | Integer | No | 1 | metric, meters | 
| Field Comments | field_field_comments | String | No | Unlimited | Comments made while collecting sample | 
| Archivist Comments | field_archivist_comments | String | No | Unlimited | Comments from person cataloguing sample | 
| Fate | field_fate | Entity Reference | no | 1 | list includes culled/released | 
| Fish Tag Type |  field_fish_tag_type | Field Collection | No | 5 | A field collection, a user can enter up to 5 tags that might have been on the fish | 
| Tag Type |  field_tag_type | Entity Reference | No | 1 | The tag type, floy/carcass | 
| Tag Code ID | field_tag_code_id  | String | No | 1 | The tag id, for example, a floy tag id might be: 452eF3 | 
| Gender | field_gender | Field Collection | Yes | 1 | A field collection, a user can enter multiple gender observations 
| Sex | field_sex  | Entity Reference | Yes | 1 | The gender of the fish | 
| Sex Determination Method | field_sex_source | Entity Reference | Yes | 1 | The method used to characterize gender, dissection/visual | 
| Maturity |  field_maturity | Field Collection | No | 1 |  A field collection, a user can enter multiple gender observations | 
| Maturity |  field_maturity | Entity Reference | No | 1 | Reference to *FishBase Glossary Controlled Vocab* for grilse/smolt | 
| Maturity Determination Method |  field_maturity_determination_met| Entity Reference | No | 1 | How the maturity was determined, field/image |


## Sample Set Container

- Machine name: *container*

The Container content type is a secondary content type in the Data Catalogue (IFBA Archive ). It represents a group of samples and how they are physically held in reality.

| Label | Machine Name | Field Type | Required Field | Allowed Number of Values | Notes
| --- | --- | --- | --- | --- | --- |
| Container ID |  field_container_id | String | Yes | Unlimited | The id of the container that holds all of the samples | 
| Sample Set Container | field_sample_container	 | Entity Reference  | Yes | 1 | The individual sample containter, envelope or slide | 
| Sample Type | field_sample_type_ | Entity Reference  | Yes | 1 | Scales or otoliths | 
| Sample Set State | field_sample_state | Entity Reference  | Yes | 1 | Burned and cracked, unanalysed, etc.. | 
| Sample Set Compromised | field_sample_set_compromised | Boolean | Yes | 1 | yes/no | 
| Sample Set Compromised Description | field_sample_set_compromised_description | String | No | Unlimited | Describe sample set integrity |
| Archive Location | field_archive_location | String | Yes | 1 | links to archive ID, where it is in the physical sample repository | 
| Contact Email | field_contact_email | String | Yes | 1 | ex) irish_national_biochronology_archive@marine.ie | 
| Date Archived | field_date_archived | Date | Yes | 1 | the date the sample was logged and put away | 
| Programme | field_programme | Entity Reference | Yes | Unlimited | Reference to *Programme Taxonomy in MI Data Catalouge* | 
| Number of Samples in Container | field_number_of_samples_in_conta | Integer | No | Unlimited | How many envelopes are in the container? | 


## Archive Location

- Machine name: *Archive Location*

The Archive Location content type is a secondary content type in the Data Catalogue(Newport Archives). It represents where the containers can be found in the Newport Sample Archive.

| Label | Machine Name | Field Type | Required Field | Allowed Number of Values | Notes
| --- | --- | --- | --- | --- | --- |
| Archive ID |  field_archive_id | String | Yes | Unlimited | Primary key, links to container table, archive id and parent unit are self linking | 
| Name | field_name | String | Yes | 1 | The name of the sample repository | 
| Description | field_description | No | 1 | | 
| Type | field_type | Controlled List | Yes | 1 | e.g. Main collection, personal, seperate collection | 
| Parent Unit | field_parent_unit | string | Yes | 1 | e.g. drawer box is in, self links to Archive ID | 
