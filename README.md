# 环境

1.PHP 5.6 + (推荐 PHP 7.1.1)
2.MYSQL 5.5 + 
3.以及安装和配置过程中涉及到的种种东西。

# 安装重点注意

编辑 /usr/local/nginx/conf/vhost/你的域名.conf

修改 root 那一行为

root /home/wwwroot/你的域名/public;

然后添加下面这一段到 server
location / 
{
	try_files $uri $uri/ /index.php$is_args$args;		                
}

cd /home/wwwroot/你的域名
apt-get install git -y
git clone -b new_master https://github.com/****/ss-panel-v3-mod.git tmp && mv tmp/.git . && rm -rf tmp && git reset --hard
chown -R root:root *
chmod -R 755 *
chown -R www:www storage
chattr -i .user.ini
mv .user.ini public
cd public
chattr +i .user.ini
service nginx restart

在当前目录下安装依赖

$ php composer.phar install


