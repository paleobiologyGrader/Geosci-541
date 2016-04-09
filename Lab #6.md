> 19/20

### Problem set 1

#### Question 1

````R
> nrow(DataPBDB)
[1] 34166
> nrow(MacroPBDB)
[1] 9013
> 34166-9013
[1] 25153
#25153 occurrences were lost.
````

#### Question 2

The reason that so much data were lost is that the Macrostrat database only includes data from few localities. However, PBDB includes the data from the entire world.

## Problem set 2

#### Question 1

````R
> Richness<-specnumber(OrderMatrix, MARGIN = 1)
> sort(Richness)

# 1:Chancellor; 2:Kinzers Fm; 3:Stephen Fm; 4:Marjum Limestone; 5:Wheeler Shale; 6:Langston Fm;
7:Weymouth Fm; 8:Snowy Range Fm; 9:Parker Slate; 10:Forteau Fm (Harkless Fm)  

> CandidateUnits<-c("Chancellor","Kinzers Fm","Stephen Fm","Marjum Limestone","Wheeler Shale","Langston Fm","Weymouth Fm","Snowy Range Fm","Parker Slate","Forteau Fm")
````

#### Question 2:

````R
> GenusFrequencies<-apply(GenusMatrix,2,sum)
````

#### Question 3:

````R
> barplot(table(GenusFrequencies))
````

#### Question 4

We call this type of curved distribution hollow curve   

#### Question 5

````R
> median(GenusFrequencies)
[1] 2
> RareGenera<-which(GenusFrequencies<=2)
````

> Almost, but incomplete -1 points

## Problem set 3:

#### Question 1

````R
> CandidateMatrix<-subset(GenusMatrix[CandidateUnits,])
````

#### Question 2

````R
> PercentShared
      Chancellor       Kinzers Fm       Stephen Fm Marjum Limestone 
       0.5714286        0.2586207        0.3055556        0.3559322 
   Wheeler Shale      Langston Fm      Weymouth Fm   Snowy Range Fm 
       0.2307692        0.1632653        0.6764706        0.1951220 
    Parker Slate       Forteau Fm 
       0.2812500        0.5652174 

Forteau Fm, Chancellor, Weymouth Fm, Marjum Limestone are the four units that are most likely to qualify as Lagerstatten, because they have higher percentage of genera.
````

#### Question 3
Chancellor is a very famous Lagerstatten, because it is Burgess Shale. The significance of Burgess Shale to Paleobiology is that it contains the best record of Cambrian animal fossils. This locality reveals the presence of creatures from the Cambrian explosion.

