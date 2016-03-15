## Part 1 

> Final Grade 17.8/20

#### Question 1:
1, 8, 11, and 20 are species #1
4, 5, 10, 15, 21, 22, and 25 are species #2
3, 7, 9, 13, 16, 17, and 19 are species #3
2, 6, 12, and 18 are species #4
14, 23, and 24 are species #5

The reason I group #1 together is that they all have relatively same shell size. Moreover, they all share similar ribbings.
The reason I group #2 together is that they all share the similar ribbings, which are distinct from the group #1.
The reason I group #3 together is that they all seem to lack of ribbings, and they all have similar shell width.
The reason I group #4 together is that they are all much smaller than group #1, #2, and #3, plus they all have ribbings.
The reason I group #5 together is that even though they are roughly the same size as group #4, they do not present ribbings on their shells.

#### Question 2:
The morphological features that I think are important are size, ribbing types and shell width.

#### Question 3:
The adults have more growth bands, because as they grow, they need more space to live in. As a result, they need to expand their shell. That leads to more growth bands. Moreover, the adults have more compact ribbings. I think it is also because of the growth of the shell.

#### Question 4: 
After reading about females are usually larger than males, I realized that size should never be the only matrix while grouping species. As a result, I disregarded all small changes in body size and grouped the same species mainly based on their ribbing types.

## Part 2, Subsection 2

1)

> Next time show what R code you used to find the names.
> names(plethodon)

They are land, links, species, site and outline.

2) 

````R
> class(plethodon)
[1] "list"
> class(hummingbirds)
[1] "list"
````

They are both lists.

3)

````R
> dim(plethodon[[1]])
[1] 12  2 40
````

## Part 2, Subsection 2

1)

the first object in the list record the landmark data

2)

````R
> ProcrustesHummingbirds<-gpagen(hummingbirds[["land"]])
````

3)

````R
> plotTangentSpace(ProcrustesHummingbirds[["coords"]],warpgrids=FALSE,verbose=FALSE)
````

4)

> Why do you think there are three? You should have described the plot and what about it made you think there are three. -1 point

There are a least three species.

## Part 3

1) 

Fangs longer than 6 inches

2)

> Fangs or sulfurous order, -0.5

<strike>Adorable eyelashes</strike>

3)

Adorable eyelashes

4)

Taxa C, D and E have sulfurous odor.

5)

E has laser death ray, but D does not.

6)

Adorable eyelashes is a synapomorphy, because it is not unique to a taxon.

7)

Family 1: monophyletic

Family 2: polyphyletic

<strike>Family 3: If family 3 includes their most recent common ancestor, then the answer is monophyletic. Otherwise, the answer is polyphyletic.</strike>
> Family 3 is monophyletic

8)

I do not think it is advisable, because they do not share any characteristics after evolved from their most recent common ancestor, indicating that they are not closely related.

9)
> -0.5 points

<strike>Group 1: polyphyletic</strike>
> paraphyletic

Group 2: If includes their most recent common ancestor, the answer is monophyletic. Otherwise, the answer is polyphyletic.
> polyphyletic

<strike>Group 3: polyphyletic</strike>
> paraphyletic

Group 4: If includes their most recent common ancestor, the answer is monophyletic. Otherwise, the answer is polyphyletic.
> monophyletic

Group 5: polyphyletic

Part 4:
1)
Peramorphosis is responsible for the evolution of mccullochi
Pedomorphosis is responsible for the evolution of gigantea

2)
Mccullochi has undergone a greater degree of heterochrony.

> *G. gigantea* has undergone more. - 0.5 points

Question 3:
Pedomorphosis is represented in the Olenellus example.
