
# 本地环境安装

   ### composer node npm 安装方式见前文档
   
  `composer update` 项目根目录
  
  `npm install`
  
  ### copy .env.example改名为 .env
  
  .env 里配置本地相关数据库参数
  
  ### nignx 404 
  
  #try_files $uri $uri/ /index.php?$query_string
  
  ### laravel 404
  
  注意.env配置
   `APP_URL=http://web.test`
   `DOMAIN_WEB=http://web.test`
