How do I undo this?

1. Revert NGINX config by removing this from `/etc/nginx/sites-available/www.baltimorenode.org`:
    ```
    location = / {
        proxy_pass https://baltimorenode.github.io/temporary-homepage/;
    }
    ```
1. Remove WordPress hack:
    ```
    root@localhost:/home/nodepress/www.baltimorenode.org/www# diff canonical.php__before-jnm-hack-20200325 wp-includes/canonical.php 
    440c440,441
    < 	$redirect['path'] = preg_replace( '|/' . preg_quote( $wp_rewrite->index, '|' ) . '/*?$|', '/', $redirect['path'] );
    ---
    > 	// 20200325 jnm hacking wordpress core... what could go wrong? uncomment following line to undo
    > 	//$redirect['path'] = preg_replace( '|/' . preg_quote( $wp_rewrite->index, '|' ) . '/*?$|', '/', $redirect['path'] );
    ```
