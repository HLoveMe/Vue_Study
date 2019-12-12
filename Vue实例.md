* Vue实例创建

	```
	new Vue({
		el:"#app",
			//提供一个页面上已经存在的节点作为挂载点
		template:"<div />"一个字符串模板作为 Vue 实例的标识使用
		render 　　;字符串模板的代替方案
		data:{ //表示该Vue实例数据 
			1：Vue 数据来源
			2：vue.$data可以访问原始数据
			3：需要使用的数据在data进行声明
			name:"朱"，
			age:18
		},
		computed:{ //计算属性
			fullname:function(){
				//计算属性 声明为函数 
				//但是使用当做属性值来使用
				//会在渲染时再次计算
				//具有缓存功能 除了渲染 和 所引用的属性改变 才会再次调用
				return "zzH"
			}
			//计算属性的set get
			Dome:{
			   set: function(v) {
		        this.a = v;
		      },
		      get: function() {
		        return this.a + "zzh";
		      }
			}
			使用计算属性
			<div>{{funllname}}{{Dome}}</div>
		},
		watch:{
			//用于监听属性修改
			//计算属性只有当关联属性 并产生变化后 才会被更新
			falg[属性名称](){}
			name(newv, oldv){
				xxx
			}
		},
		filters:{//过滤器
			//过滤器和计算属性效果差不错  仅仅用作简单的文本处理
			sex:function(v){
				if(v==1)return "Men";
				return "WoMen"
			},
			trim:function(v){
				return v.trim()
			},
			date:fun(date,formate){
				return date.xxxx(formate)
			}
		
			<div>{{1 | sex}}</div>
			<div>{{1 | sex | trim}}</div>
			<div>{{"2019,1,1" | date("YY-MM-DD")}}</div>
		}
	})
```
* Vue实例对象

	* Vue实例中 computed methods不要使用监听函数
		
		```
		创建Vue时 使用监听函数会让this指向当前环境的所处上下文环境 Window
		```
* el template render 指定模板
	
	* 优先级 render> template>el
	
	* el:提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标

	* template:一个字符串模板作为 Vue 实例的标识使用。模板将会 替换 挂载的元素。挂载元素的内容都将被忽略，除非模板的内容有分发插槽。

	* render 字符串模板[template]的代替方案，允许你发挥 JavaScript 最大的编程能力。该渲染函数接收一个 createElement 

	* el 选取存在的节点作为Vue挂载点
	
		```
			<body>
		        <div id="app">
		            {{name}}
		        </div>
		    </body>
		    <script>
		        new Vue({
		            el: "#app",
		            data: {
		                name: "aa"
		            }
		        })
		    </script>
		```
	* el template 字符串作为模板

		```
		<body>
	       	<div id="app2"> </div>
   		</body>
	    <script>
	        new Vue({
	            el:"#app2",
	            data:{name:'name'},
	            template: "<div id="dome">{{name}}11</div>"
	        })
	        1:选取已经存在的节点#app2
	        2:使用template替换#app2 
	        3:页面无#app2节点
	        4:#dome作为Vue挂载点
	    </script>
		```
	* el render 

		```
		new Vue({
		  render:(createElement) => createElement(App),
		  el: "#app",
		  data:{
		    name:'111'
		  },
		})
		1:执行createElement创建页面节点
		2:选取页面中的#app作为Vue对象的挂载点
		```	
		
* Vue实例加载流程
	
	![](./images/lifecycle.png)
	
* html加入Vue

	```
	<html>
	    <head>
	        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	    </head>
	
	    <body>
	        <div id="app">
	            {{name}}
	        </div>
	    </body>
	    <script>
	        new Vue({
	            el: "#app",
	            data: {
	                name: "aa"
	            }
	        })
	    </script>
	</html>
	
	```