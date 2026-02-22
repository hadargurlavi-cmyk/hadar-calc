// Scientific Calculator Pro (Node.js Version)

const readline = require("readline");

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

let isDegree = true;
let history = [];

console.log("🔬 Scientific Calculator Pro");
console.log("Type expressions like:");
console.log("  sin(30), cos(60), tan(45)");
console.log("  sqrt(9), log(100)");
console.log("  2^3, pi, e");
console.log("Type 'mode' to toggle DEG/RAD");
console.log("Type 'history' to see history");
console.log("Type 'exit' to quit\n");

function convertTrig(value) {
  return isDegree ? value * Math.PI / 180 : value;
}

function evaluateExpression(input) {
  try {

    // Replace constants
    input = input.replace(/pi/g, "Math.PI");
    input = input.replace(/e/g, "Math.E");

    // Replace power operator ^
    input = input.replace(/\^/g, "**");

    // Replace functions
    input = input.replace(/sqrt\(/g, "Math.sqrt(");
    input = input.replace(/log\(/g, "Math.log10(");

    input = input.replace(/sin\(([^)]+)\)/g, (_, val) =>
      `Math.sin(${convertTrig(eval(val))})`
    );

    input = input.replace(/cos\(([^)]+)\)/g, (_, val) =>
      `Math.cos(${convertTrig(eval(val))})`
    );

    input = input.replace(/tan\(([^)]+)\)/g, (_, val) =>
      `Math.tan(${convertTrig(eval(val))})`
    );

    // Check division by zero
    if (input.includes("/0")) {
      return "Error";
    }

    const result = eval(input);

    if (!isFinite(result)) return "Error";

    return result;

  } catch {
    return "Error";
  }
}

function prompt() {
  rl.question(">> ", (input) => {

    if (input.toLowerCase() === "exit") {
      console.log("Goodbye 👋");
      rl.close();
      return;
    }

    if (input.toLowerCase() === "mode") {
      isDegree = !isDegree;
      console.log("Mode:", isDegree ? "DEG" : "RAD");
      return prompt();
    }

    if (input.toLowerCase() === "history") {
      console.log("📜 History:");
      history.forEach(item => console.log(item));
      return prompt();
    }

    const result = evaluateExpression(input);

    console.log("=", result);

    if (result !== "Error") {
      history.push(input + " = " + result);
    }

    prompt();
  });
}

prompt();let isDegree = true;
const display = document.getElementById("display");
const historyDiv = document.getElementById("history");

function append(val){ display.value += val; }
function clearDisplay(){ display.value = ""; }

function toggleMode(){
  isDegree = !isDegree;
  document.querySelector(".special").innerText = isDegree ? "DEG" : "RAD";
}

function convertTrig(value){
  return isDegree ? value * Math.PI / 180 : value;
}

function calculate(){
  try{
    let expression = display.value;

    if(expression.includes("/0")){
      display.value = "Error";
      return;
    }

    // חישוב פונקציות טריגונומטריות במעלות
    expression = expression.replace(/Math\.sin\(([^)]+)\)/g, (_, val) =>
      `Math.sin(${convertTrig(eval(val))})`
    );
    expression = expression.replace(/Math\.cos\(([^)]+)\)/g, (_, val) =>
      `Math.cos(${convertTrig(eval(val))})`
    );
    expression = expression.replace(/Math\.tan\(([^)]+)\)/g, (_, val) =>
      `Math.tan(${convertTrig(eval(val))})`
    );

    let result = eval(expression);

    if(!isFinite(result)){
      display.value = "Error";
      return;
    }

    historyDiv.innerHTML += display.value + " = " + result + "<br>";
    display.value = result;

  } catch {
    display.value = "Error";
  }
}

// פונקציה לפתירת משוואות ריבועיות ax²+bx+c
function solveQuadratic(){
  const a = parseFloat(prompt("a ="));
  const b = parseFloat(prompt("b ="));
  const c = parseFloat(prompt("c ="));

  if(a === 0){
    alert("זה לא משוואה ריבועית!");
    return;
  }

  const D = b*b - 4*a*c;
  let result;

  if(D < 0){
    result = "אין פתרונות ממשיים";
  } else if(D === 0){
    result = -b / (2*a);
  } else {
    const x1 = (-b + Math.sqrt(D)) / (2*a);
    const x2 = (-b - Math.sqrt(D)) / (2*a);
    result = `x₁=${x1}, x₂=${x2}`;
  }

  display.value = result;
  historyDiv.innerHTML += `ax²+bx+c: ${result}<br>`;
}