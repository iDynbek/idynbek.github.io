---
layout: post
title:  "Open-source OCR for mixed Kazakh and Russian, Intro"
date:   2026-02-23 20:00:00 +0500
categories: ocr kazakh russian
---

This is the first post in a series about building an open-source OCR system for mixed Kazakh and Russian text. In this series, we will explore the challenges of OCR for these languages, the tools and techniques we can use, and the results we can achieve.

I will be updating this series regularly as the project progresses, so stay tuned for more updates and insights.

# Motivation

When I was working on a project that involved processing scanned documents in Kazakh and Russian, I found that existing OCR solutions were not accurate enough for my needs. The mixed nature of the text, with both Kazakh and Russian characters, posed a significant challenge for OCR systems that were primarily designed for one language or the other. This motivated me to build an open-source OCR system that could handle mixed Kazakh and Russian text effectively.

# Challenges

As for any low-resource language, the major challenge in building an OCR system is to find enough training data. The process of fine-tuning is more or less streamlined, given the availability of numerous open-source OCR models. However, the lack of training data for Kazakh and Russian, especially in mixed contexts, makes it difficult to achieve high accuracy.

Also probably the major challenge is to generate a good quality annotated dataset of handwritings.

Another major challenge is probably that I do not have much computational resources to train a good OCR model. For the time being I will be using a customer type GPU.

# Plan

To address this challenge, I plan to collect and annotate a dataset of scanned documents that contain mixed Kazakh and Russian text. This will involve manually transcribing the text from the scanned images and creating a training set for the OCR model. The process of annotation will be looped, as I will be utilizing the model's predictions to assist in the annotation process, which will help to speed up the creation of the training dataset. I have plans on exploring various annotation techniques, as using semi-supervised learning, or using a teacher model to distill knowledge to a student model, which can help to improve the performance of the OCR system with limited annotated data.

# Due diligence

## Current state of the art solutions

Specific for KK-RU OCR, ISSAI recently released a small VLM Qolda.
Other solutions with targeted kaz-rus OCR are Tesseract.

For cyrillic OCR in general I am aware of PaddleOCR, Qwen3-VL also claims to have good performance on cyrillic datasets.

For handwritten OCR we have a fine-tuned version of TrOCR by Microsoft.

Benchmarks say that these OCR models are one way or aronud are good. But I still have to test them on my own. Maybe I should construct a test benchmark dataset.

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
