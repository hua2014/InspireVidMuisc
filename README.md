# InspireVidMuisc
Jion VidMuse-LSTV-M into InspireMuisc to surport Video Mode 

## InspireMuisc + VidMuse

- fork InspireMuisc: https://github.com/hua2014/FunMusic
- fork VidMuse: https://github.com/hua2014/VidMuse

```
git submodule add https://github.com/hua2014/FunMusic.git InspireMusic
git submodule add https://github.com/hua2014/VidMuse.git VidMuse-main
```

添加或更新子模块后，需在父项目中提交变更；子模块如有更新（一般在各自单独的项目中维护），需要父项目中同步更新至最新提交；

# [子模块常用操作](https://blog.csdn.net/lianghudream/article/details/148654036)

## 添加
添加子模块：`git submodule add <仓库URL> <本地路径>`
- 示例：`git submodule add https://github.com/user/lib.git libs/lib`

提交变更：
```py
git add .gitmodules libs/lib
git commit -m "添加子模块 lib"
```

## 克隆

克隆含子模块的项目
```py
# 方法 1（推荐递归克隆）：
git clone --recursive <主仓库URL>

# 方法 2（分步初始化）：
git clone <主仓库URL>
cd <主项目目录>
git submodule init      # 初始化配置
git submodule update    # 拉取子模块代码
```

## 更新
更新子模块:

| 场景	| 命令 | 
| ----	| --- | 
| 更新所有子模块到最新提交	| `git submodule update --remote --recursive` | 
| 更新指定子模块	|  `git submodule update --remote <子模块路径>` | 
| 切换到子模块特定版本	| `bash cd <子模块路径> git checkout <分支/标签/Commit>` | 


提交主仓库变更：子模块更新后需提交新 Commit ID：
```py
git add <子模块路径>
git commit -m "更新子模块版本"
```


## 子模块的日常维护
拉取子模块最新代码：
```py
git submodule foreach git pull origin master  # 所有子模块拉取 master 分支
```

批量操作所有子模块
```py
git submodule foreach --recursive 'git checkout main'  # 所有子模块切到 main 分支
```
