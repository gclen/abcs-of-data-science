---
toc: false
layout: post
description: 
categories: [data_science]
title: Z is for Zero to Done
permalink: /blog/z-is-for-zero-to-done
comments: true
---

We’ve covered a [lot of topics]({{ site.baseurl }}/categories) in these 26 blogs. Kudos to you if you’ve made it this far! In this blog I want to cover what the end-to-end data science process looks like. A lot of this will depend on the goals of the project and your organization:

* Are you trying a smaller data science to learn about a particular topic?
* Are you trying to build a product to be used by other people?
* How mature is your organization with regards to data science? If you’re the first one doing this, things will take longer.
* Do you have a team of people or are you doing this individually?

There are 5 major steps you need to do in most data science projects

1. Define your problem
2. Prepare your data
3. Train your model
4. Get feedback
5. Productionize your pipeline

### Define your problem

As you’re starting you’ll want to answer the following questions. I find it’s helpful to write down your answers or talk about them with a friend/colleague.

* **What are you trying to solve?** Talk about the problem that you are trying to solve. You should make this as **specific** as possible. If you are trying to do “machine learning for cyber security” figure out what aspect is most interesting/useful. A more specific problem is “can I predict if a file is malware or not?”
* **Why are you trying to solve it?** Describe how solving this problem will benefit people. This could be benefiting yourself (a learning experience), internal clients (make them more productive), or benefit customers/the world more broadly. 
* **How is this solution going to be used?** Write down if the problem is solved how your solution will be used. Is it going to make decisions automatically? Is it going to give context to a human so that they have extra information? Is it trying to predict something about an individual data point or is it trying to group related things together?
* **Who is asking for a solution to this problem?** Document who is asking for this to be solved. These people could be domain experts, your boss, or someone else. Make sure that everyone has the same expectations. For more about this read [Y is for You Should Talk to Your Clients]({{ site.baseurl }}/blog/y-is-for-you-should-talk-to-your-clients).
* **How would you do it manually?** Try to go through the process of solving the problem manually multiple times. For example, if you’re trying to figure out if a file is malware or not, sit down with some cybersecurity analysts and triage the files together. This will give you a better understanding of the domain and may give you ideas for relevant features.
* **What tools are you going to use?** If this is just an individual project you’re free to use whatever you like! If you’re working in a team you’ll need to figure out which tools people have the most experience with. In some cases you might be forced to use an existing set of tools if they are the ones adopted by your organization.

### Prepare your data

Without data, it’s pretty hard to do data science! Make sure you have data that you can use (or at least process into something useful).

* **What data do you have available?**
* **Are there external datasets you can use to enrich your data?**
* **What data processing do you need?** In all real-world cases you’ll need to do [data munging]({{ site.baseurl }}/blog/m-is-for-munging-data). For text data you’ll need to apply [natural language processing]({{ site.baseurl }}/blog/n-is-for-natural-language-processing) techniques to create features from it.
* **Do you need to embed your data or do dimension reduction?** In many cases you’ll need to embed your data into a feature space. For more information on that I recommend reading [E is for Embeddings]({{ site.baseurl }}/blog/e-is-for-embeddings) and [U is for UMAP]({{ site.baseurl }}/blog/u-is-for-umap).
* **Do you have labels?** If you’re working on a supervised learning problem then you need labelled data. For more information about ways to get that read [L is for Labelling Data]({{  site.baseurl }}/blog/l-is-for-labelling-data). 
* **Have you explored your data?** You’ll need to look at your data and see if there are missing values, [visualize]({{ site.baseurl }}/blog/v-is-for-visualization) it, look for relevant features etc.

### Train your model

Once you’ve processed your data you’ll actually need to train your model(s).

* **Does your problem require a supervised or unsupervised model?** If you are trying to predict something about individual data points you’ll want to use [supervised learning]({{ site.baseurl }}/blog/s-is-for-supervised-learning). If you’re trying to group stuff together you’ll want to do [clustering]({{ site.baseurl }}/blog/c-is-for-clustering).
* **What kind of model should you choose?** This depends on the problem and data type but here are my starting points. If you have images you might want to use [deep learning]({{ site.* baseurl }}/blog/d-is-for-deep-learning) (typically convolutional neural networks are used). For text or tabular data it’s a good idea to start with  [Random Forest or Gradient Boosted Trees]({{ site.baseurl }}/blog/x-is-for-xgboost). It’s worth trying to get a simple model working (even if it’s not the new shiny thing).
* **Are there pretrained models you can start from?** [Transfer learning]({{ site.baseurl }}/blog/t-is-for-transfer-learning) is a powerful technique that can let you make progress quickly.
* **Do you need to do any post-processing?** Especially in the case of clustering you might need to apply additional filters on your clusters for them to be useful. For example, your model could find 1000 groups of stuff but a human might only have time to look at 50 groups. Heuristics on top of your clusters can be a useful way to rank your clusters in terms of usefulness.

### Get feedback

You should continuously ask for feedback on all parts of your pipeline. This will help make sure that you and your clients are on the same page.

* **Is the output of your models useful?** If you show the results of your model to subject matter experts do they agree with it? You may want to look into [model interpretability]({{ site.baseurl }}/blog/i-is-for-interpretability) methods to try and figure out why your model made a given prediction.
* **Does your output fit into your customers workflow?**
* **Are your models biased in any way?** This can be a hard problem to diagnose but it’s an extremely important one. For more information read [B is for Bias]({{ site.baseurl }}/blog/b-is-for-bias).

### Productionize your pipeline

Once you have a successful prototype, it’s time to put it into production. As your doing so, you’ll want to think about the following:

* **How can you access the results of your model?** One option is setting up a REST API using a framework like [FastAPI](https://fastapi.tiangolo.com/). Many cloud providers like Azure and AWS offer SaaS solutions for this. Are you results available as part of an app?
* **Are you retraining the model on a regular basis?** You should retrain the model periodically to ensure that it’s behaving as you expect. You’ll need to measure model drift which is how the performance changes over time on new data. 
* **Is your workflow repeatable?** For more on this read [R is for Reproducibility]({{ site.baseurl }}/blog/r-is-for-reproducibility). How easy is it for someone else to maintain your workflow?

### Summary

There are lots of moving parts involved in completing a fully productionized data science pipeline. It’s okay if it seems overwhelming! No one is an expert in everything, which makes it even more important to work with other people. If you have any questions don’t hesitate to leave a comment, send me a message on [twitter](https://twitter.com/abcsofdatasci) send me an email at abcsofdatascience [at] gmail [dot] com.

### Other resources

* [Practical Tips for Real-World Data Science](https://locallyoptimistic.com/post/practical_ml/)
* [Applied Machine Learning Process](https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/)
* [How to Define Your Machine Learning Problem](https://machinelearningmastery.com/how-to-define-your-machine-learning-problem/)


