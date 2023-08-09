# Django-drf-vue3-rbac



权限的管理：

- v1版本，简单粗暴方式实现
- v2版本，简单粗暴方式实现+简单
- v3版本，用户&角色&权限



### 1.设计和实现

- 确定项目共有多少角色：管理员、财务、审核员
- 每个角色都具备的功能权限
- 前端

  - 登录，选择角色+登录，vuex=>token、role
  - 后台管理

    - 动态菜单，每种角色加载自己的菜单
      - vuex中保存了当前用户角色role
      - 定义路由
      - 打开页面，读取所有路由 筛选：is_menu = true && role 合法
    - 是否有权范文页面（路由）

      - 基于路由的导航守卫实现
        - 读取vuex中保存当前用户角色 role
        - 获取当前要访问的路由 to，找到规定可访问的roleList
        - 判断是否有权
      - 页面的局部功能是否有权限：增删改
        - 展示：无权限不展示【vuex中保存当前用户角色role判断是否有此功能】
        - 功能：列入页面加载发送ajax请求
          - if（hasPermission(["admin","manager"])）


- 后端

  - 用户登录成功，返回token凭证

  - 后续再来，认证组件，保障凭证正确 + role

  - 权限的校验

    - 在每个视图中role，判断是否有权限访问。
    - 基于drf的权限组件
    - 基于配置 + 权限组件

    ```python
    
    router = router.SimpleRouter()
    router.register(r'api/users', views.UserView, basename='user')
    
    setting.py
    permission = {
        'admin':{
            'info':["GET","POST","PUT"],
            'order':["GET","POST"]
        },
        'user':{},
        'manager':{}
    }
    ```




### 2.功能的开发

#### 2.1 vue

- 创建项目
- 创建基本路由 + 页面
  - 登录页面
  - 后台管理
- 是否能访问路由
- 动态菜单
  - 读取所有的路由 + 筛选 is_menu = True
  - 菜单列表
    - [{title:"?",name:"?"},{title:"?",name:"?"},{title:"?",name:"?"}]

### 2.2 后端

- 创建 django 项目



### 3 功能的完善

#### 3.1 关于返回值

```bash
{"code":1000,"data":[]}
```

是否关注状态码？

- 不用状态码
- 使用状态码

**正常返回**

**异常返回**



### 3.2 axios + 请求 + jwt + 跨域



### 3.3 业务开发

-  前端
- 后端



## V3版本，用户&角色&权限

### 1.设计思路

#### 1.1 整体思路

- 角色和权限 多对多
- 用户&角色 一对多 或 多对多
- 关于菜单=路由（两级菜单）



#### 1.2 功能

- 权限的管理
  - 权限&菜单等信息录入
  - 用户&角色&权限 分配

- 登录
  - 根据用户信息获取到此用户的所有权限
  - 路由列表
  - 获取用户所有权限=>路由=>菜单
- 动态菜单menu
- 页面访问权限router
- 按钮展示
- 权限的管理



#### 1.3 实现思路

- 模拟登录 + 模拟访问
- 实现权限的管理
- 更换真实数据
- 业务功能



### 2 功能实现





















