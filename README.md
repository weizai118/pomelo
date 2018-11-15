## Pomelo -- a fast, scalable game server framework for node.js

Pomelo is a fast, scalable game server framework for [node.js](http://nodejs.org).
It provides the basic development framework and many related components, including libraries and tools.
Pomelo is also suitable for real-time web applications; its distributed architecture makes pomelo scale better than other real-time web frameworks.

[![Build Status](https://travis-ci.org/NetEase/pomelo.svg?branch=master)](https://travis-ci.org/NetEase/pomelo)

 * Homepage: <http://pomelo.netease.com/>
 * Mailing list: <https://groups.google.com/group/pomelo>
 * Documentation: <http://github.com/NetEase/pomelo>
 * Wiki: <https://github.com/NetEase/pomelo/wiki/>
 * Issues: <https://github.com/NetEase/pomelo/issues/>
 * Tags: game, nodejs


## Features

### Complete support of game server and realtime application server architecture

* Multiple-player game: mobile, social, web, MMO rpg(middle size)
* Realtime application: chat,  message push, etc.

### Fast, scalable

* Distributed (multi-process) architecture, can be easily scale up
* Flexible server extension
* Full performance optimization and test

### Easy

* Simple API: request, response, broadcast, etc.
* Lightweight: high development efficiency based on node.js
* Convention over configuration: almost zero config

### Powerful

* Many clients support, including javascript, flash, android, iOS, cocos2d-x, C
* Many libraries and tools, including command line tool, admin tool, performance test tool, AI, path finding etc.
* Good reference materials: full docs, many examples and [an open-source MMO RPG demo](https://github.com/NetEase/pomelo/wiki/Introduction-to--Lord-of-Pomelo)

### Extensible

* Support plugin architecture, easy to add new features through plugins. We also provide many plugins like online status, master high availability.
* Custom features, users can define their own network protocol, custom components very easy.

## Why should I use pomelo?
Fast, scalable, real-time game server development is not an easy job, and a good container or framework can reduce its complexity.
Unfortunately, unlike web, finding a game server framework solution is difficult, especially an open source solution. Pomelo fills this gap, providing a full solution for building game server frameworks.
Pomelo has the following advantages:
* The architecture is scalable. It uses a multi-process, single thread runtime architecture, which has been proven in the industry and is especially suited to the node.js thread model.
* Easy to use, the development model is quite similar to web, using convention over configuration, with almost zero config. The [API](http://pomelo.netease.com/api.html) is also easy to use.
* The framework is extensible. Based on the node.js micro module principle, the core of pomelo is small. All of the components, libraries and tools are individual npm modules, and anyone can create their own module to extend the framework.
* The reference materials and documentation are quite complete. In addition to the documentation, we also provide [an open-source MMO RPG demo](https://github.com/NetEase/pomelo/wiki/Introduction-to--Lord-of-Pomelo) (HTML5 client), which is a far better reference material than any book.

## How can I develop with pomelo?
With the following references, you can quickly familiarize yourself with the pomelo development process:
* [Pomelo documents](https://github.com/NetEase/pomelo/wiki)
* [Getting started](https://github.com/NetEase/pomelo/wiki/Welcome-to-Pomelo)
* [Tutorial](https://github.com/NetEase/pomelo/wiki/Preface)


## Contributors
* NetEase, Inc. (@NetEase)
* Peter Johnson(@missinglink)
* Aaron Yoshitake 
* @D-Deo 
* Eduard Gotwig
* Eric Muyser(@stokegames)
* @GeforceLee
* Harold Jiang(@jzsues)
* @ETiV
* [kaisatec](https://github.com/kaisatec)
* [roytan883](https://github.com/roytan883)
* [wuxian](https://github.com/wuxian)
* [zxc122333](https://github.com/zxc122333)
* [newebug](https://github.com/newebug)
* [jiangzhuo](https://github.com/jiangzhuo)
* [youxiachai](https://github.com/youxiachai)
* [qiankanglai](https://github.com/qiankanglai)
* [xieren58](https://github.com/xieren58)
* [prim](https://github.com/prim)
* [Akaleth](https://github.com/Akaleth)
* [pipi32167](https://github.com/pipi32167)
* [ljhsai](https://github.com/ljhsai)
* [zhanghaojie](https://github.com/zhanghaojie)
* [airandfingers](https://github.com/airandfingers)

## License

(The MIT License)

Copyright (c) 2012-2017 NetEase, Inc. and other contributors

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
Pomelo 详细介绍
pomelo 是由网易开发的基于node.js开发的高性能、分布式游戏服务器框架， 也可作为高实时web应用框架。

Pomelo

Pomelo的应用范围

pomelo最适合的应用领域是网页游戏、社交游戏、移动游戏的服务端，开发者会发现pomelo可以用如此少的代码达到强大的扩展性和伸缩性。当然还不仅仅是游戏，很多人断言未来的web时代是实时web应用的时代， 我们发现用pomelo开发高实时web应用也如此合适， 而且伸缩性比其它框架好。目前不推荐将pomelo用于大型的MMO rpg游戏开发，尤其是3d游戏， 还是需要象bigworld这样的商用引擎来支撑。

Pomelo的理念

pomelo的第一个理念是让游戏（高实时web应用）服务器的开发变得非常简单， 而不是解决某类算法或系统上的难题。这个设计理念跟rails是很类似的；第二个理念是重视性能和可伸缩性，用户用pomelo开发出来的游戏天生具有很强的伸缩性，扩展也很容易。我们在性能优化上也花了很多功夫，并且会持续进行；第三个理念是让第三方很容易扩展，框架用了很多插件式的设计， 组件component、路由规则、甚至管理控制台都可以完全由第三方扩展。

 

Pomelo的框架组成

pomelo包括三部分:

框架, pomelo的核心, 与以往单进程的游戏框架不同, 它是高性能、分布式的游戏服务器框架，并且使用很简单

库, 包括了开发游戏的常用工具库， 如人工智能(ai), 寻路， aoi等

工具包, 包括管理控制台, 命令行工具, 压力测试工具等

pomelo特性

快速、易上手的游戏开发模型和api

高可伸缩的多进程架构， 支持MMO的场景分区和其它各类分区策略

方便的服务器扩展机制，可快速扩展服务器类型和数量

方便的请求、响应、广播、服务器通讯机制， 无需任何配置

注重性能，在性能、可伸缩性上做了大量的测试、优化

提供了较多扩展组件，包括游戏开发常用的库和工具包

提供了完整的MMO demo代码(客户端html5)，可以作为很好的开发参考

基于socket.io开发，支持socket.io支持的多种语言客户端

为什么使用pomelo？

高并发、高实时的游戏服务器的开发是很复杂的工作。跟web应用一样， 一个好的开源容器或开发框架可以大大减少游戏开发的复杂性，让开发变得更加容易。
遗憾的是目前在游戏服务器开发领域一直没有太好的开源解决方案。 pomelo将填补这个空白， 打造一款完全开源的高性能（并发）游戏服务器框架。 pomelo的优势有以下几点：

架构的可伸缩性好。 采用多进程单线程的运行架构，扩展服务器非常方便， node.js的网络io优势提供了高可伸缩性。

使用非常容易， 开发模型与web应用的开发类似，基于convention over configuration的理念， 几乎零配置， api的设计也很精简， 很容易上手。

框架的松耦合和可扩展性好， 遵循node.js微模块的原则， framework本身只有很少的代码，所有component、库、工具都可以用npm module的形式扩展进来。任何第三方都可以根据自己的需要开发自定义module。

提供完整的开源MMO游戏demo参考(基于HTML 5)。 一个超过1万行代码的游戏demo，使开发者可以随时借鉴demo的设计与开发思路。

在线演示：http://pomelo.netease.com/demo.html
