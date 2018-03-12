1. `<meta name="apple-mobile-web-app-capable" content="yes" />`
    - 这meta的作用就是删除默认的苹果工具栏和菜单栏。
    - content有两个值”yes”和”no”,当我们需要显示工具栏和菜单栏时，这个行meta就不用加了，默认就是显示。
2. `<meta name="format-detection" content="telephone=no" />`
    - format-detection翻译成中文的意思是“格式检测”
    - meta name="format-detection" content="telephone=no"  =>  阻止自动识别数字为电话号码
    - meta name="format-detection" content="email=no"     =>  阻止自动识别邮箱
    - meta name="format-detection" content="adress=no"   =>  禁止跳转至地图
    - 也可以连写：meta name="format-detection" content="telephone=no,email=no,adress=no"  =>  连写
3. 视口
    - <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />