---
# Blog posts live in _posts/. Add a new file named YYYY-MM-DD-title.md
title: "First year of PhD"
date: 2025-10-15
permalink: /posts/2025/10/first-year/
excerpt: "Learnings from my first year"
---

Going into a machine learning PhD is a huge decision. Committing to four years of research is a big commitment and you constantly have doubts, moments of wondering if you've made the right choice and moments of feeling like you can't do it. Talking to my friends, these feelings are all natural. The PhD is all about learning, and I feel like the first year is all about learning how to learn in this research setting. So with that in mind, here are some of few tips that I've picked up so far on how to make the most of it all.

## Getting to grips with your project

Often you are thrown into the project with a lot of freedom and knowing exactly what you need to do can be confusing to say the least. My first piece of advice would be to get hands on your data. Machine learning has had a boom over the last decade due to three main reasons:

1. The amount of data available has increased significantly
2. We now have the compute to process this data and train models
3. Software libraries have made it easier to build and train models

Understanding you data is crucial to the scess of your project, which models to consider and techniques to explore. For example, the EHR data I have appears as medcodes which can also be translated into natural language, meaning I can consider using NLP models to understand the data or make a custom model instead that build directly off the medcodes. Additionally, I have information regarding patients who have been diagnosed with cancer, which type of cancer and which stage as well. This means my data is labelled and as such, for building a cancer diagnosis model, I can consider using supervised learning techniques. By understanding the data, I can then dive into the literature background, considering how I can use the ideas within my project.

The literature reivew is key in the PhD and the best way to do this in my opinion is to keep organsied. Throughout the early years, so much of what you read can be directly relevant, or only slighly. Yet it's still beneficial to keep a log of everything that you have read. Personally, I have been using a Notion database to keep track of everything that I have read. Within this database, I have the following columns:

| Field |
| --- |
| Title |
| Tags |
| Summary |
| Methodology |
| Future Areas to look into |
| Relevance |
| Link |

Whilst reading any paper, I simultaneously fill in my database. By soring by date and tags, I can easily pick up any paper that I have read and dive right back into the main ideas.

Usually as part of the PhD, you will join a supervisor and their lab group. Depending on the size of the lab, there will be a certain few PhD students and postdocs who all work under the supervisor. My next advice would be to use your supervisors and peers. At the start of the PhD, I was always concerned with trying to impress my supervisors. Whilst this is important, the only person in charge of your PhD is you. Your supervisors are there to guide you and help you, but ultimately it is your responsibility to make the most of your PhD. Use your supervisors as a resource to help get feedback on your ideas, areas you are confused about, and don't worry about looking stupid! Similarly, your peers are bound to have a wealth of knowledge for more informal chats. Some of my best ideas have come from having a brutally honest chat with a peer, bouncing ideas and trying to use their expertise for my specific domain.

Finally, sometimes you can get bogged down by the literature. The papers and ideas sometimes seem endless and often the best way to see what works best is just trying to implment it yourself. Commonly, I have thought of an idea that seems appropriate, and have come to implementation before realising that it is a subpotimal solution compared to another technique. Whilst this can be time consuming, every time I have tried to implement code from a paper or write my own, I have really understood all the steps I need to take on my way to building a successful model.

## Getting the most out of machine learning

ML is such a broad yet fast moving field and staying on top of the latest advancments can be challenging. Often I was reading papers, but struggling to understand the methodlogies as I didn't have the required background knowledge. This is key, and I would always reccomend revisiting this material periodically to really drive it home. I have loved reading from [Understanding Deep Learning](https://udlbook.github.io/udlbook/) which contains many intuitive visualisation for core concepts. Supplemented with youtube channels such as [Andrew Ng](https://www.youtube.com/@AndrewNg), [Welch Labs](https://www.youtube.com/@WelchLabsVideo), [Deepia](https://www.youtube.com/@Deepia-ls2fo), [3Blue1Brown](https://www.youtube.com/@3blue1brown) and [Andrej Karpathy](https://www.youtube.com/@AndrejKarpathy) and many [Medium](https://medium.com/) blogs, you really can learn so much even with little background knowledge about your topic. However, as much as I hate to admit it, twitter has been one of the most useful resources for staying up to date with the latest breakthroughs, libraries and news in the field. People are often talking about the implications of new papers or interesting interview questions that could come up, and I find liking the post usueful for referencing back to when I need to.

One of the major benefits of being a PhD studnet is the flexibility with your time.
