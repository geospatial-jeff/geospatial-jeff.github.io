---
title: 'Thinking about Geospatial Thinking'
date: 2019-03-04 00:00:00
description: Something something something
featured_image: '/images/demo/demo-square.jpg'
---
In 1953, Watson and Crick published a 2-page paper proposing a three-dimensional, double-helix model representing the physical structure of DNA.  Although the complete history of the discovery of DNA is out of the scope of this post, it's worth nothing that none of the research teams including Watson and Crick were close to an answer until an X-ray diffraction image (famously called Photograph 51) was captured in 1952, revealing a two-dimensional cross section of crystallized DNA.

![Photograph51](https://upload.wikimedia.org/wikipedia/en/b/b2/Photo_51_x-ray_diffraction_image.jpg)
**<center>Figure 1: Photograph 51 showing the two-dimensional structure of DNA, captured with X-ray diffraction in 1952 by Raymond Gosling</center>**

Watson and Crick's proposed answer then required fitting a three-dimensional spatial model to the existing two-dimensional representation provided by Photograph 51 and based on their understanding of the molecular and structural requirements of DNA.  

Albert Einstein famously did not start speaking until he was 4 and described his thinking processes as primarily verbal, stating "the words or the language, as they are written or spoken, do not seem to play any role in my mechanism of thought" but rather "elements in thought are certain signs and more or less clear images which can be 'voluntarily' reproduced and combined".  The thought processes used by the aforementioned scientists exemplify the process of <b><i>spatial thinking</i></b>, which uses space as a vehicle for structuring problems, finding answers, and expressing solutions.  

## Spatial Thinking
Every single person on Earth relies on spatial thinking every day but it's such a natural part of our thought process that it becomes really hard to define, difficult to uncouple from our daily lives.  Is it likely that the spatial thinking employed by Einstein to imagine the universe in innovative ways is the same process used by Watson and Crick to develop the double helix?  Most likely not.  The scientists were born in different locations with different academic upbringings with expertise in different fields trying to solve fundamentally different problems.  Spatial thinking happens to be incredibly individualized and use-case driven, which means there really is no way to assign a proper universal definition.  Instead, I'd like to examine what it means to think spatially by decomposing the concept into its smaller parts.

The most authoritative source for thinking about spatial thinking is the National Research Council's 2006 report titled [Learning to Think Spatially](https://www.nap.edu/catalog/11019/learning-to-think-spatially), which conceptualizes spatial thinking as "a constructive amalgam of three elements: concepts of space, tools of representation, and processes of reasoning", which are described in the table below:

| Element | Definition     |
| :------------- | :------------- |
| Space       | Provides the conceptual and analytical framework within which data can be integrated, related, and structured.       |
| Representation       | Provides internal and cognitive or external and graphic forms within which structured information can be stored, analyzed, comprehended, and communicated to others.       |
| Reasoning       | Provides the means of manipulating, interpreting, and explaining the structured information     |

This is actually quite simple!  In order to think spatially we need to (1) define our space, (2) choose some way to represent our space, and (3) use our sense of spatial reasoning to assert something about our representation.

##### Concepts of Space
One of the really cool and powerful aspects of space is that it is ambiguous, amorphous, and generally up to interpretation.  Space can be a concrete thing (such as an architect's scale model of a building), a graphical/numerical representation (such as lat/long points in a GIS), an abstract concept (such as clustering social media users by shared connections) or a mental abstraction (such as a taxi driver's mental map of a city).

<img src="https://imgs.xkcd.com/comics/map_of_the_internet.jpg" style="width:600px"/>
**<center>Figure 2: Mapping the internet with abstract space. </center>**



##### Tools of Representation
Representations help the thinker remember, understand, and communicate about the properties of and relationships between objects represented in space.  They are necessary because space is simply too individualized and too complex to explain in its entirety (more on this later!); representations thus provide a simplified model of our space which promotes interaction, communication, and understanding.  Perhaps the most powerful example of a spatial representation is spatial data!  The raster and vector data models are simply computerized representations of various real-world objects and phenomenon within a defined concept of space.

##### Processes of Reasoning
Spatial reasoning is the underlying set of spatial tools at our disposal used to assert information about the given representation.  An architect may assert spatial reasoning by performing various measurements on a scale model, an intelligence analyst may identify an unknown object by examining its appearance in multiple satellite feeds.  Once again, the process behind spatial reasoning varies across use-cases but is ultimately grounded in the individual's spatial literacy, which is acquired through education, experience, and intuition.  Unlike the previous two aspects of spatial thinking, there are definitely correct and incorrect forms of spatial reasoning (ex. there are known methods to accurately measure distances).

---

Fully understanding the given representation is one of the most critical elements of any type of spatial thinking, as the representation ultimately allows the thinker to communicate, interact, and derive information from the underlying space.  Representations are simple models of the underlying space, so its useful to know a little bit about modeling theory!  Thankfully, whether we know it or not, we are all experts at modeling and have been perfecting our modeling skills our entire lives!


## Modeling Theory 101
To give an overview of modeling theory I'd like to propose an extended metaphor.  Think about the word <b><i>TREE</i></b>.  I'm sure a similar mental image pops into most people's mind.  But think about how much more complex the physical manifestation of a tree is compared to the four letter word we use to represent it.  It's so complex that we've come up with other words like <b><i>LEAF</i></b> and <b><i>TRUNK</i></b> to describe various parts of the tree.  Each one of those words has even more associated words to help give us a better understanding of what the word TREE actually represents.

<img src="https://i.pinimg.com/236x/76/53/10/765310fa26d8a92e4fc6c848636d2aad--cloud-art-word-clouds.jpg" style="width:400px"/>

Words are nothing more than models for the objects they represent, so anyone with a vocabulary is familiar with the concept of modeling!  It turns out that modeling is a fundamental aspect of how humans understand and communicate about information.  Without models, we lose the ability to simplify the world around us, creating an overwhelming mess of stimuli which quickly overwhelms our little brains.  Models, however, give us the power to understand the world around us through simplification.

###### Understanding through Simplification
If models are the building blocks of information, combining multiple models through contextualization is the key to understanding.  When we are children we may simply understand that trees are tall, green, and fun to climb on.  But as we grow up so does our tree-related vocabulary; we learn new and fancy words like PHOTOSYNTHESIS which build on our mental understanding of what a tree actually is.  Understanding what photosynthesis is on its own isn't too useful, but understanding how it works with respect to a tree and all its various parts builds understanding.

Our metaphorical lifelong pursuit of tree-related knowledge brings up an interesting question.  Can we ever fully understand what a tree is?  Some particularly inspired people (foresters, environmental scientists etc.) might spend their entire lives trying to do so.  They might come close, but modeling theory dictates that they won't.  This segways nicely into an important aphorism in the modeling and statistics communities which states that "all models are wrong".  Models are nothing more than a simplification of reality which means, by definition, a model can never be 100% accurate; there will always be some error.  Even the Matrix, a system designed by our robot overlords to distract us with a virtual reality while they harvest our bodies for energy, is not a perfect model of reality and has several glitches which Neo recognizes when he sees the [black cat](https://matrix.fandom.com/wiki/Black_cat) twice in the first movie of the critically acclaimed series.

This aphorism is often extended with "all models are wrong but some are more useful than others."  I like this version more, its less pessimistic and helps to convey that just because something is inherently wrong doesn't make it useless.  In fact, we've already seen that simplifications of reality are quite useful for explaining, predicting, and understanding the world around us.

###### Evaluating Models
So if some models are useful and some are not, how can we distinguish between the two?  How can we compare two models and know which one is better?  The answer lies in the model's information pathway, or the steps which the model takes to derive information.  The pathway ultimately depends on the model and its purposes.  The information pathway of verbal models such as the word TREE, is largely dependent on cultural differences.  These differences may manifest themselves within the model's expression of itself (TREE in English vs ARBRE in French) or in the object the model represents (willow tree vs eucalyptus tree).  Just like a textbook about trees written in French wouldn't be too useful to an English speaking student, a textbook about sequoias wouldn't be too useful to someone studying forestry in Africa.  Climate change models, on the other hand,  assume different information pathways based on the specific input data used by the model.  It is common for climate change models to estimate the impact of climate change across multiple information pathways with varying degree of socioeconomic activity with the goal of modeling climate outputs given different possible growth scenarios.  If my research goal is studying the impact of climate change assuming high adoption of renewable energy, a "worst-case-scenario" model would not be too helpful to my research.  An architect might construct a scale model differently based on the requirements of the project.  Maybe the architect is planning an incredibly massive apartment complex and requires a small, less-detailed scale-model of the entire complex to inform his initial plans.  When the architect moves to the interior design of individual apartments, he might switch to a greatly
detailed model of the apartment.

## Spatial Thinking with Spatial Data
Since spatial thinking is personalized, I can only really speak at length to my own experiences.  The flavor of spatial thinking I've come to use most is data driven as my primary use case is generating actionable intelligence from spatial data.  In this scenario, the primary concept of space I work with is the Earth, the representation is spatial data (such as a satellite image), and the reasoning is performed primarily with a GIS.  My ultimate goal is to use spatial reasoning to assert information about the space (Earth!) using my representation (the data!) as a vehicle for communicating my assertion in a way that informs decision making.

Let's break this down a little more.  We learned earlier that when thinking spatially the tool of representation is a model for the underlying space, and geospatial data is no different!  A satellite image is nothing more than a digital model of the Earth captured at a specific time (acquisition date) and bounded to a given extent in space (limited by the extent of the image).  Furthermore, the image comes from a satellite which orbits the Earth at a constant speed and is equipped with a camera of a specific configuration.  The orbit and camera configuration determine the spatial, spectral, temporal, and radiometric resolution of the image; four common metrics used to assess the usefulness of a sensor to a specific application.

Different sources of spatial data have their own unique information pathways.  A passive electro-optical sensor, such as Landsat8 or Sentinel2, collects information by measuring the magnitude of electromagnetic radiation reflected from the Earth's surface within certain bandwidths.  A SAR sensor, on the other hand, is an active sensor which bounces radar waves off the Earth and listens for their return, very similar to echolocation.  Both sensors are trying to accomplish similar things but do so very differently.

More often than not, my data driven process of spatial thinking is very similar to the extended metaphor presented earlier and explicitly relies on the concept of spatial modeling, an extension of standard modeling theory focusing on inherently spatial phenomenon.  Similar to how we can layer together multiple models (words) to expand our understanding of a TREE, spatial data can also be layered to enhance our understanding of the Earth!  This is a process known as data fusion which has become a fairly standard practice throughout the spatial industry for deriving actionable insights from spatial data.

### Spatial Data Fusion
Perhaps the most explicit example of the value of data fusion is dimensionality.  The vast majority of spatial data is two-dimensional, presenting a "top-down" model of the world.  Unfortunately, this isn't a useful model in a lot of applications because the world is three-dimensional (four if you count time and ten if you are a fan of string theory).  Humans can typically visualize three-dimensional representations of overhead imagery due to third-dimension artifacts (shadows, contours, etc.) but computers cannot.  A common way to add dimensionality is by fusing elevation data (LIDAR, DEM etc.) with overhead imagery.  The resulting product is a more realistic model of the Earth because it incorporates all three dimensions.

<img src="https://www.researchgate.net/profile/Gang_Chen46/publication/322367962/figure/fig5/AS:667627512950801@1536186211894/Residential-versus-commercial-buildings-from-2D-to-3D-image-credit-Google-MapC.png" style="width:400px;"/>

Data fusion gives us a sandbox for experimenting with the world.  A chemist who has discovered a new molecule has a variety of options at his disposal.  He can look at the molecule under a microscope.  He can try heating it up or cooling it down, or maybe mixing it with other molecules.  Each experiment he performs builds his understanding of the molecule under study.  The same is true with spatial data.  We can mix and match; add and subtract; warp and translate; and generally do whatever we want to spatial data as long as the output is useful to our application and our process is sound.  Each disparate data source we bring into the analysis adds a unique representation which builds a larger, more robust, and more realistic picture of the world.

Data fusion is often a bottom up process.  We start by learning everything there is to know about the specific problem we are trying to solve.  We use the information we have gained combined with our knowledge of spatial data to identify which source(s) are useful to our application.  We then fuse the identified sources to create a realistic model of the world which (hopefully) enables the solution to the problem.  If it doesn't, its back to the drawing board and the process repeats.  This is a very much simplified version of the path most spatial data practitioners walk; a path which is founded on spatial thinking.

## Geospatial Thinking and AI
What is the difference between a neural net trained to classify images as "cat vs. dog" and a neural net trained to classify objects (ex. buildings) on the Earth's surface?  Both neural nets are



A great example of spatial thinking occurs at the intersection of GIS and AI in the upcoming field of GeoAI.  



I often question the role of artificial intelligence within the geospatial community.  Machine/deep learning are incredibly powerful tools for analyzing geospatial data at scale but by no means are a silver bullet.  When working with AI, or really any black box models, it is easy to fall into the mentality of "throw stuff at the wall and see what sticks."  This doesn't work particularly well with spatial data



Machine/deep learning are incredibly powerful tools for analyzing geospatial data at scale but by no means are a silver bullet.  An effective AI strategy requires an equally smart and effective data strategy to scale successfully while producing accurate results.  When working with AI, or really any black box models, it is easy to fall into the mentality of "throw stuff at the wall and see what sticks."  This doesn't work particularly well with spatial data and is actually the complete opposite mindset of data fusion; which inherently requires making educated choices about one's data strategy based on one's understanding of the underlying problem.  




Fortunately, good spatial thinking provides an avenue for building solid data strategies.  



Machine/deep learning are incredibly powerful tools for analyzing geospatial data and is greatly enhanced by good spatial thinking.  An effective AI strategy requires an equally smart and effective data strategy to scale succesfully while producing accurate results.  This is especially important with geospatial data, which is quite nuanced by nature.  














Machine/deep learning are incredibly powerful tools for analyzing spatial data but require a smart and effective data strategy to scale successfully while producing accurate results.  This is especially important with geospatial data, which is quite nuanced by nature, and quite difficult to achieve.  Fortunately, good spatial thinking provides an avenue for creating a solid data strategy.  Both methods of learning are typically implemented through





Machine/deep learning are incredibly powerful tools for analyzing spatial data but require a smart and effective data strategy to scale successful while producing accurate results.  This is especially important with geospatial data, which is quite nuanced by nature, and quite difficult to achieve.  

Both methods of learning are typically implemented through artificial neural networks, which are inspired by and operate similarly to the biological neural networks in the human brain.  As such, many argue that biological plausibility is an important quality of any learning framework.  If the goal is to model the human brain, then its worth understanding how to encode spatial thinking into learning frameworks.  




## Geospatial Thinking
Geospatial thinking is exactly what it sounds like, spatial thinking with a focus on geography.  But why is geography important?  Because not all space is the same, even if it appears to be.  The tendency of individuals


## Geospatial Thinking
Geospatial thinking is exactly what it sounds like, spatial thinking with a focus on geography.  But why is geography important?  Because not all space is the same, even if it appears to be.  The tendency of individuals to think about space differently means that individuals also utilize space differently.  One of the founding principles of geography is spatial autocorrelation, which states that "everything is related to everything else, but near things are more related than distance things."  Applied to our previous statement and we realize that individuals who are close to one another utilize space similarly, this is also called culture.  Keep in mind that "close" is a spatial comparison, and can refer to really any concept of space.  Individuals who frequent the same blogs are likely like minded in their opinions just as those who live in the same city are likely to be fans of the same sports teams.

### Data-Driven Geospatial Thinking
Since spatial thinking is personalized, I can only really speak at length to my own experience.  The flavor of spatial thinking I've come to use most is data driven as my primary use-case is generating actionable intelligence from geospatial data.  In this scenario, the primary concept of space I work with is the Earth, the representation is geospatial data (such as a satellite image), and the reasoning is performed with a GIS.  My ultimate goal is to use spatial reasoning to assert information about the space (Earth!) using my representation (the data!) as a vehicle for communicating my assertion in a way that informs decision making.  In doing so, I can actively use geospatial thinking to generate information about the Earth


___

Learning to Think Spatially quotes:

"However, spatial thiking itself is not a content-based discipline in the way that physics, biology, and economics are disciplines: it is not a stand-alone subject in its own right.  Spatial thinking is a way of thinking that permeates those disciplines and, the committee would argue, virtually all other subject matter disciplines."

"The key to spatial thinking is a constructive amalgam of three elements: concepts of space, tools of representation, and processes of reasoning.  It is the concept of space that makes spatial thinking a distinct form of thinking.  By understanding the meanings of space, we can use its properties as a vehicle for structuring problems, finding answers, and expressing and communicating solutions"
- "Space provides the conceptual and analytical framework within which data can be integrated, related, and structured into a whole.  Representations--either internal and cognitive or external and graphic--provide the forms within which structured information can be stored, analyzed, comprehended, and communicated to others.  Reasoning processes provide the means of manipulating, interpreting, and explaining the structured information"

"In terms of its power and pervasiveness, spatial thinking is on a par with, although perhaps not yet as well recognized and certainly not as well formalized as, mathematical or verbal thinking.  It can be contrasted with verbal thinking"

"Process of problem solving using the coordinated use of space, representation, and reasoning"

"Spatial thinking uses representations to help us remember, understand, reason, and communicate about the properties of and relations between objects represented in space, whether or not those objects themselves are inherently spatial.  Objects can be concrete things (as in a cognitive map of roads and neighborhoods in a city) or abstract concepts (as in a 2d graphic plot from a multidimensional scaling model of the love-hate relationships in a Shakespeare play)"

""



OUTLINE
- watson and crick/einstein intro
- define spatial thinking by talking about concepts of space, tools of representation, and processes of reasoning.
- talk about geospatial thinking, how its different from spatial thinking and why that distinction matters.
- talk about my own brand of geospatial thinking (data-driven)
- introduction to modelling
- data sources as models of the Earth
- data fusion the practice of building a realistic model of the Earth by fusing multiple data sources
- talk about AI, how spatial thinking/data fusion inform AI, how AI builds off the concept of spatial modeling and requires spatial thinking for success
  - decarte labs example (tree + lidar)
  - GEOBIA example
