<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Keno Number Picker</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      padding: 2em;
      background-color: #f0f0f0;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(10, 1fr);
      gap: 0.5em;
      max-width: 600px;
      margin: 1em auto;
    }
    .square {
      border: 1px solid #ccc;
      padding: 1em;
      background: white;
      border-radius: 6px;
      font-weight: bold;
      font-size: 1.2em;
    }
    .picked {
      background-color: gold;
      color: black;
    }
    button {
      padding: 1em 2em;
      font-size: 1.2em;
      margin-top: 1em;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Keno Number Picker</h1>
  <p>Click the button to draw 20 random numbers!</p>
  <div class="grid" id="kenoGrid"></div>
  <button onclick="pickNumbers()">Pick 20 Numbers</button>

  <script>
    const grid = document.getElementById('kenoGrid');

    // Create the grid of numbers
    for (let i = 1; i <= 80; i++) {
      const square = document.createElement('div');
      square.className = 'square';
      square.textContent = i.toString().padStart(2, '0');
      grid.appendChild(square);
    }

    function pickNumbers() {
      const allSquares = document.querySelectorAll('.square');
      allSquares.forEach(s => s.classList.remove('picked'));

      const picks = new Set();
      while (picks.size < 20) {
        picks.add(Math.floor(Math.random() * 80));
      }

      picks.forEach(index => {
        allSquares[index].classList.add('picked');
      });
    }
  </script>
</body>
</html>
