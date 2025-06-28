---
layout: post
title: '<span class="black">Children of the Revolution</span>'
subtitle: '<span class="black">Mapping the interelated Network of Guillotine Victims</span>'
cover-img: /assets/img/image6.png
thumbnail-img: /assets/img/image6.png
share-img: /assets/img/image6.png
tags: [poetry]
author: Harrison Waddell
title-color: "#2F2F2F"
subtitle-color: "#2F2F2F"
author-color: "#2F2F2F"
date-color: "#2F2F2F"
---


I have been oddly fascinated by the French Revolution lately. My Friend Ismail, sent me a copy of *The Oxford History of the French Revolution* by William Doyle, which sparked my interest, which I supplemented with *Revolutions* by Mike Duncan. At the same time, I have been interested in Network Theory for a while. Finally, I read Edward Tufte's *The Visual Display of Quantitative information*, while working on the entropy paper. The relation between these three things is probably unclear.

While exploring the NetworkX python library, I came accross this visualization in the gallery. 
![Napoleon]({{ 'assets/img/napoleon 1.png' | relative_url }}){: .mx-auto.d-block :}

At first I was not sure what was going on, the data provided in the example linked to a internet archive page from 2016, that was exclusively data - without any context. However, a quick bit of internet sleuthing led me to Edward Tufte's website. It turns out, this networkX gallery image was a recreation of what Tufte described as "probably the best statistical graph ever drawn". Of course the networkX version was cool enough to catch my eye, but certainly not the best graph ever drawn. 

This map however, the original by Charles Joseph Minard, made in 1869 (well into Minards 80s), certainly lives up to the description.  
![Napoleon]({{ 'assets/img/Minard.jpg' | relative_url }}){: .mx-auto.d-block :}

Thus I did my best to more faithfully recreate the graph, at least the part that I had data to do. It took some iterations, but I was able to recreate something that while it pales in compairison, I am proud of. 

![Napoleon]({{ 'assets/img/napoleon 2.png' | relative_url }}){: .mx-auto.d-block :}

Happy with my finished product, it occured to me that there might be more to explore with this library and the french revolution. One often repeated phrase in Mike Duncan's revolutions is to some effect or another, that the revolution ate it's own children.

In the wake of the Women's March on Versaille, as the National Constituent Assembly followed the King to Paris, the members previously gathered and coloc'ed by province and geography, found housing and seating based on ideology. Creating potentially the first analog echo chambers. What became of the revolution is certainly a direct consequence of this, but also as a result the revolutions most notable victims we're often very interconnected. 

Thus I began seeing in my mind an animation of the ever expanding network of victims of the revolution, otherwise put I saw a map of the eaten children of the revolution. The original working title for this exploration was *the children eaten along the way*, but it seemed far too grim without context that makes it only slightly less grim. 

THe data for this map, was not easy to come by. It required learning SPARQL, Wikipedia's query language, not too difficult as it is quite similiar to SQL. After a few failed attempts to use the presribed metadata IDs, I figured it would probably be easier to just scrape wikipedia, looking for corresponding links. Thankfully a list of guillotine victims with wikipedia pages already existed, I supplemented it with political factions and death dates. In the end, the end product is directionally correct, but is far from exhaustive, and certainly picks up historical connections more accurately then contemporary relationships. 

It is however still a very cool way of walking through the key years of the first era of the revolution. 

Thus...

![Network]({{ 'assets/img/image2.png' | relative_url }}){: .mx-auto.d-block :}

With the execution of Louis XVI, our first edge is formed. Arnaud II de la Porte, who aided the King in the flight to Varennes, was the second victim of the Guillotine. Before his death, La Porte, was one of the King’s most trusted advisors \- managing the personal wealth of the King.  

The next major historical event, the assassination of Jean-Paul Marat. Charlotte Corday held Marat responsible for the September massacres of the previous year. 

![Network]({{ 'assets/img/image4.png' | relative_url }}){: .mx-auto.d-block :}

![Network]({{ 'assets/img/image1.png' | relative_url }}){: .mx-auto.d-block :}

4 days after the assassination, Charlotte Corday is put to death by Guillotine. On our network, she joins the King and La Porte, likely due to her belief that the king should not have been executed and her “right wing” Girondist views. 

![Network]({{ 'assets/img/image9.png' | relative_url }}){: .mx-auto.d-block :}

Nearly a year after her Husband’s death, Marie Antoinette is put to death. Up to this point our network is primarily composed of close relations to the king, but as the terror begins and progresses, the revolution will begin to eat its own children.   

![Network]({{ 'assets/img/image5.png' | relative_url }}){: .mx-auto.d-block :}

The purge of the Girondins marks the beginning of the reign of terror for many. The Girondins who had pushed for war in Austria and “opposed” the execution of Louis XVI were charged with royalism. In all 22 Girondins were condemned, and 22 we’re decapitated by guillotine, while only 21 we’re executed by guillotine, the dead body of Charles Éléonor Dufriche de Valazé was beheaded a day after he committed suicide. In our network Map, only three have made it, centralized through Brissot, the leader of the Girondins.   

![Network]({{ 'assets/img/image8.png' | relative_url }}){: .mx-auto.d-block :}

The “ultra-radicals” is a Historian created term to capture the radical anti-christianization movement led by Jaques Hebert. They are our next batch of guillotine victims. We can see that they form this tight pack on the left side, centered through Hebert. Because this group was never quite formalized like some other factions I have not included a faction tag. However the men executed for ties to Hebert and dechristianization are as follows: Jacques Hébert, Pierre-Ulric Dubuisson, Antoine-François Momoro, Charles-Philippe Ronsin, and François-Nicolas Vincent. This groups proximity to the king from a community detection perspective is odd. 

![Network]({{ 'assets/img/image7.png' | relative_url }}){: .mx-auto.d-block :}

The indulgents we’re a group of moderates, advocating for an end to the war with allied powers, opposing dechristianization and calling for a slowdown to the terror. Only two weeks after the fall of the indulgents factional enemy, the ultras, they too would fall. 

As a result of a scandal during the liquidation process of the East India monopoly, many of the very politically powerful indulgents we’re tried and executed. Georges Danton, Camille Desmoulins, Fabre d'Églantine among others we’re executed on April 5th. Interestingly the community detection algorithm has picked up very well on the group, despite many being categorized differently by Wikipedia’s factions. 

![Network]({{ 'assets/img/image3.png' | relative_url }}){: .mx-auto.d-block :}

The thermidorian reaction was a Coup-D’etat that removed Maximillien Robespierre from his now relatively consolidated position of power. It entailed the execution by guillotine of Robespierre and his brother, Louis Antoine de Saint-Just, and their supporters as well as 70 members of the Paris Commune. It is often marked as the end of the terror. Though another 12 victims make our network.

![Network]({{ 'assets/img/image6.png' | relative_url }}){: .mx-auto.d-block :}

The network in a lot of ways tells a major part of the story of the French revolution. We could see on our graph some of the most pivotal moments of the revolution. The flight to Varennes, the execution of Louis XVI and Marie Antoinette, the murder of Jean-Paul Marat, the political infighting and the eventual fall of Robespierre. In many ways this is less a reflection of the network and more a reflection of the guillotine. However the network draws out some interesting pieces. Either through historical reflection or the nature of the revolution, the victims of the revolution were a deeply intertwined group. The community detection algorithm was able to pick up on some of the factions, most of the Girondins were in community 1 with only Lucille Desmoulins misidentified. Community 2 picks up a lot of the indulgents, though less accurately than the Girondins.

![Network]({{ 'assets/img/image10.png' | relative_url }}){: .mx-auto.d-block :}

The French Revolution was a time of great change. What often strikes me is the speed many young French people grew to notoriety. In the end, the revolution did not just devour its children… it brought them together, intertwined the fate of the nation and the people guiding it, and held itself to a standard impossible to adhere to, which in the end was a weight too heavy for many of it’s sons and daughters to bear.   


