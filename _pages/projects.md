---
title: "Projects"
layout: splash
author_profile: true
permalink: /projects/
date: 2016-06-08
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/projects/feature_matching.png
  caption: "Featuer matching in the process of panorama building."
excerpt: "Natural Language Processing. Computer Vision. Deep Learning."

intro_nlp:
  - excerpt: '**Natural Language Processing Related Projects (Updating soon)**'
intro_ml: 
  - excerpt: '**Machine Learning Related Projects**'
intro_cv: 
  - excerpt: '**Computer Vision Related Projects**'

ml_row:
  - image_path: /assets/images/projects/gi.png
    image_caption: "Predicted interaction scores between pair-wise genes"
    alt: "gene interaction"
    title: "Genetic Interactions Prediction"
    excerpt: 'Predicting pairwise gene interactions using gene ontotype and random forest procedure described in [Yu, et al. (Cell Systems, 2016)](http://www.cell.com/cell-systems/abstract/S2405-4712(16)30033-3) 
    on the *S. cerevisiae* data'
    url: /assets/pdfs/gi.pdf
    btn_label: "Read More"
    
  - image_path: /assets/images/projects/face_recog.png
    image_caption: "Face recognition with different face poses"
    alt: "face recognition"
    title: "Face Recognition"
    excerpt: 'Face recognition with PCA, LDA, KNN and Naive Bayes'
    url: /assets/pdfs/face_recog.pdf
    btn_label: "Read More"
  
cv_row:
  - image_path: /assets/images/projects/panorama.png
    image_caption: "Panorama built with three photos"
    alt: "panorama completed"
    title: "Photo Mosaics Implementation"
    excerpt: 'An end-to-end pipeline for image panorama stitching.'
    url: /assets/pdfs/panorama.pdf
    btn_label: "Read More"
    
  - image_path: /assets/images/projects/faces.png
    image_caption: "Face swapping between male and female"
    alt: "face-swapped image"
    title: "Face swapping in images and video."
    excerpt: "Implemented face replacement by using Triangulation and Thin Plate Spline (TPS), and improved swapped image with blending."
    url: /assets/pdfs/face_swap.pdf
    btn_label: "Read More"
    
  - image_path: /assets/images/projects/sfm.png
    image_caption: "Point cloud display"
    alt: "structure from motion"
    title: "Structure from Motion"
    excerpt: "3D Scene reconstruction and simultaneously obtaining camera pose wrt the scene."
    url: /assets/pdfs/sfm.pdf
    btn_label: "Read More"
---
{% include feature_row id="intro_nlp" type="center" %}

{% include feature_row id="intro_ml" type="center" %}
{% include feature_row id="ml_row" type="left" %}

{% include feature_row id="intro_cv" type="center" %}
{% include feature_row id="cv_row" type="left" %}

