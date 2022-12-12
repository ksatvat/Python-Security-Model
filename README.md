
# Python Security model
Python does not implement privilege separation (not “inside” Python) to reduce the attack surface of Python. Once an attacker is able the execute arbitrary Python code, the attacker gets a full access to the system. Privilege separation can be implemented “outside” Python by putting Python inside a sandbox.
Example with bpo-36506 (closed as not a bug): getattr() executes arbitrary code by design, it is not a vulnerability.

## Use the most recent major stable version of Python
Python 3 was released date back in 2008 and starting from Jan 1, 2020, the Python Foundation announced that Python 2 will stop receiving security updates or support from the community. 
If you are still using old versions of Python below Python 3, then you should start considering how to migrate your codebase to Python 3. Start using Python 3 for your new projects or you leave yourself open to security vulnerabilities. Make sure to use stable versions like 3.10, 3.9 to avoid problems with incompatible modules and packages.
To check for your Python version, you can run:
python –version
