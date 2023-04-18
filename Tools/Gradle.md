# Gradle 常見配置與使用情境

## 管理套件版本

```groovy
dependencies {
    // 指定套件版本
    implementation 'com.example:library:1.0.0'
    // 動態版本
    // 使用 1.x 最新版
    implementation 'com.example:library:1.+'
    // 使用 1.0.x 任意版本號
    implementation 'com.example:library:1.0.*'
    // 尋找大於等於 1.0.0，小於不等於 2.0.0 的版本號
    implementation 'com.example:library:[1.0.0,2.0.0)'
    // 停用相依套件的傳遞，只使用直接相依，不使用間接相依
    implementation('com.example:example:1.0') {
        transitive = false
    }
    // 全域停用相依套件傳遞
    configurations.all {
        transitive = false
    }
    // 排除特定套件群組(命名空間)和套件模組(名稱)
    implementation('com.example:example:1.0') {
        exclude group: 'org.unwanted', module: 'unwanted-dependency'
    }
    // 強制使用特定版本
    implementation('com.example:example-library') {
        force = true
        version {
            strictly '1.0.0'
        }
    }
    // 全域強制使用特定版本
    configurations.all {
        resolutionStrategy {
            force 'com.example:example-library:1.0.0'
        }
    }

}
```
