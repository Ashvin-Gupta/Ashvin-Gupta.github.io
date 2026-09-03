---
# Blog posts live in _posts/. Add a new file named YYYY-MM-DD-title.md
title: "First year of PhD"
date: 2025-10-15
permalink: /posts/2025/10/first-year/
excerpt: "Learnings from my first year"
---
Deciding whether or not to do a PhD is a huge decision. You are devoting the next 3/4 years of your life to a program where you will constantly doubt yourself, be lost for direction and wonder whether it will be worth it. Do not worry, all of these feelings are natural! Of course, you meet some PhD students whose project is all set out for them, who receive great supervision and breeze through the program... however, this is much rarer. The PhD is all about learning to be uncomfortable with not knowing, something I am still getting used to two years in. In this blog, I'm going to detail some of the habits and tips that I have picked up that have allowed me to enjoy my PhD while still completing strong pieces of research.

## Learn the basics
When I first started my PhD, I would often read papers and struggle to understand exactly what they did and all the terminology. Terms such as *hidden state*, *boosting* and *channels* meant very little to me. Going back to the basics helps greatly, and this means machine learning basics, not just deep learning. Once you have a strong grasp of what linear regression, high-dimensional space and Bayesian formulations conceptually mean, you will be able to understand these papers much more fluently. I strongly recommend coding, using PyTorch or, even better, NumPy, the main architecture your project will focus on, such as a Transformer or CNN. Although it will take a bit of time, going through each step really helped me understand all the components of the model.

There are also great resources online. My personal favourite for deep learning has been [Understanding Deep Learning](https://udlbook.github.io/udlbook/), which also contains notebooks you can work through in your own time. Often, it is easier for me to visualise concepts, so channels such as [Welch Labs](https://www.youtube.com/@WelchLabsVideo), [Deepia](https://www.youtube.com/@Deepia-ls2fo), [3Blue1Brown](https://www.youtube.com/@3blue1brown), [StatQuest](https://www.youtube.com/@statquest) and [Andrej Karpathy](https://www.youtube.com/@AndrejKarpathy) are resources I still use frequently. To keep up with what people are getting excited about in the community, unfortunately, Twitter has been my best resource. I have seen many people discuss the latest papers, release interview preparation guides and even job applications here, so do not neglect it.

## Organisation
In the first year especially, a lot of time is devoted to reading the literature. Depending on your interests, this can be highly exciting or extremely boring. Either way, it is absolutely required for a PhD, and having a broad understanding of your field will benefit you greatly. I would recommend keeping track of everything you read, no matter how relevant you think it is to your project at this time. I have been using Notion and created a database with the following fields:

<table>
  <thead>
    <tr>
      <th>Title</th>
      <th>Tags</th>
      <th>Summary</th>
      <th>Methodology</th>
      <th>Future Areas to look into</th>
      <th>Relevance</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Title of Paper</td>
      <td>e.g. Deep Learning, EHR</td>
      <td>One or two lines summarising the paper's key points</td>
      <td>Methods or models used (e.g. Transformer, Logistic Regression)</td>
      <td>e.g. Extensions, datasets, improvements suggested</td>
      <td>High/Medium/Low — how relevant it is for your project</td>
      <td><a href="https://link-to-paper.com">Link</a></td>
    </tr>
  </tbody>
</table>

This has probably been my number one resource throughout my PhD. On top of this, I keep a weekly log of *Things to Do*, *Completed Tasks*, *Ongoing Tasks* and *Questions*, which, on top of general organisation, is a healthy reminder that I am making progress even if there is no visible output.

## Get hold of your data
One thing I can't emphasise enough is to get hold of your data as quickly as possible. This is especially true in the healthcare field, where data is often messy and can be held in a secure environment. Once you have access to your data, you can begin to understand whether you need to complete any preprocessing, how much memory and time it requires to train on and what other papers with your type of data have done. Make sure to also understand how people actually learn from this data. For example, if your data has hard labels, then you can use supervised learning. If not, then you may have to do some sort of self-supervised learning. It is easy to get bogged down in the literature, and often only through trying to implement things yourself can you understand what has potential and what does not.

## Understand your supervisors
When I first started the PhD, I was focused on trying to impress my supervisors. Whilst this is beneficial (you want to show that you can be trusted to work independently), it is your PhD, not theirs! Each supervisor will have their thoughts about your project and where it should go, but you know your project best. It took me too long to realise that I should be using my supervisors as resources. Some supervisors may be great at coming up with ideas, others will be great at critiquing your papers, while some may not be present at all. Focus on what you and your project need to succeed, and how your supervisors can help with this.

## Use time to think
It is tempting to dive headfirst into the project and immediately start coding. I am still learning that it is best to really think about your project. What I mean by this is to understand where the gap and novelty are within your field, how you could actually set up a training objective, what task you are actually trying to solve, what baselines are already present in the literature and how you are going to evaluate the model. It is incredibly easy to neglect the last two points, but these are incredibly important for showing others that your new formulation truly does work. It is, of course, a fine balance, as too much thinking time can result in no experiments. But I would recommend really trying to understand what problem you are trying to solve, and then following the route with the highest signal and expected payoff from the literature.

## Make friends
The PhD can feel like a lonely battle. Labs have varying amounts of social activity, and you may find yourself working from home a lot. Having a strong support network can be immensely useful for your mental health and enjoyment. I was lucky enough to be placed on a CDT with 20 or so other students. Very quickly, I formed a new friendship group, and I can't explain how fundamental this has been for me.

Of course, everyone's experience is different, and what works for me might not work for you. Perhaps the most important bit of advice to keep in mind is that every PhD is different. Feeling inferior is natural within this field, and I don't think it will ever truly go away, no matter how many publications you can output, so do not compare and understand how great it is to be doing a PhD!

![Friends](/images/First-year/San-Diego.png)
My friends and I enjoying some relaxation at the beach during NeurIPS, 2025, San Diego


