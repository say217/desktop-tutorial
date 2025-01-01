# Welcome to GitHub Desktop!

This is your README. READMEs are where you can communicate what your project is and how to use it.

Write your name on line 6, save it, and then head back to GitHub Desktop.
    
    ```python
    
def create_file(file_name, content=""):
    with open(file_name, 'w') as file:
        file.write(content)
    print(f"File '{file_name}' created.")

def read_file(file_name):
    if os.path.exists(file_name):
        with open(file_name, 'r') as file:
            content = file.read()
        print(f"Content of '{file_name}':\n{content}")
    else:
        print(f"File '{file_name}' does not exist.")

def delete_file(file_name):
    if os.path.exists(file_name):
        os.remove(file_name)
        print(f"File '{file_name}' deleted.")
    else:
        print(f"File '{file_name}' does not exist.")

def copy_file(source, destination):
    if os.path.exists(source):
        shutil.copy(source, destination)
        print(f"File '{source}' copied to '{destination}'.")
    else:
        print(f"Source file '{source}' does not exist.")

def move_file(source, destination):
    if os.path.exists(source):
        shutil.move(source, destination)
        print(f"File '{source}' moved to '{destination}'.")
    else:
        print(f"Source file '{source}' does not exist.")

# Example usage
create_file('example.txt', 'Hello, world!')
read_file('example.txt')
copy_file('example.txt', 'example_copy.txt')
move_file('example_copy.txt', 'example_moved.txt')
delete_file('example.txt')
delete_file('example_moved.txt')
    ```