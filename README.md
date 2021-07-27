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



