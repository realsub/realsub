<!-- Maintained upstream in the RealSub app repository; do not edit here directly.
     One file per language (English / 简体中文 / 繁體中文 / 日本語) — change one, change all four. -->

# 教程

[English](./) · **简体中文** · [繁體中文](README.zh-TW.md) · [日本語](README.ja.md)

这些都是**可选的进阶配置**。RealSub 装上即可用(模型内置,默认翻译源开箱即用),下面的教程面向
想要更快、更省、或完全离线的翻译方案的用户。

> **状态:规划中。** 下列文章的正文尚未发布。可以关注本仓库,或在新版本发布后再来看。

---

## 计划中的文章

### 1. 本地大模型翻译(llama-server + Sakura 等)

在本机跑翻译模型并让 RealSub 连上它,做到**文本完全不出本机**,也没有联网请求的往返延迟。

计划覆盖:

- Windows 上安装 `llama.cpp` / `llama-server`,以及量化模型文件的选择;
- 与识别模型共用同一张显卡时的显存分配;
- RealSub 里的具体设置(设置 → 翻译 → 翻译来源 = **本地**,地址 `http://127.0.0.1:8178`)
  以及如何确认它真的生效了;
- 延迟的真实预期,以及什么情况下本地翻译**不值得**。

**授权提醒(重要)**:Sakura 等模型的授权条款**禁止商业用途**,因此 RealSub 不内置、不分发
任何此类模型。教程只讲如何部署**你自己获取的**模型,遵守该模型授权是使用者的责任。

### 2. 用智谱(bigmodel.cn)的免费 API Key 作为翻译源

面向希望比默认翻译源更低延迟的中国大陆用户,也适用于任何想接 OpenAI 兼容接口的人。

计划覆盖:

- 在 bigmodel.cn 注册并申请 API Key(需要大陆手机号);
- 在 RealSub 里填写:设置 → 翻译 → 翻译来源 = **大模型(OpenAI 兼容)**,
  接口地址 `https://open.bigmodel.cn/api/paas/v4`,你的 Key,模型名 `glm-4-flash`;
- 请求失败时会发生什么(RealSub 会退回默认翻译源并在界面提示);
- **免费额度、模型名与接口地址由厂商决定且可能变动**——文章会标注撰写日期,请以厂商官网当时的
  说明为准。

RealSub 不内置、不预填、不代理任何第三方账号。同一步骤的摘要见 [FAQ Q2](../faq.zh.md)。

---

## 投稿

有值得分享的配置?欢迎发到
[Discussions](https://github.com/realsub/realsub/discussions),优秀内容会署名收录到本目录。
