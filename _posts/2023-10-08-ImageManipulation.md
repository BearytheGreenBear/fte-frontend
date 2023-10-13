---
toc: false
comments: true
layout: post
title: Image Manipulation
description: Upload an image
type: hacks
courses: { compsci: {week: 1} }
---

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        /* Define styles for left and right halves */
        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100vh;
        }
        .left-half, .right-half {
            width: 50%;
            padding: 20px;
            box-sizing: border-box;
            color: black;
        }
        .left-half {
            background-color: #f0f0f0;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .right-half {
            background-color: #e0e0e0;
            text-align: center;
        }
        .p1 {
        font-family: 'Playfair Display', serif;
        color: blue; /* This is a new text color for elements with class, .p1 */
    }
    </style>


</head>
<body>
    <div class="container">
        <div class="left-half">
            <p class="p1">Upload an Image</p>
            <input type="file" id="imageInput" accept="image/*">
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
        </div>
        <div class="right-half">
            <p class="p1">Image Manipulation</p>
            <button id="manipulateButton">Manipulate!</button>
        </div>
    </div>
</body>
