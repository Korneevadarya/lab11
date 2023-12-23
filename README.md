# Лабораторная работа 11
## Итоговый проект
### Интерактивный календарь
### инструкция и описание
Запускаем код: python lab.py
Выбираем год и месяц чтобы посмотреть как выглядел сам месяц в этот год.
### Программа
```python
import calendar
import tkinter as tk
from tkinter import ttk


def show_calendar():
    year = int(year_entry.get())
    month = int(month_combobox.get())

    cal_content = calendar.month(year, month)

    result_text.configure(state='normal')
    result_text.delete('1.0', tk.END)
    result_text.insert(tk.END, cal_content)
    result_text.configure(state='disabled')


root = tk.Tk()
root.title("Интерактивный календарь")

# Создаем элементы интерфейса
year_label = ttk.Label(root, text="Год:")
year_entry = ttk.Entry(root, width=10)

month_label = ttk.Label(root, text="Месяц:")
month_combobox = ttk.Combobox(root, values=list(range(1, 13)), width=5)

show_button = ttk.Button(root, text="Показать", command=show_calendar)

result_text = tk.Text(root, height=10, width=25)
result_text.configure(state='disabled')

# Размещаем элементы на экране
year_label.grid(row=0, column=0, padx=5, pady=5, sticky='e')
year_entry.grid(row=0, column=1, padx=5, pady=5)

month_label.grid(row=0, column=2, padx=5, pady=5, sticky='e')
month_combobox.grid(row=0, column=3, padx=5, pady=5)

show_button.grid(row=1, column=0, columnspan=4, padx=5, pady=5)

result_text.grid(row=2, column=0, columnspan=4, padx=5, pady=5)

root.mainloop()
```

