# Peony 文件管理器预览特性的实现

[English] | 简体中文

[English]: ../en_US/Implementation&#32;of&#32;the&#32;Peony&#32;File&#32;Manager&#32;preview&#32;feature.md

## 源项目简介

[Peony] 文件管理器是 UKUI 桌面环境的默认文件管理器，它可以很容易的管理、操作和修改文件和目录。它基于 GIO 和 Qt 构建了一套接口，并具有其自己插件机制。

[Peony]: https://github.com/ukui/peony

## 项目介绍

本项目的主旨是为 Peony 文件管理器提供文件预览特性的支持与实现，使其能够在右侧预览窗体中对不同类型的文件支持文件内容的预览。

  * 对于文本类型的文件，比如 PDF、txt 等，支持简单的编辑功能；
  * 对于图片类型文件，比如 PNG、JPEG 等，支持简单的方向、大小调整的编辑功能；
  * 对于视频、音频类型的文件，支持快速的播放预览；
  * 对于压缩文件类型文件，支持对其包含内容的预览；
  
## 技术要求

**必要**

  - C++，基础
  - 数据结构，基础

**可选**

  - Qt5,基础

## 特性检查表

  * [ ] 文本文件预览和编辑
    
    | 文件类型              | MIME type                                                               | 预览支持 | 编辑支持 |
    |-----------------------|-------------------------------------------------------------------------|:--------:|:--------:|
    | 文本文件              | text/plain                                                              | &#9744;  | &#9744;  |
    | PDF                   | application/pdf                                                         | &#9744;  | &#9744;  |
    | doc 文件              | application/msword                                                      | &#9744;  | &#9744;  |
    | docx 文件             | application/vnd.openxmlformats-officedocument.wordprocessingml.document | &#9744;  | &#9744;  |
    | OpenDocument 文件     | application/vnd.oasis.opendocument.text                                 | &#9744;  | &#9744;  |
    | CSV 文件              | text/csv                                                                | &#9744;  | &#9744;  |
    | JSON 文件             | application/json                                                        | &#9744;  | &#9744;  |
    | HTML 文件             | text/html                                                               | &#9744;  | &#9744;  |
    | JavaScript 源代码文件 | text/javascript                                                         | &#9744;  | &#9744;  |
    | PHP 源代码文件        | application/x-httpd-php                                                 | &#9744;  | &#9744;  |
    | 富文本文件            | application/rtf                                                         | &#9744;  | &#9744;  |
    | shell 脚本            | application/x-sh                                                        | &#9744;  | &#9744;  |
    
  * [ ] 图像文件预览和编辑
  
    | 文件类型  | MIME type                | 预览支持 | 大小编辑支持 | 旋转支持编辑 |
    |-----------|--------------------------|:--------:|:------------:|:------------:|
    | icon 文件 | image/vnd.microsoft.icon | &#9744;  | &#9744;      | &#9744;      |
    | JPEG 图片 | image/jpeg               | &#9744;  | &#9744;      | &#9744;      |
    | PNG 图片  | image/png                | &#9744;  | &#9744;      | &#9744;      |
    | SVG 图片  | image/svg+xml            | &#9744;  | &#9744;      | &#9744;      |
    | WEBP 图片 | image/webp               | &#9744;  | &#9744;      | &#9744;      |
  
  * [ ] 音视频文件预览
  
    | File type     | MIME type         | Preview Support |
    |---------------|-------------------|:---------------:|
    | aac 音频文件  | audio/aac         | &#9744;         |
    | MP3 音频文件  | audio/mpeg        | &#9744;         |
    | CD 音频文件   | application/x-cdf | &#9744;         |
    | OGG 音频文件  | audio/ogg         | &#9744;         |
    | Opus 音频文件 | audio/opus        | &#9744;         |
    | wav 音频文件  | audio/wav         | &#9744;         |
    | WEBM 音频文件 | audio/webm        | &#9744;         |
    | AVI 视频文件  | video/x-msvideo   | &#9744;         |
    | MP4 视频文件  | video/mp4         | &#9744;         |
    | MPEG 视频文件 | video/mpeg        | &#9744;         |
    | OGG 视频文件  | video/ogg         | &#9744;         |
    | WEBM 视频文件 | video/webm        | &#9744;         |
  
  * [ ] 压缩文件预览
    
    | 文件类型   | MIME type           | 预览支持 |
    |------------|---------------------|:--------:|
    | BZ 压缩包  | application/x-bzip  | &#9744;  |
    | BZ2 压缩包 | application/x-bzip2 | &#9744;  |
    | GZ 压缩包  | application/gzip    | &#9744;  |
    | RAR 压缩包 | application/vnd.rar | &#9744;  |
    | TAR 压缩包 | application/x-tar   | &#9744;  |
    | ZIP 压缩包 | application/zip     | &#9744;  |

## 开发计划

待定

## 联系

  * 导师：[Yue Lan], [邮件联系他]

[Yue Lan]: https://github.com/Yue-Lan
[邮件联系他]: mailto:lanyue@kylinos.cn

## 授权条款

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

本文使用授权协议 [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/)。
