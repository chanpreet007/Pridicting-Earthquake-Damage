## Features
The dataset mainly consists of information on the buildings' structure and their legal ownership. Each row in the dataset represents a specific building in the region that was hit by Gorkha earthquake.

There are 39 columns in this dataset, where the building_id column is a unique and random identifier. The remaining 38 features are described in the section below. Categorical variables have been obfuscated random lowercase ascii characters. The appearance of the same character in distinct columns does not imply the same original value.

Description
geo_level_1_id, geo_level_2_id, geo_level_3_id (type: int): geographic region in which building exists, from largest (level 1) to most specific sub-region (level 3). Possible values: level 1: 0-30, level 2: 0-1427, level 3: 0-12567.
count_floors_pre_eq (type: int): number of flo
ors in the building before the earthquake.
age (type: int): age of the building in years.
area_percentage (type: int): normalized area of the building footprint.
height_percentage (type: int): normalized height of the building footprint.
land_surface_condition (type: categorical): surface condition of the land where the building was built. Possible values: n, o, t.
foundation_type (type: categorical): type of foundation used while building. Possible values: h, i, r, u, w.
roof_type (type: categorical): type of roof used while building. Possible values: n, q, x.
ground_floor_type (type: categorical): type of the ground floor. Possible values: f, m, v, x, z.
other_floor_type (type: categorical): type of constructions used in higher than the ground floors (except of roof). Possible values: j, q, s, x.
position (type: categorical): position of the building. Possible values: j, o, s, t.
plan_configuration (type: categorical): building plan configuration. Possible values: a, c, d, f, m, n, o, q, s, u.
has_superstructure_adobe_mud (type: binary): flag variable that indicates if the superstructure was made of Adobe/Mud.
has_superstructure_mud_mortar_stone (type: binary): flag variable that indicates if the superstructure was made of Mud Mortar - Stone.
has_superstructure_stone_flag (type: binary): flag variable that indicates if the superstructure was made of Stone.
has_superstructure_cement_mortar_stone (type: binary): flag variable that indicates if the superstructure was made of Cement Mortar - Stone.
has_superstructure_mud_mortar_brick (type: binary): flag variable that indicates if the superstructure was made of Mud Mortar - Brick.
has_superstructure_cement_mortar_brick (type: binary): flag variable that indicates if the superstructure was made of Cement Mortar - Brick.
has_superstructure_timber (type: binary): flag variable that indicates if the superstructure was made of Timber.
has_superstructure_bamboo (type: binary): flag variable that indicates if the superstructure was made of Bamboo.
has_superstructure_rc_non_engineered (type: binary): flag variable that indicates if the superstructure was made of non-engineered reinforced concrete.
has_superstructure_rc_engineered (type: binary): flag variable that indicates if the superstructure was made of engineered reinforced concrete.
has_superstructure_other (type: binary): flag variable that indicates if the superstructure was made of any other material.
legal_ownership_status (type: categorical): legal ownership status of the land where building was built. Possible values: a, r, v, w.
count_families (type: int): number of families that live in the building.
has_secondary_use (type: binary): flag variable that indicates if the building was used for any secondary purpose.
has_secondary_use_agriculture (type: binary): flag variable that indicates if the building was used for agricultural purposes.
has_secondary_use_hotel (type: binary): flag variable that indicates if the building was used as a hotel.
has_secondary_use_rental (type: binary): flag variable that indicates if the building was used for rental purposes.
has_secondary_use_institution (type: binary): flag variable that indicates if the building was used as a location of any institution.
has_secondary_use_school (type: binary): flag variable that indicates if the building was used as a school.
has_secondary_use_industry (type: binary): flag variable that indicates if the building was used for industrial purposes.
has_secondary_use_health_post (type: binary): flag variable that indicates if the building was used as a health post.
has_secondary_use_gov_office (type: binary): flag variable that indicates if the building was used fas a government office.
has_secondary_use_use_police (type: binary): flag variable that indicates if the building was used as a police station.
has_secondary_use_other (type: binary): flag variable that indicates if the building was secondarily used for other purposes.
Feature data example
Here's an example of one of the rows in the dataset so that you can see the kinds of values you might expect in the dataset. Some are numeric, some are categorical, and there are often missing values. 

field	value
geo_level_1_id	8
geo_level_2_id	396
geo_level_3_id	1108
count_floors_pre_eq	2
age	15
area_percentage	4
height_percentage	7
land_surface_condition	t
foundation_type	r
roof_type	n
ground_floor_type	v
other_floor_type	q
position	s
plan_configuration	d
has_superstructure_adobe_mud	1
has_superstructure_mud_mortar_stone	1
has_superstructure_stone_flag	0
has_superstructure_cement_mortar_stone	0
has_superstructure_mud_mortar_brick	0
has_superstructure_cement_mortar_brick	1
has_superstructure_timber	0
has_superstructure_bamboo	0
has_superstructure_rc_non_engineered	0
has_superstructure_rc_engineered	0
has_superstructure_other	1
legal_ownership_status	v
count_families	1
has_secondary_use	0
has_secondary_use_agriculture	0
has_secondary_use_hotel	0
has_secondary_use_rental	0
has_secondary_use_institution	0
has_secondary_use_school	0
has_secondary_use_industry	0
has_secondary_use_health_post	0
has_secondary_use_gov_office	0
has_secondary_use_use_police	0
has_secondary_use_other	0
Performance metric
We are predicting the level of damage from 1 to 3. The level of damage is an ordinal variable meaning that ordering is important. This can be viewed as a classification or an ordinal regression problem. (Ordinal regression is sometimes described as an problem somewhere in between classification and regression.)

To measure the performance of our algorithms, we'll use the F1 score which balances the precision and recall of a classifier. Traditionally, the F1 score is used to evaluate performance on a binary classifier, but since we have three possible labels we will use a variant called the micro averaged F1 score.

Fmicro=2⋅Pmicro⋅RmicroPmicro+Rmicro

where

Pmicro=∑3k=1TPk∑3k=1(TPk+FPk),  Rmicro=∑3k=1TPk∑3k=1(TPk+FNk)

and TP
 is True Positive, FP
 is False Positive, FN
 is False Negative, and k
 represents each class in 1,2,3
.

In Python, you can easily calculate this loss using sklearn.metrics.f1_score with the keyword argument average='micro'. Here are some references that discuss the micro-averaged F1 score further:

Scikit-Learn Documentation
Blog Post
Submission format
The format for the submission file is two columns with the building_id and the damage_grade. The data type of damage_grade is an integer with values of 1,2,3
, so make sure there is no decimal point and no other numbers in your submission. For example 1 would be valid, and 1.0 would not.

For example, if you predicted:

building_id	damage_grade
11456	1
16528	1
3253	1
18614	1
1544	
