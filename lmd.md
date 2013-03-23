# LMD: Lazy Module Declaration [![Build Status](https://secure.travis-ci.org/azproduction/lmd.png?branch=master)](http://travis-ci.org/azproduction/lmd)

Большие JavaScript-приложения порождают огромную задержку при запуске. 1 Мб JavaScript-кода требует ~300-6000ms!, не затрагивая DOM. LMD выполняет модуль, только когда он будет запрошен. Данная библиотека предоставляет интерфейс модулей, схожий с AMD.

## Почему LMD? Почему не AMD (RequireJS)?

 - Дизайн модулей похож на Node.JS
   - На самом деле, LMD может работать с любыми JavaScript-модулями
   - Нет обертки для определения модулей!
   - Можно использовать node-модули без грязных приемов вроде `typeof exports ? :`
   - Но также можно использовать и функции-обертки. IIFE? - Отлично!
   - Вы можете использовать строки как строки без каких-либо шаблонных плагинов
   - Вы можете использовать JSON-файлы как объекты
 - Полная и честная изоляция
   - LMD-пакет полностью изолирован от глобальных данных (глобальные функции не могут получить доступ к LMD-пакетам, но LMD может)
   - Модули изолированы от LMD и от других модулей
   - Модули могут быть помещены в "песочницу" (сторонние модули, могут только экспортировать)
   - Плагины изолированы от LMD и от каждого модуля
 - Lazy interpretation and load
   - LMD can load off-package modules (all loaders can do it =)
   - It can interpret(eval) modules when they are required
 - Список зависимостей располагается в отдельном .json файле
   - Ну... Список из двух зависимостей в файлах это еще нормально, но 5+ - головная боль
   - Модуль изолирован от файловой системы
   - Если путь к модулю изменяется, нужно отредактировать всего один файл
   - Можно использовать динамическую загрузку require()
 - Наследование конфигурации
   - Простая настройка разработки, тестирования и продакшн-релизов
 - Наблюдатель построения
   - Наблюдатель определяет изменения в файлах и перестраивает проект
 - Гибкий исходный код
   - Минимальная версия весит всего 288bytes
   - Высоко-оптимизированный код
   - LMD выполняет оптимизацию на этапе построения
 - Встроенные средства анализа кода
   - Its easy to enable believe me!
   - No extra servers or movements are required for off-package modules Code-Coverage
 - Прозрачный кэш localStorage
   - Change config and html a bit and voila!
 - require() is not overloaded
   - Overloaded require is the way to mess in source
   - require.css() for css
   - require.js() for js (non LMD-modules)
   - require.async() for async LMD-modules (objects, strings, modules)
 - More
   - Can load CSS
   - Can work with Node.js and Worker environment


## What's on the board

  * All builders/loaders stuff bla-bla-bla
  * Build Analyzer (1-click code coverage, depends, startup perfomance)

![](images/coverage_package.png)

  * Smart and simple CLI tool

![](images/lmd_cli.png)

  * GUI for LMD (in development)

![](images/lmd_gui_prototype.png)

## Other features

1. Modules are similar to AMD: there is a require, but no define
2. LMD does not create globals
3. LMD is standalone, tiny and flexible (minimal only 288bytes!)
4. Each function-module can be initialized/evaled on demand (`lazy: true`)
5. LMD module is as easy to debug as normal JavaScript file
6. Build system compresses JavaScript files using UglifyJs
7. LMD module can define object via `return` or `module.exports` or `exports` as CommonJS Module
8. Module can be wrapped automatically in builder so you can write your modules as node.js modules
9. Starting from version 1.5.2 LMD can require off-package modules `"async": true`
(see [Asynchronous module require](https://github.com/azproduction/lmd/wiki/Off-package-modules))
10. From version 1.6.0 LMD can cache all in-package modules in localStorage `"cache": true`
(see [Local Storage cache](https://github.com/azproduction/lmd/wiki/LocalStorage-cache))
11. From version 1.6.2 LMD can include off-package css `css: true` and js-files `js: true`(for jsonp, cross-origin JS or non LMD modules)
12. LMD package is possible to run as Web Worker or execute as Node.js script
(see [Web Worker and Node.js](https://github.com/azproduction/lmd/wiki/Workers-and-Node))
13. LMD works in all modern browsers and in older IE
14. LMD can convert non-LMD modules to LMD to use jquery or any other as in-package LMD module
(see [LMD module form third-party modules](https://github.com/azproduction/lmd/wiki/Adopting-modules))
15. LMD can protect your code from 3-party modules (see [Modules sandbox](https://github.com/azproduction/lmd/wiki/Module-sandbox))
16. Code Coverage? - Easy! (see [Code coverage](https://github.com/azproduction/lmd/wiki/Analytics-and-Code-coverage))
17. Ready for production - `lmd.js` is 100% covered by unit tests see [test/README.md](test) for details
18. SourceMap for all LMD modules (see [Source map](https://github.com/azproduction/lmd/wiki/SourceMap))
19. Reach CLI interface

## Installing

`npm install lmd -g` global is prefered for LMD CLI comands.

## Getting started with LMD

See [Getting Started](https://github.com/azproduction/lmd/wiki/Getting-started)
and [Wiki](https://github.com/azproduction/lmd/wiki/)

## LMD Config file

**Minimal**

```javascript
{
    "root": "../modules/",
    "output": "../module.lmd.js", // Path are relative to the root parameter
    "modules": {
        "*": "*.js" // use wildcards or specify regex string to grep
    }
}
```

See [LMD Config](https://github.com/azproduction/lmd/wiki/LMD-config) for more information

**Note**

 - You can extend config file with another using `"extends": "path/to/file.lmd.json"` parameter
 - You can also specify module depends by adding `"depends"` options see [Modules dependencies](https://github.com/azproduction/lmd/wiki/Module-dependencies)

## Build LMD package from Console

`lmd build your_buiild_name`

See [LMD CLI](https://github.com/azproduction/lmd/wiki/CLI)

## Grunt integration and task

Install this grunt plugin next to your project's [grunt.js gruntfile](https://github.com/gruntjs/grunt/wiki/Getting-started) with: `npm install grunt-lmd`

Then add this line to your project's `grunt.js` gruntfile:

```javascript
grunt.loadNpmTasks('grunt-lmd');
```

See [grunt-lmd](https://github.com/azproduction/grunt-lmd) for details

## LMD Plugins

### Off-package LMD module loader

  * `async` - Provides `require.async()` function. if modules uses off-package module set this to true. See [demo](http://lmdjs.org/examples/plugins/async/), [code](examples/plugins/async/)
  * `async_plain` - enables async require of both plain and function-modules
  * `async_plainonly` - if you are using only plain modules enable that flag instead of `async_plain`. See [demo](http://lmdjs.org/examples/plugins/async_plainonly/), [code](examples/plugins/async_plainonly/)
  * `preload` - this plugins is simmilar to `async`, it only caches modules without executing them. See [demo](http://lmdjs.org/examples/plugins/preload/), [code](examples/plugins/preload/)
  * `preload_plain` - same as `async_plain`
  * `async_plainonly` - same as `async_plainonly`

### Cache

  * `cache` - stores all application lmd itself + all modules in localStorage this flag will force all modules to be lazy. See [demo](http://lmdjs.org/examples/plugins/cache/), [code](examples/plugins/cache/)
  * `cache_async` - enables localStorage cache for `require.async()`. See [demo](http://lmdjs.org/examples/plugins/cache_async/), [code](examples/plugins/cache_async/)

### Non-LMD modules loader

  * `js` - if you are going to load non LMD javascript modules `require.js()` set this flag to true. See [demo](http://lmdjs.org/examples/plugins/js/), [code](examples/plugins/js/)
  * `css` - enables css-loader feature `require.css()`. See [demo](http://lmdjs.org/examples/plugins/css/), [code](examples/plugins/css/)
  * `image` - enables image-loader feature `require.image()`. See [demo](http://lmdjs.org/examples/plugins/image/), [code](examples/plugins/image/)

### Environment optimization

  * `worker` - set true if LMD package will run as worker
  * `node` - set true if LMD package will run as Node.js script. See [demo](http://lmdjs.org/examples/plugins/node/), [code](examples/plugins/node/)
  * `ie` - **enabled by default** set false if script will run only in modern browsers
  * `opera_mobile` - set true if LMD package will run in Opera Mobile
  * `file_protocol` - set to true if LMD package itself or it parts will be loaded using `file://` protocol

### Loaders (async, js, css, image) features and optimizations

  * `race` - set true if you are performing simultaneous loading of the same resources
  * `parallel` - enables simultaneous loading `require.js([a, b, c], ..)` resources will be executed in load order! And passed to callback in list order. See [demo](http://lmdjs.org/examples/plugins/parallel/), [code](examples/plugins/parallel/)
  * `promise` - enables promise interface for all loaders `require.js('a.js').then()`. See [demo](http://lmdjs.org/examples/plugins/promise/), [code](examples/plugins/promise/)

### Extra module types

  * `shortcuts` - enables shortcuts in LMD package. See [demo](http://lmdjs.org/examples/plugins/promise/), [code](examples/plugins/promise/) (promise example uses shortcuts)
  * `amd` - enables AMD RequreJS modules in LMD package. See [demo](http://lmdjs.org/examples/plugins/amd/), [code](examples/plugins/amd/)

### Stats and Code coverage

  * `stats` - enables `require.stats()` function - every module require, load, eval, call statistics. See [demo](http://lmdjs.org/examples/plugins/stats/), [code](examples/plugins/stats/)
  * `stats_coverage` - enables code coverage for all in-package modules, you can use list of module names to cover only modules in that list. See [demo](http://lmdjs.org/examples/plugins/stats_coverage/), [code](examples/plugins/stats_coverage/)
  * `stats_coverage_async` - enables code coverage for all off-package function-modules for that option you can NOT use list of off-package module names. This options is VERY HEAVY +50Kb sources. Each async LMD module will be parsed and patched on the client - it may take A LOT of time
  * `stats_sendto` - enables `require.stats.sendTo(host[, reportName])` function. It POSTs stats&coverage report to specified stats server

## Special features

  * glob - you can specify glob pattern (eg `"${name}": "js/*.js"`) to match multiply files. See [demo](http://lmdjs.org/examples/features/glob/), [code](examples/features/glob/)
  * interpolation - you can use templates in your config string values to make your life easier. See [demo](http://lmdjs.org/examples/features/interpolation/), [code](examples/features/interpolation/)
  * sandbox - some of your modules can be in the "sandbox". They cant require, but can provide some resources. See [demo](http://lmdjs.org/examples/features/sandbox/), [code](examples/features/sandbox/)
  * optimize - optimisations of LMD source(not your project files) without minification/packing. See Optimisations section of [LMD Plugins overview](https://github.com/azproduction/lmd/wiki/LMD-Plugins-overview) wiki page. See [demo](http://lmdjs.org/examples/features/optimize/), [code](examples/features/optimize/)
  * adaptation - using any JavaScripts as modules. See Wiki page [Adopting modules](https://github.com/azproduction/lmd/wiki/Adopting-modules). See [demo](http://lmdjs.org/examples/features/adaptation/), [code](examples/features/adaptation/)
  * bundles - a way to split your application into separete parts. See [demo](http://lmdjs.org/examples/features/bundles/), [code](examples/features/bundles/)
  * lmdjs_configs - you can write config files in JavaScript. See [demo](http://lmdjs.org/examples/features/lmdjs_configs/), [code](examples/features/lmdjs_configs/)

## Config extras

  * mixins - you can mix your build configs (eg `lmd build index+ru+dev`) to create your special builds. See [demo](http://lmdjs.org/examples/features/mixins/), [code](examples/features/mixins/)
  * depends - your modules can have own depends. You can notify LMD by adding global "depends" paramenter or specify "depends" for each module. See [demo](http://lmdjs.org/examples/features/depends/), [code](examples/features/depends/)
  * extends - your configs can inherit other configs (eg development extends production). See [demo](http://lmdjs.org/examples/features/extends/), [code](examples/features/extends/)

## Bash/zsh completion

Installation `lmd completion >> ~/.bashrc` (or `~/.zshrc`). Do not forget to restart shell.

**Other ways**

  * You can add `. <(lmd completion)` to your rc file
  * Or, maybe: `lmd completion > /usr/local/etc/bash_completion.d/lmd`

## Running tests

`phantomjs` is required to run test via `npm test` see [test](test) for details

--

LMD is developing with help of [these people](AUTHORS)

If you like LMD - ★ it via `npm star lmd`
