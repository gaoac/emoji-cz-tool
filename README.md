# emoji-cz-tool

#### 写在前面

关于Git，大家想必都很熟悉，因为我们几乎每天都在重复着`git add`、`git commit`、`git push`等命令，自然也就留下很多“痕迹”，如果没有好的规范和工具来约束，可能就会出现以下情况：
![](https://raw.githubusercontent.com/gaoac/images-library/master/blog/git_commit_error.png)

因此，规范和工具的重要性就体现出来了：

> 关于 Git Commit message 的写法规社区有多种，本文采用的的 Angular 规范是目前使用最广的写法，比较合理和系统化，并且有配套的工具。

#### 相关工具：

- [commitizen](https://github.com/commitizen/cz-cli)
- [gitmoji](https://github.com/carloscuesta/gitmoji/)
- [emoji-cz](https://github.com/kevin940726/emoji-cz)

#### 安装

```bash
npm install -g commitizen
# OR
# yarn global add commitizen

npm install -g emoji-cz
# OR
# yarn global add emoji-cz

# set as default adapter globally(全局配置，详细配置见下文)
echo '{ "path": "emoji-cz" }' > ~/.czrc
```

#### 配置

emoji-cz 官方例子内容：

```javascript
{
  "path": "emoji-cz",  // 指定commitizen使用的adapter（使用该适配器后，无法生成changelog,故若需要自动生成changelog，可以选择选择conventional-changelog）
  "emoji-cz": {
      // Overwrite types prompted to the command line.
      "types": {
        "Fix": {
          "emoji": "🐝", // overwrite "Fix" emoji to a bee
          "name": "Bug", // overwrite "Fix" name to "Bug"
          "description": "Dirty bug" // overwrite description of "Fix"
        },
        // add a new type "Chore"
        "Chore": {
          "emoji": "❓",
          "description": "Other changes that don't modify src or test files"
        }
      },

      // Overwrite the output commit subject in the specified format.
      // Below is the default format,
      // [emoji] will be replace with the chose type's emoji,
      // [name] will be replace with the chose type's name,
      // [subject] will be replace with the subject you entered.
      // One example output of the format can be: `✨ Feat: initial commit`
      "format": "[emoji] [name]: [subject]"
    }
}

```

(可参考[emoji-cz-tool](https://github.com/gaoac/emoji-cz-tool)仓库中`.cz.json`文件已按照 gitmoji 补全，可直接使用)

##### 全局配置

编辑 ~/.czrc 文件（内容如`.cz.json`文件）

##### 项目配置

在项目根目录创建`.cz.json`文件

#### 使用

以后，凡是用到 git commit 命令，一律改为使用 git cz。这时，就会出现选项，用来生成符合格式的 Commit message（commitizen 与 emoji 结合）。如图：

```bash
? Select the type of change that you're committing: (Use arrow keys)
❯ ✨  Feat:                   A new feature
  🐛  Fix:                    A bug fix
  📝  Docs:                   Documentation only changes
  🎨  Style:                  Changes that do not affect the meaning of the code
  🔨  Refactor:               A code change that neither fixes a bug nor adds a feature
  🚀  Perf:                   A code change that improves performance
  ✅  Test:                   Adding tests.
```

再看提交记录，是不是赏心悦目多了：

![](https://raw.githubusercontent.com/gaoac/images-library/master/blog/git_commit_normal.png)