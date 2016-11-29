NGINX routing
traffic is assinged a tag and then redirected to the apporpriate location
https://www.digitalocean.com/community/tutorials/how-to-target-your-users-with-nginx-analytics-and-a-b-testingt
```
split_clients "variable_to_evaluate" $new_variable {
        percent_group%        value_to_store;
        percent_group%        value_to_store;
    }

}
```
Example
```
split_clients "${remote_addr}" $designtest {
    10%         ".first";
    10%         ".second";
    *           "";
}
```
Server Example
```
http {

    . . .

    split_clients "${remote_addr}" $designtest {
        10%     ".first";
        10%     ".second";
        *       "";
    }

    server {
        listen 80;
        server_name localhost;
        root /usr/share/nginx/html;

        index index${designtest}.html;

        location / {
            try_files $uri $uri/ =404;
        }
    }
}
```
It's also important to remember that the ${remote_addr} check is just a useful example. You can hash based on the value of any of Nginx's variables that works in strings. You can find a list of those included with the Core module here, although other variables are available through other modules. Check the documentation for more information.
http://nginx.org/en/docs/http/ngx_http_core_module.html#variables
