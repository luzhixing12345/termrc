# dotfiles

## 简介

非 terminal 深度用户, 简单同步配置一下基础环境

文档: [dotfiles document](https://luzhixing12345.github.io/dotfiles/)

## 安装

```bash
./install.sh
```

## 其他

### 初始化 ssh 的 key

> 因为 `authorized_keys` 总是打不对

```bash
wget -O - https://raw.githubusercontent.com/luzhixing12345/dotfiles/main/scripts/ssh.sh | sudo bash 
```

### ssh

```bash
ssh-keygen -t rsa -C "luzhixing12345@163.com"
cat ~/.ssh/id_rsa.pub
```

```bash
ssh -T git@github.com
```

clangd settings

```json
{
    "clangd.fallbackFlags": [
        "-I${workspaceFolder}/include"
    ],
    "clangd.arguments": [
        "--background-index", // 在后台自动分析文件(基于complie_commands)
        "-j=12", // 同时开启的任务数量
        "--clang-tidy", // clang-tidy功能
        "--clang-tidy-checks=performance-*,bugprone-*",
        "--all-scopes-completion", // 全局补全(会自动补充头文件)
        "--completion-style=detailed", // 更详细的补全内容
        "--header-insertion=iwyu" // 补充头文件的形式
    ]
}
```

[.clang-format](./.clang-format)

```bash
BasedOnStyle: Google
IndentWidth: 4
AllowShortFunctionsOnASingleLine: None
AllowShortBlocksOnASingleLine: Never
AllowShortIfStatementsOnASingleLine: false
ColumnLimit: 120
BinPackArguments: false
BraceWrapping:
  AfterStruct: true
  AfterFunction: true
  AfterClass: true
  AfterControlStatement: true
  SplitEmptyFunction: false
  SplitEmptyRecord: false
  SplitEmptyNamespace: false
  BeforeCatch: true
  BeforeElse: true
  IndentBraces: true
```

[launch.json](./.vscode/launch.json)

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "debug",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/src/ls",
            "args": ["/home/kamilu/"],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "将反汇编风格设置为 Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

## 参考

- [vim color](https://vim.fandom.com/wiki/Xterm256_color_names_for_console_Vim)
- [color](https://www.ditig.com/256-colors-cheat-sheet)
