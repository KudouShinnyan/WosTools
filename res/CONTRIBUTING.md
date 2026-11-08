# 翻译贡献

[简体中文](CONTRIBUTING.md) · [English](CONTRIBUTING_EN.md)

## 可改的文件

界面文案在以下文件里，新增语言时再加一个：

- `res/values/strings.xml`（英文，默认）
- `res/values-zh-rCN/strings.xml`（简体中文）
- `res/values-zh-rTW/strings.xml`（繁体中文，台湾）
- `res/values-zh-rHK/strings.xml`（繁体中文，香港）
- `res/values-b+zh+Hant/strings.xml`（繁体中文，通用 Hant）
- `res/values-ja/strings.xml`（日文）
- `res/values-<locale>/strings.xml`（新增语言，如 `values-ko`、`values-fr`）

请勿改动本仓库其它文件。

## 规则

1. 所有语言文件的 `<string name="...">` key 必须与默认英文完全一致，当前共 **168** 个。不要新增、删除或重命名 key。
2. 格式化参数必须保持数量与类型一致，例如 `%1$d`、`%1$s`。顺序可随语言调整，个数不能变。
3. 字符串值里不要出现裸的反斜杠、`&`、`<`、`>` 或未转义的引号；aapt2 会直接报资源编译错误。需要引号请用中文引号或 `「」`。
4. 不要改 XML 声明、`<resources>` 结构，也不要加注释块。
5. 属性名与页面 / 按钮用词以游戏内实际显示为准：简体中文看简中界面，繁体中文看繁中界面，日文看日文界面，英文看英文界面。APP 自有的决策词（保留 / 重洗 / 品质提升）不照抄游戏按钮。繁体中文的穿透力写作殺傷力。

## 新增语言

把 `values-<locale>/strings.xml` 放进 `res/` 即可：编译后跟随系统会自动生效，无需改构建配置或 Java 代码；地区限定符用 `-r`（如 `zh-rTW`）。若要覆盖所有繁体中文 Hant 区域，可另加 `values-b+zh+Hant`。

本版本已把繁体中文登记到主页语言下拉；后续新增语言若也要出现在下拉，仍需维护者另外登记四处：`AppPrefs.Lang` 枚举、`AppPrefs.wrap()` 的 `Locale`、主页 spinner 选项、以及所有语言文件里的 `lang_<xx>` 文案。

本仓库路径是 `res/values-xx/`，本地编译工程对应 `app/src/main/res/values-xx/`，合并后由维护者搬运。

## 提交

提交 PR 时说明改了哪种语言、依据是哪张游戏截图。合并后由维护者同步进本地编译工程，再随下个版本发布。

本仓库不含应用源码，翻译 PR 不会被用于构建其它衍生安装包。
