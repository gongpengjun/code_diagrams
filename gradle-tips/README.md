# Gradle技巧

### 查看有哪些projects

```
$ gradle projects
```

### 查看有哪些tasks

```
$ gradle tasks --all
```

查看某个子project(如sub-project1)的tasks

```
$ gradle :sub-project1:tasks --all
```

### 查看某个task(如compileJava)的详细信息

```
$ gradle -q help --task compileJava
```

### 查看项目的gradle详细报告

```
$ gradle build --scan
```
