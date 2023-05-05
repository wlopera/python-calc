# python-calc
Python - calculadora

### calc.py
```
from tkinter import *

root = Tk()
frame = Frame(root)
frame.config(width="500", height="500")
frame.pack()

operator = ""
typeOperator=""
result1 = 0
result2 = 0
isTotal = False

# --------------------- Boton numericos-----------------------------


def createButtonNumeric(frame, value, rowv, colv):
    button = Button(frame, text=value, width="4", command=lambda: pressKey(
        str(value)), font=("Comic Sans MS", 12))
    button.grid(row=rowv, column=colv, padx=4, pady=4)
    return button

# --------------------- Boton Click-----------------------------


def createButtonClick(frame, value, rowv, colv, functionv):
    button = Button(frame, text=value, width="4",
                    command=functionv, font=("Comic Sans MS", 12))
    button.grid(row=rowv, column=colv, padx=4, pady=4)
    return button

# --------------------- Operacion suma ----------------------------------
def process(oper):
    global operator, result1, result2, isTotal, typeOperator
    operator = oper  
    typeOperator=oper  
    if result2 != 0 and isTotal == False:
        match oper:
            case "+":
                result1 += result2            
            case "-":
                result1 -= result2            
            case "*":
                result1 *= result2            
            case "/":
                result1 /= result2                    
        result2 = 0
    else:
        isTotal = False
        result2 = 0

    number.set(str(result1))
    accumulated.set(str(result1) + operator)
    print(11111, result1, result2)

# --------------------- Operacion resultado-----------------------------


def equal():
    global result1, result2, isTotal, typeOperator

    accumulated.set(str(result1) + "+" + str(result2) + "=")
    print("operador:" , typeOperator)
    match typeOperator:
        case "+":
            result1 += result2            
        case "-":
            result1 -= result2            
        case "*":
            result1 *= result2            
        case "/":
            result1 /= result2       
            
    number.set(str(result1))
    isTotal = True

# --------------------- Acumulado ------------------------------------------
accumulated = StringVar()

screen = Entry(frame, textvariable=accumulated)
screen.grid(row=1, column=1, padx=2, columnspan=4)
screen.config(fg="black", justify="right", width=38)

# --------------------- Pantalla ------------------------------------------
number = StringVar()

screen = Entry(frame, textvariable=number)
screen.grid(row=2, column=1, padx=2, pady=10, columnspan=4)
screen.config(bg="black", fg="white", justify="right", width=38)

# --------------------- Fila 1 ------------------------------------------
button7 = createButtonNumeric(frame, 7, 3, 1)
button8 = createButtonNumeric(frame, 8, 3, 2)
button9 = createButtonNumeric(frame, 9, 3, 3)
buttonDivide = createButtonClick(frame, "/", 3, 4, lambda:process("/"))


# --------------------- Fila 2 ------------------------------------------
button4 = createButtonNumeric(frame, 4, 4, 1)
button5 = createButtonNumeric(frame, 5, 4, 2)
button6 = createButtonNumeric(frame, 6, 4, 3)
buttonMultiply = createButtonClick(frame, "*", 4, 4, lambda:process("*"))

# --------------------- Fila 3 ------------------------------------------
button1 = createButtonNumeric(frame, 1, 5, 1)
button2 = createButtonNumeric(frame, 2, 5, 2)
button3 = createButtonNumeric(frame, 3, 5, 3)
buttonSub = createButtonClick(frame, "-", 5, 4, lambda:process("-"))

# --------------------- Fila 4 ------------------------------------------
button0 = createButtonNumeric(frame, 0, 6, 1)
buttonDecimal = createButtonNumeric(frame, ".", 6, 2)
buttonEqual = createButtonClick(frame, "=", 6, 3, lambda: equal())
buttonAdd = createButtonClick(frame, "+", 6, 4, lambda:process("+"))


# --------------------- Pulsaciones Teclado -----------------------------
def pressKey(value):
    global operator, result1, result2

    if operator == "" and result2 == 0:
        if operator == "":
            number.set(number.get() + value)
            result1 = int(number.get())
        else:
            number.set(value)
            result1 = int(number.get())
            operator = ""
    else:
        if operator == "":
            number.set(number.get() + value)
            result2 = int(number.get())
        else:
            number.set(value)
            result2 = int(number.get())
            operator = ""

root.mainloop()
```

### Salida:

![Captura](https://user-images.githubusercontent.com/7141537/236568179-19da9cc2-468c-4995-8134-70382d72007f.PNG)


