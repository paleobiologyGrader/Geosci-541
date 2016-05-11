# Lab #12
> 20/20 + EC

## Problem Set 1
1)
````R
> TriassicSynapsids<-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> TriassicDiapsids<-downloadPBDB(Taxa=c("Diapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> JurassicDiapsids<-downloadPBDB(Taxa=c("Diapsida"),StartInterval="Jurassic",StopInterval="Neogene")
> JurassicSynapsids<-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Jurassic",StopInterval="Neogene")
````

2)
````R
> TriassicDiapsids<-cleanRank(TriassicDiapsids,"genus")
> GeneraTriassicDiapsids<-unique(TriassicDiapsids[,"genus"])
#There are 389 Diapsid genera in the Triassic dataset
> TriassicSynapsids<-cleanRank(TriassicSynapsids,"genus")
> GeneraTriassicSynapsids<-unique(TriassicSynapsids[,"genus"])
#There are 116 Synapsid genera in the Triassic dataset
````

3)
````R
> JurassicDiapsids<-cleanRank(JurassicDiapsids,"genus")
> GeneraJurassicDiapsids<-unique(JurassicDiapsids[,"genus"])
> DiapsidsSurvivor<-intersect(GeneraTriassicDiapsids,GeneraJurassicDiapsids)
#37 Triassic Diapsid genera survived.
> DiapsidsVictims<-setdiff(GeneraTriassicDiapsids,GeneraJurassicDiapsids)
#352 Triassic Diapsid genera were victims.

> JurassicSynapsids<-cleanRank(JurassicSynapsids,"genus")
> GeneraJurassicSynapsids<-unique(JurassicSynapsids[,"genus"])
> SynapsidsSurvivor<-intersect(GeneraTriassicSynapsids,GeneraJurassicSynapsids)
#9 Triassic Synapsids genera survived.
> SynapsidsVictims<-setdiff(GeneraTriassicSynapsids,GeneraJurassicSynapsids)
#107 Triassic Synapsids genera were victims.
````

4)
````R
> DiapsidsOdds<-(length(DiapsidsSurvivor)/length(GeneraTriassicDiapsids)) / (length(DiapsidsVictims)/length(GeneraTriassicDiapsids))
> SynapsidsOdds<-(length(SynapsidsSurvivor)/length(GeneraTriassicSynapsids)) / (length(SynapsidsVictims)/length(GeneraTriassicSynapsids))
> OddsRatio<-DiapsidsOdds/SynapsidsOdds
> OddsRatio
[1] 1.249684
# Because the odds ratio is bigger than 1, it indicates that Diapsid genera were more likely to survive the T/J transition than Synapsids
> log(OddsRatio)
[1] 0.222891
````

5)
````R
> StandardError<-sqrt(1/length(DiapsidsSurvivor) + 1/length(DiapsidsVictims) + 1/length(SynapsidsSurvivor) + 1/length(SynapsidsVictims))
> UpperLimit<-log(OddsRatio) + (StandardError*1.96)
> LowerLimit<-log(OddsRatio) - (StandardError*1.96)
> LowerLimit
[1] -0.5370353
# I cannot say that this odds is statistically significant, because the lower limit is negative, indicating that we cannot rule out the possibility that there was not actually an advantage for Synapsids. 
````

## Problem Set 2
1)
````R
> TriassicDiapsidsSynapsids<-downloadPBDB(Taxa=c("Synapsida","Diapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> JurassicDiapsidsSynapsids<-downloadPBDB(Taxa=c("Synapsida","Diapsida"),StartInterval="Jurassic",StopInterval="Neogene")
````

2)
````R
> TriassicDiapsidsSynapsids<-cleanRank(TriassicDiapsidsSynapsids,"genus")
> MeanLatitudes<-tapply(TriassicDiapsidsSynapsids[,"paleolat"],TriassicDiapsidsSynapsids[,"genus"],mean)
````

3)
````R
> JurassicDiapsidsSynapsids<-cleanRank(JurassicDiapsidsSynapsids,"genus")
> TJSurvivors<-subset(TriassicDiapsidsSynapsids,TriassicDiapsidsSynapsids[,"genus"]%in%unique(JurassicDiapsidsSynapsids[,"genus"])==TRUE)
> TJSurvivors<-unique(TJSurvivors[,"genus"])

> TJVictims<-subset(TriassicDiapsidsSynapsids,TriassicDiapsidsSynapsids[,"genus"]%in%unique(JurassicDiapsidsSynapsids[,"genus"])!=TRUE)
> TJVictims<-unique(TJVictims[,"genus"])
````

4)
````R
> TriassicDiapsids2<-subset(TriassicDiapsidsSynapsids,TriassicDiapsidsSynapsids[,"genus"]%in%GeneraTriassicDiapsids==TRUE)
> TriassicDiapsids2<-unique(TriassicDiapsids2[,"genus"])

> TriassicSynapsids2<-subset(TriassicDiapsidsSynapsids,TriassicDiapsidsSynapsids[,"genus"]%in%GeneraTriassicSynapsids==TRUE)
> TriassicSynapsids2<-unique(TriassicSynapsids2[,"genus"])
````

5)
````R
> TJVictimsArray<-array(0,dim=length(TJVictims),dimnames=list(TJVictims))
> FinalMatrix<-merge(MeanLatitudes,TJVictimsArray,all=TRUE,by="row.names")
> FinalMatrix<-transform(FinalMatrix,row.names=Row.names,Row.names=NULL)
> colnames(FinalMatrix)<-c("MeanLatitudes","Survivor/Victim")
> FinalMatrix[is.na(FinalMatrix[,"Survivor/Victim"]),]<-1
> Regression<-glm(FinalMatrix[,"Survivor/Victim"]~FinalMatrix[,"MeanLatitudes"],family="binomial")
> summary(Regression)
# Estimate: 0.0007725; The mean latitude of a Triassic genus is not a good predictor of its survival across the T/J extinction, because the estimate is rather small; Moreover, the p-value is 0.881, indicating that there is high chance that it happens due by chance.
````

## Extra Credit:
````R
> TJDiapsidsArray<-array(1,dim=length(TriassicDiapsids2),dimnames=list(TriassicDiapsids2))
> IntermediateMatrix<-merge(MeanLatitudes,TJDiapsidsArray,all=TRUE,by="row.names")
> IntermediateMatrix<-transform(IntermediateMatrix,row.names=Row.names,Row.names=NULL)
> FinalMatrix<-merge(IntermediateMatrix,TJVictimsArray,all=TRUE,by="row.names")
> FinalMatrix<-transform(FinalMatrix,row.names=Row.names,Row.names=NULL)
> colnames(FinalMatrix)<-c("MeanLatitudes","Diapsids1/Synapsids0","Survivor/Victim")
> FinalMatrix[is.na(FinalMatrix[,"Diapsids1/Synapsids0"]),]<-0
> FinalMatrix[is.na(FinalMatrix[,"Survivor/Victim"]),]<-1
> Regression<-glm(FinalMatrix[,"Survivor/Victim"]~FinalMatrix[,"MeanLatitudes"] + FinalMatrix[,"Diapsids1/Synapsids0"],family="binomial")
> summary(Regression)
# They are both bad indicators for survival rate, because they both have high p-values, indicating that the chance it happens is rather high.
````
