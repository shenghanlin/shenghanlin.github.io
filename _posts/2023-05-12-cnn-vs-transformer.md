---
layout: post
title: CNN vs Transformer
date: 2023-05-12 15:53:00-0400
description: Why use Transformer outperforms CNN??
categories: kaggle cnn transformer
giscus_comments: true
related_posts: true
toc:
  sidebar: left
---
## Introduction

In the [PetFinder.my - Pawpularity Contest](https://www.kaggle.com/competitions/petfinder-pawpularity-score/), participants were challenged to predict which pets were more likely to be adopted based on their images and metadata. Initially, Convolutional Neural Networks (CNNs) showed promising results in this competition. However, as time went on, a new model called Transformer emerged and surpassed CNN by a significant margin. This raises the question: **Why did the Transformer outperform CNN?**

## Why??

When it comes to adopting a pet, humans are often drawn to pets that look appealing. However, this appeal is not solely dependent on a cute face; it considers the entire picture, including the tail, fur, surroundings, and more. Similarly, we expect a deep learning model to consider these factors when making predictions. Let's delve into what CNN and Transformer models focus on in an image before making their decisions.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cnn_vs_transformer.gif" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    GradCAM of CNN vs AttentionMAP of Transformer.
</div>

From the animation above, we can observe that the CNN model (`EfficientNet`) mainly concentrates on the facial features of the image, such as the eyes, nose, and mouth. On the other hand, the Transformer model (`ViT`) pays attention to all the features of the image, including the tail, fur, surroundings, and more. 


## How??

Now that we understand the "why," let's explore the **"How" behind the Transformer's success and the CNN's limitations.**

### Convolutional Neural Network (CNN)

Code:
* train: [PetFinder: CNN [TPU][Train] 🐶](https://www.kaggle.com/awsaf49/tf-petfinder-image-tpu-train)
* infer: [PetFinder: CNN [TPU][Infer] 🐶](https://www.kaggle.com/awsaf49/tf-petfinder-image-tpu-infer)

> CNNs are limited by their **local receptive field**. During the convolutional process, a CNN can only perceive information within its `kernel_size`, which means it lacks the context of regions outside that area—a limitation referred to as "local-context." Typically, the kernel size in a CNN model is set to `3x3` or `5x5`. While the receptive field of a CNN expands as the model's depth increases, thanks to the reduction in resolution, it still remains "short-sighted" due to the limited receptive field. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="https://149695847.v2.pressablecdn.com/wp-content/uploads/2018/01/conv-full-layer.gif" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Mechanism of CNn
</div>

### Transformer

Code:
* train: [PetFinder: Transformer [TPU][Train] 😺](https://www.kaggle.com/awsaf49/tf-petfinder-vit-cls-tpu-train/)
* infer: [PetFinder: Transformer [TPU][Infer] 😺](https://www.kaggle.com/awsaf49/tf-petfinder-vit-cls-tpu-infer)

> On the other hand, Transformers possess a superpower known as the **Global Receptive Field**. This allows them to perceive the entire picture when making decisions. Transformers achieve this global awareness through a mechanism called `self-attention` which dynamically focuses on relevant information from different parts of the image enabling better understanding of the scene.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="https://upload.wikimedia.org/wikipedia/commons/3/3e/Vision_Transformer.gif" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Mechanism of Vision Transformer
</div>

> **Summary:** CNNs are limited by their local-context perspective while Transformers can capture the broader context of an image, including the appealing features that contribute to a pet's adoptability.
{: .block-tip }

<!-- ```python

```

A regular blockquote can be used as following:

```markdown
> This is a regular blockquote
> and it can be used as usual
```

> This is a regular blockquote
> and it can be used as usual

These custom styles can be used by adding the specific class to the blockquote, as follows:

```markdown
> ##### TIP
>
> A tip can be used when you want to give advice
> related to a certain content.
{: .block-tip }
```

> ##### TIP
>
> A tip can be used when you want to give advice
> related to a certain content.
{: .block-tip }

```markdown
> ##### WARNING
>
> This is a warning, and thus should
> be used when you want to warn the user
{: .block-warning }
```

> ##### WARNING
>
> This is a warning, and thus should
> be used when you want to warn the user
{: .block-warning }

```markdown
> ##### DANGER
>
> This is a danger zone, and thus should
> be used carefully
{: .block-danger }
```

> ##### DANGER
>
> This is a danger zone, and thus should
> be used carefully
{: .block-danger } -->
