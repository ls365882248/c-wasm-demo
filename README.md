# C to WASM


brew install gcc

brew install mingw-w64

brew install emscripten

create a C file

emcc helloworld.c -o helloworld.html -s NO_EXIT_RUNTIME=0

## Module
编译的 html 里面有一个 **Module** 定义，实际(maybe)是实现了 **emscripten** 的 Module object

```js
var Module = {
  preRun: [],
  postRun: [],
  print: () => {},
  printErr: () => {},
  canvas: () => {},
  setStatus: () => {},
  totalDependencies: 0,
  monitorRunDependencies: () => {}
};
```

emscripten
```js
var Module = {
  'print': function(text) { alert('stdout: ' + text) },
  'printErr': function(text) { alert('stderr: ' + text) },
  // --snip--
};
```

https://emscripten.org/docs/api_reference/module.html