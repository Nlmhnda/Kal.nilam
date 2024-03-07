index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>kalkulator</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <div class="kalkulator">
      <input type="text" placeholder="0" id="inputbox">
      <div>
        <button class="main" onclick="clearAll()">AC</button>
        <button class="main" onclick="deleteOne()">DEL</button>
        <button class="operator" onclick="percentage()">%</button>
        <button class="operator" onclick="divide()">/</button>
      </div>
      <div>
        <button onclick="appendNumber(7)">7</button>
        <button onclick="appendNumber(8)">8</button>
        <button onclick="appendNumber(9)">9</button>
        <button class="operator" onclick="multiply()">*</button>
      </div>
      <div>
        <button onclick="appendNumber(4)">4</button>
        <button onclick="appendNumber(5)">5</button>
        <button onclick="appendNumber(6)">6</button>
        <button class="operator" onclick="subtract()">-</button>
      </div>
      <div>
        <button onclick="appendNumber(1)">1</button>
        <button onclick="appendNumber(2)">2</button>
        <button onclick="appendNumber(3)">3</button>
        <button class="operator" onclick="add()">+</button>
      </div>
      <div>
        <button onclick="appendNumber(0)">0</button>
        <button onclick="appendNumber('.')">.</button>
        <button class="hasil" onclick="calculate()">=</button>
      </div>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>

style.css
* {
  margin: 0; 
  padding: 0; 
  box-sizing: border-box; 
  font-family: 'Poppins', sans-serif; 
}

.container {
  height: 100vh; 
  width: 100%; 
  background: #303136; 
  display: flex; 
  align-items: center; 
  justify-content: center; 
}

.kalkulator {
  background: #171717; 
  padding: 26px; 
  border-radius: 20px; 
}

input {
  width: 335px; 
  padding: 25px; 
  margin: 10px; 
  background: transparent; 
  border: none; 
  outline: none; 
  font-size: 45px; 
  text-align: right; 
  color: #fff; 
}
input::placeholder {
  color: #fff; 
}

button {
  border: none; 
  outline: none;
  width: 60px; 
  height: 60px; 
  border-radius: 10px; 
  background: #303136; 
  font-size: 21px; 
  font-weight: 600; 
  color: white; 
  margin: 10px; 
  cursor: pointer;
}

.hasil {
  width: 144px; 
  color: white; 
  background: orange; 
  font-weight: 700; 
}

.main {
  color: white; 
  }
.operator {
   color:white;
   background:blueviolet;
 }

 script.js

 document.addEventListener('DOMContentLoaded', function () {
  let input = document.getElementById('inputbox');
  let buttons = document.querySelectorAll('button');

  let string = "";
  
  buttons.forEach(button => {
    button.addEventListener('click', (e) => {
      if (e.target.textContent === '=') {
        try {
          string = eval(string);
          input.value = string;
        } catch (error) {
          input.value = 'Error';
        }
      } else if (e.target.textContent === 'AC') {
        string = "";
        input.value = string;
      } else if (e.target.textContent === 'DEL') {
        string = string.substring(0, string.length - 1);
        input.value = string;
      } else {
        string += e.target.textContent;
        input.value = string;
      }
    });
  });
});
 

