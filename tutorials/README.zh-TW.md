<!-- Maintained upstream in the RealSub app repository; do not edit here directly.
     One file per language (English / 简体中文 / 繁體中文 / 日本語) — change one, change all four. -->

# 教學

[English](./) · [简体中文](README.zh.md) · **繁體中文** · [日本語](README.ja.md)

這些都是**可選的進階設定**。RealSub 裝上即可用(模型內建,預設翻譯來源開箱即用),下面的教學面向
想要更快、更省、或完全離線的翻譯方案的使用者。

> **狀態:規劃中。** 下列文章的正文尚未發布。可以關注本儲存庫,或在新版本發布後再來看。

---

## 規劃中的文章

### 1. 本地大型語言模型翻譯(llama-server + Sakura 等)

在本機執行翻譯模型並讓 RealSub 連上它,做到**文字完全不出本機**,也沒有連網請求的往返延遲。

預計涵蓋:

- Windows 上安裝 `llama.cpp` / `llama-server`,以及量化模型檔的選擇;
- 與識別模型共用同一張顯示卡時的顯示記憶體分配;
- RealSub 裡的具體設定(設定 → 翻譯 → 翻譯來源 = **本地**,位址 `http://127.0.0.1:8178`)
  以及如何確認它真的生效了;
- 延遲的真實預期,以及什麼情況下本地翻譯**不值得**。

**授權提醒(重要)**:Sakura 等模型的授權條款**禁止商業用途**,因此 RealSub 不內建、不散佈
任何此類模型。教學只講如何部署**你自己取得的**模型,遵守該模型授權是使用者的責任。

### 2. 用智譜(bigmodel.cn)的免費 API Key 作為翻譯來源

面向希望比預設翻譯來源更低延遲的中國大陸使用者,也適用於任何想接 OpenAI 相容介面的人。

預計涵蓋:

- 在 bigmodel.cn 註冊並申請 API Key(需要中國大陸手機號);
- 在 RealSub 裡填寫:設定 → 翻譯 → 翻譯來源 = **大模型(OpenAI 相容)**,
  介面位址 `https://open.bigmodel.cn/api/paas/v4`,你的 Key,模型名 `glm-4-flash`;
- 請求失敗時會發生什麼(RealSub 會退回預設翻譯來源並在介面提示);
- **免費額度、模型名與介面位址由廠商決定且可能變動**——文章會標註撰寫日期,請以廠商官網當時的
  說明為準。

RealSub 不內建、不預填、不代理任何第三方帳號。同一步驟的摘要見 [FAQ Q2](../faq.zh-TW.md)。

---

## 投稿

有值得分享的設定?歡迎發到
[Discussions](https://github.com/realsub/realsub/discussions),優秀內容會署名收錄到本目錄。
