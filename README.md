## 2019 Programming 1 Portfolio
**By Haru Yoo**

jiyoyoo9679@granitesd.org

## First Semester Processing Calculator
**Completed Nov, 2018**

Object-Oriented calculator with features including...
![Calculator Buttons](https://github.com/hyy9679/Programming-Portfolio-2019/blob/master/Images/Screen%20Shot%202019-05-08%20at%201.37.38%20PM.png)

![Calculator Buttons](https://github.com/hyy9679/Programming-Portfolio-2019/blob/master/Images/CalcScreenshot.png)

'''
Button[] numBtns = new Button[10];
Button[] opBtns = new Button[11];
String displayVal, leftVal, rightVal;
char opVal;
float result;
boolean firstNum;



void setup() {
  size(690, 580);
  background(#4D2404);
  textSize(25);
  numBtns[0] = new Button(128, 448, 190, 80, color(#994708)).asNumber(0);
  numBtns[1] = new Button(78, 148, 80, 80, color(#994708)).asNumber(1);
  numBtns[2] = new Button(178, 148, 80, 80, color(#994708)).asNumber(2);
  numBtns[3] = new Button(278, 148, 80, 80, color(#994708)).asNumber(3);
  opBtns[0] = new Button(378, 148, 80, 80, color(#994708)).asOperator("+");
  numBtns[4] = new Button(78, 248, 80, 80, color(#994708)).asNumber(4);
  numBtns[5] = new Button(178, 248, 80, 80, color(#994708)).asNumber(5);
  numBtns[6] = new Button(278, 248, 80, 80, color(#994708)).asNumber(6);
  opBtns[1] = new Button(378, 248, 80, 80, color(#994708)).asOperator("-");
  numBtns[7] = new Button(78, 348, 80, 80, color(#994708)).asNumber(7);
  numBtns[8] = new Button(178, 348, 80, 80, color(#994708)).asNumber(8);
  numBtns[9] = new Button(278, 348, 80, 80, color(#994708)).asNumber(9);
  opBtns[2] = new Button(378, 348, 80, 80, color(#994708)).asOperator("*");
  opBtns[3] = new Button(278, 448, 80, 80, color(#994708)).asOperator(".");
  opBtns[4] = new Button(378, 448, 80, 80, color(#994708)).asOperator("÷");
  opBtns[5] = new Button(530, 148, 190, 80, color(#994708)).asOperator("Clear");
  opBtns[6] = new Button(478, 248, 80, 80, color(#994708)).asOperator("π");
  opBtns[7] = new Button(578, 248, 80, 80, color(#994708)).asOperator("()");
  opBtns[8] = new Button(478, 348, 80, 80, color(#994708)).asOperator("^");
  opBtns[9] = new Button(578, 348, 80, 80, color(#994708)).asOperator("±");
  opBtns[10] = new Button(530, 448, 190, 80, color(#994708)).asOperator("=");
  displayVal = ""; 
  leftVal = "";
  rightVal = "";
  opVal = ' ';
  result = 0.0;
  firstNum = true;
}

void draw() {
  background(#4D2404);
  for (int i=0; i<numBtns.length; i++) {
    numBtns[i].display();
    numBtns[i].hover();
  }
  for (int i=0; i<opBtns.length; i++) {
    opBtns[i].display();
    opBtns[i].hover();
  }
  updateDisplay();
}
void updateDisplay() {
  fill(255);
  rect(294, 50, 530, 60, 7);
  textAlign(CENTER);
  fill(0);
  text(displayVal, 268, 60);
}

void mouseReleased() {
  for (int i=0; i<numBtns.length; i++) {
    if (numBtns[i].hov) {
      if (firstNum) {
        leftVal += numBtns[i].v;
        displayVal = leftVal;
      } else {
        rightVal += str(numBtns[i].v);
        displayVal = rightVal;
      }
    }
  } 
  for (int i=0; i<opBtns.length; i++) {
    if (opBtns[i].hov) {
      if (opBtns[i].op == "+") {
        opVal = '+';
        firstNum = false;
      } else if (opBtns[i].op == "-") {
        opVal = '-';
        firstNum = false;
      } else if (opBtns[i].op == "*") {
        opVal = '*';
        firstNum = false;
      } else if (opBtns[i].op == "±") {
        if (firstNum){
          leftVal = str(float(leftVal)*-1);
          displayVal = leftVal;
        } else {
          rightVal = str(float(rightVal)*-1);
          displayVal = rightVal;
        }

         if (firstNum) {
        leftVal += opBtns[i].op;
        displayVal = leftVal;
      } else {
        rightVal += opBtns[i].op;
        displayVal = rightVal;
      }
      } else if (opBtns[i].op == "÷") {
        opVal = '÷';
        firstNum = false;
      } else if (opBtns[i].op == "=") {
        performCalc();
        } else if (opBtns[i].op == "Clear") {
        clearButton();
      }
      }
    }}
  


void performCalc() {
  if (opVal == '+') {
    result = float(leftVal) + float(rightVal);
    displayVal = str(result);
  } else if (opVal == '-') {
    result = float(leftVal) - float(rightVal);
    displayVal = str(result);
  } else if (opVal == '*') {
    result = float(leftVal) * float(rightVal);
    displayVal = str(result);
  } else if (opVal == '÷') {
    result = float(leftVal) / float(rightVal);
    displayVal = str(result);
  } else if (opVal == '^') {
    result = int(leftVal) ^ int(rightVal);
    displayVal = str(result);
  } 
  firstNum = true;
}

void clearButton() {
   displayVal = "0.0"; 
  leftVal = "0.0";
  rightVal = "0.0";
  opVal = ' ';
  result = 0.0;
  firstNum = true;
  
}
'''
