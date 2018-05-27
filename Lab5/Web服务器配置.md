# Web服务器配置

## 实验环境
- Ubuntu 16.04 server  
- nginx
- verynginx
- wordpress

## 实验过程

### 环境配置

###### 安装配置nginx和verynginx  

- 安装nginx  
```
sudo apt install nginx
```  
- 安装verynginx

```
git clone https://github.com/alexazhou/VeryNginx.git  
sudo apt-get install libpcre3-dev  
sudo apt-get install libssl-dev  
sudo apt-get install build-essential  
编辑/opt/verynginx/openresty/nginx/conf/nginx.conf 修改user=www-data
```  
- 启动nginx  
```
sudo /opt/verynginx/openresty/nginx/sbin/nginx
```  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/verynginx.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/nginx.PNG)

###### 安装配置wordpress

- 参考链接  
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04  
https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04

- 成功访问
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/http.PNG)

### 实现结果

###### 设置反向代理  

- vernginx配置  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/matcher.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/Proxy%20Pass.PNG)  

###### 安全加固要求
- 限制IP访问

  - verynginx设置Matcher匹配，Response响应和Filter过滤。
  - 使用IP地址方式均无法访问上述任意站点，并向访客展示自定义的友好错误。
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/%E5%AE%89%E5%85%A8%E5%8A%A0%E5%9B%BAmatcher.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/filter.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/response.PNG)
  - 结果如下  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/%E9%99%90%E5%88%B6IP.PNG)  
- 在不升级Wordpress版本的情况下，通过定制VeryNginx的访问控制策略规则，热修复WordPress < 4.7.1 - Username Enumeration  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/matcher2.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/filter2.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/1.PNG)

  - 结果如下
  ![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/%E6%96%87%E4%BB%B6%E7%A6%81%E6%AD%A2%E8%AE%BF%E9%97%AE.PNG)

- 白名单访问
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/%E7%99%BD%E5%90%8D%E5%8D%95.PNG)

- 通过定制VeryNginx的访问控制策略规则实现：  

  - 限制Wordpress站点的单IP访问速率为每秒请求数 < 20  
  ![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/limit.PNG)  
  - 自定义错误页面  
  ![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/response2.PNG)  

- 禁止curl访问  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/curl%20matcher.PNG)  
![image](https://raw.githubusercontent.com/CUCCS/2015-linux-public-wq0712/master/Lab5/image/curl%20filter.PNG)
  