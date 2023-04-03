# Python Worker Extension Timer

This is an example repo to demonstrate how to build a Python Worker extension in Azure Functions.

## Features

This project framework provides the following features:

* Calculate the time elapsed in every HTTP triggers
* Overwrite the HTTP response from your function to display the elapsed time.

## Getting Started

### Prerequisites

* [Python 3.7 or above](https://www.python.org/downloads). To check the full list of supported Python versions in Azure Functions, see the [Python developer guide](https://docs.microsoft.com/azure/azure-functions/functions-reference-python#python-version).
* The [Azure Functions Core Tools](functions-run-local.md#v2), version 4.0.5095 or later to support v2 [Python programming model](https://learn.microsoft.com/azure/azure-functions/functions-reference-python).
* [Visual Studio Code](https://code.visualstudio.com/) installed on one of the [supported platforms](https://code.visualstudio.com/docs/supporting/requirements#_platforms).

### Demo

1. Open a Windows PowerShell or any Linux shell as you prefer.
2. Change your directory into the `_example/`
3. Create a Python virtual environment by `py -m venv .venv` in Windows, or `python3 -m venv .venv` in Linux.
4. Activate the Python virutal environment with `.venv\Scripts\Activate.ps1` in Windows PowerShell or `source .venv/bin/activate` in Linux shell.
5. Install the packages for your function app project `pip install -r requirements.txt`
6. Start the function host with `func host start --verbose`

You should now be able to access `http://localhost:7071/api/HttpTrigger`.
Each http response reports the time elapsed of processing the request.

### Installation

To install this Python worker extension package in an existing function app:

* Add a VCS URL in your requirements.txt `git+https://github.com/Azure-Samples/python-worker-extension-timer`
* Run `pip install -r requirements.txt`
* In your FunctionApp/HttpTrigger, add the following lines to enable this feature:

```python
from python_worker_extension_timer import TimerExtension
TimerExtension.configure(append_to_http_response=True)
```

In the v1 programming model, add the lines in the *\_\_init.py\_\_* file. In the v2 programming model, add the lines in the *function_app.py* file.

## Resources

* [Develop Python worker extensions for Azure Functions](https://learn.microsoft.com/azure/azure-functions/develop-python-worker-extensions)
