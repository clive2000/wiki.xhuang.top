# 部署Olaindex

{% embed url="https://imwnk.cn/archives/bt-olaindex" %}



发现用docker-compose部署会简单很多，把nginx改成了caddy，caddy2设置文件写起来也简单很多很多，bootstrap项目在github repo里

```bash
git clone https://github.com/clive2000/docker_php_bootstrap
cd docker_php_bootstrap
# 更改caddy/Caddyfile域名
cd opt/code
git clone https://github.com/YukiCoco/OLAINDEX-Magic tmp
mv tmp/.git .
rm -rf tmp
git reset --hard
```

```bash
docker-compose up -d
alias myphp='docker run -it -v $PWD:/opt/code -w /opt/code --rm PHPIMAGENAME '
cd opt/code 
cp database/database.sample.sqlite database/database.sqlite
myphp composer install -vvv
chmod -R 755 storage/
chown -R www-data:www-data *
myphp php artisan od:install
chown -R www-data:www-data *
```



