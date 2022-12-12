
# Python Security model
Python does not implement privilege separation (not “inside” Python) to reduce the attack surface of Python. Once an attacker is able the execute arbitrary Python code, the attacker gets a full access to the system. Privilege separation can be implemented “outside” Python by putting Python inside a sandbox.
Example with bpo-36506 (closed as not a bug): getattr() executes arbitrary code by design, it is not a vulnerability.

## Use the most recent major stable version of Python
Python 3 was released date back in 2008 and starting from Jan 1, 2020, the Python Foundation announced that Python 2 will stop receiving security updates or support from the community. 
If you are still using old versions of Python below Python 3, then you should start considering how to migrate your codebase to Python 3. Start using Python 3 for your new projects or you leave yourself open to security vulnerabilities. Make sure to use stable versions like 3.10, 3.9 to avoid problems with incompatible modules and packages.
To check for your Python version, you can run:
python –version



## Use a Virtual Environment 
 When building any Python projects, it’s always advisable to use a virtual environment as it helps to prevent conflict in Python modules, as well as have the same modules on both local and production environments. 
 Using a virtual environment prevents having malicious Python dependencies in your projects and shipping the same to production by using `pip freeze` to generate requirements.txt. If you have malicious packages in your Python environments, using a virtual environment will prevent having the same packages in your Python codebase since it is isolated.
 To create a virtual environment, you can either use Virtualenv or Pipenv which help create isolated virtual environments. Pipenv helps to manage, have a predictable and up-to-date environment. 
With Pipenv, you can manage your installations, virtual environments, look through your dependency tree, and scan your dependencies for known vulnerabilities.
 You can set up Virtualenv: 
pip install virtualenv
virtualenv -p /path/to/python <env_name>

## Set Debug  = false
For some Python frameworks, such as Django, debug is set to true by default in new projects. This can be helpful in development to show errors in our code but is not so useful when we deploy the project to live on a server available to the public. Displaying errors in our code publicly could show a weakness in our security that will be exploited.
So, when deployed live, always set the following:
Debug = false
You can find the Debug option in settings.py if you are using a framework like this.
Moreover, the Python code can be also developed in debug mode – documentation. This can influence the usage of “assert” – it is not recommended to use it to verify sensitive and crucial parts of code, as with the optimized mode (non-debug) all the asserts are removed from the code. 
