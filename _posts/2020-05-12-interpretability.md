---
title: 'Interpretable and Explainable Deep Learning for Image Processing'
date: 2020-05-12
permalink: /posts/interpretability
tags: [interpretability,explainability,trustworthy,medical imaging]
image: blog_post2.jpg
categories: blog
---

Interpretability, explainability, or the lack of either, have been popular talking points in the deep learning community. The terms are generally ill-defined and the black-box nature of models, such as deep neural networks, makes it challenging to harness their power in real world applications. In this blog post, I explore notions of interpretability and explainability for both humans and machines, and discuss how we can even begin to make progress towards truly interpretable or explainable algorithms for image processing.

Trusting the output, and more importantly the decision making process, of machine learning models is crucial if they are to be used in many situations. Consider a critical medical imaging example, where a radiologist takes a CT scan of a suspected stroke patient arriving in hospital. Identifying the particular type of stroke early on is vital for administering the correct treatment as quickly as possible. This is key to maximising the chance of a positive response to treatment [1]. In many cases, the brain does not appear abnormal for the first several hours after the onset of stroke, and the stroke region may be too small to be seen on the CT scan [2]. Suppose we could harness the power of a deep learning model to classify the type of stroke a patient has had, given their CT. If the model performed well, it could help the radiologist to more accurately diagnose the patient at an earlier stage. 

 <figure class="image">
  <p align="center">
    <img src="/assets/img/blog_post3.jpg" alt="my alt text" width="400">
    <figcaption>Image: Roy Scott, Ikon Images / Getty Images</figcaption>
  </p>
 </figure>


However, such a model would only be useful if the doctor could understand and trust the decision making mechanism of the model. In fact, the process which led to the model’s decision is likely to be more informative to the radiologist than the single output itself. So, given interpretability and explainability are extremely desirable properties in some situations, how do we formalise these ideas? The notions of these concepts that particularly resonate with me are inspired by those of Professor Cynthia Rudin at Duke University [3]:

* Interpretable models are inherently not black-box, i.e. the human user can comprehend the internal mechanisms of the model and have an understanding as to how it is making decisions. For example, a shallow decision tree algorithm with a relatively small number of meaningful features is an interpretable model.
* Explainable models are models (which could be black-box) that are coupled with a technique which provides a post-hoc explanation for the output of each test instance. For example, a neural network with a saliency map could be deemed explainable, if we can trust and use the information provided by the saliency map. This is more subjective.
* Interpretable models are explainable by default, since the explanations can be immediately derived from the underlying model design.

The process behind human decision making is black-box to us: we cannot comprehend all of the conscious and subconscious neural processes involved in making a decision on something. 

<figure class="image">
  <p align="center">
    <img src="/assets/img/blog_post2.jpg" alt="my alt text" width="400">
    <figcaption>Illustration: Gary Waters, Science Source</figcaption>
  </p>
</figure>

However we, as humans, can of course provide contextual explanations as to why we made particular decisions. Let’s consider the (non-)interpretability and explainability of humans with an example. Amanda visits a restaurant and orders clams. She enjoys them but feels ill the following day. One month later, she returns to the same restaurant but chooses to order lasagne instead. How do we understand Amanda’s decision to order lasagne over clams? Of course, one option is to ask Amanda herself:

<figure class="image">
  <p align="center">
    <img src="/assets/img/blog_post.png" alt="my alt text" width="400">
    <figcaption>Original Illustration: Bill Brown, The Guardian</figcaption>
  </p>
</figure>

As discussed previously, Amanda is not interpretable because we cannot understand the true inner workings of her brain. However, she can provide us with a post-hoc explanation for her decision, making her explainable. But how much can we trust this explanation? 

While Amanda’s reasoning is certainly plausible, it is unlikely that this is the sole reason for her not ordering clams. Even if Amanda *hadn’t* fallen ill after eating the clams, perhaps she would have chosen something else to eat anyway. Maybe Amanda walked past another restaurant guest eating lasagne on her way in. Or the temperature today was colder and Amanda fancied something more hearty. Maybe it was near the end of the financial month and the clams were more expensive. Or perhaps Amanda simply just wanted to try something different. There is likely to be a plethora of factors leading to Amanda’s decision, many of them subconscious. We cannot gain a complete understanding of Amanda’s decision making process, either through the explanation she gave post-hoc, or by examining the biological processes involved in her brain. So can we really class Amanda as being *fully* explainable or interpretable in this instance? I don’t believe we can. But this does not mean we cannot strive towards developing interpretable and explainable machine learning models. If we view a machine learning model as an information provider to the human user, it is vital that the model’s rationale can be trusted and understood to be as useful as possible to the human’s ultimate decision making process.

If we focus on explainability of inherently non-interpretable models, we have to be confident that the explanation of a particular decision is not misleading, incomplete or biased. For example, Amanda may have given a different explanation if the chef had asked her why she didn’t order clams, for fear of insulting them. This reasoning can be applied to machine learning too. True explainability - with foolproof and meticulous explanations - of black-box deep learning models is a very non-trivial task. Some researchers may argue that some insight is more desirable than none, but we have to be careful of how we interpret and use that insight. For example, saliency maps are common tools used to find the regions of the input image which maximise the gradient of the output with respect to the individual pixel values. If the saliency map highlights a certain region of the input image, how do we interpret *how* the model is using that information? Is the model seeing what we see as humans? What if the absence of something in the image was particularly important in making the decision, and we can’t see that? Saliency maps produce ambiguous explanations and are limited to pixel-level information in the image. 
 
 <figure class="image">
  <p align="center">
    <img src="/assets/img/blog_post4.png" alt="my alt text" width="400">
    <figcaption>Image: Hideyuki Matsumoto et. al, 2011.</figcaption>
  </p>
 </figure>

In reality, a neural network has extracted higher level features, such as textures, shapes or something more abstract, and used that information to make the final decision. If we can understand the higher level feature representation learned by a neural network, or encourage the neural network to learn a feature representation that makes sense to us as humans, then we are in a better place to produce more precise explanations. We could use this *disentangled* representation of the images as input to an interpretable model, such as a rule-based method like a decision tree. Using the higher level features of the image as input makes more sense than the raw pixel values themselves, and is closer to the human perception of images. I argue that, without this focus, we cannot even begin to build truly explainable or interpretable deep learning models for image processing.  
 
 <figure class="image">
  <p align="center">
    <img src="/assets/img/blog_post5.png" alt="my alt text" width="400">
    <figcaption>Image: Shoaib Ahmed Siddiqui et al, 2017.</figcaption>
  </p>
 </figure>

The lack of trust in black-box models can be a roadblock preventing their deployment in many real world applications, particularly critical ones such as medical diagnosis. Interpretability could be one avenue towards trustability: if we can comprehend the decision-making mechanism of the model, perhaps we, as humans, are more willing to work *alongside* it to make a collective decision. The first step towards interpretable or explainable machine learning models for image processing is to understand the higher level feature representation used by the black-box models for classification. To aid this, we may need to encourage the models to learn feature representations which are sensical and translatable to the human user. As discussed in this post, striving for explainable black-box models is challenging: one has to be confident that the explanation produced is non-ambiguous. Therefore, I argue that uncovering and understanding the ‘hidden’ feature representation of images learned by neural networks is a vital first step towards trustworthiness, interpretability, and subsequently explainability.

### References

[1] Marchese, G., Prochazka, B., Widimsky, P. *The importance of time: Time delays in acute stroke.* Cor et Vasa 58:2, e225-e232 (2016).

[2] Stroke Center. *Stroke Diagnosis Imaging Tests: CT scan.* Available at: [http://www.strokecenter.org/patients/stroke-diagnosis/imaging-tests/ct-scan/](http://www.strokecenter.org/patients/stroke-diagnosis/imaging-tests/ct-scan/) (Accessed 22/4/20).

[3] Rudin, C. *Stop Explaining Black Box Machine Learning Models for High Stakes Decisions and Use Interpretable Models Instead.* Nature Machine Intelligence 1, 206-215 (2019). 
