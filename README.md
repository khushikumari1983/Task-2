mport random
import string
import tkinter as tk
from tkinter import messagebox

def generate_password():
    user_word = entry_word.get()

    if not user_word:
        messagebox.showerror("Invalid Input", "Please enter a word to include!")
        return


    random_length = 6
    characters = string.ascii_letters + string.digits + string.punctuation

    random_part = ''.join(random.choice(characters) for _ in range(random_length))
    password_list = list(user_word + random_part)
    random.shuffle(password_list)
    password = ''.join(password_list)

    result_label.config(text="Your Password:\n" + password)


root = tk.Tk()
root.title("Password Generator")
root.geometry("400x400")
root.resizable(False, False)
root.configure(bg="#ffe6f0")


def styled_label(text, size=12, fg="#4a148c", bg="#ffe6f0"):
    return tk.Label(root, text=text, font=("Helvetica", size, "bold"), fg=fg, bg=bg)


tk.Label(
    root, text="Secure Password Generator",
    font=("Helvetica", 16, "bold"),
    fg="#880e4f", bg="#ffe6f0"
).pack(pady=10)


styled_label("Enter a word to include:", 12, "#6a1b9a").pack(pady=8)
entry_word = tk.Entry(root, font=("Arial", 12), justify='center', bg="#fff3e0", fg="#4a148c")
entry_word.pack(pady=5)


generate_button = tk.Button(
    root, text="Generate Password", font=("Arial", 12, "bold"),
    bg="#865eb8", fg="white", padx=10, pady=5,
    activebackground="#6a1b9a", activeforeground="white",
    relief="raised", bd=3,
    command=generate_password
)
generate_button.pack(pady=20)


result_label = tk.Label(
    root, text="", font=("Arial", 12, "bold"),
    fg="#1a237e", bg="#ffe6f0", wraplength=380, justify='center'
)
result_label.pack(pady=10)



root.mainloop()
