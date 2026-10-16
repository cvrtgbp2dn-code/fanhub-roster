# FanHub · 云端名单库

这个仓库只干一件事：放着「名单库」的原始数据，GitHub 自动把它转成客户端要读的两个文件。

> 现在是**空的**（见最后一节），这很正常。

## 你要做的（3 步）

1. 打开本仓库的 `source/` 文件夹
   https://github.com/cvrtgbp2dn-code/fanhub-roster

2. `Add file` → `Upload files` → 把名单库的 **CSV** 拖进去
   - 文件名随意（`.csv` / `.txt` 都认）
   - 想要多份就传多个，脚本会**自动合并去重**
   - **同名会自动覆盖旧的**

3. 拉到页面底部点 `Commit changes`

完事。约 30 秒后 GitHub 自动重新生成 `roster.js`，**下次打开 FanHub 就是新名单库**。

> 快捷入口（直接进上传页）：
> https://github.com/cvrtgbp2dn-code/fanhub-roster/upload/main/source

## 数据格式

- **CSV**：只读**第一列**（有表头也不影响，当普通一行读；建议去掉表头）
- **纯文本**：一行一个数据ID
- 编码 UTF-8 优先，GBK 也认
- 自动去重（不分大小写）

## 仓库结构

```
source/     ← 只有这里需要你动手（放原始名单库 CSV）
tools/      ← 转换脚本 build_roster.py（自动跑，不用管）
.github/    ← 自动化流程配置（自动跑，不用管）
roster.js   ← 自动生成（客户端读这个）
version.js  ← 自动生成（客户端比对版本用）
```

## 客户端从哪里读

- 主源：https://cvrtgbp2dn-code.github.io/fanhub-roster/
- 备用：https://fastly.jsdelivr.net/gh/cvrtgbp2dn-code/fanhub-roster@main/
  （`raw.githubusercontent.com` 在部分网络下不通，所以没有使用）

## 现在是空的（这很正常）

`source/` 里还没有文件，所以生成的是一份 **0 条**的占位名单库。
**空库时 FanHub 不会把所有数据标成「不在库」** —— 它会把一切当成「在库」正常用。
你把 CSV 传上来，自动就生效，**不用改任何设置**。

## 需要"删掉"某些数据时

自动流程只做合并、**不会删**。真要重建：先把 `source/` 里的旧文件删掉，再上传新的。
