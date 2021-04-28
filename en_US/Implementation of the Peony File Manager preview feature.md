# Implementation of Peony File Manager preview feature

English | [简体中文]

[简体中文]: ../zh_CN/Peony&#32;文件管理器预览特性的实现.md

## Origin Project

[Peony] is the default file manager for the UKUI Desktop Environment. It makes it easy to manage, manipulate, and customize files and directories.  It has a set of interfaces based on GIO and Qt and has its own plugin mechanism.

[Peony]: https://github.com/ukui/peony

## Project description

The  purpose of this project is to provide support and implementation of file preview features for Peony File Manager, which allows it to support preview of file content for different types of files in the right preview panel.

  * For text type files, such as PDF, txt, etc.  Support simple editing functions.
  * For image type files, such as PNG, JPEG, etc. Support simple editing functions of orientation and resizing.
  * For video and audio type files, support a quick glimpse of playback.
  * For compressed archive type files, such as GZ, ZIP, etc. Support show the files it contains.

## Technical Requirements

**Required**

  * C++, basic
  * Data structure, basic
  
**Optional**

  * Qt5, basic
  * ECMAScript, basic

## Technical Keywords

**Text Data Parser**, **Audio/Video frame process**, **XML Parser**, **ffmpeg**

## Technical Details

The technical focus of the File Manager preview feature is on the breadth of file type support and preview performance.

The breadth of file type support requires special parsing and processing of some of them due to the large number of file types and different data formats in modern operating systems. For performance issues, since large text and long audio and video are common in file manager scenarios, memory consumption and asynchronous issues need to be taken into account when designing their data parsing.

### Complex format document parsing

For documents like PDF, doc/docx, rtf, we want to implement their preview not as images, but as text data so that their content can be quickly selected and copied. In Peony today, PDFs are previewed by generating images via poppler, and there are many libraries like pdf.js in web browsing services that provide text parsing support for such files. Further, you can consider using the node.js ecosystem combined with Qt WebEngine to further do these tasks.

## Features CheckList

  * [ ] Text preview and edit
  
    | File type                                   | MIME type                                                               | Preview Support | Edit Support |
    |---------------------------------------------|-------------------------------------------------------------------------|:---------------:|:------------:|
    | Text                                        | text/plain                                                              | &#9744;         | &#9744;      |
    | Adobe Portable Document Format              | application/pdf                                                         | &#9744;         | &#9744;      |
    | Microsoft Word                              | application/msword                                                      | &#9744;         | &#9744;      |
    | Microsoft Word (OpenXML)                    | application/vnd.openxmlformats-officedocument.wordprocessingml.document | &#9744;         | &#9744;      |
    | OpenDocument text document                  | application/vnd.oasis.opendocument.text                                 | &#9744;         | &#9744;      |
    | Comma-separated values (CSV)                | text/csv                                                                | &#9744;         | &#9744;      |
    | JSON format                                 | application/json                                                        | &#9744;         | &#9744;      |
    | HyperText Markup Language (HTML)            | text/html                                                               | &#9744;         | &#9744;      |
    | JavaScript                                  | text/javascript                                                         | &#9744;         | &#9744;      |
    | Hypertext Preprocessor (Personal Home Page) | application/x-httpd-php                                                 | &#9744;         | &#9744;      |
    | Rich Text Format (RTF)                      | application/rtf                                                         | &#9744;         | &#9744;      |
    | Bourne shell script                         | application/x-sh                                                        | &#9744;         | &#9744;      |
  
  * [ ] Image preview and edit
      
    | File type                      | MIME type                | Preview Support | Size Edit Support | Rotation Edit Support |
    |--------------------------------|--------------------------|:---------------:|:-----------------:|:---------------------:|
    | Icon format                    | image/vnd.microsoft.icon | &#9744;         | &#9744;           | &#9744;               |
    | JPEG images                    | image/jpeg               | &#9744;         | &#9744;           | &#9744;               |
    | Portable Network Graphics      | image/png                | &#9744;         | &#9744;           | &#9744;               |
    | Scalable Vector Graphics (SVG) | image/svg+xml            | &#9744;         | &#9744;           | &#9744;               |
    | WEBP image                     | image/webp               | &#9744;         | &#9744;           | &#9744;               |

  
  * [ ] Media preview
  
    | File type                   | MIME type         | Preview Support |
    |-----------------------------|-------------------|:---------------:|
    | AAC audio                   | audio/aac         | &#9744;         |
    | MP3 audio                   | audio/mpeg        | &#9744;         |
    | CD audio                    | application/x-cdf | &#9744;         |
    | OGG audio                   | audio/ogg         | &#9744;         |
    | Opus audio                  | audio/opus        | &#9744;         |
    | Waveform Audio Format       | audio/wav         | &#9744;         |
    | WEBM audio                  | audio/webm        | &#9744;         |
    | AVI: Audio Video Interleave | video/x-msvideo   | &#9744;         |
    | MP4 audio                   | video/mp4         | &#9744;         |
    | MPEG Video                  | video/mpeg        | &#9744;         |
    | OGG video                   | video/ogg         | &#9744;         |
    | WEBM video                  | video/webm        | &#9744;         |

  * [ ] Compressed archive preview
  
    | File type               | MIME type           | Preview Support |
    |-------------------------|---------------------|:---------------:|
    | BZip archive            | application/x-bzip  | &#9744;         |
    | BZip2 archive           | application/x-bzip2 | &#9744;         |
    | GZip Compressed Archive | application/gzip    | &#9744;         |
    | RAR archive             | application/vnd.rar | &#9744;         |
    | Tape Archive (TAR)      | application/x-tar   | &#9744;         |
    | ZIP archive             | application/zip     | &#9744;         |

## Development Plan

The current implementation of the plugin is divided into several phases.

### Phase 1

One to two weeks, the implementation of the plugin structure, including graphical windows, abstraction of parsing services, etc.

### Phase 2

Parsing and display of basic text files, such as txt, source code, etc.

### Phase 3

Display preview of images, audio.

### Phase 4

Playback of video frames, quick editing of image size and orientation.

### Phase 5

Text parsing of complex documents.


## Contact

* Mentor: [Yue Lan], [Mail to him]

[Yue Lan]: https://github.com/Yue-Lan
[Mail to him]: mailto:lanyue@kylinos.cn
    
## License

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
