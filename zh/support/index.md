---
layout: default
title: MeetMi 支持
---

# MeetMi 支持

版本：`managed-ai-apple-pages-v2`<br>
适用于 App Store 上的 MeetMi Managed AI，macOS 与 iPhone 版（同一记录、共用一份订阅）。

[English](../../support/) · [隐私政策](../privacy/)

## 联系方式

开通 Apple Developer Program 后，本页会公布公开支持邮箱和响应预期。在此之前，本页是审核与产品共用的草稿。

请不要在支持邮件中发送 API Key、License、JWT、交易 JWS 或会议转写。

## MeetMi 做什么

MeetMi 在设备上转写会议；用户同意后，会把转写、问题和相关工作区片段经 MeetMi Worker → OpenRouter → 已列出的 ZDR 供应商发送。原始音频不保存、不上传。语音识别和翻译留在设备端。

首发只有一个月订阅，没有 Credit 加购。额度耗尽或权益不可用时，只停止新的 AI 请求；本地转写、翻译、历史和导出继续。

## 购买与订阅

1. 打开设置 → Apple 服务（iPhone 上是齿轮图标，再点「Apple 服务」标签）。
2. 购买 MeetMi 托管 AI 月度订阅，或使用「恢复购买」。一份订阅同时覆盖 Mac 与 iPhone 版；在另一台设备上恢复购买会显示同一订阅和同一剩余额度。
3. 在 Apple 账户 / App Store 订阅设置中管理或取消订阅。MeetMi 不能自行取消 Apple 订阅。

家庭批准中的购买不会打断本地会议功能。退款和撤销由 Apple 处理后，再反映到 MeetMi 权益。

## 权限

- 麦克风：会议开始后听使用者发言。iPhone 上这是唯一的音源，把手机放在扬声器旁或在会议室里使用。
- macOS 屏幕与系统音频：听会议软件里的对方声音。原始音频不保存。iPhone 没有系统音频采集。
- 用户选择的文件夹：读取资料并写回纪要。两端都保存 security-scoped bookmark；iPhone 上经「文件」选择器选择（iCloud Drive 或本机）。文件夹被移动或权限被撤回后，需要重新选择。

系统权限不等于其他参会者的同意。用户必须完成法律或组织政策要求的告知。

## 会议、工作区与纪要

- 只有用户按下开始后才会采集。
- 暂停会停止采集和自动 AI；结束会议仍可生成纪要，因为那是一次明确操作。
- 纪要写到工作区的 `Meetings` 子文件夹；未选择工作区时写到「文稿/Meetings」。分享按钮可把会议以 Markdown 或纯文本经系统分享表导出（iPhone 上如「存储到文件」）。
- iPhone 上已开始的会议在锁屏后继续转写。
- 移除工作区只是让 App 忘记它，不会删除文件夹。

## AI、额度与网络故障

- 云端 AI 需要有效订阅、剩余额度和已接受的数据说明。
- 撤回云端 AI 同意会停止新的云端发送。
- 剩余 Credit、本周期包含额度和永久 Credit 分开显示。首发不出售永久 Credit。
- 会议时长估算不是商店承诺。
- Relay、OpenRouter 或上游故障只停止 AI。

## 删除数据

- 在 App 内删除会议记录。
- 在设置中清除可重建缓存和 Debug 日志。
- 在 Finder（macOS）或「文件」App（iPhone）中删除工作区文件。
- 卸载 App 不会删除用户选择的工作区。
- 上线后可通过已发布的支持联系方式申请删除服务端权益/用量记录。

## 已知限制

- 需要 macOS 26 或 iOS 26 及更新版本（只做 iPhone，本版没有 iPad 布局）。
- iPhone 只用麦克风；iOS 上不存在系统音频采集。
- 中国大陆在独立法律评估完成前排除。
- 模拟器没有本机语音模型。
- 这些页面已发布在 https://kinlu.github.io/meetmi/ ，对外可访问。

## 审核路径

审核员可以在任一平台购买或恢复 Sandbox 月度商品，同意或拒绝云端 AI，选择文件夹，开始/暂停/结束会议，并确认纪要写回。不需要 API Key、JSON 文件或命令行。
