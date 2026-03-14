# auto
此项目自动化相关（涉及到的工具，vscode+cline插件+各种AI的key，下面主要使用了DeepSeek，Gemini等）

------

# 一、生成url.txt url文件

 复制要批量转存和转发生成url的所有文本bbbb，然后进入vs + cline插件中，写下下面这段prompt

@/url.txt  清空原来的文件，把下面这段文本，截取出url，每个URL一行，如果url，没有https:// ，则前面加上，确保url是完整的是合法url，保存到url.txt文件中

------

# 二、执行批量转存工具

1. python python quark.py
2. 按步骤，完成生成批量的转发URL

------

# 三、按⬇️的mcp的prompt，实现github的自动识别分类及仓库提交

----------

## MCP自动判别，资源仓库类别，实现自动化提交及生成相关文件等操作的prompt



注意全程中文交流，获取用户mswnlz存在哪些github仓库，同时先确保先把每个仓库更新到最新版本，然后把mswnlz.github.io仓库也更新到最新代码后然后排除掉，注意下面所有操作都跟这个仓库没关系，先分析这些github仓库的特征及格式到写法，然后判断下面输入的这些文件描述和链接，分别所属的类别，对应到最相关的仓库中，进行修改对应文件及相关操作，完成提交github版本记录
具体要求如下，请严格执行
	1	先更改每条的名字，把每条名字后面增加"-超过100T资料总站网站-doc.869hr.uk"，比如:微信视频号下载工具 (稀有版，无限制)  | https://pan.quark.cn/s/b0db800df5b9,更改为微信视频号下载工具 (稀有版，无限制)-超过100T资料总站网站doc.869hr.uk | https://pan.quark.cn/s/b0db800df5b9
	2	具体操作的仓库名称需要你根据资源名称去判断，放到哪个仓库中，一定是在现有的这些仓库中去找去尽量匹配，如果没有严格匹配的，就相对的匹配，放在相对匹配的库中去操作，不允许新开仓库
	3	我提供的是资源名称和url，需要你先转成markdown格式，并且，每个注意加换行，确保一个资源一行，然后做下面的事情
	4	对应到仓库，首先判断当前年月份有没有对应的文件名， 1）如果没有对应以当前年月命名的md文件，则按年月追加到仓库中，文件名格式比如 2025 年 6月，则 202506.md 2）有的话，则直接修改对应的文件内容，记得先获取文件的sha值（至于怎么获取到，你自己想办法你可以做到的，比如看之前的commit记录中或者其他办法等，反正你好好思考能算出sha值的办法，再执行），然后修改后，提交的时候，需要在json里面填写这个sha值，这是必须的字段，3）如果新建的年月文件，获取不到sha，也能提交的话，那就不用获取sha就行，你自己判断，4）使用 git 命令（如 git ls-tree）在本地仓库获取 SHA，5）另外，把要增加的内容，追加到文件内容的最下面
	5	判断年月md文件在仓库的readme.md文件中有没有索引，没有的话加上年月md的索引，加的位置在readme文件的多语言下面追加，同时，如果已经有其他年月的md索引，要放在原有的年月md前面，这样按时间倒序，新加的年月md在前面，原来的年月md在后面，另外保证进到仓库中，通过readme文件，能点击链接到这个仓库的其他文件中，然后链接名字就叫这个md文件名即可，也就是年月的名字
	6	所有这些格式都按照markdown格式填写到文件中及做文件修改
	7	提交仓库的版本说明中，要填写除去链接外的提交的文本内容，这样能很好知道这次提交的相关详细内容是什么，可以详细一些，不要只是概要的几个字，比如： 微信视频号下载工具 (稀有版，无限制)  | https://pan.quark.cn/s/b0db800df5b9，则删除链接后的提交说明是：增加  微信视频号下载工具 (稀有版，无限制) ，如果仓库提交了多个资源，则增加多个文本，每个文本单独一行即可，都放在提交版本说明中，字数多没关系
	8	提交仓库版本时，因为仓库设定了提交的branchi和提交内容的描述，所以务必，注意每次提交的json格式里面，都要有增加这两个字段，不然提交github会不成功；"message": "更新 README.md 内容", // 新增：提交说明中，要填写除去链接外的提交的文本内容，这样能很好知道这次提交的相关内容是什么 "branch": "main" // 新增：目标分支名
	9	完成所有资源github提交后，运行生成网站的脚本trigger-update.sh，确保这些更新已经网站上生效
	10	确认本地仓库的上面的这些更改，都已经提交到了github仓库版本管理上，先获取最新github版本，如果还有没有提交的完成提交，不要有本地改动没有提交到github上的改动
	11	确保提交到了远程仓库，确保提交到了远程仓库，确保提交到了远程仓库
	12	然后等待 3 分钟，是为了确保网站更新完成，编译工程完成后，刚提交的这些每个条目资源，对应的完整的网页url，输出一下，比如 中医十二经络易堵点自我疏通手法课程：https://doc.869hr.uk/curriculum/202508#中医十二经络易堵点自我疏通手法课程-超过100T资料总站网站-doc869hruk ，这样的格式输出，有了这个完整的list，我就能直接复制，去其他地方转发了


----------

# 四、配置了github workflow action，自动发送更新的资源到TG群组：

![image](https://github.com/user-attachments/assets/33d8cd8d-36ca-451d-a783-3d4362601a6b)


----------

# 五、自动发推


<img width="587" alt="iShot_2025-06-17_09 34 40" src="https://github.com/user-attachments/assets/a5141896-840e-44f2-96c3-ea9b0900c504" />


### 一
安装库：npm install @actions/core twitter-api-v2
工程位置：https://github.com/PLhery/node-twitter-api-v2

### 二
获取推特官方API token：https://developer.x.com/en


------------------
# 六，基于github仓库，做了个网站，https://doc.869hr.uk
<img width="1103" alt="image" src="https://github.com/user-attachments/assets/921f54d6-82b2-4376-8594-cca9ac968d4e" />
并支持搜索
<img width="1091" alt="image" src="https://github.com/user-attachments/assets/500c9118-7366-43da-a6d5-324f69c4ca32" />


---------------

# 七、Skills 自动化工具

## Skills 仓库位置

Skills 存放在两个位置：

1. **主仓库**：`/Users/m./Documents/QNSZ/project/skills/`
   - GitHub：https://github.com/wlzh/skills
   - 包含所有自定义 Skills

2. **OpenClaw Skills**：`~/npm-global/lib/node_modules/openclaw/skills/`
   - OpenClaw 内置 Skills

## quark-mswnlz-publisher Skill

**当前版本**: v1.2.0 (2026-03-14 更新)

**功能**：Quark → mswnlz GitHub → 网站重建 完整自动化流程

**位置**：`/Users/m./Documents/QNSZ/project/skills/quark-mswnlz-publisher/`

### 核心功能

| 功能 | 说明 |
|------|------|
| 夸克批量转存 | 新建批次文件夹 → 批量转存 URL |
| 推广文件复制 | 从 `temp/要共享的文件` 自动复制到每个分享文件夹 |
| 自动生成分享链接 | 永久 + 加密 + 随机提取码 |
| 自动归类 | 根据标题关键词自动归类到对应仓库 |
| Telegram 通知 | 频道单条 + 群组汇总（多仓库只发一条）|
| 站点自动更新 | 触发 mswnlz.github.io 重建 |

### 使用方法

1. **准备推广文件**（一次性）：
   - 在夸克网盘创建 `temp/要共享的文件` 文件夹
   - 上传推广文件（免责声明、解压密码等）

2. **准备输入文件**：
   ```bash
   # 编辑 items.json
   [
     {"title": "资源名称", "url": "https://pan.quark.cn/s/xxx"}
   ]
   ```

3. **执行批量处理**：
   ```bash
   cd /Users/m./Documents/QNSZ/project/QuarkPanTool
   python batch_runner.py
   ```

4. **自动执行**：
   - 复制推广文件到每个文件夹
   - 生成分享链接
   - 归类到对应仓库
   - 提交到 GitHub
   - 发送 Telegram 通知
   - 触发站点重建

### 脚本说明

| 脚本 | 功能 |
|------|------|
| `quark_batch_run.py` | 批量转存 + 生成分享链接 |
| `quark_copy.py` | 复制推广文件 |
| `mswnlz_publish.py` | 发布到 GitHub + 发送 Telegram 通知 |
| `trigger_site_rebuild.sh` | 触发站点重建 |

### 仓库映射

| 资源类型 | 仓库名 |
|---------|--------|
| 书籍/文档 | book |
| 电影/视频 | movies |
| AI 相关 | AIknowledge |
| 教育课程 | curriculum |
| 教育知识 | edu-knowlege |
| 健康养生 | healthy |
| 自媒体 | self-media |
| 跨境电商 | cross-border |
| 传统文化 | chinese-traditional |
| 工具软件 | tools |

## Telegram 通知机制

### 通知配置

| 目标 | 类型 | 发送方式 | 内容 |
|------|------|----------|------|
| @dabaziyuan | 频道 | 每条单独发 | 完整资源信息 + GitHub 链接 |
| tgmShare 话题 5 | 群组 | 汇总消息 | 更新仓库列表 + 频道链接 |
| tgmShareAI 话题 2 | 群组 | 汇总消息 | 更新仓库列表 + 频道链接 |

### GitHub Secrets

| Secret | 值 |
|--------|-----|
| `BOT_TOKEN` | Telegram Bot Token |
| `TELEGRAM_CHANNEL_ID` | `@dabaziyuan` |

### 群组汇总消息格式

```
📝 资源更新

已更新仓库：book、movies、curriculum
共 5 项资源

📦 https://t.me/dabaziyuan
```

## 推广文件

### 夸克网盘位置
`temp/要共享的文件`

### 文件清单

| 文件 | 用途 |
|------|------|
| `必看免责声明-及加入资源分享群...txt` | 免责声明 + 联系方式 + 赚钱教程 |
| `1.【解压密码869hr.uk】-移动端...html` | 移动端解压密码获取页面 |
| `0.【双击获取解压密码】-Mac...webloc` | Mac 快捷方式 |
| `0.【双击获取解压密码】-Windows...url` | Windows 快捷方式 |

### 工作原理

1. 用户提前上传推广文件到 `temp/要共享的文件`
2. Skills 脚本在转存后自动复制到每个分享文件夹
3. 无需实现上传 API，简单可靠

---------------

# 待办TODO

自动生成转存地址，需要mcp server封装，或者n8n等的api调用，
可以改造工程，夸克批量转存这个Python：https://github.com/ihmily/QuarkPanTool?tab=readme-ov-file

----------
