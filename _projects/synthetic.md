---
layout: page
title:  "Synthetic Data"
date:   2016-01-01 08:43:59
permalink: /synthetic/
categories: ml
desc: "A python utility to generate synthetic data using Numpy"

---

**Technologies**: python,gaussian stats model

**RepoLink**: https://github.com/Gaurav-Pande/synthetic-data-generation.git

**Referencedlink**: https://github.com/SheffieldML/GPy.git


### The Idea:

This is a very interesting topic and project which has always attracted my attentions. Being a part of organization like Cisco, I have many time came accross a situation when i need some live data sets to work on, but this is hard dependency, which I would like to remove. So I basically want to generate some synthetic data which is not actually synthetic but rather matches with the live network data and what about after generating this model, if I can fit a noisy dataset to this synthetic data, and can say "hey, look your data is this, but it should be like this" and than if move a step further what if i can than predict values based on these methods.


### My Poc

I did this small poc using gaussian stats model. GPy is a Gaussian Process (GP) framework written in python, from the Sheffield machine learning group.Gaussian processes underpin range of modern machine learning algorithms. In GPy, we can use python to implement a range of machine learning algorithms based on GPs.

So I used the poisson distribution to generate a synthetic data which fits the poission curve, and I say it an ideal network real time data. I than generate a noissy data which I superimpose over the ideal data and try to fit the curve, and than once I did train my data, I predict some values based on the trained data set.


This is the very beginning stage of it. The code is raw and not very good. But as I am learning, I am planning to build a framework which should be robust and can accomodate other statistical models. 



---
