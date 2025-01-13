- Custom virtual environment and jupyter client is necessary to isolate projects from rest of the system.
	- Project uses its own kernel and environment where it can install and use only the packages it needs.
- Requirement
	- Python should be installed in the computer.
	- Using `pip` or `package manager` install `jupyter` and `jupyter-notebook`
- ### Creating virtual environment
	- Virtual environment is created using the `venv` module
	- In the terminal, type 
	  ```bash
	  python -m venv /path/to/new/virtual/environment
	  ```
	- This will create a virtual environment in that directory.
	- In this case, the name of the virtual environment will be `environment`
- ### Creating jupyter kernel
	- First, initiate the specific virtual environment by sourcing to it.
	- In the terminal, type
	  ```bash
	  source ${VIRTUAL_ENVIRONMENT_NAME}/bin/activate
	  ```
	- It will source to that virtual environment.
	- The `activate` code may vary depending on the shell or operating system. Such as, For windows `activate.bat`, For fish shell `activate.fish` etc.
	- Using `pip` install `ipykernel` package.
	- ```bash
	  pip install --user ipykernel
	  ```
	- Next, add the virtual environment to`jupyter`.
	- ```bash
	  python -m ipykernel install --user --name=${KERNEL_NAME}
	  ```
- ### Checking and removing jupyter kernel
	- To check the list of jupyter kernels
	  ```bash
	  jupyter kernelspec list
	  ```
	- To remove jupyter kernel
	  ```bash
	  jupyter kernelspec uninstall ${KERNEL_NAME}
	  ```
	-