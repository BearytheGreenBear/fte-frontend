---
toc: false
comments: true
layout: post
title: Image Combiner
description: Upload two images!
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
        }
        @keyframes rgbLightEffect {
            0% {
               border-color: red;
            }
            10% {
                border-color: yellow;
            }
            20% {
                border-color: lime;
            }
            30% {
                border-color: aqua;
            }
            40% {
                border-color: blue;
            }
            50% {
                border-color: fuchsia;
            }
            60% {
                border-color: blue;
            }
            70% {
                border-color: aqua;
            }
            80% {
                border-color: lime;
            }
            90% {
                border-color: yellow;
            }
            100% {
                border-color: red;
            }
        }
        .left-half, .right-half, .bottom-half{
            width: 500px;
            height: 300px;
            padding: 10px;
            box-sizing: border-box;
            color: black;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
        }
        .left-half {
            background-color: #333333;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .right-half {
            background-color: #444444;
            text-align: center;
        }
        .bottom-half {
            background-color: #222222;
            text-align: center;
            align-items: center;
            width: 100%;
        }
        .p1 {
            font-family: 'Verdana', sans-serif;
            color: #CCCCCC;
            /* src: url('fonts/fontface.css'); */
        }
        /* @font-face {
        font-family: 'Roblox';
        src: url('Roblox-Font-Bold.ttf');
        } */
        .container2 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'Verdana', sans-serif;
            color: #CCCCCC;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
            overflow: break-word;
        }
        .container3 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'Verdana', sans-serif;
            border: 5.5px solid transparent;
            border-color: red;
        }
        .dropbtn {
            color: white;
            padding: 16px;
            font-size: 16px;
            border: none;
            cursor: pointer;
        }
        .dropdown {
            position: relative;
            display: inline-block;
        }
        .dropdown-content {
            display: none;
            position: absolute;
            min-width: 160px;
            overflow: auto;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            z-index: 1;
        }
        .dropdown-content option {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }
        .button {
            border-radius: 10px;
        }
    </style>



</head>



<body>
    <div class="container3">
    </div>
    <div class="container">
        <div class="left-half">
            <h1 class="p1"><strong>Upload Images!</strong></h1>
            <input type="file" id="imageInput" accept="image/*">
            <input type="file" id="imageInput2" accept="image/*">
            <h3 class="p1">Merge Direction: </h3>
            <div class="dropdown">
            <select id="direction" class="dropbtn">
                <div class="dropdown-content">
                    <option value="Vertical">Vertical</option>
                    <option value="Horizontal">Horizontal</option>
                </div>
            </select>
            </div>
        </div>
        <div class="right-half">
            <h1 class="p1"><strong>Merge</strong></h1>
            <button id="manipulateButton" class="button">-- -- Merge ! -- --</button>
        </div>
    </div>
    <div class="container">
        <div class="bottom-half">
            <h1 class="p1"><strong>Pixelated Image</strong></h1>
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
            <br>
            <button id="downloadButton" class="button">Download Pixelated Image</button>
            <br>
        </div>
    </div>
    <div class="container2">
        <div>
            <h1 class="p1"><Strong>How does this work?</Strong></h1>
        </div>
        <div>
            <h4 class="p1">The above pixelate function works by downscaling the image and averaging out the RGB values over a certain box, depending on the size you specify (unfortunately not implemented yet). Then, it rescales the image up to create a pixelated image!</h4>
        </div>
    </div>


<script>
    uploadedImageName = "";
    const resultContainer = document.getElementById("result");
    const url = "http://localhost:8017/api/pixel-partner-api";
    // const url = "https://fte.stu.nighthawkcodingsociety.com/api/pixel-partner-api";
    const test_url = url + "/test";
    const pixelate_url = url + "/pixelate/";
    const combine_url = url + "/combine/";
    const options = {
        method: 'GET', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
            // 'Content-Type': 'application/x-www-form-urlencoded',
        },
    };
    const post_options = {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
            // 'Content-Type': 'application/x-www-form-urlencoded',
        },
    };
    // fetch the API
    fetch(test_url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
        // check for response errors
        if (response.status !== 200) {
            error('GET API response failure: ' + response.status);
            return;
        }
        // valid response will have JSON data
        response.json().then(data => {
            console.log(data);
        })
    })
    // catch fetch errors (ie Nginx ACCESS to server blocked)
    .catch(err => {
    error(err + " " + test_url);
    });
    function handleImageUpload() {
        const imageInput = document.getElementById('imageInput');
        const imageInput2 = document.getElementById('imageInput2');
        const uploadedImage = document.getElementById('uploadedImage');
        const direction = document.getElementById('direction').value;
        const leftHalf = document.getElementById('left-half'); //new code

        const file = imageInput.files[0];
        const file2 = imageInput2.files[0];
        if (file && file2) { // Check if both files are selected
            const reader = new FileReader();
            const reader2 = new FileReader();
            let image1Data = ""; // Base64 data for the first image
            let image2Data = ""; // Base64 data for the second image

            reader.readAsDataURL(file);
            reader2.readAsDataURL(file2);

            reader.onload = function (e) {
                image1Data = e.target.result.split(',')[1];
                const fileName = file.name;
                uploadedImageName = file.name;
                const fileExtension = fileName.split('.').pop();

                reader2.onload = function (f) {
                    image2Data = f.target.result.split(',')[1];

                    // Fetch the API with both image data
                    data = {"direction": direction, "base64image1": image1Data, "base64image2": image2Data}
                    console.log(data)
                    const imageOptions = {...post_options, method: 'POST', body: JSON.stringify(data)};
                    fetch(combine_url, imageOptions)
                        .then(response => {
                            // Check for response errors
                            if (response.status !== 200) {
                                error('GET API response failure: ' + response.status);
                                return;
                            }
                            // Valid response will have JSON data
                            response.json().then(data => {
                                console.log(data)
                                const pixelatedImage = new Image();
                                pixelatedImage.src = 'data:image/' + fileExtension + ';base64,' + data['base64image'];

                                // Set a max-height for the image to fit within the text box
                                pixelatedImage.style.maxHeight = '100%';

                                uploadedImage.src = pixelatedImage.src;
                                uploadedImage.style.display = 'block';

                                pixelatedImage.onload = function () {
                                    const parent = document.querySelector('.bottom-half');
                                    const ratio = parent.clientWidth / pixelatedImage.width;

                                    if (ratio < 1) {
                                        const maxHeight = ratio * pixelatedImage.height
                                        parent.style.height = (maxHeight + 175) + 'px';
                                    } else {
                                        parent.style.height = (pixelatedImage.height + 175) + 'px';
                                    }
                                }
                            })
                        })
                };
            };
        }
    }
    function handleDownloadClick() {
    const uploadedImage = document.getElementById('uploadedImage');
    const pixelatedImage = new Image();
    pixelatedImage.src = uploadedImage.src;

    const imageInput = document.getElementById('imageInput');
    const imageInput2 = document.getElementById('imageInput2');
    const file1 = imageInput.files[0];
    const file2 = imageInput2.files[0];

    if (file1 && file2) {
        const name1 = file1.name.split('.')[0];
        const name2 = file2.name.split('.')[0];
        const extension = file1.name.split('.')[1];
        const downloadName = name1 + '-' + name2 + '.' + extension;

        // Create an anchor element for downloading
        const downloadLink = document.createElement('a');
        downloadLink.href = pixelatedImage.src;
        downloadLink.download = downloadName;
        downloadLink.style.display = 'none';

        // Append the anchor element to the document and trigger a click event
        document.body.appendChild(downloadLink);
        downloadLink.click();

        // Remove the anchor element
        document.body.removeChild(downloadLink);
    }
}
    const downloadButton = document.getElementById('downloadButton');
    downloadButton.addEventListener('click', handleDownloadClick);
    const manipulateButton = document.getElementById('manipulateButton');
    manipulateButton.addEventListener('click', handleImageUpload);
</script>

</body>
<br><br>