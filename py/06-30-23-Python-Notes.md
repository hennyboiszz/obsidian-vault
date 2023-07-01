# Notes Related to Python and polars on 06-30-23

## Links
[https://code.visualstudio.com/docs/python/python-tutorial](vscode python tutorial)

## Steps to create python project that imports and uses polars

Steps:
1. Create a directory and cd into it, the open in your editor: 
    ```zsh
    $ mkdir hello_python
    $ cd hello_python
    $ code . // The following steps are going to assume that this opens vscode for us 
    ```
2. Next, we are going to enter the keyboard shortcut to lookup a command this is *CMD* + *Shift* + *P*. In this search bar we are going to lookup *Python: Create Environment* then click **.venv** and select which version of python we are going to use the 3.11 version because it is the version that is recommended to use with **polars**. This will result in a **.venv** to appear in the workspace
3. Create a file with same name as your directory and ending in **.py**
```zsh
$ touch hello_python.py
```