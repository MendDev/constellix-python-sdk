# Python SDK for Constellix API v4


# Setup
In order to get this SDK works for python, you need to get installed:
PIP, setuptools and requests

To install dnsmesdk package locally, go to package root directory and execute the next command:

python2:
```
python setup.py install --old-and-unmanageable
```
python3:
```
python3 setup.py install --old-and-unmanageable
```

# Usage Examples

Setting apikey and secretkey over environment variables

```
export CONSTELLIX_API_KEY=<api_key>
export CONSTELLIX_SECRET_KEY=<secret_key>
```

```python
from constellixsdk import ConstellixApi
from sonarsdk import SonarApi

constellix = ConstellixApi()
sonar = SonarApi()
```

Passing apikey and secretkey to ConstellixApi and SonarApi objects

```python
from constellixsdk import ConstellixApi
from sonarsdk import SonarApi

constellix = ConstellixApi("api_key", "secret_key")
sonar = SonarApi("api_key", "secret_key")
```

Please check examples folder for sample usages


# Mend

Add to internal repository

```
gcloud artifacts print-settings python \
    --project=mend-dev \
    --repository=python-platform \
    --location=us
```

Follow instructions above

```
python -m venv venv
pip install --upgrade pip
python -m pip install --upgrade build
python -m build
python -m pip install --upgrade twine
pip install keyring
pip install keyrings.google-artifactregistry-auth
keyring --list-backends
twine upload --repository-url https://us-python.pkg.dev/mend-dev/python-platform/ dist/*
```

To use in another project

# Update the environment so that it can access the Mend API SDK

```
pip install keyrings.google-artifactregistry-auth
```

```
# not needed just confirms the keyring is installed correctly.
keyring --list-backends
```
 
# Install the Mend API SDK - pulls the latest version automatically.

```
RUN pip install --index-url https://us-python.pkg.dev/mend-dev/python-platform/simple/ constellixsdk
```

