#Defining "Suicide Attempt" in Free-text Clinical Notes

##### How to get a text mining algorithm to identify a "suicide attempt" in free-text clinical notes?

First we have to **define** "suicide attempt" in such a way that we try and capture any mention of it clinical notes. Then feed this to the text-mining algorithm so that it can go about identifying mentions of suicide attempt.

So how to define suicide attempt for a text mining algorithm?

_Please note that this is not to define the concept of suicide attempt. This application is not claiming that suicide attempts can be defined in a general way. This is merely an app trying to identify mentions of a suicide attempt in clinical notes to be used as a research variable._

This repo is a record of how I defined suicide attempt, for text mining application and for my future reference:

#### 1) Use key clinical codes
...and/or key features in clinical codes. There are clinical codes supplied by WHO which describe suicide attempt and which have been used in suicide epidemiology literature when describing suicide or suicide attempts. They can be found here: [ICD-10 codes](http://apps.who.int/classifications/icd10/browse/2015/en#/X60-X84)

#### 2) Investigate a random sample from the dataset 

In other words, use the clinical dataset itself and identify the most common and unique mentions of "suicide attempt". 

#### 3) Get clinician input

Ask clinical staff members how they would record suicide attempt in this particular dataset. Show them the list you've generated from doing the above two exercise. Ask they to suggest any relevant terms or phrases. 



***************
I'll list out the terms / phrases i extracted from each "exercise", i've listed above. 


#### 1) Using key clinical codes

Here's the list of ICD-9, ICD-CM and ICD-10 codes from the WHO ICD website. These codes have also been used in suicide epidemiology literature. 

**_Screenshot 1_**
![ICD 9 and ICD-CM codes] (https://cloud.githubusercontent.com/assets/10629155/12849801/76f9833a-cc19-11e5-84c7-84440811e8f3.png) 

**_Screenshot 2_**
![ICD10 Code Screenshot](https://cloud.githubusercontent.com/assets/10629155/12849775/4f10d594-cc19-11e5-90df-b5048e0b2a89.png)

 


**From the lists in Figure 1 and 2, here are the Key Terms I derived to highlight or flag up a suicide attempt****_List derived from ICD 9, ICD 9 CM and ICD 10 codes in Screenshots above_**
		self-inflict*
		self inflict*
		poison*
		self-poison*
		self poison*		hang*		strangl*		strangu*		submer*		cut*		jump*		asphyxiat*		overdose		ingested*		suffocat*		drown*		handgun		rifle		shotgun		lying before		crash*		firearm*		pierc* 		shoot*		stab*		shot		tried to cut [him/her] self		took an overdose		took an OD		tried to poison [him/her] self		tried to suffocate [him/her]self		tried to strangle [him/her]self
		self-damag*
		self damag*		E950		E951 to E952		E953		E954		E955		E956		E957		E958		E959		E980 - E989		E850 - E858
		994.7
		960 - 977		X60		X61		X62		X63		X64		X65		X66		X67		X68		X69		X70		X71		X72		X73		X74		X75		X76		X77		X78		X79		X80		X81		X82		X83		X84		Y87.0		Z72.8		Z91.5

#### 2) Investigate a random sample from the dataset

A random selection of 145 clinical notes (data not shown), each with the term "suici*" or "attempt" mentioned somewhere in the notes. 


	suicide attempt*	attempt* suicide	suicidal behaviour
	attemp to commit suicide	attempt to suicide	suicid* [0, 3] attempts	attempts [1, 4] suicid*	suicid* behaviour	suicid* gesture	attempt* at suicide	attempt to commit suicide	attempt to suicide	attempt at suicide	previous suicide attempt by jumping	previous suicide attempt by hanging	previous suicide attempt by taking	after a suicide attempt	previous attempt to jump off	tried to kill [him / her] self	suicide attempt failed	next time [he/she] attempts suicide	his suicide attempt was not successful	suicide attempt due to depression	following a suicide attempt	attempted to take [his/her] life	first attempt at [his/her] life	attempted to commit suicide	walked in front of motor	walked in front of vehicles	walked in front of moving	walked in front of traffic	attempt on his life	history of suicide attempt*	attempt[ed] / tried to hang herself / himself	overdose	self-poison	[Description of High number] tablets	cut, cutting, lacerat*, burning	hit[ting] herself / himself	burnt herself / himself	self-inflicted injury	submersion
	

#### 3) Clinician Input

Three clinicians, who are actively using the electronic health register in their day to day practice, reviewed the terms above and  gave their input on the above lists and added the following:

	she / he jump[ing/ed] off a / in front of / from	she / he stood in front of a	attempt[ed] / tried to shoot herself / himself	attempt[ed] / tried to drown herself / himself	attempt[ed] / tried to strangle herself / himself
	"intent"	"did you think you would die"
	drowing
	hanging
	take one's life



The above lists were collated to form a Gazateer, which will be used to annotate and classify documents.
 
|                       | **Gold Starndard** |             |         
| -------------         | -------------      | ------------|
| **Training Set**      |  Suicide Attempt   | Not a Suicide Attempt|
| Suicide Attempt       |                    |             |        
| Not a Suicide Attempt |                    |             |        



###Next steps

1) Annotate a gold standard set of documents using standard rules that define suicide attempt.
			Annotated 500 documents as the Gold Standard
			Gold Standard documents had one of the 'suicide attempt' words or phrases mentioned. 
			Following rules were followed:
			To code as Positive, answer the following two questions:
			- Is the reference to 'suicide attempt' a current/recent one? Or is it a reference to a past suicide attempt?

			- if the answer to either of the questions above is 'Yes', then code the reference as 'positive'. Otherwise code as 'negative'/'unknown'. 


2) Annotate a training set 
	Annotated 500 documents to train models. 

3) Build models (using machine learning algorithms) and identify model of best fit, using precision and recall. 
