#
# Dockerfile for building Myapp images
# 
# https://github.com/yana111/lnmp-study.git
#

FROM lnmp_nginx
MAINTAINER yana <cylichan@hotmail.com>

#配置nginx

ENV \
	HTTP_PHP_CONFIG \\\n\\\t#php\\\n\\\tlocation ~ \\\\.php$ {\\\n\\\t\\\troot    /usr/local/nginx/html/laravel/public;\\\n\\\t\\\tfastcgi_pass   php7:9000;\\\n\\\t\\\tfastcgi_index    index.php;\\\n\\\t\\\tfastcgi_param  SCRIPT_FILENAME    /usr/local/nginx/html/laravel/public\$fastcgi_script_name;\\\n\\\t\\\tinclude    fastcgi_params;\\\n\\\t}\\\n\\\n\\\t

RUN \
	sed -i -e "s@# deny access to .htaccess files, if Apache@${HTTP_PHP_CONFIG}# deny access to .htaccess files, if Apache@" /usr/local/nginx/conf/nginx.conf
RUN \
	sed 74,81d /usr/local/nginx/conf/nginx.conf

EXPOSE 80 443


#启动nginx
ENTRYPOINT ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
