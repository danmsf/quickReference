
# Google's Colab Snippets

## Reference Google Drive


```python
# Source:
# https://medium.com/@burakteke/tutorial-on-using-google-colab-for-kaggle-competition-620393c22821

# Install a Drive FUSE wrapper.
# https://github.com/astrada/google-drive-ocamlfuse
!apt-get install -y -qq software-properties-common python-software-properties module-init-tools
!add-apt-repository -y ppa:alessandro-strada/ppa 2>&1 > /dev/null
!apt-get update -qq 2>&1 > /dev/null
!apt-get -y install -qq google-drive-ocamlfuse fuse

# Authenticate GDrive
from google.colab import auth
auth.authenticate_user()

# Authenticate FUSE library
# Generate creds for the Drive FUSE library.
from oauth2client.client import GoogleCredentials
creds = GoogleCredentials.get_application_default()
import getpass
!google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret} < /dev/null 2>&1 | grep URL
vcode = getpass.getpass()
!echo {vcode} | google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret}

# Make a folder (alias) and port it to GDrive
!mkdir -p my_drive
!google-drive-ocamlfuse my_drive

# Done
!ls my_drive/
# or run code:
# !python3 my_drive/python_script.py
```
