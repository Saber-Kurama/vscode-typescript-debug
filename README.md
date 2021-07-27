# vscode-typescript-debug
vscode调试 ts方式

## 参考文章


### tasks.json和launch.json

[如何使用 VS Code 调试 TypeScript](https://pkief.medium.com/how-to-debug-typescript-with-vs-code-9cec93b4ae56)

#### launch.json

```
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "pwa-node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "program": "${workspaceFolder}/src/app.ts",
      "preLaunchTask": "npm: build",
      "sourceMaps": true,
      "smartStep": true,
      "outFiles": [
        "${workspaceFolder}/out/**/*.js"
      ]
    }
  ]
}
```

[使用VSCode的Task自动编译和调试Typescript项目](https://juejin.cn/post/6869196721734778887#heading-4)

```
{
	"tasks": [
		{
			"type": "typescript",
			"tsconfig": "tsconfig.json",
			"problemMatcher": [
				"$tsc"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"label": "tsc: 构建 - tsconfig.json"
		}
	]
}
```

### ts-node 方式

直接在 `JavaScript Debug Terminal` 的控制台中

```
node file.js // 可以调试js
ts-node src/app.ts
```

在 launch.json 中配置

```
{
  "type": "node",
  "request": "launch",
  "name": "ts-node",
  "runtimeArgs": [
    "-r",
    "ts-node/register"
  ],
  "args": [
    "${workspaceFolder}/src/app.ts"
  ]
}
```

直接在 `JavaScript Debug Terminal` 的控制台中 调试最为方便

一些问题
`TS6133: 'saber' is declared but its value is never read.`

```
  tsconfig 
  {
    "noUnusedLocals": true, // 修改成false
  }

```
`(node:20769) Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.`

```
  tsconfig 
  {
    "module": "esnext", // esnext 修改 CommonJS 或者注释掉
  }

ts-node 找不到 声明文件

```

```

[将 ts-node 与全局类型一起使用](https://blakewilliams.me/posts/using-ts-node-with-global-types)