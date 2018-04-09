Nginx image for laravel 5
=========================

Nginx container for Laravel 5 applications. Laravel is not installed in the Image.

Document Root
-------------

The required document root for laravel is set to `<your laravel
project>/public`. This is de recommended setup for laravel production.

Environment variables
---------------------

### DNS_RESOLVER

By setting `DNS_RESOLVER` you can make sure that nginx will run without the
fastcgi already available. Nginx will resolve the name of the application
container via DNS. When you set `DNS_RESOLVER` to 'auto' the value set in
`/etc/resolv.conf` inside the container will be used by nginx for resolving
(This will default to docker interal dns resolving). If you want to use an
external resolver you can also set a specific ipv4 address.

Overriding or adding extra configuration for nginx
--------------------------------------------------

When there is a need to add additional configuration to your nginx config you
can add a config file in the `/etc/nginx/include/overrides.conf` location. That
file is included in the default server configuration. You can for example add
additional configuration for a maintenance page. Or you could set
`client_max_body_size`, ...

~~~ sh
$ docker run -v /path/to/overrides.conf:/etc/nginx/include/overrides.conf dockerwest/nginx-laravel:<version>
~~~

Versions
--------

The following versions are available:
- stable: last stable version of nginx
- mainline: last mainline version of nginx

License
-------

MIT License (MIT). See [License File](LICENSE.md) for more information.
