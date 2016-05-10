## Problem Set 1

> 20/20

1)
`> TriassicUnits<-read.csv("https://macrostrat.org/api/units?interval_name=Triassic&format=csv")`

2)
````R
> nrow(TriassicUnits)
[1] 838
# I downloaded 838 Triassic units.
````

3)
````R
> TriassicUnits[1:10,]
````

The are mostly igneous rocks; I do not believe these units are relevant for an investigation of fossil preservation, because the hight temperature could have melted the fossil. Moreover, fossils are more commonly found in sedimentary rocks.

4)
b_age is the starting age and t_age is the ending age of each unit.

5)
These units are not constrained to only the Triassic, because some of the units’ starting age is way before Triassic period

## Problem Set 2
1)
`> TriassicUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Triassic&format=csv")`

2)
`> RistrictedTriassicUnits<-TriassicUnits[which(TriassicUnits[,"b_age"]<=252.17&TriassicUnits[,"t_age"]>=201.3),]`

3)

````R
# Cretaceous:
> CretaceousUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Cretaceous&format=csv")
> RestrictedCretaceousUnits<-CretaceousUnits[which(CretaceousUnits[,"b_age"]<=145.5&CretaceousUnits[,"t_age"]>=65.5),]

# Jurassic:
> JurassicUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Jurassic&format=csv")
> RestrictedJurassicUnits<-JurassicUnits[which(JurassicUnits[,"b_age"]<=199.6&JurassicUnits[,"t_age"]>=145.5),]

# Triassic:
>TriassicUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Triassic&format=csv")
>RistrictedTriassicUnits<-TriassicUnits[which(TriassicUnits[,"b_age"]<=252.17&TriassicUnits[,"t_age"]>=201.3),]

# Permian:
> PermianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Permian&format=csv")
> RistrictedPermianUnits<-PermianUnits[which(PermianUnits[,"b_age"]<=298.9&PermianUnits[,"t_age"]>=252.17),]

# Carboniferous:
> CarboniferousUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Carboniferous&format=csv")
>RistrictedCarboniferousUnits<-CarboniferousUnits[which(CarboniferousUnits[,"b_age"]<=359.2&CarboniferousUnits[,"t_age"]>=299),]

# Devonian:
> DevonianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Devonian&format=csv")
> RistrictedDevonianUnits<-DevonianUnits[which(DevonianUnits[,"b_age"]<=419.2&DevonianUnits[,"t_age"]>=358.9),]

# Silurian:
> SilurianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Silurian&format=csv")
> RistrictedSilurianUnits<-SilurianUnits[which(SilurianUnits[,"b_age"]<=443&SilurianUnits[,"t_age"]>=416),]

# Ordovician:
> OrdovicianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Ordovician&format=csv")
> RistrictedOrdovicianUnits<-OrdovicianUnits[which(OrdovicianUnits[,"b_age"]<=485.4&OrdovicianUnits[,"t_age"]>=443.8),]
````

4)
`> UnitFreqs<-c(nrow(CretaceousUnits),nrow(JurassicUnits),nrow(TriassicUnits),nrow(PermianUnits),nrow(CarboniferousUnits),nrow(DevonianUnits),nrow(SilurianUnits),nrow(OrdovicianUnits))`

5.
````R
> UnitFreqsTriassic<-c(nrow(CretaceousUnits),nrow(JurassicUnits),nrow(PermianUnits),nrow(CarboniferousUnits),nrow(DevonianUnits),nrow(SilurianUnits),nrow(OrdovicianUnits))
> mean(UnitFreqsTriassic)
[1] 2425.571
> sd(UnitFreqsTriassic)
[1] 1365.805
> (713-2425.571)/1365.805
[1] -1.253891
#TriassicUnits is 1.253891 SD below the mean
````

6)
No, I don’t think the Triassic has a statistically lower number of units than the other periods, because there is more than 5% chance that this could happen by chance. This can be said because 1.25<1.96, where 95% of the area of a normal distribution falls within. 

7) 
````R
> UnitFreqsTriassicJurassic<-c(nrow(CretaceousUnits),nrow(PermianUnits),nrow(CarboniferousUnits),nrow(DevonianUnits),nrow(SilurianUnits),nrow(OrdovicianUnits))
> mean(UnitFreqsTriassicJurassic)
[1] 2624.167
> sd(UnitFreqsTriassicJurassic)
[1] 1381.018
> (713-2624.167)/1381.018
[1] -1.383883
#Triassic is 1.383883 SD below the mean; It means the Triassic still dose not have a statistically lower number of units than the other periods, because there is still more than 5% chance that this could happen by chance.
````

## Problem Set 3
1)
````R
> URL<-"https://macrostrat.org/api/columns?format=geojson_bare&project_id=1"
> AllMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
> plot(AllMap)
````

2)
````R
>  URL1<-"https://macrostrat.org/api/columns?format=geojson_bare&interval_name=Olenekian&project_id=1&lith_class=sedimentary"
> GotURL1<-getURL(URL1)
> IAMap<-readOGR(GotURL1,"OGRGeoJSON",verbose=FALSE)
> plot(AllMap)
> plot(IAMap,col="#B051A5",add=TRUE)
````

3)
````R
> DataPBDB<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Olenekian",StopInterval="Olenekian")
> points(DataPBDB[c("lng","lat")],pch = 19, col = "blue")
````

4)
````R
> URL2<-"https://macrostrat.org/api/columns?format=geojson_bare&interval_name=Lopingian&project_id=1&lith_class=sedimentary"
> GotURL2<-getURL(URL2)
> LopMap<-readOGR(GotURL2,"OGRGeoJSON",verbose=FALSE)
> plot(AllMap)
> plot(LopMap,col="#FBA794",add=TRUE)
````

5)
````R
> DataPBDB<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Lopingian",StopInterval="Lopingian")
> points(DataPBDB[c("lng","lat")],pch = 19, col = "blue")
````

6)
There was an increase in the areal extent of North American sedimentary units across the P/T boundary, because the purple area (sedimentary units) is larger the pink orangish area.
There was an increase in percentage of sedimentary units with reported fossils in them across the P/T boundary. The reason is that there are a lot more occurrences in the early Triassic, whereas the sedimentary units only increased a little bit.
Overall, both of our observations reject these two hypothesis. We actually have better fossil sampling of the available sedimentary rock from the Early Triassic and it has a higher availability of sedimentary rock.
