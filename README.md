mport webbrowser
import tkinter as tk
import threading
import time

def show_rickroll_popup():
    popup = tk.Tk()
    popup.title("Rickrolled!")
    popup.configure(bg="black")
    popup.geometry("400x120")
    popup.resizable(False, False)

    label = tk.Label(
        popup,
        text="You just got Rickrolled!",
        font=("Arial", 18, "bold"),
        fg="white",
        bg="black",
        justify="center"
    )
    label.pack(expand=True, padx=20, pady=20)

    def close_after_delay():
        time.sleep(5)
        popup.destroy()

    threading.Thread(target=close_after_delay, daemon=True).start()
    popup.mainloop()

def show_virus_warning():
    popup = tk.Tk()
    popup.title("WARNING!")
    popup.configure(bg="black")
    popup.geometry("500x180")
    popup.resizable(False, False)

    label = tk.Label(
        popup,
        text="WARNING: do not close the pop up message.\nIt will cause harm to the computer by sending a virus\nand leading to stealing of private information.",
        font=("Arial", 14, "bold"),
        fg="red",
        bg="black",
        justify="center"
    )
    label.pack(expand=True, padx=20, pady=20)

    def close_and_rickroll():
        popup.destroy()
        webbrowser.open("https://www.youtube.com/watch?v=dQw4w9WgXcQ")
        show_rickroll_popup()

    # Close after 10 seconds
    def close_after_delay():
        time.sleep(10)
        close_and_rickroll()

    threading.Thread(target=close_after_delay, daemon=True).start()
    popup.protocol("WM_DELETE_WINDOW", close_and_rickroll)
    popup.mainloop()

show_virus_warning()
