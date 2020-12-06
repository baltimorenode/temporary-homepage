How do I undo this?

1. Revert NGINX config by removing this from `/etc/nginx/sites-available/www.baltimorenode.org`:
    ```
    location = / {
        proxy_pass https://baltimorenode.github.io/temporary-homepage/;
    }
    ```
1. (Optionally) Remove WordPress `home` location:

    https://baltimorenode.org/home is provided by the https://redirection.me/ WordPress plugin, but it's not actually a redirect.
    It's simply configured to pass-through the location `/`, and because it does this at the WordPress level,
    it bypasses the NGINX `proxy_pass` described above.
