This is Sample-App
==================


Overview
--------

This is a demo application using Kohana 3.3+ with REST, MongoDB, Backbone.js and Marionette.js.
My goal is to learn how to use Marionette.js and MongoDB with a REST backend based on Kohana 3.3.

You can see a demo here:
http://sampleapp.li/


Requirements
------------

This application needs the following dependencies:

  *   PHP 5.3, and PHP modules: cURL, iconv, mcrypt, mongodb
  *   A HTTP server (like Apache or Lighttpd)
  *   A local mail server which is allowed to send emails to Internet
  *   A MongoDB server


Quick installation notes
------------------------

Clone the repository, and init its dependencies:

```bash
$ git clone --recursive https://github.com/tchemineau/sample-app.git
```

On the system:

```bash
$ mkdir ./data/cache ./data/log
$ chown www-data:www-data ./data/cache ./data/log
```

Adjust your settings into the following files:

  *   `application/config/app.local.php`
  *   `application/config/mongodb.local.php`

This is a example of Lighttpd configuration:

```
$HTTP["host"] =~ "^example\.com$" {
    server.document-root = "/var/www/example.com/www/"
    server.name = "example.com"
    accesslog.filename = "/var/log/lighttpd/example.com.access.log"
    alias.url = (
        "/sample-app/assets/" => "/var/www/example.com/www/sample-app/data/cache/assets/",
        "/sample-app/" => "/var/www/example.com/www/sample-app/public/"
    )
    url.rewrite-if-not-file  = (
        "^/sample-app/(.+)" => "/sample-app/index.php/$1"
    )
    setenv.add-environment = (
        "KOHANA_ENV" => "production"
    )
}
```


Tests
-----

Use PHPUnit to tests the project (tests are yet not written):

```bash
$ export KOHANA_ENV="testing"
$ phpunit --bootstrap=application/bootstrap.tests.php --group=sampleapp tests.php
```

All tests are stored into the `modules/sampleapp/tests/` directory.


Thanks
------

This project uses the following components:

  *   [Kohana](http://kohanaframework.org/)
  *   [Kohana-Assets](https://github.com/tchemineau/kohana-assets)
  *   [Kohana-Email](https://github.com/tchemineau/kohana-email)
  *   [Kohana-Mongodb](https://github.com/tchemineau/kohana-mongodb)
  *   [Kohana-Password](https://github.com/tchemineau/kohana-password)
  *   [Kohana-Restful](https://github.com/tchemineau/kohana-restful)
  *   [Kohana-Twig](https://github.com/tchemineau/kohana-twig)
  *   [RequireJS](http://requirejs.org/)
  *   [Underscore.js](http://underscorejs.org/)
  *   [jQuery](http://jquery.com/)
  *   [Backbone.js](http://backbonejs.org/)
  *   [backbone.session.js](https://github.com/makesites/backbone-session)
  *   [Marionette.js](http://marionettejs.com/)
  *   [marionette.formview.js](https://github.com/onehealth/marionette.formview)
  *   [Bootstrap](http://twitter.github.io/bootstrap/)


