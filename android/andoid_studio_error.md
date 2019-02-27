# Andoid Studio 常见问题

### 错误 ```:transformClassesWithExtractJarsForDebug```

- 错误详情

```
org.gradle.api.tasks.TaskExecutionException: Execution failed for task ':transformClassesWithExtractJarsForDebug'.
```

```
Unexpected scopes found in folder 'build/intermediates/transforms/InjectTransform/debug'. Required: SUB_PROJECTS. Found: EXTERNAL_LIBRARIES, PROJECT, SUB_PROJECTS
```

- 解决方案

```
关掉 instant run
```

## 参考资料

- [Android Studio常见错误集](http://xyzlf.cn/2017/04/10/android-studio-error.html)
