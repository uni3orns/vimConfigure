# 20131225更新版

**需要线上做以下处理**

`waf本身代码有更新，请重新git一份`

1. 重新编译pcre，开启JIT模块

        wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.32.tar.gz
        tar -zxvf pcre-8.32.tar.gz
        cd pcre-8.32
        ./configure --enable-jit
        make && make install

2. 升级luajit到2.1

        git clone http://luajit.org/git/luajit-2.0.git  
        git checkout v2.1

3. 删除旧版本luajit，重新编译新luajit

        $luajit -v 为 LuaJIT 2.1.0-alpha 时为正确版本

4. 下载lua-resty-core编译安装

        git clone http://github.com/agentzh/lua-resty-core.git
        make install
	
    请记住安装路径，将会在第五步使用

5. 重新编译nginx，需要两个模块`lua-nginx-module(v0.9.3)`、`pcre-8.32`,请更新线上环境lua-nginx-module模块

        ./configure --prefix=/opt/nginx --add-module=/tmp/lua-nginx-module --with-pcre=/tmp/pcre-8.32 --with-pcre-jit
    
6. 在`init.lua`中更新添加了`require "resty.core"` ，可以在小米的git上获取新版本，也可以自己添加到第一行

7. 在`nginx.conf`中`http`下添加了`lua_package_path "/usr/local/lib/lua/?.lua;;";`(为第二步的安装目录)

	**原配置变为以下配置**

        lua_package_path "/usr/local/lib/lua/?.lua;;";
        init_by_lua_file  /opt/nginx/conf/init.lua;  
        access_by_lua_file /opt/nginx/conf/waf.lua;



###**其他步骤和以前的一样**
