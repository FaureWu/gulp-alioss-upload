# ALI OSS UPLOAD

用于上传到阿里云oss服务器的gulp插件

## 安装

```bash
$ npm install --dev gulp-alioss-upload
```
or
```bash
$ yarn add -dev gulp-alioss-upload
```

## 使用方法

在gulp配置文件gulpfile.js中新增task任务

```js
const gulp = require('gulp')
const oss = require('gulp-alioss-upload')

gulp.task('upload:oss', function() {
  const options = {
    accessKeyId: "**************",
    accessKeySecret: "*************",
    endpoint: "https://***********.aliyuncs.com",
    region: "***********",
    bucket: "*********",
    path: "src/assets/",
    formats: ['png', 'jpeg', 'jpg', 'svg'],
    prefix: "@oss",
  }
  return gulp.src(['src/**/*.js', 'src/**/*.css'])
    .pipe(oss(options))
    .pipe(gulp.dest('./dist/'))
})
```

## 使用方法

在监听的文件中，比如我们需要引入图片资源，且希望能上传到oss，图片路径写成@oss/logo.png即可

## 参数介绍
* accessKeyId 必填 阿里云oss key
* accessKeySecret 必填 阿里云oss secret
* endpoint 必填 阿里云oss服务器地址
* region 必填 阿里云oss region
* bucket 必填 阿里云oss bucket
* path 选填 默认值/ 需要上传的资源根路径
* formats 选填 默认值['png', 'jpg', 'jpeg', 'svg', 'bmp', 'gif', 'webp', 'tiff'] 可上传的资源格式
* prefix 选填 默认值@oss 以此为开头的资源引用会被上传到阿里云oss并替换地址
