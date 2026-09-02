# Python Commands

Here are some sets of Python commands that can assist you in your day-to-day activities.

- Download Packages with Dependencies
```bash
pip wheel -r requirements.txt -w [Download Path]
```

- Install Packages from requirements.txt file with Dependencies
```bash
pip install -r requirements.txt --no-index --find-links [Packages Path]
```

- Install a Package
```bash
pip install --no-index [Package Path]
```

- Install a Package with Dependencies
```bash
pip install [Package Name] --no-index --find-links [Package Path]
```

- Download Python
```bash
wget https://www.python.org/ftp/python/3.12.6/Python-3.12.6.tgz
```

- Compile Python in Offline Mode
```bash
./configure --prefix=/data/requirement/Python-3.12.6-compiled --with-openssl=/data/requirement/openssl-1.1.1 --enable-shared && make && make install
```

- Create Python Environment
```bash
[Python Path] -m venv [Environment Name Like .uat or .prod]
```

- Fix libpython Error, Place in the `.bashrc` file
```bash
export LD_LIBRARY_PATH=/data/requirement/openssl/lib:/data/requirement/Python-3.11.4-compiled/lib
```

- Fake a Migration
```bash
python manage.py migrate [Migrate Group] [Migrate Name] --fake
```

### Packages Commands

Here are some sets of Python packages commands that can assist you in your day-to-day activities.

- Start Celery
```bash
celery -A [App Name] worker -B -Q celery -E -l `info --logfile=logs/celery.log --detach
```

- Kill Celery
```bash
ps -aux | grep -i celery | grep -v grep | awk '{print $2}' | xargs kill -15
```

- Start Uwsgi
```bash
uwsgi --ini uwsgi-deploy.ini
```

- Reload Uwsgi
```bash
uwsgi --reload uwsgi-master.pid
```
