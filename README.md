# Лабораторная работа 11
## Итоговый проект
### Интерактивный календарь
### инструкция и описание
Запускаем код: python lab.py

Выбираем год и месяц и день.

Пишем сообщение или напоминание которое надо сохранить.
Нажимаем `сохранить`, теперь оно храниться в словаре, но при перезапуски программы сообщения не сохраняються.

После чего можно написать ещё несколько сообщение на другие даты и при вводе необходимой даты и нажимания на кнопку `получить` выскакивает окошко со сохранёным сообщением.
### Программа
```python
import tkinter as tk
from tkinter import messagebox

class calendarapp:
    def __init__(self, root):
        self.root = root
        self.root.title("calendar app")

        # создание элементов интерфейса
        self.year_label = tk.Label(root, text="год:")
        self.year_entry = tk.Entry(root)
        self.month_label = tk.Label(root, text="месяц:")
        self.month_entry = tk.Entry(root)
        self.day_label = tk.Label(root, text="день:")
        self.day_entry = tk.Entry(root)
        self.message_label = tk.Label(root, text="сообщение:")
        self.message_entry = tk.Entry(root)
        self.save_button = tk.Button(root, text="сохранить", command=self.save_message)
        self.get_button = tk.Button(root, text="получить", command=self.get_message)

        # размещение элементов на сетке
        self.year_label.grid(row=0, column=0, sticky="e")
        self.year_entry.grid(row=0, column=1)
        self.month_label.grid(row=1, column=0, sticky="e")
        self.month_entry.grid(row=1, column=1)
        self.day_label.grid(row=2, column=0, sticky="e")
        self.day_entry.grid(row=2, column=1)
        self.message_label.grid(row=3, column=0, sticky="e")
        self.message_entry.grid(row=3, column=1)
        self.save_button.grid(row=4, column=0)
        self.get_button.grid(row=4, column=1)

    def save_message(self):
        year = self.year_entry.get()
        month = self.month_entry.get()
        day = self.day_entry.get()
        message = self.message_entry.get()

        if year and month and day and message:
            # сохранение сообщения в указанной дате
            date_key = f"{year},{month},{day}"
            if date_key not in self.calendar:
                self.calendar[date_key] = {}
            self.calendar[date_key] = message
            messagebox.showinfo("сообщение сохранено", "сообщение сохранено успешно.")
        else:
            messagebox.showerror("ошибка", "пожалуйста, заполните все поля.")

    def get_message(self):
        year = self.year_entry.get()
        month = self.month_entry.get()
        day = self.day_entry.get()

        if year and month and day:
            # проверка наличия сообщения в указанной дате
            date_key = f"{year},{month},{day}"
            if date_key in self.calendar:
                message = self.calendar[date_key]
                messagebox.showinfo("сообщение", message)
            else:
                messagebox.showwarning("сообщение не найдено", "сообщение не найдено для указанной даты.")
        else:
            messagebox.showerror("ошибка", "пожалуйста, заполните все поля.")

    def run(self):
        self.calendar = {}
        self.root.mainloop()

# создание и запуск приложения
root = tk.Tk()
app = calendarapp(root)
app.run()
```

