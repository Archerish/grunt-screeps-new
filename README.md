[![npm version](https://badge.fury.io/js/grunt-screeps.svg)](https://badge.fury.io/js/grunt-screeps)

# grunt-screeps-new

> 一个支持Token登陆的用于提交Screeps代码的Grunt插件（非官方）

本插件是基于官方插件 [grunt-screeps](https://github.com/screeps/grunt-screeps) 以及 [gdborton](https://github.com/gdborton) 和 [dbe](https://github.com/dbe) 的提交完成的

## Getting Started
如果你没有使用过 [Grunt](https://www.gruntjs.net/) , 请查看官方的教程 [快速入门](https://www.gruntjs.net/getting-started), 了解关于创建 [Gruntfile](https://www.gruntjs.net/sample-gruntfile) 和使用Grunt插件的相关知识. 熟悉了相关知识后，可以通过如下命令安装本插件：

```shell
npm install grunt-screeps-new 
```

### Usage Example

**Gruntfile.js:**
```js
module.exports = function(grunt) {

    grunt.loadNpmTasks('grunt-screeps');

    grunt.initConfig({
        screeps: {
            options: {
                // 通过host设置服务器地址，默认官服
                host: 'screeps.com',
                // 通过accountAlias设置账户昵称
                accountAlias: 'LABEL_FOR_THIS_ACCOUNT',
                branch: 'default',
                ptr: false,
                // 注意：Token登陆为可选项，有Token的情况下优先使用Token登陆
                // Token登陆只能用于官服，无法应用于私服
                token: 'YOUR_AUTH_TOKEN',
                // email/password 登陆方式用于私服.
                email: 'YOUR_EMAIL',
                password: 'YOUR_PASSWORD',
                // 通过branch设置提交分支，默认main分支
                branch: 'main'
            },
            dist: {
                files: [
                    {
                        expand: true,
                        cwd: 'dist/',
                        src: ['**/*.{js,wasm}'],
                        flatten: true
                    }
                ]
            }
        }
    });
}
```

配置完成后可以用以下命令来提交disk目录下的代码：
```
grunt screeps
```

如果想要了解更多第三方提交的相关知识，请查看Screeps官方的 [文档](http://docs.screeps.com/contributed/advanced_grunt.html).