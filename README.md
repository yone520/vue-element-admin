# vue-element-admin
[源码](https://github.com/yone520/vue-element-admin-source)    
[预览](https://yone520.github.io/vue-element-admin)

这个项目模仿大佬来的，为什么模仿的话，其实不是我没事儿做，主要是因为权限的问题，很多开源项目的权限都是基于什么 [admin,editor] 来的，还有种是后端控制前端路由，这样现在很多开源项目都不是这种方案，包括 antd pro v4, v5是可以得了，但是毕竟是React的，所以我来弄个vue版本的以后好用。

## 技术栈

- ElementUI（2.5.4）
- Vue（2.5.17）
- Vuex（3.0.1）
- VueRouter（3.0.1）
- Axios（0.19.0）
- lodash
- moment
- js-cookie
- nprogress
- vue-i18n

## 登陆角色

admin, editor, 任意输入

### 其实这里多少角色不是很重要，主要是看接口返回的可访问路由字段 
// 类似这种，['canAdmin', 'canEditor', 'canEditorA', 'canEditorB', 'table']

```javascript
export const Login = ({
  username,
  password
}) => {
  return new Promise((resolve) => {
    let role = ''
    if (username === 'admin') { // 模拟admin
      role = JSON.stringify(['canAdmin', 'canEditor', 'canEditorA', 'canEditorB', 'table']);
    } else if (username === 'editor') { // 模拟editor
      role = JSON.stringify(['canAdmin', 'canEditor', 'canEditorA']);
    } else { // 如果后台没有返回，路由就只会渲染不需要任何权限的路由
      role = JSON.stringify([])
    }
    setTimeout(() => {
      resolve({
        userInfo: {
          username
        },
        token: 'fdaksfahsudfoajfjasd;flk',
        role: role
      })
    }, 1000)
  })
}

```

## 完成功能
- [x] 登陆
- [x] 多语言
- [x] 角色切换
- [x] 可搜索的路由
- [ ] 网络请求(感觉没必要写，每个公司，大不同)

