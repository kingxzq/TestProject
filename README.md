# 博客系统简易测试

## 核心模块

- Utils.py
  - 功能：浏览器驱动管理和截图工具
  - 核心类：Driver
  - 特性：
    - 使用webdriver-manager自动管理Chrome驱动版本
    - 支持按日期分类的截图保存功能（路径：../images/YYYY-MM-DD/）
    - 采用单例模式（通过BlogDriver全局实例）

## 测试用例模块

- BlogLogin.py
  - 测试场景：
    - 成功登录（loginSucTest）
    - 失败登录（loginFailTest）
  - 测试步骤：
    1. 访问登录页面（http://120.26.87.94:8080/blog_login.html）
    2. 输入用户名密码（zhangsan/123456）
    3. 验证登录结果
- BlogList.py
  - 测试场景：博客列表页验证
  - 测试步骤：
    1. 访问列表页（http://120.26.87.94:8080/blog_list.html）
    2. 验证页面元素（标题、描述）
    3. 点击首篇文章跳转详情页
- BlogDetail.py
  - 测试场景：博客详情页验证
  - 测试步骤：
    1. 验证页面元素（标题、日期、正文）
    2. 自动检测页面跳转状态

1. 执行入口

- RunCases.py
  - 执行流程：
    1. 成功登录
    2. 列表页测试
    3. 详情页验证
    4. 关闭浏览器

## 技术特点

1. 浏览器管理

- 使用Chrome无头浏览器（可通过取消options注释启用）
- 页面加载策略：默认normal（可配置为eager）
- 自动处理浏览器驱动版本管理

1. 测试验证机制

- 隐式验证方式：
  - 通过find_element检测元素存在性
  - 页面标题验证
  - 弹窗处理（登录失败场景）
- 截图记录：
  - 每个测试步骤自动截图
  - 按测试方法名+时间戳命名截图文件

1. 测试数据

- 测试账号：zhangsan/123456
- 错误账号：zhangsan/111
- 测试文章ID：2

## 执行流程 

登录成功 → 列表页验证 → 文章跳转 → 详情页验证 → 退出浏览器
