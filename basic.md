# React


0. 定义:

        - 操作虚拟DOM以将数据渲染为HTML视图的开源JavaScript库

1. React的优点:

        - 采用组件化模式, 声明式编码, 提高开发效率以及组件复用率 (extensive)
        - 在React Native中可以使用React语法进行移动端开发 (useful)
        - 使用虚拟DOM + 优秀的Diffing 算法, 尽量减少与真实DOM的交互 (performance)

2. Jsx:
        
        - 全称: JavaScript XML, 一种类似于XML的js扩展语法: js + XML
        - 本质是React.createElement(compoennt, props, ..)方法的语法糖, 因而极大地简化了virtual dom对象创建的代码量 (纯js创建虚拟DOM: React.createElement(...))
        - 需要babel进行翻译, 翻译成React.createElement(...)的形式
        - 最终被创建virtual dom对象就是一个普通的js对象
        
        
        jsx的语法:
            - 定义虚拟DOM时, 不要写引号
            - 标签中混入js表达式时要使用{}, 一个表达式会产生一个值, 可以放在任何一个需要值的地方, eg: a, a+b, demo(1), arr.map(), function test() {}, 而不能是语句/代码
            - 样式的类名指定不要用class, 要用className="..."
            - inline样式要用style={{key: value}}的形式来写
            - 只能有一个根标签, 如果有多个用<div></div>包起来
            - 标签必须闭合
            - 标签首字母:
                (1). 若小写字母开头, 则将标签改为html同名元素; 若html中没有对应标签, 则报错
                (2). 若大写字母开头, 则会视为component来渲染, 如果没有则报错
![reactJsx](imagePool/reactJsx.png)


3. 组件

    a. 组件 vs 模块
    
        - 模块: 向外提供特定功能的js程序, 一般就是一个js文件
        - 组件: 用来实现局部功能效果的代码和资源的集合(html/css/js/image等等资源)
    
    
    b. 函数组件 -- 简单组件 (组件无状态)
    
    ![functionComponent](imagePool/functionComponent.png)
    
    
    c. 类组件 -- 复杂组件 (组件有状态)
    
    ![classComponent](imagePool/classComponent.png)
    
    
    d. 组件实例 ( 类式组件 ) 的三大核心属性: state, props, refs
    
        (1). state
                - state 是一个对象, 里面存放键值对代表class member + val
                - 组件被称为"状态机", 通过更新组件的state来更新对应的页面显示(重新渲染组件)
                - 组件中constructor 和 render方法中的this为组件实例对象
                - 组件自定义的方法中this为undefined, 需要
                    a. 强制绑定this: 通过函数对象的bind()
                    b. 箭头函数 + 赋值语句
                - 状态数据不能直接修改, 需要借助this.setState({key: val})
                
    ![componentState](imagePool/componentState.png)

        (2). props
                - 每个组件对象都会有props(properties的简写)属性
                - 组件标签的所有属性都保存在props中
                - 通过标签属性从组件外向组件内传递变化的数据
                - 组件内部不能修改props数据, props是read-only
                
    ![classComponentProps](imagePool/classComponentProps.png)
    ![funcComponentProps](imagePool/funcComponentProps.png)
    
        (3). refs
        
            a. string形式的ref -- 性能最慢, 不推荐 ❌
            b-1. 回调inline函数形式的ref  -- 工程常用 ⭐️⭐️⭐️⭐️
            
    ![inlineCallbackRef](imagePool/inlineCallbackRef.png)
            
            b-2. 回调外部函数形式的ref ⭐️⭐️⭐️
            
    ![callBackRef](imagePool/callBackRef.png)
    
            c. React.createRef() -- 官方推荐使用 ⭐️⭐️⭐️⭐️⭐️
    
    ![React.createRef](imagePool/React.createRef.png)
