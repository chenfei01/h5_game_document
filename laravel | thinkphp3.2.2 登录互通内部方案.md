### 由于h5站点游戏登录页面需要依赖www站点的登录状态

#### laravel设置顶级域名cookie，让h5站点可以共享cookie

1. laravel设置session.php中的domain参数，在.env中：

    `SESSION_DOMAIN=.xxxx.com`
    
2. 登录后设置自定义cookie，该值为当前登录的session_id：

    `Cookie::queue('xxx', $xxx, 60*24*30);`
    
3. 设置的自定义cookie选择不使用系统加密，在中间件EncryptCookies.php中：

    `protected $except = ['xxxx'];`
    
4. 自定义的session_id cookie使用约定的key加密,不与框架自带cookie laravel_session冲突

5. 登录后请求h5对应接口，附带相关参数，session_id易名token传送过去，注意sign验证数据合法性

#### thinkphp处理游戏登录流程

1. web站请求对应接口后保存相关数据(user_id, session_id/token, name....)注意验证数据

2. 游戏登录链接必须附带user_id和token参数,未附带token则直接转到登录页

    `http://xx.xxxxxx.com/mobile.php/game/open_game/cha/179/gaid/mWXfdSJyoLcj5P3FMe2?userId=1&userAccount=u_001&gameAppid=mWXfdSJyoLcj5P3FMe2&channelId=179&channelExt=&timeStamp=1561430924&nonce=BVm3frIB&userPhone=13370061261&userSex=&userHeadicon=&sign=e430d77971eb16f27f0499138dc33e7e&token=pSrphhdBPhxyRgcy3E46hI6DUWrwHRRO3tlzHa8i`
    
3. 获取顶级域名cookie xxxxx,用约定的key加密token,比对验证，(注意！！！不要用tp的cookie()获取指定cookie，拿不到！！！)

    `$web_cookie = $_COOKIE['xxxxxx'];`
    
    `$xxx = signSortData(['xxxx' => $_GET['token']], self::WEBMARKET_API_KEY);`
    
4. 参数中的user_id和token查询数据库验证

    `M('webmarket_user', 'tab_')->where(['user_id' => $userid, 'token' => $_GET['token']])->find();`
    
#### 每个人的登录session_id不同，则加密后的参数不同，泄露登录后的游戏链接也不会直接登录，因为cookie session_id验证不通过
