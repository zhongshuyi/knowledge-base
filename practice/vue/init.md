# 初始化项目

## 需要的信息来源

pnpm 中文文档 : https://www.pnpm.cn/

Vite 官方中文文档：https://vitejs.cn/vite3-cn/

## 新建 vite 项目

使用 pnpm 包管理器

```bash
pnpm create vite
```

需要填写你的项目名称，然后选择 Vue 与  TypeScript

```bash
√ Project name: ... your-project-name
√ Select a framework: » Vue
√ Select a variant: » TypeScript
```

目录结构

```text
│   .gitignore # git 忽略文件
│   index.html # 入口HTML
│   package.json # 项目配置文件
│   README.md 
│   tsconfig.json #  ts项目配置文件
│   tsconfig.node.json 
│   vite.config.ts # vite 配置文件
│
│
├───public # 不打包的静态资源
│       vite.svg # 网站图标
│
└───src # 主目录
    │   App.vue # 主组件
    │   main.ts # 入口文件
    │   style.css # 样式文件
    │   vite-env.d.ts # vite环境配置文件
    │
    ├───assets
    │       vue.svg # 需要打包的静态资源
    │
    └───components # 组件目录
            HelloWorld.vue # 组件
```

`tsconfig.json` 是 ts 项目的项目配置文件

[tsconfig.json 官方文档](https://www.tslang.cn/docs/handbook/tsconfig-json.html)

