# flask_site
nginx, supervisor, gunicorn
working directory is /var/www/project_flask/
# установите python3-pip и python3-venv:
sudo apt install python3-pip python3-venv
# настроить Python по умолчанию в вашей системе Ubuntu:
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10
# проверьте версию Python и Pip, а также проверьте модуль venv Python:
python --version
pip --version
python -m venv -h
# установить nginx и supervisor:
sudo apt install nginx supervisor
# создаем директорию проекта:
mkdir -p /var/www/project_flask/
# даем права, если нужно:
sudo chown -R cubinez85:cubinez85 /var/www/project_flask/
sudo chmod 755 /var/www/project_flask/
# устанавливаем виртуальное окружение:
cd /var/www/project_flask/
python -m venv venv
source venv/bin/activate
# устанавливаем flask и gunicorn:
pip install flask gunicorn
# создаем app.py (см в дир проекта)
# создаем дир /templates и index.html(см в дир проекта)
mkdir -p templates/
nano templates/index.html
# в дир /var/www/project_flask/ создаем wsgi.py (см в дир проекта):
nano wsgi.py
# Создайте новый файл конфигурации « /etc/supervisor/conf.d/app.conf » (см в дир проекта)
# далее настройка nginx (см в дир проекта):
sudo nano /etc/nginx/sites-available/app.conf
sudo ln -s /etc/nginx/sites-available/app.conf /etc/nginx/sites-enabled/ 
sudo nginx -t
# установить модули Flask-MySQLdb mysql-connector-python
pip install Flask-MySQLdb mysql-connector-python
# установить инструменты сборки pkg-config
sudo apt-get install pkg-config build-essential libmysqlclient-dev
