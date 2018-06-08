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

intro_1: 
  - excerpt: '**Computer Vision Related Projects**'
intro_2:
  - excerpt: '**Natural Language Processing Related Projects (Updating soon)**'

  
feature_row1:
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
    title: "Structure from Mothion"
    excerpt: "3D Scene reconstruction and simultaneously obtaining camera pose wrt the scene."
    url: /assets/pdfs/sfm.pdf
    btn_label: "Read More"
---
{% include feature_row id="intro_2" type="center" %}
{% include feature_row id="intro_1" type="center" %}
{% include feature_row id="feature_row1" type="left" %}

