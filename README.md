# H5游戏平台项目上线历程备忘文档
### linux服务器相关
  1. 安装git
  
   `yum install git`
  
  2. 配置git用户
  
   `git config --global user.name "nuoying"`
  
   `git config --global user.email "303975128@qq.com"`
  
   `cat ~/.gitconfig` 可以查看配置用户
  
  3. 生成rsa
  
   `ssh-keygen -t rsa -C "303975128@qq.com"` (邮箱为代码托管网站注册的邮箱)
    
  4. 添加公钥至代码托管网站
    
   `cat ~/.ssh/id_rsa.pub` 复制公钥至代码托管网站的SSH公钥设置处
   
  5. 服务器配置托管
  
   `git init` 进入项目根目录
   
   `git remote add origin git@gitee.com:nuoying_chenfei/WebMarket.git` 添加项目托管网站ssh地址
   
   `cat .git/config` 可以查看配置参数
   
   `ssh -T git@github.com` 验证SSH连接
   
  6. 提交上传代码
  
  `git add -A`
  
  `git commit -m "first commit"`
  
  `git push origin master`
  
  7. 更新被拒绝
  
  `git push -u origin +master` 强行上传
  
  **注意：！！！提示（Are you sure you want to continue connecting (yes/no)?）时！！！**
   
   **！！！键入yes！！！**
          
   **！！！不要按回车！！！**
          
   **！！！不要按回车！！！**
          
   **！！！不要按回车！！！**
