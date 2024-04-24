#<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Design Manifesto: Goals for Design</title>
    <style>
        body {
            background-image: url('https://raw.githubusercontent.com/brunodigennaro/manifesto/1c043e916ffb615ff49a8fed7ba623fe91edf5f4/gradient_background.gif');
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
            height: 100vh;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Georgia, serif;
            font-weight: lighter;
        }
        .container {
            max-width: 800px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            cursor: move;
            user-select: none;
            position: absolute;
        }
        h1 {
            text-align: center;
            margin-bottom: 30px;
        }
        ol {
            list-style-position: inside;
            padding-left: 0;
        }
        li {
            margin-bottom: 15px;
        }
        li:nth-child(odd) {
            text-align: left;
        }
        li:nth-child(even) {
            text-align: right;
        }
        .dog-link {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 100px;
            height: 100px;
            background-image: url('https://www.omfgdogs.com/omfgdogs.gif');
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
            border-radius: 50%;
            cursor: pointer;
            animation: spin 2s linear infinite, move 4s ease-in-out infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        @keyframes move {
            0% { right: 20px; }
            50% { right: calc(100% - 120px); }
            100% { right: 20px; }
        }
    </style>
</head>
<body>
    <div id="draggable" class="container" draggable="true" ondragstart="drag(event)">
        <h1>Manifesto: Goals for Design</h1>
        <ol>
            <li>Growth is consistent</li>
            <li>Think simple</li>
            <li>Start before you know how</li>
            <li>Design helps the world</li>
            <li>Design communicates information</li>
            <li>Design is a visual language</li>
            <li>Be present</li>
            <li>Attention to detail matters</li>
            <li>Enjoy the process</li>
        </ol>
    </div>

    <a href="https://www.omfgdogs.com/#" target="_blank" class="dog-link"></a>

    <script>
        const draggable = document.getElementById('draggable');
        let isDragging = false;
        let currentX;
        let currentY;
        let initialX;
        let initialY;
        let xOffset = 0;
        let yOffset = 0;

        draggable.addEventListener('mousedown', dragStart);
        document.addEventListener('mouseup', dragEnd);
        document.addEventListener('mousemove', drag);

        function dragStart(e) {
            initialX = e.clientX - xOffset;
            initialY = e.clientY - yOffset;

            if (e.target === draggable) {
                isDragging = true;
            }
        }

        function dragEnd(e) {
            initialX = currentX;
            initialY = currentY;

            isDragging = false;
        }

        function drag(e) {
            if (isDragging) {
                e.preventDefault();
                currentX = e.clientX - initialX;
                currentY = e.clientY - initialY;

                xOffset = currentX;
                yOffset = currentY;

                setTranslate(currentX, currentY, draggable);
            }
        }

        function setTranslate(xPos, yPos, el) {
            el.style.transform = `translate3d(${xPos}px, ${yPos}px, 0)`;
        }
    </script>
</body>
</html>
