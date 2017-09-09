# Part I: The Culture Wars

For those of you who may be less familiar with the current state of American society and politics I thought I'd start with a brief overview of the culture wars.

Unlike a traditional war, which involves people shooting at each other with guns and tanks, the culture wars are a conflict between opposing value systems, and the fights chiefly take place online in the bowels of internet comment threads.

Talking about the American culture war specifically, we have the Alt-Right versus (what I'm calling) the Social Justice Left. While each side may prioritize political issues differently than the traditional left and right sides of American politics, in general each side is roughly comparable to what you’d think of as the traditional left and the right.

##### The Alt-Right

The Alt-Right's origins lie chiefly in online chat rooms and forums such as 4chan, and they can be thought of as kind of an amorphous agglomeration of people across America. The Alt-Right doesn’t have an official party platform or recognized leaders, so it's difficult to basket this community into one distinct entity. One could even draw a limited comparison between the Alt-Right and hipsters, in the sense that people who are labeled as ‘Alt-Right’ don’t necessarily want that distinction.

Still, if you were forced to summarize the general beliefs of the Alt-Right, most members would believe in white nationalism, anti-feminism, anti-Semitism, and the virtues of political-incorrectness.

##### The Social Justice Left

On the other side of this war we have the Social Justice Left, who could also be referred to as the Alt-Left or maybe just the extreme-left of the Democratic Party. I would say think of your average hardcore Bernie Sanders supporter and this is a good representation of what I mean by the Social Justice Left.

The members of this group tend to be young and tech-savvy. A lot of their discussion takes place on social media platforms like Facebook, Tumblr, and Twitter.

The Social Justice Left is more closely aligned with the traditional Democratic Party, but what they consider the most important political issues differs slightly. Most members of the Social Justice Left think that addressing LGBTQ rights, feminism, and racial issues are the top priorities of our time. Political correctness is also a major theme of their platform.

# Part II: Language

Now that we’ve covered the basics of the culture wars, let’s get into the specifics of my project, which aimed to examine how each side discusses the topics that are important to them.

Specifically, I hoped to examine the sentiment of discussion, for example, does one side consistently talk about things in a more negative manner than the other. I also hoped to use natural language processing (NLP) algorithms to identify those topics most important to each side. While a human could pretty easily identify the top one or two topics that are of interest to each side, applying machine learning to this problem might reveal topics that wouldn't be visible to human inspection.

##### Gathering the Data

I used the Disqus API to query comments from seven different websites (Disqus is a company that provides an easy to use comment system and platform for websites). If available, I downloaded 50,000 comments from each website.

In terms of data cleaning, I went through a fairly straight-forward process. I first removed very short comments, as they were unlikely to add anything of value to the analysis. A lot of these were just things like “lol” and “you suck”. Next I converted to lowercase, removed links, removed most punctuation, got rid of things like emojis, and anything in a foreign language. Finally I lemmatized the text, which is a process of converting words to their base form.

##### Sentiment

I used an NLTK library called Vader to do the sentiment analysis, and just to get it out of the way, the results were not that interesting. Vader classifies comments as positive, negative, or neutral, and there was essentially no difference between the alt-right and the social justice left in the sentiment of their comments.

##### Topic Clustering

Comment clustering by topic proved to be more interesting. I tried several algorithms to identify topics, but Latent Dirichlet Allocation (LDA) analysis provided topics that made the most intuitive sense.

After I gathered topics for both groups I clustered comments using the standard K-means clustering algorithm. Most comments were centered on one topic only, although there were a few that were a hybrid of several topics. 

Alt-Right Topics:
- presidential election
- American macro issues
- African Americans & the Police
- white nationalism
- religion (Islam)

Social Justice Left Topics:
- presidential election
- domestic economics
- BLM & the police
- Donald Trump
- LGBTQ rights
- right-wing issues

You can see some similarities, like the presidential election (though admittedly, most politically-oriented websites would have been talking about the presidential election in 2016). Notice that there was a racial / police cluster for both groups, though obviously each group talked about this issue quite differently.

# Follow Up

If I were to spend more time on this project I'd like to explore the sentiment analysis more deeply. I was using a generic library to rank the sentiment of my comments, but a custom library that takes into account the political nature of my corpus would be more appropriate. I'd also do a bit more data cleaning to eliminate entire comments that were not directly relevant to the political nature of the project (i.e. comments about people's pets, where they're vacationing, etc).

I'd also like to dive deeper into a specific topic shared by both groups and see if we can better understand how each group talks about the same thing. For example, both the Alt-Right and the Social Justice Left discussed the role of police in society, but what was unique about how each group discussed this topic?