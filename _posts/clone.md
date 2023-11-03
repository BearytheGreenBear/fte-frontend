
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
               border-color: #000080;
            }
            50% {
                border-color: #ADD8E6;
            }
            100% {
                border-color: #000080;
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
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #CCCCCC;
            /* src: url('fonts/fontface.css');  */
        }
        /*@font-face {
        font-family: 'Roblox';
        src: url('.././fonts/Roblox-Font.ttf');
        } */
        .container2 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #CCCCCC;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
            overflow: break-word;
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
        {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .box {
            position: relative;
            width: 880px;
            height: 350px;
            display: flex;
            justify-content: center; 
            align-items: center;
            background: rgba(0,0,0,0.5);
            overflow: hidden;
            border-radius: 20px;
        }
        .box::before {
            content: '';
            position: absolute; 
            width: 150px; 
            height: 275%;
            background: linear-gradient(#00ccff,#d400d4);
            animation: animate 4s linear infinite;
        }
        .box::after {
            content: ''; 
            position: absolute; 
            inset: 4px; 
            background: #0e1538;
            border-radius: 16px;
        }
        @keyframes animate {
            0%{
                transform: rotate(0deg);
            }
            100%{
                transform: rotate(360deg);
            }
        }
        .box h2 {
            position: relative;
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #fff;
            font-size: 10em;
            z-index: 10;
        }
        body {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Verdana', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            flex-direction: column;
        }
        .a {
            position: relative;
            padding: 20px 60px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.5);
            margin: 10px;
            transition: 1s;
            text-decoration: none;
            overflow: hidden;
            -webkit-box-reflect: below 1px linear-gradient(transparent, transparent, #0004);
        }
        .a:hover {
            background: var(--clr);
            box-shadow: 0 0 10px var(--clr), 0 0 30px var(--clr);
        }
        .a::before {
            content: '';
            position: absolute;
            width: 40px;
            height: 420%;
            background: var(--clr);
            transition: 1s;
            animation: animate 2s linear infinite;
            animation-delay: calc(0.33s * var(--i));
        }
        .a:hover::before {
            width: 120%;
        }
        @keyframes animate {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        .a::after {
            content: '';
            position: absolute;
            inset: 4px;
            background: #011e41;
        }
        .a:hover::after {
            background: var(--clr);
        }
        .a span {
            position: relative;
            z-index: 1;
            font-size: 2em;
            color: white;
            opacity: 0.5;
            text-transform: uppercase;
            letter-spacing: 4px;
            transition: 0.5s;
        }
        .a:hover span {
            opacity: 1;
        }
    </style>



</head>



<body>
    <div class="box">
            <h2><strong>WELCOME!!</strong></h2>
        </div>
        <br><br><br><br>
<!-- <img src="https://media.tenor.com/RRhijk6pHAoAAAAd/good-morning.gif" alt="Background GIF"> -->
        <br>
    </div>
    <div class="container">
        <div class="left-half">
            <h1 class="p1"><strong>Upload an Image</strong></h1>
            <input type="file" id="imageInput" accept="image/*">
            <h3 class="p1">Pixelation Level: </h3>
            <div class="dropdown">
            <select id="pixelationLevel" class="dropbtn">
                <div class="dropdown-content">
                    <option value="2">2</option>
                    <option value="4">4</option>
                    <option value="8" selected>8</option>
                    <option value="16">16</option>
                    <option value="32">32</option>
                </div>
            </select>
            </div>
        </div>
        <div class="right-half">
            <h1 class="p1"><strong>Pixelator</strong></h1>
            <br>
            <br>
            <div style="--clr: 	#6da7d9;--i:0;">
                <button id="manipulateButton" class="a"><a href="#"><span>Pixelate!</span></a></button>
            </div>
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
    //const url = "https://fte.stu.nighthawkcodingsociety.com/api/pixel-partner-api";
    const test_url = url + "/test";
    const pixelate_url = url + "/pixelate/";
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
        const uploadedImage = document.getElementById('uploadedImage');
        const pixelationLevel = document.getElementById('pixelationLevel').value;
        const leftHalf = document.getElementById('left-half'); //new code

        const file = imageInput.files[0];
        if (file) {
            const reader = new FileReader();
            reader.readAsDataURL(file);

            reader.onload = function (e) {
                const base64Data = e.target.result.split(',')[1];
                const fileName = file.name;
                uploadedImageName = file.name;
                const fileExtension = fileName.split('.').pop();
                // fetch the API
                // add option to change pixelate level
                data = {"pixelate_level": pixelationLevel, "base64image": base64Data}
                const image_options = {...post_options, method: 'POST', body: JSON.stringify(data)};
                fetch(pixelate_url, image_options)
                .then(response => {
                    // check for response errors
                    if (response.status !== 200) {
                        error('GET API response failure: ' + response.status);
                        return;
                    }

                    // valid response will have JSON data
                    response.json().then(data => {
                        console.log(data)
                            const pixelatedImage = new Image();
                            pixelatedImage.src = 'data:image/' + fileExtension + ';base64,' + data['base64image'];

                            // Set a max-height for the image to fit within the text box
                            pixelatedImage.style.maxHeight = '100%';

                            uploadedImage.src = pixelatedImage.src;
                            uploadedImage.style.display = 'block';

                            pixelatedImage.onload = function() {
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
        }
    };
    function handleDownloadClick() {
        const uploadedImage = document.getElementById('uploadedImage');
        const pixelatedImage = new Image();
        pixelatedImage.src = uploadedImage.src;

        // checking if no images is uploaded
        if (uploadedImage.width == 0) {
            //sends alert
            alert('Please upload an image before trying to download');
            return;
        }
        // Create an anchor element for downloading
        const downloadLink = document.createElement('a');
        downloadLink.href = pixelatedImage.src;
        downloadLink.download = uploadedImageName.split('.')[0] + "_pixelated." + uploadedImageName.split('.')[1];
        downloadLink.style.display = 'none';

        // Append the anchor element to the document and trigger a click event
        document.body.appendChild(downloadLink);
        downloadLink.click();

        // Remove the anchor element
        document.body.removeChild(downloadLink);

    }
    const downloadButton = document.getElementById('downloadButton');
    downloadButton.addEventListener('click', handleDownloadClick);
    const manipulateButton = document.getElementById('manipulateButton');
    manipulateButton.addEventListener('click', handleImageUpload);
</script>

</body>
<br><br>