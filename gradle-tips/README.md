# Gradle技巧

## 一、常用命令

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

### 查看properties

```
$ gradle -q properties
```

### 查看task间依赖关系

```
$ gradle dependencies
```


### 查看项目的gradle详细报告

```
$ gradle build --scan
```

### 查看某个依赖库(如commons-logging)的详细信息

```
$ gradle dependencyInsight --dependency commons-logging
```

## 二、常见问题

### 2.1 代理开关

问题现象：依赖解析失败

```
$ gradle --refresh-dependencies

> Could not resolve all files for configuration ':compile'.
   > Could not find commons-io:commons-io:2.5.
     Searched in the following locations:
       - https://repo.maven.apache.org/maven2/commons-io/commons-io/2.5/commons-io-2.5.pom
       - https://repo.maven.apache.org/maven2/commons-io/commons-io/2.5/commons-io-2.5.jar
     Required by:
         project :
```

查看debug信息，发现是代理g.cn导致https连接被拒

```
$ gradle --debug --refresh-dependencies
[DEBUG] [org.apache.http.impl.execchain.MainClientExec] Opening connection {tls}->http://g.cn:80->https://repo.maven.apache.org:443
[DEBUG] [org.apache.http.impl.execchain.MainClientExec] CONNECT refused by proxy: HTTP/1.1 404 Not Found
[DEBUG] [org.apache.http.impl.execchain.MainClientExec] Connection discarded
```

解决方法：关掉g.cn代理

```
$ cat ~/.gradle/gradle.properties
#systemProp.https.proxyPort=80
#systemProp.http.proxyHost=g.cn
#systemProp.https.proxyHost=g.cn
#systemProp.http.proxyPort=80
```
### 2.2 Gradle运行速度慢

问题现象：Gradle从maven仓库或jcenter仓库下载依赖速度很慢

解决方法：使用阿里云的jcenter镜像

```
$ cat build.gradle
repositories {
	jcenter { url 'https://maven.aliyun.com/repository/jcenter' }
	jcenter()
	maven { url 'https://maven.aliyun.com/repository/apache-snapshots' }
	maven { url 'https://maven.aliyun.com/repository/central' }
	mavenCentral()
}
```

## 三、参考文档

- [Command-Line Interface](https://docs.gradle.org/current/userguide/command_line_interface.html)
- [Gradle DSL Reference](https://docs.gradle.org/current/dsl/)
- [Search Gradle Plugins](https://plugins.gradle.org/)
- [Search Gradle Dependency Libs](https://mvnrepository.com/)
- [Android Gradle plugin](https://developer.android.com/studio/releases/gradle-plugin)

