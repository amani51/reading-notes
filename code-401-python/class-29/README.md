# Class-29
## API Deployment
#### Managing Django Settings:
- **Different environments** 
    - Issue: you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings . You need an approach that allows you to keep all these Django setting configurations.
    - solution: extend all environment-specific settings in the `settings_local.py` file, which is ignored by VCS
    ```python
    ALLOWED_HOSTS = ['localhost']
    DEBUG = True
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'local_db',
            'HOST': '127.0.0.1',
            'PORT': '5432',
        }
    }
    ```

- **Sensitive data** 
    - Issue: You have `SECRET_KEY` in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.
    - solution: use environment variables in Django.
    ```python
    import os

    SECRET_KEY = os.environ['SECRET_KEY']
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': os.environ['DATABASE_NAME'],
            'HOST': os.environ['DATABASE_HOST'],
            'PORT': int(os.environ['DATABASE_PORT']),
        }
    }
    ```
- **Sharing settings between team members**: You need a general approach to eliminate human error when working with the settings.

- **Django settings are a Python code**: This is a curse and a blessing at the same time. It gives you a lot of flexibility, but can also be a problem – instead of key-value pairs, settings.py can have a very tricky logic.
- **12 Factors**
    - 12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud. It was created by `Heroku`

#### What Is SSH
- SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.

- SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

- The example below shows a typical SSH prompt. Any Linux or macOS user can SSH into their remote server directly from the terminal window. Windows users can take advantage of SSH clients like Putty. You can execute shell commands in the same manner as you would if you were physically operating the remote computer.