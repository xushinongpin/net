php -v 查看版本

php -m 查看php扩展



win工具

	PHPstorm 【程序开发软件】

	squePro 【数据库管理软件】



安装composer

	https://pkg.phpcomposer.com/





配置中国镜像

	composer config -g repo.packagist composer https://packagist.phpcomposer.com



创建laravel项目

	composer create-project laravel/laravel laravel54 "5.4.\*" 【laravel54 创建目录名称；laravel/laravel 默认在GitHub的laravel/laravel里面找  "5.4.\*" 下载5.4的分支】



启动laravel  【 手册 https://d.laravel-china.org/docs/5.4 】

	php artisan serve【默认8000端口】

	php artisan help serve【查看使用方法】

	php artisan serve --port=8888【更换端口启动】



设置数据库密码

SET PASSWORD for 'root'@'localhost' = password\('yournewpassword'\);





php artisan【查看有什么用法】

	php artisan migrate:install【数据迁移】

	php artisan --help make:controller【查看 make:controller 的用法】

		php artisan make:controller PostController【 创建 controller 】

	php artisan help make:migration【 查看 make:migration 方法 】

		php artisan make:migration create\_posts\_table【 创建文章表 会存在 \database\migrations\ 这个目录下 】





	创建表报错SQLSTATE\[42000\]: Syntax error or access violation: 1071 Specified key was too long; max key length is 1000 bytes \(SQL: alter table \`users\` add unique \`users\_email\_unique\`\(\`email\`\)\) 解决方法

		\app\Providers\AppServiceProvider.php

		①添加：use Illuminate\Support\Facades\Schema;

		②修改boot 加入默认值

			public function boot\(\)

		    {

		        //mb4string 767/4 = 191.xxx

		        Schema::defaultStringLength\(191\);

		    }

	创建模型

	php artisan make:model Post



	tinker的使用

	php artisan tinker

		使用方法

		添加

			&gt;&gt;&gt; $post = new \App\Post\(\);

			=&gt; App\Post {\#689}

			&gt;&gt;&gt; $post-&gt;title = "this is post1";

			=&gt; "this is post1"

			&gt;&gt;&gt; $post-&gt;content = "this is post1 content";

			=&gt; "this is post1 content"

			&gt;&gt;&gt; $post-&gt;save\(\);

			=&gt; true

		查看

			&gt;&gt;&gt; App\Post::find\(2\); 【 find针对主键 】

			&gt;&gt;&gt; App\Post::where\('title','this is post1'\)-&gt;first\(\); 【 根据title 查找一条 】

			&gt;&gt;&gt; App\Post::where\('title','this is post1'\)-&gt;get\(\);  【 查找title对应的所有数据，返回的是对象 】

		修改操作

			&gt;&gt;&gt; $post = App\Post::find\(2\);

			=&gt; App\Post {\#696

			     id: 2,

			     title: "this is post1",

			     content: "this is post1 content",

			     user\_id: 0,

			     created\_at: "2018-01-23 20:05:35",

			     updated\_at: "2018-01-23 20:05:35",

			   }

			&gt;&gt;&gt; $post-&gt;title = "this is post3";

			=&gt; "this is post3"

			&gt;&gt;&gt; $post-&gt;save\(\);

			=&gt; true

		删除

			&gt;&gt;&gt; $post = App\Post::find\(2\);

			=&gt; App\Post {\#683

			     id: 2,

			     title: "this is post3",

			     content: "this is post1 content",

			     user\_id: 0,

			     created\_at: "2018-01-23 20:05:35",

			     updated\_at: "2018-01-24 04:14:45",

			   }

			&gt;&gt;&gt; $post-&gt;delete\(\);

			=&gt; true



	设置时区

		C:\wamp\www\laravel54\config\app.php 【 修改 'timezone' =&gt; 'UTC', UTC改为中国时区 Asia/Shanghai】



文章模块

	路由

		路由routes

			Route::get\('/','\[控制器\]@\[行为\]'\); 【Route::get\('/posts','\AppHttp\Controllers\PostController@index'\);】

			// Route::post\('/posts','\AppHttp\Controllers\PostController@index'\);

			// Route::any\('/posts','\AppHttp\Controllers\PostController@index'\);

			// Route::match\(\['get','post'\],'/posts','\AppHttp\Controllers\PostController@index'\);

			// Route::put\('/posts','\AppHttp\Controllers\PostController@index'\);

			//Route::get\('/{id}','\AppHttp\Controllers\PostController@show'\);传id的方法

			function show\($id\){

				//$post = \App\Post::find\($id\);

				.....

			}

			//Route::get\('/posts/{post}','\AppHttp\Controllers\PostController@show'\);不是传id是文章的方法

			function show\(\App\Post $post\){

				//.....

			}



			/\*

				put提交的必须一个隐藏表单传过去，不能method=put

				&lt;form action="/posts" method="POST"&gt;

					&lt;input type="hidden" name="\_method" value="PUT"/&gt; 或者 {{method\_field\("PUT"\)}}

				&lt;/form&gt;

			\*/

			分组的方法

			/\*Route::group\(\['prefix' =&gt; 'posts'\],function\(\){

				Route::get\('/','\AppHttp\Controllers\PostController@index'\);

				Route::get\('/{id}','\AppHttp\Controllers\PostController@show'\);

				Route::get\('//create','\AppHttp\Controllers\PostController@index'\);

				Route::post\('/','\AppHttp\Controllers\PostController@index'\);

				Route::any\('/','\AppHttp\Controllers\PostController@index'\);

				Route::match\(\['get','post'\],'/','\AppHttp\Controllers\PostController@index'\);

				Route::put\('/','\AppHttp\Controllers\PostController@index'\);

			}\);\*/

			文章路由

				文章列表

					\vendor\nesbot\carbon\src\Carbon\Carbon.php 【 模板时间调用格式 】

					\database\factories\ModelFactory.php   【 批量添加数据到数据库  github地址	https://github.com/fzaninotto/Faker

					使用操作tinker  php artisan tinker

						&gt;&gt;&gt; factory\(App\Post::class,100\)-&gt;make\(\); 

						&gt;&gt;&gt; factory\(App\Post::class,100\)-&gt;create\(\);

					】

					分页手册 https://d.laravel-china.org/docs/5.4/pagination

				添加文章

					需要传 \_token 数据 {{csrf\_field\(\)}}

					直接添加失败需要修改model

						\app\Post.php【或者添加公共model

							\app\Model.php【

								// protected $guarded = \[\];//fields that can't be injected

	    						// protected $fillable = \['title','content'\];//field that can be injected

							】

						】

					语言包修改

						新建zh目录复制en所有文件，然后修改 \resources\lang\zh\validation.php

						修改\config\app.php 的 'locale' =&gt; 'en', 为 'locale' =&gt; 'zh',



					公开磁盘 \config\filesystems.php

						'default' =&gt; env\('FILESYSTEM\_DRIVER', 'local'\), 改为 'default' =&gt; env\('FILESYSTEM\_DRIVER', 'public'\),



						artisan 执行 php artisan storage:link

				编辑文章

					需要传 \_method 数据  {{method\_field\("PUT"\)}}

				删除文章

				文章详情

		模板 blade

	表设计

		表设计

		模型

	页面逻辑

		文章列表

		添加文章

		编辑文章

		删除文章

		文章详情



登录注册

	自带功能

		php artisan make:auth

	页面搭建

		登录页面

			php artisan make:controller LoginController

		注册页面

			php artisan make:controller RegisterController

		个人设置

			php artisan make:controller UserController



	业务逻辑

		注册

		登录

		认证权限

			修改权限设置

			php artisan make:policy PostPolicy 【 生成在 \app\Policies\PostPolicy.php 】

			\app\Providers\AuthServiceProvider.php  【 权限注册 】

		头像设置



laravel功能

路由        route

模板        blade

模型        model

控制器      controller

数据迁移    migration

数据填充    seed

命令行      tinker

分页        paging





核心日志类

	查看日志

		\vendor\laravel\framework\src\Illuminate\Foundation\Application.php 里面的

		linux：  tail -f storage\logs\laravel.log

		window： type storage\logs\laravel.log

