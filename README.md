# Python-Calulator-using-Tkinter-GUI
I have created the Python-Calulator using Tkinter GUI and also deployed in desktop installation.
Here's a comprehensive and visually appealing GitHub README template for your calculator project:

---

# 🧮 Python Calculator

![Calculator](https://img.shields.io/badge/Calculator-Python-blue.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Contributions](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)

![image](https://github.com/user-attachments/assets/03dd8869-88bb-4abc-b990-62fa868827f0)

# File Explorer
![image](https://github.com/user-attachments/assets/8d8bc98f-f49b-4138-8bb3-b99a6cfaf0b2)
# Screen Shot
# Desktop Application
![image](https://github.com/user-attachments/assets/66c5f31f-611a-45f3-97a8-fcddd484db22)

![image](https://github.com/user-attachments/assets/681fd755-5853-4e1a-9e8c-4bc72ed79069)

![image](https://github.com/user-attachments/assets/4a283eb4-8ac5-4e09-9cf1-a763eee6d645)

![image](https://github.com/user-attachments/assets/d2c2ab9f-a2a3-42a0-bcca-90e8be3fe0bb)

![image](https://github.com/user-attachments/assets/8098865a-7dbb-42d8-9e18-a5d021ed6bcc)

## ✨ Overview

Welcome to the Python Calculator project! This simple yet powerful calculator application is built using Python and `tkinter`. It offers basic arithmetic operations, a square root function, and a user-friendly graphical interface.

## 📋 Features

- ➕ **Addition**
- ➖ **Subtraction**
- ✖️ **Multiplication**
- ➗ **Division**
- ✔️ **Square Root Calculation**
- 🔄 **All Clear (AC) Function**

## 🛠️ Installation

### Prerequisites

- **Python 3.x**: Make sure you have Python installed. [Download Python](https://www.python.org/downloads/)

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ARIBFIB/calculator.git
   cd calculator
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application:**
   ```bash
   python calculator.py
   ```

## 🖥️ Using PyInstaller

To create an executable file, you can use `PyInstaller`:

1. **Install PyInstaller:**
   ```bash
   pip install pyinstaller
   ```

2. **Create the executable:**
   ```bash
   cd D:\Python Calculator
   pyinstaller --onefile calculator.py
   ```

3. **Find your executable:**
   The executable will be located in the `dist` directory.

## 📂 Project Structure

```
calculator/
├── calculator.py
├── README.md
├── requirements.txt
└── dist/
    └── calculator.exe
```
# Full Source Code
```
from tkinter import *
import math

# Initialize the main window
root = Tk()
root.title('Calculator App')

# Global variables to store the current input and the last input
answerVariableGlobal = ""
answerLabelForSquareRoot = ""

# StringVar variables to update the labels
answerEntryLabel = StringVar()
answerFinalLabel = StringVar()

# Create the display for the current input
Label(root, font=('futura', 25, 'bold'),
      textvariable=answerEntryLabel,
      justify=LEFT, height=2, width=7).grid(columnspan=4, ipadx=120)

# Create the display for the final answer
Label(root, font=('futura', 25, 'bold'),
      textvariable=answerFinalLabel,
      justify=LEFT, height=2, width=7).grid(columnspan=4, ipadx=120)


def changeAnswerEntryLabel(entry):
    global answerVariableGlobal
    global answerLabelForSquareRoot

    answerVariableGlobal = answerVariableGlobal + str(entry)
    answerLabelForSquareRoot = answerVariableGlobal
    answerEntryLabel.set(answerVariableGlobal)

-----
def clearAnswerEntryLabel():
    global answerVariableGlobal
    global answerLabelForSquareRoot
    answerLabelForSquareRoot = answerVariableGlobal
    answerVariableGlobal = ""
    answerEntryLabel.set(answerVariableGlobal)


def evaluateSquareRoot():
    global answerVariableGlobal
    global answerLabelForSquareRoot
    try:
        sqrtAnswer = math.sqrt(eval(str(answerLabelForSquareRoot)))
        clearAnswerEntryLabel()
        answerFinalLabel.set(sqrtAnswer)
    except (ValueError, SyntaxError, TypeError, ZeroDivisionError):
        try:
            sqrtAnswer = math.sqrt(eval(str(answerVariableGlobal)))
            clearAnswerEntryLabel()
            answerFinalLabel.set(sqrtAnswer)
        except (ValueError, SyntaxError, TypeError, ZeroDivisionError):
            clearAnswerEntryLabel()
            answerFinalLabel.set("Error!")


def evaluateAnswer():
    global answerVariableGlobal
    try:
        evaluatedValueAnswerLabelGlobal = str(eval(answerVariableGlobal))
        clearAnswerEntryLabel()
        answerFinalLabel.set(evaluatedValueAnswerLabelGlobal)
    except (ValueError, SyntaxError, TypeError, ZeroDivisionError):
        clearAnswerEntryLabel()
        answerFinalLabel.set("Error!")


def allClear():
    global answerVariableGlobal
    global answerLabelForSquareRoot
    answerVariableGlobal = ""
    answerLabelForSquareRoot = ""
    answerEntryLabel.set("")
    answerFinalLabel.set("")


def createButton(txt, x, y):
    Button(root, font=('futura', 15, 'bold'),
           padx=16, pady=16, text=str(txt),
           command=lambda: changeAnswerEntryLabel(txt),
           height=2, width=9).grid(row=x, column=y, sticky=E)

-----
buttons = ['AC', '√', '%', '/', '7', '8', '9', '*', '4', '5', '6', '-', '1', '2', '3', '+', '', '0', '.', '=']
buttonsListTraversalCounter = 0

for i in range(3, 8):
    for j in range(0, 4):
        if buttonsListTraversalCounter < len(buttons):
            createButton(buttons[buttonsListTraversalCounter], i, j)
            buttonsListTraversalCounter += 1

# Button for SquareRoot
Button(root, font=('futura', 15, 'bold'),
       padx=16, pady=16, text="√",
       command=lambda: evaluateSquareRoot(),
       height=2, width=9).grid(row=3, column=1, sticky=E)

# Button for AC button - clear the workspace
Button(root, font=('futura', 15, 'bold'),
       padx=16, pady=16, text="AC",
       command=lambda: allClear(),
       height=2, width=9).grid(row=3, column=0, sticky=E)

# Button for value 0 - have 2 columnspace and different dimensions
Button(root, font=('futura', 15, 'bold'),
       padx=16, pady=16, text="0",
       command=lambda: changeAnswerEntryLabel(0),
       height=2, width=21).grid(row=7, column=0,
                                columnspan=2, sticky=E)

# Button for "=" - final calc button
Button(root, font=('futura', 15, 'bold'),
       padx=16, pady=16, text="=",
       command=lambda: evaluateAnswer(),
       height=2, width=9).grid(row=7, column=3, sticky=E)

# Run the main loop
root.mainloop()

```
## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## 🙏 Acknowledgements

- **Python**: [python.org](https://www.python.org/)
- **Tkinter**: [tkinter documentation](https://docs.python.org/3/library/tkinter.html)
- **PyInstaller**: [pyinstaller.org](https://www.pyinstaller.org/)

## 🤝 Contributing

Contributions are welcome! Please fork this repository, create a new branch, and submit a pull request.

1. **Fork the repository**
2. **Create a branch** (`git checkout -b feature-foo`)
3. **Commit your changes** (`git commit -am 'Add foo'`)
4. **Push to the branch** (`git push origin feature-foo`)
5. **Create a new Pull Request**

## 📞 Contact

Feel free to reach out if you have any questions or suggestions!

- **Email**: abdulrehman286ib@gmail.com
- **GitHub**: [ARIBFIB]([https://github.com/your-username](https://github.com/ARIBFIB?tab=repositories))
- **Developer**:  Abdul Rehman Irfan
- **Contact**: 03360592060
- **LinkedIn**: [03360592060](https://www.linkedin.com/in/abdul-rehman-irfan-6454952a3/)


---

For My Other Python Tutorials
Python Tutorial Video 1: - Introduction Print Hello World
link https://youtu.be/7Nnk-_vWkJo

Python Tutorial Video 2: - Syntax 
link https://youtu.be/0ojEwmfW3mE

Python Tutorial Video 3: - Variables
link https://youtu.be/7Nnk-_vWkJo

Python Tutorial Video 4: - Python Comments
link https://youtu.be/7Nnk-_vWkJo


Python Tutorial Video 7: - Python Camel Snake Case Variable
link https://youtu.be/jBtwUzEuisw

Python Tutorial Video 8: - Python Variables   Assign Multiple Values
link https://youtu.be/h7abaCBUwfU

Python Tutorial Video 9: - Output Variables
link https://youtu.be/iYZ0cb_N0ao

Python Tutorial Video 10: - Global Variables
link https://youtu.be/cvy1FvlbFc8

Python Tutorial Video 11: - Python  Variable Exercises
link https://youtu.be/9ewi4vXpzHY

Python Tutorial Video 12: - Python  Python Built in Data Types
Tuple
int
float
string
list
stack
Queue - Not available in this video

link https://youtu.be/qAKf_Wyvjzg

Python Tutorial Video 13: - Python Numbers
link https://youtu.be/4cTYCwp69rQ

Python Tutorial Video 13: - Python Casting
link https://youtu.be/LDtZXEBD8Gc
