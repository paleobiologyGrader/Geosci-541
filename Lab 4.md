## Problem set 1

> Fantastic Job 20/20

#### Question 1:

````R
> apply(PresencePBDB,1,sum)
    Pennsylvanian  Early Ordovician Middle Ordovician   Late Ordovician 
              133                24                37                66 
       Llandovery           Wenlock            Ludlow           Pridoli 
               78                80                92                73 
    Mississippian    Early Devonian   Middle Devonian     Late Devonian 
              146               111               118                87 
       Cisuralian     Late Jurassic            Eocene   Late Cretaceous 
              130               189               600               375 
 Early Cretaceous   Middle Jurassic         Paleocene         Oligocene 
              276               179               457               518 
          Miocene    Early Jurassic       Pleistocene       Guadalupian 
              602               169               522               157 
  Middle Triassic     Late Triassic          Pliocene         Lopingian 
              124               186               568               153 
   Early Triassic 
               84 
````

In Miocene, there are 602 unique genera
In Early Jurassic, there are 169 unique genera
In Late cretaceous, there are 375 unique genera
In Pennsylvanian, there are 133 unique genera.

#### Question 2:

````R
> PresencePBDB[,1]
    Pennsylvanian  Early Ordovician Middle Ordovician   Late Ordovician 
                1                 0                 0                 1 
       Llandovery           Wenlock            Ludlow           Pridoli 
                0                 0                 0                 0 
    Mississippian    Early Devonian   Middle Devonian     Late Devonian 
                1                 0                 1                 1 
       Cisuralian     Late Jurassic            Eocene   Late Cretaceous 
                1                 0                 0                 0 
 Early Cretaceous   Middle Jurassic         Paleocene         Oligocene 
                0                 0                 0                 0 
          Miocene    Early Jurassic       Pleistocene       Guadalupian 
                0                 0                 0                 1 
  Middle Triassic     Late Triassic          Pliocene         Lopingian 
                0                 0                 0                 1 
   Early Triassic 
                1 
````

There are 29 geologic epochs in this dataset

#### Question 3:

````R
> which(PresencePBDB[,"Mytilus"]==1)
         Pridoli   Early Devonian       Cisuralian    Late Jurassic 
               8               10               13               14 
          Eocene  Late Cretaceous Early Cretaceous  Middle Jurassic 
              15               16               17               18 
       Paleocene        Oligocene          Miocene   Early Jurassic 
              19               20               21               22 
     Pleistocene  Middle Triassic    Late Triassic         Pliocene 
              23               25               26               27 
  Early Triassic 
              29 
````

Pridoli, Early Devonian, Cisuralian, Late Jurassic, Eocene, Late Cretaceous, Early Cretaceous, Middle Jurassic, Paleocene, Oligocene, Miocene, Early Jurassic, Pleistocene, Middle Triassic, Late Triassic, Pliocene, and Early Triassic contain specimens of the genus Mytilus.

#### Question 4:

We can infer that Mytilus was also present in middle and late Devonian, Mississippian, Pennsylvanian, Guadalupian, and Lopingian. The reason is that the fossil records of Mytilus were found both before and after these epochs, so it is highly possible that Mytilus was also present in the intervals. 

## Problem Set 2:

#### Question 1

````R
> NewMatrix<-PresencePBDB[c("Pleistocene","Miocene"),]
> Sum<-apply(NewMatrix,2,sum)
> table(Sum)
Sum
  0   1   2 
287 106 509 
> 509/(106+509)
[1] 0.82764228
````

#### Question 2:

Distance = 1-0.82764228 = 0.1723577

#### Question 3:

````R
> install.packages(“vegan”)
> library(vegan)
> NewMatrix<-PresencePBDB[c("Pleistocene","Miocene"),]
> vegdist(NewMatrix, method="jaccard", binary=FALSE, diag=FALSE, upper=FALSE,
+        na.rm = FALSE,) 
        Pleistocene
Miocene   0.1720779
````

#### Question 4:

````R
> NewMatrix<-PresencePBDB[c("Pleistocene", "Pliocene", "Miocene", "Oligocene", "Eocene", "Paleocene"),]
> vegdist(NewMatrix, method="bray", binary=FALSE, diag=FALSE, upper=FALSE,
+         na.rm = FALSE,) 
                Pleistocene  Pliocene   Miocene Oligocene    Eocene
Pliocene    0.2792413                                        
Miocene     0.3846615 0.3230128                              
Oligocene   0.5278826 0.4721530 0.4359682                    
Eocene      0.5554770 0.5089442 0.4691801 0.4365843          
Paleocene   0.6559233 0.6227881 0.6125356 0.5374663 0.4669565
````

Paleocene and Pleistocene are the most dissimilar, since the distance index is closer to 1.

## Problem Set 3:

#### Question 1

````R
> RandomEpochs<-PresencePBDB[c("Pliocene","Oligocene","Paleocene","Early Cretaceous","Late Jurassic","Middle Jurassic"),]
````

## Question 2:

````R
> vegdist(RandomEpochs, method="bray", binary=FALSE, diag=FALSE, upper=FALSE,
+         na.rm = FALSE,) 
                  Pliocene Oligocene Paleocene Early Cretaceous Late Jurassic
Oligocene        0.4721530                                                   
Paleocene        0.6227881 0.5374663                                         
Early Cretaceous 0.8283828 0.8010850 0.7057325                               
Late Jurassic    0.9010332 0.8779956 0.8198758        0.5311355              
Middle Jurassic  0.9120998 0.8913831 0.8219814        0.5912409     0.3882064
````

Pliocene and Middle Jurassic are the most dissimilar.

#### Question 3

Pliocene, Oligocene, Paleocene, Early Cretaceous, Late Jurassic, Middle Jurassic
Two poles are Pliocene and Middle Jurassic. Rest of the epochs are arranged by their similarity to the poles. If one epoch is more similar to a pole, it is arranged closer to the pole.

#### Question 4:
The geological timescale is controlling the gradient, meaning that the epochs that are closer together in time share more similarities.

#### Question 5:
The reason that there is a high dissimilarity between the Early Cretaceous and Paleocene epochs is that there was a huge extinction event between these two epochs called K/T extinction. This extinction caused mass extinction of species and this is probably why there is a high dissimilarity between Early Cretaceous and Paleocene epochs.

## Problem set 4

#### Question 1:

````R
> Ordovician<-downloadPBDB(Taxa=c("animalia"),StartInterval="Ordovician",StopInterval="Ordovician")
````

#### Question 2:

````R
> Ordovician<-cleanGenus(Ordovician)
````

#### Question 3:

````R
> CommunityMatrix<-abundanceMatrix(Ordovician,SampleDefinition="geoplate")
> CulledMatrix<-cullMatrix(CommunityMatrix,minOccurrences=2,minDiversity=25)
````

#### Question 4:

````R
> MatrixDCA<-decorana(CulledMatrix)
> plot(MatrixDCA,display="sites")
> tapply(Ordovician[,"paleolon"],Ordovician[,"geoplate"],mean)
> tapply(Ordovician[,"paleolat"],Ordovician[,"geoplate"],mean)
````

Orientation of samples along either axis 1 or axis 2 is not related to the average latitude or longitude of each plate by comparing the values.

