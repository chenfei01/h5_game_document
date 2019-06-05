# H5游戏平台项目上线历程备忘文档
### linux服务器相关
  1. 安装git
  
    `yum install git`
  
  2. 配置git用户
  
    `git config --global user.name "nuoying" `
  
    `git config --global user.email "303975128@qq.com"`
  
    `cat ~/.gitconfig` 可以查看配置用户
  
  3. 生成rsa
  
    `ssh-keygen -t rsa -C "303975128@qq.com" `  (邮箱为代码托管网站注册的邮箱)
    
  4. 添加公钥至代码托管网站
    
     `cat ~/.ssh/id_rsa.pub` 复制公钥至代码托管网站的SSH公钥设置处
