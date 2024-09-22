

<!-- BEST OPTION -->
<html>
<div class="calculator">
  <div class="input" id="input"></div>
  <div class="buttons">
    <div class="operators">
      <div>+</div>
      <div>-</div>
      <div>&times;</div>
      <div>&divide;</div>
    </div>
    <div class="leftPanel">
      <div class="numbers">
        <div>7</div>
        <div>8</div>
        <div>9</div>
      </div>
      <div class="numbers">
        <div>4</div>
        <div>5</div>
        <div>6</div>
      </div>
      <div class="numbers">
        <div>1</div>
        <div>2</div>
        <div>3</div>
      </div>
      <div class="numbers">
        <div>0</div>
        <div>.</div>
        <div id="clear">C</div>
      </div>
      <!-- New row for special operations -->
      <div class="numbers">
        <div id="sqrt">√</div>
        <div id="power">x²</div>
        <div id="reciprocal">1/x</div>
      </div>
    </div>
    <div class="equal" id="result">=</div>
  </div>
</div>
</html>


<style>
body {
  /* width: 500px; */
  margin: 4% auto;
  /* font-family: 'Source Sans Pro', sans-serif;
  letter-spacing: 5px;
  font-size: 1.8rem; */
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}


.calculator {
  padding: 20px;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-radius: 1px;
}


.input {
  border: 1px solid #ddd;
  border-radius: 1px;
  height: 60px;
  padding-right: 15px;
  padding-top: 10px;
  text-align: right;
  margin-right: 6px;
  font-size: 2.5rem;
  overflow-x: auto;
  transition: all .2s ease-in-out;
}


.input:hover {
  border: 1px solid #bbb;
  -webkit-box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
}


.buttons {}


.operators {}


.operators div {
  display: inline-block;
  border: 1px solid #bbb;
  border-radius: 1px;
  width: 80px;
  text-align: center;
  padding: 10px;
  margin: 20px 4px 10px 0;
  cursor: pointer;
  background-color: #ddd;
  transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.operators div:hover {
  background-color: #ddd;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #aaa;
}


.operators div:active {
  font-weight: bold;
}


.leftPanel {
  display: inline-block;
}


.numbers div {
  display: inline-block;
  border: 1px solid #ddd;
  border-radius: 1px;
  width: 80px;
  text-align: center;
  padding: 10px;
  margin: 10px 4px 10px 0;
  cursor: pointer;
  background-color: #f9f9f9;
  transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.numbers div:hover {
  background-color: #f1f1f1;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #bbb;
}


.numbers div:active {
  font-weight: bold;
}


div.equal {
  display: inline-block;
  border: 1px solid #3079ED;
  border-radius: 1px;
  width: 17%;
  text-align: center;
  padding: 127px 10px;
  margin: 10px 6px 10px 0;
  vertical-align: top;
  cursor: pointer;
  color: #FFF;
  background-color: #4d90fe;
  transition: all .2s ease-in-out;
}


div.equal:hover {
  background-color: #307CF9;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #1857BB;
}


div.equal:active {
  font-weight: bold;
}
</style>


<script>
"use strict";


var input = document.getElementById('input'), // input/output button
    number = document.querySelectorAll('.numbers div'), // number buttons
    operator = document.querySelectorAll('.operators div'), // operator buttons
    result = document.getElementById('result'), // equal button
    clear = document.getElementById('clear'), // clear button
    sqrt = document.getElementById('sqrt'), // square root button
    power = document.getElementById('power'), // power of two button
    reciprocal = document.getElementById('reciprocal'), // reciprocal button
    resultDisplayed = false; // flag to keep an eye on what output is displayed


// adding click handlers to number buttons
for (var i = 0; i < number.length; i++) {
  number[i].addEventListener("click", function(e) {
    var currentString = input.innerHTML;
    var lastChar = currentString[currentString.length - 1];


    if (resultDisplayed === false) {
      input.innerHTML += e.target.innerHTML;
    } else if (resultDisplayed === true && (lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷")) {
      resultDisplayed = false;
      input.innerHTML += e.target.innerHTML;
    } else {
      resultDisplayed = false;
      input.innerHTML = "";
      input.innerHTML += e.target.innerHTML;
    }
  });
}


// adding click handlers to operator buttons
for (var i = 0; i < operator.length; i++) {
  operator[i].addEventListener("click", function(e) {
    var currentString = input.innerHTML;
    var lastChar = currentString[currentString.length - 1];


    if (lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷") {
      var newString = currentString.substring(0, currentString.length - 1) + e.target.innerHTML;
      input.innerHTML = newString;
    } else if (currentString.length === 0) {
      console.log("Enter a number first");
    } else {
      input.innerHTML += e.target.innerHTML;
    }
  });
}


// equals button functionality
result.addEventListener("click", function() {
  var inputString = input.innerHTML;
  var numbers = inputString.split(/\+|\-|\×|\÷/g);
  var operators = inputString.replace(/[0-9]|\./g, "").split("");


  var divide = operators.indexOf("÷");
  while (divide != -1) {
    numbers.splice(divide, 2, numbers[divide] / numbers[divide + 1]);
    operators.splice(divide, 1);
    divide = operators.indexOf("÷");
  }


  var multiply = operators.indexOf("×");
  while (multiply != -1) {
    numbers.splice(multiply, 2, numbers[multiply] * numbers[multiply + 1]);
    operators.splice(multiply, 1);
    multiply = operators.indexOf("×");
  }


  var subtract = operators.indexOf("-");
  while (subtract != -1) {
    numbers.splice(subtract, 2, numbers[subtract] - numbers[subtract + 1]);
    operators.splice(subtract, 1);
    subtract = operators.indexOf("-");
  }


  var add = operators.indexOf("+");
  while (add != -1) {
    numbers.splice(add, 2, parseFloat(numbers[add]) + parseFloat(numbers[add + 1]));
    operators.splice(add, 1);
    add = operators.indexOf("+");
  }


  input.innerHTML = numbers[0]
  </script>





<!-- code 1 -->
<html>
<div class="calculator">
 <div class="input" id="input"></div>
 <div class="buttons">
   <div class="operators">
     <div>+</div>
     <div>-</div>
     <div>&times;</div>
     <div>&divide;</div>
   </div>
   <div class="leftPanel">
     <div class="numbers">
       <div>7</div>
       <div>8</div>
       <div>9</div>
     </div>
     <div class="numbers">
       <div>4</div>
       <div>5</div>
       <div>6</div>
     </div>
     <div class="numbers">
       <div>1</div>
       <div>2</div>
       <div>3</div>
     </div>
     <div class="numbers">
       <div>0</div>
       <div>.</div>
       <div id="clear">C</div>
     </div>
   </div>
   <div class="equal" id="result">=</div>
 </div>
</div>
</html>


<style>
body {
 width: 500px;
 margin: 4% auto;
 font-family: 'Source Sans Pro', sans-serif;
 letter-spacing: 5px;
 font-size: 1.8rem;
 -moz-user-select: none;
 -webkit-user-select: none;
 -ms-user-select: none;
}


.calculator {
 padding: 20px;
 -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 border-radius: 1px;
}


.input {
 border: 1px solid #ddd;
 border-radius: 1px;
 height: 60px;
 padding-right: 15px;
 padding-top: 10px;
 text-align: right;
 margin-right: 6px;
 font-size: 2.5rem;
 overflow-x: auto;
 transition: all .2s ease-in-out;
}


.input:hover {
 border: 1px solid #bbb;
 -webkit-box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
}


.buttons {}


.operators {}


.operators div {
 display: inline-block;
 border: 1px solid #bbb;
 border-radius: 1px;
 width: 80px;
 text-align: center;
 padding: 10px;
 margin: 20px 4px 10px 0;
 cursor: pointer;
 background-color: #ddd;
 transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.operators div:hover {
 background-color: #ddd;
 -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 border-color: #aaa;
}


.operators div:active {
 font-weight: bold;
}


.leftPanel {
 display: inline-block;
}


.numbers div {
 display: inline-block;
 border: 1px solid #ddd;
 border-radius: 1px;
 width: 80px;
 text-align: center;
 padding: 10px;
 margin: 10px 4px 10px 0;
 cursor: pointer;
 background-color: #f9f9f9;
 transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.numbers div:hover {
 background-color: #f1f1f1;
 -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 border-color: #bbb;
}


.numbers div:active {
 font-weight: bold;
}


div.equal {
 display: inline-block;
 border: 1px solid #3079ED;
 border-radius: 1px;
 width: 17%;
 text-align: center;
 padding: 127px 10px;
 margin: 10px 6px 10px 0;
 vertical-align: top;
 cursor: pointer;
 color: #FFF;
 background-color: #4d90fe;
 transition: all .2s ease-in-out;
}


div.equal:hover {
 background-color: #307CF9;
 -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
 border-color: #1857BB;
}


div.equal:active {
 font-weight: bold;
}
</style>


<script>
   "use strict";


var input = document.getElementById('input'), // input/output button
 number = document.querySelectorAll('.numbers div'), // number buttons
 operator = document.querySelectorAll('.operators div'), // operator buttons
 result = document.getElementById('result'), // equal button
 clear = document.getElementById('clear'), // clear button
 resultDisplayed = false; // flag to keep an eye on what output is displayed


// adding click handlers to number buttons
for (var i = 0; i < number.length; i++) {
 number[i].addEventListener("click", function(e) {


   // storing current input string and its last character in variables - used later
   var currentString = input.innerHTML;
   var lastChar = currentString[currentString.length - 1];


   // if result is not diplayed, just keep adding
   if (resultDisplayed === false) {
     input.innerHTML += e.target.innerHTML;
   } else if (resultDisplayed === true && lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷") {
     // if result is currently displayed and user pressed an operator
     // we need to keep on adding to the string for next operation
     resultDisplayed = false;
     input.innerHTML += e.target.innerHTML;
   } else {
     // if result is currently displayed and user pressed a number
     // we need clear the input string and add the new input to start the new opration
     resultDisplayed = false;
     input.innerHTML = "";
     input.innerHTML += e.target.innerHTML;
   }


 });
}


// adding click handlers to number buttons
for (var i = 0; i < operator.length; i++) {
 operator[i].addEventListener("click", function(e) {


   // storing current input string and its last character in variables - used later
   var currentString = input.innerHTML;
   var lastChar = currentString[currentString.length - 1];


   // if last character entered is an operator, replace it with the currently pressed one
   if (lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷") {
     var newString = currentString.substring(0, currentString.length - 1) + e.target.innerHTML;
     input.innerHTML = newString;
   } else if (currentString.length == 0) {
     // if first key pressed is an opearator, don't do anything
     console.log("enter a number first");
   } else {
     // else just add the operator pressed to the input
     input.innerHTML += e.target.innerHTML;
   }


 });
}


// on click of 'equal' button
result.addEventListener("click", function() {


 // this is the string that we will be processing eg. -10+26+33-56*34/23
 var inputString = input.innerHTML;


 // forming an array of numbers. eg for above string it will be: numbers = ["10", "26", "33", "56", "34", "23"]
 var numbers = inputString.split(/\+|\-|\×|\÷/g);


 // forming an array of operators. for above string it will be: operators = ["+", "+", "-", "*", "/"]
 // first we replace all the numbers and dot with empty string and then split
 var operators = inputString.replace(/[0-9]|\./g, "").split("");


 console.log(inputString);
 console.log(operators);
 console.log(numbers);
 console.log("----------------------------");


 // now we are looping through the array and doing one operation at a time.
 // first divide, then multiply, then subtraction and then addition
 // as we move we are alterning the original numbers and operators array
 // the final element remaining in the array will be the output


 var divide = operators.indexOf("÷");
 while (divide != -1) {
   numbers.splice(divide, 2, numbers[divide] / numbers[divide + 1]);
   operators.splice(divide, 1);
   divide = operators.indexOf("÷");
 }


 var multiply = operators.indexOf("×");
 while (multiply != -1) {
   numbers.splice(multiply, 2, numbers[multiply] * numbers[multiply + 1]);
   operators.splice(multiply, 1);
   multiply = operators.indexOf("×");
 }


 var subtract = operators.indexOf("-");
 while (subtract != -1) {
   numbers.splice(subtract, 2, numbers[subtract] - numbers[subtract + 1]);
   operators.splice(subtract, 1);
   subtract = operators.indexOf("-");
 }


 var add = operators.indexOf("+");
 while (add != -1) {
   // using parseFloat is necessary, otherwise it will result in string concatenation :)
   numbers.splice(add, 2, parseFloat(numbers[add]) + parseFloat(numbers[add + 1]));
   operators.splice(add, 1);
   add = operators.indexOf("+");
 }


 input.innerHTML = numbers[0]; // displaying the output


 resultDisplayed = true; // turning flag if result is displayed
});


// clearing the input on press of clear
clear.addEventListener("click", function() {
 input.innerHTML = "";
})
</script>





<!-- code 2 -->
<html>
<div class="calculator">
  <div class="input" id="input"></div>
  <div class="buttons">
    <div class="operators">
      <div>+</div>
      <div>-</div>
      <div>&times;</div>
      <div>&divide;</div>
    </div>
    <div class="leftPanel">
      <div class="numbers">
        <div>7</div>
        <div>8</div>
        <div>9</div>
      </div>
      <div class="numbers">
        <div>4</div>
        <div>5</div>
        <div>6</div>
      </div>
      <div class="numbers">
        <div>1</div>
        <div>2</div>
        <div>3</div>
      </div>
      <div class="numbers">
        <div>0</div>
        <div>.</div>
        <div id="clear">C</div>
      </div>
      <!-- New row for special operations -->
      <div class="numbers">
        <div id="sqrt">√</div>
        <div id="power">x²</div>
        <div id="reciprocal">1/x</div>
      </div>
    </div>
    <div class="equal" id="result">=</div>
  </div>
</div>
</html>


<style>
body {
  width: 500px;
  margin: 4% auto;
  font-family: 'Source Sans Pro', sans-serif;
  letter-spacing: 5px;
  font-size: 1.8rem;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}


.calculator {
  padding: 20px;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-radius: 1px;
}


.input {
  border: 1px solid #ddd;
  border-radius: 1px;
  height: 60px;
  padding-right: 15px;
  padding-top: 10px;
  text-align: right;
  margin-right: 6px;
  font-size: 2.5rem;
  overflow-x: auto;
  transition: all .2s ease-in-out;
}


.input:hover {
  border: 1px solid #bbb;
  -webkit-box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
}


.buttons {}


.operators {}


.operators div {
  display: inline-block;
  border: 1px solid #bbb;
  border-radius: 1px;
  width: 80px;
  text-align: center;
  padding: 10px;
  margin: 20px 4px 10px 0;
  cursor: pointer;
  background-color: #ddd;
  transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.operators div:hover {
  background-color: #ddd;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #aaa;
}


.operators div:active {
  font-weight: bold;
}


.leftPanel {
  display: inline-block;
}


.numbers div {
  display: inline-block;
  border: 1px solid #ddd;
  border-radius: 1px;
  width: 80px;
  text-align: center;
  padding: 10px;
  margin: 10px 4px 10px 0;
  cursor: pointer;
  background-color: #f9f9f9;
  transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}


.numbers div:hover {
  background-color: #f1f1f1;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #bbb;
}


.numbers div:active {
  font-weight: bold;
}


div.equal {
  display: inline-block;
  border: 1px solid #3079ED;
  border-radius: 1px;
  width: 17%;
  text-align: center;
  padding: 127px 10px;
  margin: 10px 6px 10px 0;
  vertical-align: top;
  cursor: pointer;
  color: #FFF;
  background-color: #4d90fe;
  transition: all .2s ease-in-out;
}


div.equal:hover {
  background-color: #307CF9;
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  border-color: #1857BB;
}


div.equal:active {
  font-weight: bold;
}
</style>


<script>
"use strict";


var input = document.getElementById('input'), // input/output button
    number = document.querySelectorAll('.numbers div'), // number buttons
    operator = document.querySelectorAll('.operators div'), // operator buttons
    result = document.getElementById('result'), // equal button
    clear = document.getElementById('clear'), // clear button
    sqrt = document.getElementById('sqrt'), // square root button
    power = document.getElementById('power'), // power of two button
    reciprocal = document.getElementById('reciprocal'), // reciprocal button
    resultDisplayed = false; // flag to keep an eye on what output is displayed


// adding click handlers to number buttons
for (var i = 0; i < number.length; i++) {
  number[i].addEventListener("click", function(e) {
    var currentString = input.innerHTML;
    var lastChar = currentString[currentString.length - 1];


    if (resultDisplayed === false) {
      input.innerHTML += e.target.innerHTML;
    } else if (resultDisplayed === true && (lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷")) {
      resultDisplayed = false;
      input.innerHTML += e.target.innerHTML;
    } else {
      resultDisplayed = false;
      input.innerHTML = "";
      input.innerHTML += e.target.innerHTML;
    }
  });
}


// adding click handlers to operator buttons
for (var i = 0; i < operator.length; i++) {
  operator[i].addEventListener("click", function(e) {
    var currentString = input.innerHTML;
    var lastChar = currentString[currentString.length - 1];


    if (lastChar === "+" || lastChar === "-" || lastChar === "×" || lastChar === "÷") {
      var newString = currentString.substring(0, currentString.length - 1) + e.target.innerHTML;
      input.innerHTML = newString;
    } else if (currentString.length === 0) {
      console.log("Enter a number first");
    } else {
      input.innerHTML += e.target.innerHTML;
    }
  });
}


// equals button functionality
result.addEventListener("click", function() {
  var inputString = input.innerHTML;
  var numbers = inputString.split(/\+|\-|\×|\÷/g);
  var operators = inputString.replace(/[0-9]|\./g, "").split("");


  var divide = operators.indexOf("÷");
  while (divide != -1) {
    numbers.splice(divide, 2, numbers[divide] / numbers[divide + 1]);
    operators.splice(divide, 1);
    divide = operators.indexOf("÷");
  }


  var multiply = operators.indexOf("×");
  while (multiply != -1) {
    numbers.splice(multiply, 2, numbers[multiply] * numbers[multiply + 1]);
    operators.splice(multiply, 1);
    multiply = operators.indexOf("×");
  }


  var subtract = operators.indexOf("-");
  while (subtract != -1) {
    numbers.splice(subtract, 2, numbers[subtract] - numbers[subtract + 1]);
    operators.splice(subtract, 1);
    subtract = operators.indexOf("-");
  }


  var add = operators.indexOf("+");
  while (add != -1) {
    numbers.splice(add, 2, parseFloat(numbers[add]) + parseFloat(numbers[add + 1]));
    operators.splice(add, 1);
    add = operators.indexOf("+");
  }


  input.innerHTML = numbers[0]
  </script>





<!-- code 3 -->
<html>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./calc.js" type="text/javascript"></script> 
    <link rel="stylesheet" href="calc.css">
    <title>Document</title>
</head>
<body>
    <h1 style="text-align:center">Calculator App</h1>
    <div class="container">
    <br>
    <table>
        <tr>
            <td colspan="3"><input type='text' id='result' class ='screen' style="text-align: right;"></td>
            <td>
                <input type='button' value = 'C' onclick="clearScreen()" class="clear"/>
            </td>
        </tr>
    </table>
    <div class="keys">
    <input type="button" value="7" class="button" onClick="display('7')"></input>
    <input type="button" value="8" class="button " onClick="display('8')"></input
    <input type="button" value="9" class="button" onClick="display('9')"></input>
    <input type="button" value="/" class="operator" onClick="display('/')"></input>
    <input type="button" value="4" class="button" onClick="display('4')"></input>
    <input type="button" value="5" class="button" onClick="display('5')"></input>
    <input type="button" value="6" class="button" onClick="display('6')"></input>
    <input type="button" value="*" class="operator" onClick="display('*')"></input>
    <input type="button" value="1" class="button" onClick="display('1')"></input>
    <input type="button" value="2" class="button" onClick="display('2')"></input>
    <input type="button" value="3" class="button" onClick="display('3')"></input>
    <input type="button" value="-" class="operator" onClick="display('-')"></input>
    <input type="button" value="0" class="button" onClick="display('0')"></input>
    <input type="button" value="." class="button" onClick="display('.')"></input>
    <input type="button" value= "=" class="button equal-sign" onClick="solve()"></input>
    <input type="button" value="+" class="operator" onClick="display('+')"></input>
</div> 
</div>
</body>
</html>

<style>
    .container {

    border: 1px solid #cccccc;

    box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);

    border-radius: 20px;

    position: absolute;

    top: 55%;

    left: 50%;

    transform: translate(-50%, -50%);

    width: 450px;

    height: 400px;

}

.keys {

    display: grid;

    grid-template-columns: repeat(4, 1fr);

    grid-gap: 10px;

    padding: 10px;

    margin:auto;

}

.button {

    height: 60px;

    padding: 5px;

    background-color: #fff;

    border-radius: 3px;

    border: 1px solid #c4c4c4;

    background-color: transparent;

    font-size: 2rem;

    color: #333;

    background-image: linear-gradient(to bottom, transparent, transparent 50%, rgba(0,0,0,.04));

    box-shadow: inset 0 0 0 1px rgba(255,255,255,.05), inset 0 1px 0 0 rgba(255,255,255,.45), inset 0 -1px 0 0 rgba(255,255,255,.15), 0 1px 0 0 rgba(255,255,255,.15);

    text-shadow: 0 1px rgba(255,255,255,.4);

}

.button:hover {

    background-color: #eaeaea;

}

.operator {

    color: #fff;

    background-color: #eebb24;

}

.clear {

    background-color: #f0595f;

    border-color: #b0353a;

    color: #fff;

    width: 80px;

    height: 30px;  

}

.clear:hover {

    background-color: #f17377;

}

.equal-sign {

    background-color: #25a8e0;

    border-color: #25a8e0;

    color: #fff;

}

.equal-sign:hover {

    background-color: #4e9ed4;

}

.screen{

    background-color:rgb(171, 219, 231);

    justify-content: left;

    color: black;

    font-size: medium;

    width: 50%;

    height: 30%;

    cursor: default;

    padding: 10px; 

    padding-left: 40%;

    margin: auto;

    margin-bottom: 10px;

}

After adding the styling, your application will look like this. 
</style>

<script>
    function display(val){

    document.getElementById('result').value += val

    return val

}
    function solve(){

    let x = document.getElementById('result').value

    let y = eval(x);

    document.getElementById('result').value = y

    return y

}
    function clearScreen(){

    document.getElementById('result').value = ''

}
</script>





<!-- mort's code -->
<!-- 
Hack 0: Right justify the result
Hack 1: Test conditions on small, big, and decimal numbers, and report on findings. Fix issues.
Hack 2: Add the common math operation that is missing from the calculator
Hack 3: Implement 1 number operation (ie SQRT) 
-->

<!-- 
HTML implementation of the calculator. 
-->

<!-- 
    Style and Action are aligned with HRML class definitions
    style.css contains the majority of style definitions (number, operation, clear, and equals)
    - The div calculator container sets 4 elements to a row
    The background is credited to Vanta JS and is implemented at the bottom of this page
-->
<style>
  .calculator-output {
    /*
      calculator output
      the top bar shows the results of the calculator;
      result to take up the entirety of the first row;
      span defines 4 columns and 1 row
    */
    grid-column: span 4;
    grid-row: span 1;
  
    border-radius: 10px;
    padding: 0.25em;
    font-size: 20px;
    border: 5px solid black;
  
    display: flex;
    align-items: center;
  }
  canvas {
    filter: none;
  }
</style>

<!-- Add a container for the animation -->
<div id="animation">
  <div class="calculator-container">
      <!--result-->
      <div class="calculator-output" id="output">0</div>
      <!--row 1-->
      <div class="calculator-number">1</div>
      <div class="calculator-number">2</div>
      <div class="calculator-number">3</div>
      <div class="calculator-operation">+</div>
      <!--row 2-->
      <div class="calculator-number">4</div>
      <div class="calculator-number">5</div>
      <div class="calculator-number">6</div>
      <div class="calculator-operation">-</div>
      <!--row 3-->
      <div class="calculator-number">7</div>
      <div class="calculator-number">8</div>
      <div class="calculator-number">9</div>
      <div class="calculator-operation">*</div>
      <!--row 4-->
      <div class="calculator-clear">A/C</div>
      <div class="calculator-number">0</div>
      <div class="calculator-number">.</div>
      <div class="calculator-equals">=</div>
  </div>
</div>

<!-- JavaScript (JS) implementation of the calculator. -->
<script>
// initialize important variables to manage calculations
var firstNumber = null;
var operator = null;
var nextReady = true;
//Build objects containing key elements
const output = document.getElementById("output");
const numbers = document.querySelectorAll(".calculator-number");
const operations = document.querySelectorAll(".calculator-operation");
const clear = document.querySelectorAll(".calculator-clear");
const equals = document.querySelectorAll(".calculator-equals");

// Number buttons listener
numbers.forEach(button => {
  button.addEventListener("click", function() {
    number(button.textContent);
  });
});

// Number action
function number (value) { // function to input numbers into the calculator
    if (value != ".") {
        if (nextReady == true) { // nextReady is used to tell the computer when the user is going to input a completely new number
            output.innerHTML = value;
            if (value != "0") { // if statement to ensure that there are no multiple leading zeroes
                nextReady = false;
            }
        } else {
            output.innerHTML = output.innerHTML + value; // concatenation is used to add the numbers to the end of the input
        }
    } else { // special case for adding a decimal; can't have two decimals
        if (output.innerHTML.indexOf(".") == -1) {
            output.innerHTML = output.innerHTML + value;
            nextReady = false;
        }
    }
}

// Operation buttons listener
operations.forEach(button => {
  button.addEventListener("click", function() {
    operation(button.textContent);
  });
});

// Operator action
function operation (choice) { // function to input operations into the calculator
    if (firstNumber == null) { // once the operation is chosen, the displayed number is stored into the variable firstNumber
        firstNumber = parseInt(output.innerHTML);
        nextReady = true;
        operator = choice;
        return; // exits function
    }
    // occurs if there is already a number stored in the calculator
    firstNumber = calculate(firstNumber, parseFloat(output.innerHTML)); 
    operator = choice;
    output.innerHTML = firstNumber.toString();
    nextReady = true;
}

// Calculator
function calculate (first, second) { // function to calculate the result of the equation
    let result = 0;
    switch (operator) {
        case "+":
            result = first + second;
            break;
        case "-":
            result = first - second;
            break;
        case "*":
            result = first * second;
            break;
        case "/":
            result = first / second;
            break;
        default: 
            break;
    }
    return result;
}

// Equals button listener
equals.forEach(button => {
  button.addEventListener("click", function() {
    equal();
  });
});

// Equal action
function equal () { // function used when the equals button is clicked; calculates equation and displays it
    firstNumber = calculate(firstNumber, parseFloat(output.innerHTML));
    output.innerHTML = firstNumber.toString();
    nextReady = true;
}

// Clear button listener
clear.forEach(button => {
  button.addEventListener("click", function() {
    clearCalc();
  });
});

// A/C action
function clearCalc () { // clears calculator
    firstNumber = null;
    output.innerHTML = "0";
    nextReady = true;
}
</script>

<!-- 
Vanta animations just for fun, load JS onto the page
-->
<script src="{{site.baseurl}}/assets/js/three.r119.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.halo.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.birds.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.net.min.js"></script>
<script src="{{site.baseurl}}/assets/js/vanta.rings.min.js"></script>

<script>
// setup vanta scripts as functions
var vantaInstances = {
  halo: VANTA.HALO,
  birds: VANTA.BIRDS,
  net: VANTA.NET,
  rings: VANTA.RINGS
};

// obtain a random vanta function
var vantaInstance = vantaInstances[Object.keys(vantaInstances)[Math.floor(Math.random() * Object.keys(vantaInstances).length)]];

//Run the animation
vantaInstance({
  el: "#animation",
  mouseControls: true,
  touchControls: true,
  gyroControls: false
});
</script>

<style>
/* // STYLING PREFERENCES for Calculator Pages  */

/* define class for redefined button */
.calc-button {
    @include button();
}

/* // STYLING FOR JS CALCULATOR */

/* class to create the calculator's container; uses CSS grid display to partition off buttons */
.calculator-container {
    width: 90vw; /* this width and height is specified for mobile devices by default */
    height: 80vh;
    margin: 0 auto;

    display: grid;
    grid-template-columns: repeat(4, 1fr); /* fr is a special unit; learn more here: https://css-tricks.com/introduction-fr-css-unit/ */
    grid-template-rows: 0.5fr repeat(4, 1fr);
    gap: 10px 10px;
}

@media (min-width: 600px) {
    .calculator-container {
        width: 40vw;
        height: 80vh;
    }
}

/* styling for the calculator number button */
.calculator-number {
    @extend .calc-button;
}

/* styling for the calculator operation button */
.calculator-operation {
    @extend .calc-button;
}

/* styling for the calculator clear button */
.calculator-clear {
    @include button(orange, black, darkorange);
}

/* styling for the calculator equals button */
.calculator-equals {
    @include button(red, black, darkred);
}
</style>