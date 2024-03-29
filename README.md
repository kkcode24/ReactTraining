# ReactTraining

[React官网传送门](https://facebook.github.io/react/index.html "React官网")
> 当前库React版本v15.3.2
# 应用开发分类介绍
>## 原生应用:
>介绍：
特别为某个操作系统做的应用, 比如iOS, Android, Blackberry等等。
iOS的开发语言:OC(Objective-C), Swift。Android的开发语言: Java 
优点：
a.访问手机的所有功能
b.速度比较快, 用户体验好
c.可以投放到应用市场(app stroe, 豌豆荚), 并进行内购, 收费下载
d.方便查找
缺点：
a.开发成本高
b.上传时间难易把控
c.内容限制
d.新版本需要重新下载
## web应用
>介绍：
web应用是为移动浏览器设计的应用, 使用普通web技术(html, css, JavaScript)实现
优点:
a.跨平台(各种智能终端的浏览器上运行)
b.开发成本低
c.可以立即上线
d.内容没有限制
e.用户更新比较快(只需要刷新浏览器)
缺点
a.加载速度慢
b.不能上传应用商店
c.必须联网
d.可以看到源码
## 混合应用
>介绍：
混合应用, 使用原生的技术(OC, Java)和web技术(html, css, js)来开发应用
优缺点：
a.原生应用的开发者做一个应用皮(应用内部只有一个控件webview, 浏览器组件), 前端人员开发移动页面, 并在原生应用中的webview中显示
  原生技术 : 前端技术 = 1 : 9
b.通过js代码, 写一个应用, 最终编译成iOS和Android版本
  原生技术 : 前端技术 = 0 : 10
c.原生的应用中某些界面使用前端来开发
  原生技术 : 前端技术 = 5 : 5
# 引用React库
## 部署开发环境
在github上，选择一个版本下载，不要下载最新的，选择一个比较稳定的下载。[传送门](https://github.com/facebook/react/releases"下载地址")<br>
下载后，在本地解压，有build文件夹和examples文件夹，还有readme.md文件。
>进入build文件夹，选择react-min.js文件和react-dom.min.js文件，复制一份放到你的demo中的js文件中。但是这并不是最终的，下面会说
## 部署后的文件内容
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>templet</title>
</head>
<body>
<div id="example"></div>
<!--react.min.js: react的核心模块-->
<script type="text/javascript" src="js/react.min.js"></script>
<!--react-dom.min.js: react中dom元素操作的模块-->
<script type="text/javascript" src="js/react-dom.min.js"></script>
<script>
//这里是我们的代码区域
</script>
</body>
</html>
```
##看一个demo
```
<script>
//这里是我们的代码区域
ReactDOM.render(
            //React.createElement(元素名, 元素属性, 元素内容);
            React.createElement('h1', null, 'Hello world!'),
            document.getElementById('example')
    );
/*ReactDom.render()作用: 把元素内容渲染到元素中.
	有两个参数:
	parameter1:虚拟DOM
	parameter2:真实DOM
*/
</script>
```
执行后页面会显示“Hello World！”
>React.createElement();是可以进行嵌套的
```
<script type="text/javascript">
//这里是我们的代码区域
ReactDOM.render(
            React.createElement('div', null,
                    React.createElement('p', null,
                            React.createElement('em', null, '今天星期一')
                    )
            ),
            document.getElementById('wrap')
    );
   </script>
```
但是这样写起来太过麻烦，作为程序员则是能坐着不站着，能躺着不坐着。因此React推荐使用JSX语法
>JSX: JavaScript extension, 带扩展的JavaScript, 并不是一门新语言, 它是一个语法糖
>那么什么是语法糖呢？
>举个创建数组的栗子：

```javascript
var arr = new Array(1, 2, 3);
//通过语法糖, 创建数组
var arr1 = [1, 2, 3];
//创建对象
var obj = new Object();
obj.name = "张三";
 //通过语法糖, 创建对象
var obj1 = {
	name: "李四"
};
```

## 如何使用JSX
>虽然JSX比起JavaScript写起来更简单，代码更直观，但是浏览器对JSX并不友好，那怎么办呢，React提供了一个中间人，就是Bable转换器。
>
>bable转换器的工作就是把ECMAScript6, JSX等转化成浏览器可以执行的js代码
>
>所以JSX的执行顺序与JS比较就多了一个X
>JSX的执行顺序：
>JSX->浏览器下载->Babel进行转换->JavaScript->浏览器执行
>JavaScript的执行顺序：
>JavaScript->浏览器下载->浏览器执行
## 引入转换器脚本
>再次进入build文件夹，选择browser.min.js文件，复制一份到demo下的js文件夹下
## 最终部署环境
```
//因此最终模板为
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div id="example"></div>
<script type="text/javascript" src="js/react.min.js"></script>
<script type="text/javascript" src="js/react-dom.min.js"></script>
<script type="text/javascript" src="js/browser.min.js"></script>
<!--注意:
type="text/babel": script内部的代码, 最终用babel的编译器进行编译后, 再执行-->
<script type="text/babel">
    //我们的代码
</script>
</body>
</html>
```
## 吃块糖
```
//使用JSX书写
<script type="text/babel">
    ReactDOM.render(
            <h1>Hello, React!</h1>,
            document.getElementById('example')
    );
</script>
```
```
//也可以嵌套
<script type="text/babel">
    ReactDOM.render(
            <div><p><em>今天天气真好!</em></p></div>,
            document.getElementById('example')
    );
</script>
```
# 聊聊JSX
## 出现尖括号&lt;&gt;会自动创建元素
```
ReactDOM.render(
            <h1>Hello React!</h1>,
            document.getElementById('example')
);
//碰到h1元素时，会自动创建h1元素，并把h1元素渲染到真实的DOM中
```
## 出现大括号{}认为是变量
```
var text = '学姐';
ReactDOM.render(
        <h1>哈喽, {text}!</h1>,
        document.getElementById('example')
);
```
>另外JSX中的{}中, 可以写表达式(变量, 运算, 函数调用)

```
ReactDOM.render(
            <div>1 + 1 = {1 + 1}</div>,
            document.getElementById('example')
);
```

## 关键词重名问题等
>1.在渲染的元素内容中, 不能出现for, class, 因为和React中的关键词重名<pre><code> for 写成 htmlFor
class 写成 className</code></pre>
2.渲染的元素内容, 只能有一个根节点
3.单标签需要用/闭合
```
ReactDOM.render(
         <div className = "bg">
             <label htmlFor="username">用户名:</label>
             <input type="text" id="username"/>
         </div>,
         document.getElementById('example')
);
```
## 循环操作

```
var arr = ['宝宝', '蓉蓉', '经纪人', '楼上邻居', '隔壁老王'];

    ReactDOM.render(
            <ul>
                <li>{arr[0]}</li>
                <li>{arr[1]}</li>
                <li>{arr[2]}</li>
                <li>{arr[3]}</li>
            </ul>,
            document.getElementById('example')
    );
```
>上面代码不符合程序员的懒特点，所以需要改，改为

```
ReactDOM.render(
            <ul>
                {
                    arr.map(function (e) {
                        //e: 代表数组中的某个元素
                        return <li>Hi, {e}!</li>
                    })
                }
            </ul>,
            document.getElementById('example')
);
```
>因为本教程不针对0基础同学，所以不再讲解JavaScript代码基础，如果想看本教程需要有HTML5和JavaScript的基础。
>简单提下数组的map和过滤方法：
>//map: 映射, 按照一定的规则, 对数组元素进行转换, 比如 1 2 3 -> 4 5 6
>//filter: 过滤, 按照一定的条件, 对数组元素进行筛选, 比如 1 2 3 -> 3
## 数组中存放元素
>当数组中存放的是元素, 可以直接使用数组进行渲染, 相当于把数组的每个元素进行渲染
```
ReactDOM.render(
            <div>{arr1}</div>,
            document.getElementById('example')
);
```
# 说说组件
## 组件的创建
>React是基于组件进行开发
>创建一个组件(类), 显示Hello world!
    1.组件名字, 以大写字母开头
    2.使用createClass创建组件
    3.组件必须实现render方法
```
var HelloWorld = React.createClass({
        //定义render方法, 当组件渲染时触发
        render: function () {
            return <h1>Hello world!</h1>
        }
});
```
## 组件的使用
>方式1: 双标签

```
ReactDOM.render(
        <HelloWorld></HelloWorld>,
        document.getElementById('example')
);
```
>方式2: 单标签

```
ReactDOM.render(
        <HelloWorld />,
        document.getElementById('example')
);
```
## 给组件赋属性值
>给组件赋属性值, 都会被记录在this.props的对象中,
>对象的属性和组件的属性一一对应

```
var HelloWho = React.createClass({
	     render: function () {
	         return <h1>Hello {this.props.name}!</h1>
	     }
});
ReactDOM.render(
            <HelloWho name="帅哥"></HelloWho>,
            document.getElementById('example')
);
```
>练习: 定义组件Link, 用于展示一个超链接
>例如: `<a href="http://www.baidu.com">百度</a>` 
>其中链接地址和链接标题可以进行设置

```
var Link = React.createClass({
      render: function () {
          return <a href={this.props.url}>{this.props.title}</a>
      }
});

ReactDOM.render(
      <Link url="http://baidu.com" title="百度"/>,
      document.getElementById('example')
 );
```
## 为组件添加样式
### 为组件添加样式的3种方法
>1.内联样式, 比如div
   2.选择器样式, 比如h1
   3.对象样式, 比如p
### 对象样式或内联样式
>1.样式的值为对象
   2.对象的属性用驼峰法命名
   3.如果值为12px, 可以省略单位px
### 综合示例
>注意：选择器样式，需要在style标签内写css
根据下面的例子写个类
```
<style>
    .title {
        text-align: center;
        color: #cc52ff;
    }
</style>
```
>js代码如下：
```
var pStyle = {
	    backgroundColor: "green",
	    fontSize: 20
};
var Message = React.createClass({
   render: function () {
       return (
               <div style={{
                   backgroundColor: "yellow",
                   borderWidth: 5,
                   borderColor: "black",
                   borderStyle: "solid"
               }}>
                   <h1 className="title">{this.props.title}</h1>
                   <p style={pStyle}>{this.props.content}</p>
               </div>
       )
   }
});
ReactDOM.render(
      <Message title="干了这碗鸡汤"             content="如果你得罪了老板，失去的只是一份工作；如果你得罪了客户，失去的不过是一份订单；是的，世上只有一个人可以得罪：你给她脸色看，你冲她发牢骚，你大声顶撞她，甚至当 着她的面摔碗，她都不会记恨你，原因很简单，因为她是你的母亲。"></Message>,
      document.getElementById('example')
);
```
## 多个组件组合成一个组件
>直接上例子
```
var ListTitle = React.createClass({
    render: function () {
        return <h1>{this.props.title}</h1>
    }
});
var ListContent = React.createClass({
 render: function () {
     return <p>{this.props.content}</p>
 }
});
var List = React.createClass({
 render: function () {
     return (
             <div>
                 <ListTitle title={this.props.t}/>
                 <ListContent content={this.props.c}/>
             </div>
     )
 }
});
ReactDOM.render(
     <List t="我真帅!" c="这是一个真理!"/>,
     document.getElementById('example')
);
```
# 谈谈props对象
>props: 组件自带的的属性, 用于组件内外的值的传递
>注: props是只读的, 只能获取, 不能修改
```
var Hello = React.createClass({
	render: function () {
	    return <h1>Hello, {this.props.name1}, {this.props.name2}</h1>
	}
});
ReactDOM.render(
    <Hello name1="小明" name2="小龙"/>,
    document.getElementById('example')
);
```
# props对象
## props是只读的
>props: 组件自带的的属性, 用于组件内外的值的传递
   注: props是只读的, 只能获取, 不能修改 

```
<script type="text/babel">
    var Hello = React.createClass({
        render: function () {
            return <h1>Hello, {this.props.name1}, {this.props.name2}</h1>
        }
    });

    ReactDOM.render(
        <Hello name1="小明" name2="小龙"/>,
        document.getElementById('example')
    );
    var values = {
        name1: '小李',
        name2: '小丽'
    };

    ReactDOM.render(
        <Hello name1={values.name1} name2={values.name2}/>,
        document.getElementById('example')
    );
</script>
```
## 延展操作符
>...(三个点, 延展操作符)是一种语法糖， 把对象的属性值赋到对应的组件中

```
<script type="text/babel">
    var Hello = React.createClass({
        render: function () {
            return <h1>Hello, {this.props.name1}, {this.props.name2}</h1>
        }
    });

    var values = {
        name1: '小牛',
        name2: '小狗'
    };
    
    ReactDOM.render(
            <Hello {...values}/>,
            document.getElementById('example')
    );
</script>

```
## 延展操作符练习

```
<script type="text/babel">
   var Link = React.createClass({
        render: function () {
            return <a {...this.props}>{this.props.name}</a>
        }
    });
    
    ReactDOM.render(
        <Link href="http://www.baidu.com" name="百度"/>,
        document.getElementById('example')
    );

    /*
     this.props = {
     href: "http://www.baidu.com",
     name: "百度"
     };
     */
</script>
```
## this.props.children
>this.props.children: 代表元素内的子元素

```
<script type="text/babel">

    //抛砖引玉demo

    var List = React.createClass({
        render: function () {
            return (
                    <ul>
                        {
                            this.props.data.map(function (e) {
                                return <li>{e}</li>
                            })
                        }
                    </ul>
            );
        }
    });

    ReactDOM.render(
            <List data={[1, 2, 3]}></List>,
            document.getElementById('example')
    );
    
    //请结合05-props.html再看
</script>
```

05-props.html

```
<script type="text/babel">

    //this.props.children: 代表元素内的子元素
    
    var ListPro = React.createClass({
        render: function () {
            return (
                    <ul>
                        {
                            this.props.children.map(function (e) {
                                return <li>{e}</li>;
                            })
                        }
                    </ul>
            );
        }
    });

    ReactDOM.render(
        <ListPro a="1" b={2}>
            <em>斜体</em>
            <strong>粗体</strong>
            <a href="# ">链接</a>
        </ListPro>,
        document.getElementById('example')
    );
</script>
```
## props指定默认值

```
<script type="text/babel">
   
    var data = 123;

    var ShowTitle = React.createClass({
        //指定默认值
        getDefaultProps: function () {
            //props是一个对象
            return {
                title: '默认标题'
            }
        },
        render: function () {
            return <h1>{this.props.title}</h1>
        }
    });
    ReactDOM.render(
            <ShowTitle title={data}/>,
            document.getElementById('example')
    );
</script>
```
# state状态
>在此之前，先说下事件机制

```
<script type="text/babel">
    //事件处理
    var MyButton = React.createClass({
        //事件触发的函数
        click: function () {
            alert(this.props.title);
        },
        render: function () {
            return <button onClick={this.click}>{this.props.title}</button>
        }
    });

    ReactDOM.render(
            <MyButton title="我是按钮的标题"></MyButton>,
            document.getElementById('example')
    );
</script>
```

>state和props的区别: 
>props用于记录组件的属性和子元素, 是一个只读的对象; state用于进行状态的记录,是一个可以修改的对象

>练习: 定义一个组件CheckBox, 包含两部分复选框, 文本; 效果: 选择复选框, 文本变为true, 取消选择, 文本变成false

请结合02-state.html看

```
<script type="text/babel">

    var CheckBox = React.createClass({
        //获取初始的状态值state
        getInitialState: function () {
            return {
                isCheck: false
            }
        },
        click: function () {
            //不能用等号"="直接修改state
            //使用setState的方法来修改state
            this.setState({
                isCheck: !this.state.isCheck
            });
        },
        render: function () {
            return (
                    <div>
                        <input type="checkbox" onClick={this.click}/>
                        <span>{this.state.isCheck ? 'true' : 'false'}</span>
                    </div>
            );
        }
    });

    ReactDOM.render(
            <CheckBox/>,
            document.getElementById('example')
    );
</script>
```
>练习: 实时显示输入内容
>请结合03-state.html看

```
<script type="text/babel">
    
    var Input = React.createClass({
        getInitialState: function () {
            return {
                content: ''
            }
        },
        change: function (event) {
            //event: 触发的事件
            console.log(event.target.value);
            this.setState({
                content: event.target.value
            });
        },
        render: function () {
            return (
                    <div>
                        <input type="text" onChange={this.change}/>
                        <p>{this.state.content}</p>
                    </div>
            );
        }
    });

    ReactDOM.render(
        <Input/>,
        document.getElementById('container')
    );
</script>
```
# 组件的生命周期
>组件的生命周期: 从创建组件到组件移除的完整的过程
React组件的生命周期,分为三个阶段:
      1.挂载阶段(Mounting): 把组件插入元素中
      2.更新阶段(Update): 重新渲染组件
      3.移除阶段(Unmounting): 从元素中移除组件
## 挂载阶段
```
<script type="text/babel">
    var Demo = React.createClass({
        getDefaultProps: function () {
            console.log("获取默认属性值");
            return {
                name: 'world'
            }
        },
        getInitialState: function () {
            console.log("初始化状态值");
            return {
                isSelect: false
            }
        },
        componentWillMount: function () {
            console.log("将要挂载组件");
        },
        render: function () {
            console.log("渲染组件");
            return <h1>Hello, {this.props.name}!</h1>
        }
    });
	//第一个渲染组件
    ReactDOM.render(
        <Demo name="三儿"/>,
        document.getElementById('example')
    );
</script>
```

## 更新阶段

```
<script type="text/babel">

    var Demo = React.createClass({
        getDefaultProps: function () {
            console.log("获取默认属性值");
            return {
                name: 'world'
            }
        },
        getInitialState: function () {
            console.log("初始化状态值");
            return {
                isSelect: false
            }
        },
        componentWillMount: function () {
            console.log("将要挂载组件");
        },
        render: function () {
            console.log("渲染组件");
            return <h1>Hello, {this.props.name}!</h1>
        },
        componentDidMount: function () {
            console.log("已经挂载组件");
        },
        componentWillReceiveProps: function () {
            console.log("将要接收到属性值");
        },
        shouldComponentUpdate: function () {
            console.log("是否可以更新组件");
            return true;
        },
        componentWillUpdate: function () {
            console.log("将要更新组件");
        },
        //render:  渲染组件
        componentDidUpdate: function () {
            console.log("已经更新组件");
        }
    });

    //第一个渲染组件
    ReactDOM.render(
        <Demo name="三儿"/>,
        document.getElementById('example')
    );

    //重新渲染组件
    ReactDOM.render(
        <Demo name="四儿"/>,
        document.getElementById('example')
    );

</script>
```
## 移除组件

```
<script type="text/babel">

    var Demo = React.createClass({
        getDefaultProps: function () {
            console.log("获取默认属性值");
            return {
                name: 'world'
            }
        },
        getInitialState: function () {
            console.log("初始化状态值");
            return {
                isSelect: false
            }
        },
        componentWillMount: function () {
            console.log("将要挂载组件");
        },
        render: function () {
            console.log("渲染组件");
            return <h1>Hello, {this.props.name}!</h1>
        },
        componentDidMount: function () {
            console.log("已经挂载组件");
        },
        componentWillReceiveProps: function () {
            console.log("将要接收到属性值");
        },
        shouldComponentUpdate: function () {
            console.log("是否可以更新组件");
            return true;
        },
        componentWillUpdate: function () {
            console.log("将要更新组件");
        },
        componentDidUpdate: function () {
            console.log("已经更新组件");
        },
        componentWillUnmount: function () {
            console.log("将要移除组件");
        }
    });

    //第一个渲染组件
    ReactDOM.render(
        <Demo name="三儿"/>,
        document.getElementById('example')
    );

    //重新渲染组件
    ReactDOM.render(
        <Demo name="四儿"/>,
        document.getElementById('example')
    );

    //移除组件
    ReactDOM.unmountComponentAtNode(
        document.getElementById('example')
    );
</script>
```
>06-lifecycle.html 是完成的测试，包含注释及代码
# React之Ajax

```
<script type="text/babel">
    var List = React.createClass({
        getInitialState: function () {
            return {
                arr: []
            }
        },
        render: function () {
            return (
                    <ul>
                        {
                            this.state.arr.map(function (e) {
                                return <li>{e}</li>
                            })
                        }
                    </ul>
            );
        },
        componentDidMount: function () {
            console.log("已经挂载组件");
            $.ajax({
                url: this.props.url,
                dataType: 'jsonp',
                type: "GET",
                jsonp: "cb",//jsonp回调的函数名的key值, 会自动将cb=success, 会调用success方法
                success: function (data) {
                    this.setState({
                        arr: data.s
                    });
                }.bind(this)
                //在函数的后面添加bind, 用于修改函数内部this的指向
            });
        }
    });


    ReactDOM.render(
            <List url="https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=大宝剑"/>,
            document.getElementById('container')
    );

</script>
```
>入门教程结束了，但是继续学习React的路程才刚刚开始，希望本教程对你有所帮助，有缘人。