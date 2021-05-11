
# A3-Pulse-of-a-nation-How-does-weekly-religious-sermons-reflect-socioeconomic-events-in-Turkey
Team members:  
* Melih Yilmaz  
* Ihsan Kahveci
* CJ Lin
* Gibbs Geng

Project page: https://cse512-21s.github.io/A3-Pulse-of-a-nation-How-does-weekly-religious-sermons-reflect-socioeconomic-events-in-Turkey/  

# Project Details 

This project aims to provide insights about weekly religious sermons in Turkey since 2001. The main narrative is about showing how the prevalence of nationalism as a topic in sermons reflects an ongoing conflict, namely the [Kurdish-Turkish conflict](https://en.wikipedia.org/wiki/Kurdish–Turkish_conflict_(1978–present)), over time. We represented the conflict with weekly aggregated casualty counts of two sides (turkish and kurdish) and civilians as explanatory variables. Topic prevalence values in range [0,1] quantify the saliency of a single topic in a given sermon, the higher the value, the more prevalent the topic. Independent variables include location and date of the sermon. Sermon texts are analyzed using Structural Topic Modelling [STM](https://www.structuraltopicmodel.com),a mixed-membership topic model which allows incorporation of document-level metadata. Like all topic models, STM is an unsupervised model, hence the biggest limitation of STM is the user-specified number of topics. Researchers often use human judgment to validate the model output. Based on this, we created a document-based interactive visualization that allows users to explore the final STM output without overloading them with model details and tells a well-contained story centered around the topic of nationalism that users can verify themselves. 

We used an existing [project](https://github.com/mroberts/stmBrowser) as a starting point. The existing solution was not well-suited for our story. It was designed for a technical audience in need of a flexible visual tool during the model specification process. Instead, we want to put more emphasis on the narrative part, leaving model details out of the end-user experience. Consequently, we have made some restrictive visualization decisions to help users focus on the key aspects of data. For example, not all topics that model outputs are coherent or relevant to our story, so we only present the topics that might provide insights to the overall story. Out of the 3 topics that we include in our visualization, Topic 10 corresponds to nationalism whereas the other two are samples of broader religious/non-religious topics. These two topics are intended to serve as baselines which users can visually compare the strength of relationship between casualties and Topic 10 against. For each topic, five keywords that characterize the given topic are also denoted. 

In the visualization, each circle represents a document (a sermon). The right-side panel presents the document's text content, an English translation of the original Turkish text, and interactively changes when user clicks a circle in the left-side scatter plot. Here is a list of design decisions we made, including choice of encodings and interaction techniques:

- X-axis is fixed to date variable, since our story primarily focuses on change over time. 
- Y-axis shows the prevalence of selected topic in sermons. User interacts with a drop-down menu and chooses among 3 topics. 
- Only prevalence values above 0.2 (20%) are shown in the plot to minimize cognitive overload.
- We added an interactive coloring function that highlights the the keywords associated with a chosen topic in the text panel. 
- User can choose between casualty categories and sermon location for color encoding. 
- We chose a binary color encoding for number of casualties (no casualties vs >= 1 casualties). We want to flash out the deathly events and mask the weeks with no conflicts as this is more relevant than what the continous color gradient conveys.
- Size (radius) encoding is implemented to show the number of casualties. We want to express the very deadly events. 
- There is a mouse-hover tooltip that shows the precise prevalence, and number of casualties in each category. 

<!-- - In addition to the scatter-plot, we also added a nonlinear trend line of given topic prevalence. 
- There is a reference line that shows the average prevalence of all religious topics. The idea is to show a comparison between religious and non-religious topics.  -->

# Contributions

**Ihsan** was responsible for data preparation and story-telling. He worked on text-processing, model selection and transform output into a JSON file. (6-8 hours) He actively participated on the decision regarding the variable and tool selection. He also prepared the project documentation. (2 hours)

**Melih** contributed to the design (~4 hours), implementation (~10 hours, includes coming to terms with D3 from scratch) and documentation (~2 hours) phases of the interactive visualization. He personally worked on redesigning the tooltips for individual documents and also implementing color encodings that reflect key features of our dataset better as well as actively participating in collective brain-storming sessions and meetings for design choices.

**CJ** contributed mainly on implementation(~10 hours). CJ highlighted the keywords in the document so it is more clear to the reader that the document is relevant to the selected topic. CJ also tried to add a trend line onto the chart, but since some information was filtered, the trend line could be misleading, trendline is not added.

**Gibbs** mainly contributed to the implementation part (~15 hours) and design (~2 hours). He implemented the changes for the controllers, changed the y axis with more expressive representations, added value filters, changed color encoding legends and several design changes (including the colors changes, bold words...). Other than that, he also actively participating in the discussions about design choices.

