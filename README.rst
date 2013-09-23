photos_project
==============================

Simple photo sharing site using Django


LICENSE: MIT

Deployment
------------

* heroku create
* heroku addons:add heroku-postgresql:dev
* heroku addons:add pgbackups
* heroku addons:add sendgrid:starter
* heroku addons:add memcachier:dev
* heroku pg:promote HEROKU_POSTGRESQL_COLOR
* heroku config:add DJANGO_CONFIGURATION=Production
* heroku config:add DJANGO_SECRET_KEY=RANDOM_SECRET_KEY
* heroku config:add DJANGO_AWS_ACCESS_KEY_ID=YOUR_ID
* heroku config:add DJANGO_AWS_SECRET_ACCESS_KEY=YOUR_KEY
* heroku config:add DJANGO_AWS_STORAGE_BUCKET_NAME=BUCKET
* git push heroku master
* heroku run python photos_project/manage.py syncdb --noinput --settings=config.settings
* heroku run python photos_project/manage.py migrate --settings=config.settings
* heroku run python photos_project/manage.py collectstatic --settings=config.settings

Run this script: (TODO - automate this)

.. code-block:: python

    from django.contrib.sites.models import Site
    site = Site.objects.get()
    site.domain = "photos.wengole.co.uk"
    site.name = "photos_project"
    site.save()