------

title: Git 操作手册
category: Git

------

## 分支

#### 创建分支

```
// 创建分支
git branch <name>

// 创建并切换到新的分支
git checkout -b <name>

// 创建远程分支
git push origin <name>

```

#### 查看分支

```
// 查看本地分支
git branch

// 查看远程分支
git branch -r

```

#### 删除分支

```
// 删除本地分支
git branch -d <name> 

// 强制删除本地分支
git branch -D <name>

// 删除远程分支
git push origin :<name>
```

## Tag

#### 增加tag

```
// 增加本地tag
git tag <tagname>

```

#### 查看tag

```
git tag -l
```

#### 删除tag

```
// 删除本地tag
git tag -d <tagname>

// 删除远程tag
git push origin :<tagname>
```