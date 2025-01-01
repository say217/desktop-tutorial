# Welcome to GitHub Desktop!

This is your README. READMEs are where you can communicate what your project is and how to use it.

Write your name on line 6, save it, and then head back to GitHub Desktop.
    
    ```python
    import tkinter as tk
    from tkinter import filedialog, messagebox
    import os
    import shutil

    class FileManager:
    def __init__(self, root):
        self.root = root
        self.root.title("Basic File Manager")
        self.root.geometry("600x400")
        
        # Directory Display Area
        self.dir_label = tk.Label(self.root, text="No Directory", width=60)
        self.dir_label.pack(pady=10)
        
        # Buttons
        self.open_btn = tk.Button(self.root, text="Open Directory", command=self.open_directory)
        self.open_btn.pack(pady=5)
        
        self.create_btn = tk.Button(self.root, text="Create Folder", command=self.create_folder)
        self.create_btn.pack(pady=5)
        
        self.delete_btn = tk.Button(self.root, text="Delete File", command=self.delete_file)
        self.delete_btn.pack(pady=5)
        
        self.rename_btn = tk.Button(self.root, text="Rename File", command=self.rename_file)
        self.rename_btn.pack(pady=5)
        
        self.refresh_btn = tk.Button(self.root, text="Refresh", command=self.refresh)
        self.refresh_btn.pack(pady=5)
        
    def open_directory(self):
        self.directory = filedialog.askdirectory()
        if self.directory:
            self.dir_label.config(text=f"Current Directory: {self.directory}")
        
    def create_folder(self):
        if hasattr(self, 'directory'):
            folder_name = filedialog.asksaveasfilename(defaultextension='', title="Enter folder name")
            if folder_name:
                try:
                    os.mkdir(folder_name)
                    messagebox.showinfo("Success", f"Folder '{folder_name}' created successfully!")
                except Exception as e:
                    messagebox.showerror("Error", f"Error: {e}")
        else:
            messagebox.showwarning("Warning", "Please select a directory first!")
    
    def delete_file(self):
        if hasattr(self, 'directory'):
            file_path = filedialog.askopenfilename(title="Select a file to delete")
            if file_path:
                try:
                    os.remove(file_path)
                    messagebox.showinfo("Success", f"File '{file_path}' deleted successfully!")
                except Exception as e:
                    messagebox.showerror("Error", f"Error: {e}")
        else:
            messagebox.showwarning("Warning", "Please select a directory first!")

    def rename_file(self):
        if hasattr(self, 'directory'):
            file_path = filedialog.askopenfilename(title="Select a file to rename")
            if file_path:
                new_name = filedialog.asksaveasfilename(initialfile=file_path, title="Enter new file name")
                if new_name:
                    try:
                        os.rename(file_path, new_name)
                        messagebox.showinfo("Success", f"File renamed to '{new_name}'")
                    except Exception as e:
                        messagebox.showerror("Error", f"Error: {e}")
        else:
            messagebox.showwarning("Warning", "Please select a directory first!")

    def refresh(self):
        if hasattr(self, 'directory'):
            self.dir_label.config(text=f"Current Directory: {self.directory}")


    if __name__ == "__main__":
    root = tk.Tk()
    app = FileManager(root)
    root.mainloop()


    ```
