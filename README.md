# calculaterpython
Calculator in python
import tkinter as tk


def button_click(symbol):
    current = display_var.get()
    if current == "Error":
        display_var.set("")

    if symbol == "=":
        try:
            result = eval(current)
            display_var.set(result)
        except:
            display_var.set("Error")
    elif symbol == "C":
        display_var.set("")
    else:
        display_var.set(current + symbol)


root = tk.Tk()
root.title("Calculator")


display_var = tk.StringVar()
display_var.set("")


display = tk.Entry(root, textvariable=display_var, font=('Arial', 20), bd=10, insertwidth=4, width=15, justify='right')
display.grid(row=0, column=0, columnspan=4)


buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('=', 4, 2), ('+', 4, 3),
    ('C', 5, 0)
]


for (symbol, row, column) in buttons:
    btn = tk.Button(root, text=symbol, font=('Arial', 20), padx=20, pady=20, command=lambda sym=symbol: button_click(sym))
    btn.grid(row=row, column=column, sticky='nsew')


for i in range(6):
    root.grid_rowconfigure(i, weight=1)
for i in range(4):
    root.grid_columnconfigure(i, weight=1)


root.mainloop()
