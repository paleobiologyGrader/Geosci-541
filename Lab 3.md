> 17.1/20

## Exercise questions 1
#### Question 1 
There are 704 collections associated with this reference

#### Question 2
The reference ID number for the the article is 24429

#### Question 3
Give credits to the person who first published the taxon.

#### Question 4:
Class: Strophomenata; order: Strophomenida; family: Strophomenidae; genus: Strophomena; species: planumbona

#### Question 5:
The data was collected in Union county

#### Question 6:
The data was collected from ordovician period.

#### Question 7:
Liberty is the geologic formation where the data was found.

## Exercise Questions 2
#### Question 1: 
Different colors represent occurrences from different period of time.

#### Question 2:
Belgian, UK, and US

#### Question 3:
Cincinnati is the city with the most occurrences of Ambonychia.

#### Question 4:
Ordovician is the period that has the most Ambonycia occurrences.

#### Question 5:
Most occurrences of Ambonychia arrayed parallel to the equator.

#### Question 6:
Ambonychia belongs to the order of Myalinida.

## Exercise Questions 3
#### Question 1:
https://paleobiodb.org/data1.2/colls/list.json?datainfo&rowcount&base_name=Ambonychia&strat=Lexington Limestone

#### Question 2: 
https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Mammal&taxon_reso=genus&interval=Paleocene,Oligocene

#### Question 3: 
https://paleobiodb.org/data1.2/taxa/opinions.csv?datainfo&rowcount&base_name=Testudines&rank=order&interval=mesozoic&op_type=all

#### Question 4:
https://paleobiodb.org/data1.2/colls/list.csv?datainfo&rowcount&base_name=Aves, Marsupialia, Sirenia&cc=US

#### Question 5: 
<strike>https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Ficus&taxon_reso=genus</strike>
> You need to use Gastropoda:Ficus to ensure that you get Ficus the snail and not the plant. -1 points.

## Exercise Questions 4
#### Question 1:
Gastrocopta belongs to the family of Gastrocoptidae.

#### Question 2:
That was the age of Aptian.

#### Question 3:
The age of the oldest occurrence of Gastrocopta is Miocene.
> No, Eocene. -1 points

#### Question 4:
The occurrence located in the extratropics when it was alive.
> No, Tropics -1 points

#### Question 5:
They are found in Kotodzha formation and Raiga formation.

## Exercise Questions 5
#### Question 1:
> URL<-"https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Pliocene"
> Derek<-read.csv(URL,row.names=1)

#### Question 2:
> dim(Derek)
[1] 39 12

#### Question 3:
The call used the collections route.

#### Question 4:
Genus is Mammut and colloquial name is Mastodon. The age is limited to Pliocene.

#### Question 5:
https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene

#### Question 6:
https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene&Show=Paleoloc

## Writing your own API function in R

> Good Job

````R
> downloadPBDB<-function(taxon,interval){
+ URLpt1<-c("https://paleobiodb.org/data1.2/occs/list.csv?base_name=")
+ URLpt2<-c("&interval=")
+ URL<-paste(URLpt1,taxon,URLpt2,interval,sep="")
+ Data<-read.csv(URL,row.names=1)}
> 
> AbraData<-downloadPBDB(taxon="Abra",interval="Pleistocene")
> AbraData[1:6,1:6]
       record_type reid_no flags collection_no identified_name identified_rank
94761          occ      NA    NA          7108   Abra aequalis         species
256368         occ      NA    NA         20604   Abra aequalis         species
256386         occ      NA    NA         20606   Abra aequalis         species
425385         occ      NA    NA         41501   Abra aequalis         species
427341         occ      NA    NA         41705   Abra aequalis         species
427901         occ      NA    NA         41740   Abra aequalis         species

> TRexData<-downloadPBDB(taxon="Tyrannosaurus",interval="Mesozoic")
> TRexData[1:6,1:6]
       record_type reid_no flags collection_no       identified_name
139292         occ   22878    NA         11917     Tyrannosaurus rex
139293         occ      NA    NA         11918 Tyrannosaurus cf. rex
219998         occ      NA    NA         22654     Tyrannosaurus rex
220009         occ      NA    NA         22657     Tyrannosaurus rex
280101         occ      NA    NA         26760     Tyrannosaurus rex
291021         occ      NA    NA         14640 Tyrannosaurus cf. rex
       identified_rank
139292         species
139293         species
219998         species
220009         species
280101         species
291021         species
````

## Morphologic Measurements
#### Question 1:
Glyptophiceras sinuatum:1,3, 4,7,8,9,10,13,15,16,17,19,20,21,22,25
Submeekoceras mushbachanum: 5, 11, 12, 23, 24
Xenoceltites variocostatus: 6, 14, 18
I grouped them this way based on the ratio of width/diameter. The Glyptophiceras sinuatum has the smallest ratio, the Xenocelitites variocostatus has the largest ratio, and the Submeekoceras mushbachanum has the intermediate ratio.

#### Question 2:
The first two persons to name this species were Grayard and Bucher (2008)
“Smithian (Early Triassic) ammonoid faunas from northwestern Guangxi (South China): taxonomy and biochronology”<-name of the article

#### Question 3

> You forgot to answer the last question! -2 points.
