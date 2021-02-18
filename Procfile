release:       ./setup.py
web: gunicorn gettingstarted.wsgi
heroku config:set WEB_CONCURRENCY=3
web: gunicorn hello:app
heroku apps:create
heroku addons:create heroku-redis -a sushi
pip install redis
pip install celery
import celery
app = celery.Celery('./app.py')
import os
app.conf.update(BROKER_URL=os.environ['REDIS_URL'],
                CELERY_RESULT_BACKEND=os.environ['REDIS_URL'])