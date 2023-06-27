# Sections

## Knowledge

### How does pyenv work?
pyenv allows you to select what specific python version to use for each application
it does this with with **shim executables** that are in injected into your **PATH** to pass on
the commands that correspond to the version of python that you want to use 

### Understanding your PATH

When you run a command like **python** or **pip** your OS is going to begin to search
through a list of directories to find a executable file with that name. This list of directories
lives in an **environment variable** called **PATH** with each directory in the list separated by a
colon.

Ex. of PATH variable:
```
/usr/local/bin:/usr/bin:/bin
``` 

When your OS searches the variable from left to right so:
	`/usr/local/bin` then `/usr/bin` then `/bin`

This means that directories in the **/usr/local/bin**, takes precedence over directories of the same name in both **/usr/bin** and **/bin**

### What are shims?

pyenv works by inserting a directory of **shims** at the front of your **PATH** variable.

```
$(pyenv root)/shims:/usr/local/bin:/usr/bin:/bin
```

pyenv does this through a process called **rehashing** where it maintains **shims** in that directory to match every python command across every version. 

#### shims definition:
+ shims are a lightweight executable that simply pass along your command along to pyenv.

#### example of pyenv's role 
		   
For this is example **with pyenv installed**. say we run the command:
```zsh
$ pip
```

Our operating system will:

1. Begin to search your **PATH** variable for an executable file called **pip**.
2. It will locate the **pyenv shim** named **pip** in the _beginning_ of your **PATH** 
3. It will then run the **shim** named **pip** that will then **pass your command to along to pyenv**


## Understanding Python version selection with pyenv

#### A shim file must determine a python version

	After you run a command in your shell your operating system will run into the shim file corresponding with the command and executes it. 

	When your operating system executes a shim that shim file has to determine which version of python use passing it along to pyenv.

	The shim detremines which version from 4 different sources and searches each one of these sources in order as follows.

#### PYENV_VERSION
- The `PYENV_VERSION` _environment variable_ **(optional)**: Is a local variable to set and control the environment of your **current shell session**, this variable is the first to be searched and therefore has the **highest precedence** in determining which version to pass along. This variable also controls the least amount of scope in comparison to the other sources. 
- `PYENV_VERSION` can be set using the pyenv **shell** command as follows:
```zsh 
$ pyenv shell  
```

#### .python-version 
- The `.python-version` _file_ **(optional)**: This file will be used in order to set a directories python version allowing us to specify for each application which python version to use. 
- The `.python-version` _file_ can be set using the pyenv **local** command as follows:
```zsh
$ pyenv local 
```

#### Parent .python-version
- When the current directory that a shell command is ran in does not have a `.python-version` file then then your OS will then begin to look for one in subsequent parent directories until one is located an a version is determined.

#### Global $(pyenv root)/version 
This can be altered using the pyenv **global** command as follows:
```zsh
$ pyenv global
```

## Suggested build environment for sane development

### For Mac 
	we first need the XCode Command Line Tools 
```zsh
$ xcode-select --install 
```
and install **home brew**

next run 

```zsh
$ brew install openssl readline sqlite3 xz zlib tcl-tk
```


