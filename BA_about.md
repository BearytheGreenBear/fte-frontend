---
layout: page
title: About Our Team
permalink: /about/
---
<head>
    <style>
        /* Define styles for left and right halves */
        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .left-half, .right-half, .bottom-half{
            height: 250px;
            padding: 5px;
            color: #444444;
            font-family: 'IBM Plex Sans Hebrew', monospace;
        }
        .left-half {
            height: 300px;
            width: 575px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .right-half {
            width: 425px;
            text-align: center;
            border-left: 3px solid #bde4f4;
        }
        .bottom-half {
            border-top: 3px solid #bde4f4;
            text-align: center;
            align-items: center;
            width: 100%;
        }
        .p1 {
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #3A3B3C;
            /* src: url('fonts/fontface.css');  */
        }
        .p2 {
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
        .a {
            position: relative;
            padding: 13px 24px;
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
            width: 1200%;
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
            color: #ffcf01;
            font-family: 'IBM Plex Sans Hebrew', monospace;
            opacity: 0.7;
            text-transform: uppercase;
            letter-spacing: 4px;
            transition: 0.5s;
        }
        .a:hover span {
            opacity: 1;
        }
        *{
            box-sizing: border-box;
        }
        .label{
            background-color: #111;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
            border-radius: 50px;
            padding: 5px;
            height: 26px;
            width: 50px;
        }
        body{
            transition: background 0.18s linear;
        }
        body.dark{
            background-color: #191d2b;
        }
        .checkbox{
            opacity: 0;
            position: absolute;
        }
        .ball{
            background-color: #ffffff;
            border-radius: 50%;
            position: absolute;
            top: 2px;
            left: 2px;
            width: 22px;
            height: 22px;
            transition: transform 0.15s linear;
        }
        .checkbox:checked + .label .ball {
            transform: translateX(24px);
        }
        .fa-moon{
            color: #f1c40f;
        }
        .fa-sun{
            color: #f39c12;
        }
        .light-text{
            color: #3A3B3C;
        }
        .dark-text{ 
            color: #CCCCCC;
        }
    </style>
</head>
<body>
<br><br>
    <h8 class="p1 light-text"><strong>Light Switch down below</strong></h8>
    <div>
        <input type="checkbox"
            class="checkbox" id="checkbox" >
    <label for="checkbox" class="label">
        <i class="fas fa-moon"></i>
        <i class="fas fa-sun"></i>
        <div class="ball"></div>
    </label>
    </div>
    <div>
    <br>
    <h2 class="p1"> <strong>Scrum Master: Ian Wu</strong></h2>
    </div>
    <div>
    <br>
    <h3 class="p1"> FrontEnd: Ian Wu, Jason Guan</h3>
    </div>
    <div>
    <br>
    <h3 class="p1"> BackEnd: Ian Wu, Trever Huang, Kyle Liang</h3>
    </div>
    <br>
<br>



<script>
    const checkbox = document.getElementById('checkbox');
    const textElements = document.querySelectorAll('.p1, .p2, h1');
    checkbox.addEventListener('change', () => {
    document.body.classList.toggle('dark');
    //change the overall theme color.
    textElements.forEach((element) => {
    element.classList.toggle('dark-text');
    element.classList.toggle('light-text');
    //change the overall text color.
    });
    });
</script>

</body>
<br><br>