---
layout: default
title: MeetMi 隐私政策
---

# MeetMi 隐私政策

版本：`managed-ai-apple-pages-v1`<br>
生效日期：阶段 9 启用 GitHub Pages 时填写<br>
适用范围：通过 Apple App Store 分发的 MeetMi Managed AI，首发为 macOS。未来 iOS/iPadOS Managed 版沿用本政策，除非另行发布新版本。

开发者/经营主体、地址和隐私联系方式将在开通 Apple Developer Program 后回填。在此之前，本页是 App 与商店材料必须对齐的权威草案。

[English](../../privacy/) · [支持](../support/)

## 1. 适用范围

本政策适用于通过 Apple App Store 分发的 MeetMi Managed AI。

MeetMi Local 是独立的 BYOK 产品：使用不同 App 身份、数据目录、偏好、日志和 Keychain，由用户自己的 API Key 直连用户选择的 OpenRouter 或 HTTPS Responses endpoint，不经过 MeetMi Worker，也没有 MeetMi Credit 或订阅权益。

## 2. 设备端处理

- 麦克风和 macOS 系统音频只在用户主动开始会议后用于转写。
- 原始音频不由 MeetMi 保存，也不上传到 MeetMi Worker、OpenRouter 或模型上游。
- 语音识别与字幕翻译使用 Apple 设备端能力完成。
- 会议转写、建议、分析、纪要、工作区索引和文档缓存默认保存在设备或用户明确选择的工作区。
- iOS/iPadOS 版本只使用麦克风，不捕获其他 App 的系统音频。

## 3. Managed 云端 AI

在用户明确同意后，App 可能发送设备端生成的会议转写、用户问题和明确表达的关注点、已有分析、AI 按需读取的相关工作区文档片段，以及严格工具调用和结构化输出所需的协议数据。

数据接收链：

```text
MeetMi Apple Managed → MeetMi Worker → OpenRouter → 当前 App 内 policy 列出的 ZDR 模型上游
```

当前 App 内 policy 使用 DeepSeek V4 Flash，以及 DigitalOcean、Morph、CoreWeave、Together 的 ZDR 范围。MeetMi Worker 不主动持久化或记录转写、问题、文档片段、请求正文、上游错误正文或流式响应内容。这些内容仍会在请求处理时短暂经过 Worker 内存，并被 OpenRouter 和上游模型服务商为路由与推理而瞬时处理。上游看到的是 Worker 的网络地址，而不是用户设备直接连接时的公网 IP。

App 会在发送前展示中转域名、模型、ZDR provider 范围、数据范围和 policy 版本。接收链、模型、provider、数据范围或政策发生实质变化时，旧同意失效，需要重新同意。

## 4. 联网检索

联网检索**默认关闭**，并与录音须知、Managed AI 同意分开保存，可以单独撤回。它只在「深入研究」和「与 MeetMi 讨论」中使用；**实时建议与会议纪要永不联网，这一点由服务端强制**，不只是 App 内的设置。

**服务商与域名。** 搜索服务商是 **Exa**（`api.exa.ai`）。请求由 MeetMi Worker 转发，Exa 看到的是 Worker 的网络地址，而不是用户设备直接连接时的公网 IP。这条链路独立于 AI 推理链路，不经过 OpenRouter。

**发送什么。** 只发送由模型从会议内容中提炼出的**检索词**；需要读取原文时，另外发送**结果页网址**，由 Exa 抓取正文后返回。会议转写全文、工作区文档原文和用户提问不会发给 Exa。

**保留与训练。** Exa 的公开条款说明：发给它的检索词可能被保留，并用于改进和训练它自己的模型。**这一点与云端 AI 不同**——云端 AI 走的是服务端强制的零留存（ZDR）链路，联网检索不是。检索词由会议内容提炼，可能包含会中出现的公司名、人名等专有名词。用户在**第一次开启联网检索时必须明确确认这一条**之后功能才会启用。Exa 的条款见 <https://exa.ai/privacy-policy>。

**跨境处理。** Exa 是美国服务商，请求在其服务器处理。

**重新同意。** 搜索服务商、域名或联网检索政策版本发生变化时，已有的联网检索同意即失效，需要重新确认。该变化不影响录音须知与 Managed AI 同意。

**启用时机。** 联网检索随正式中转服务一同在 App Store 版本启用；在此之前 App 内会明确显示该版本不联网检索。

## 5. Apple 购买、权益与 Credit

- 购买和订阅通过 Apple StoreKit / App Store 处理；MeetMi 不在 App 内处理完整银行卡信息。
- App 会把必要的 StoreKit transaction JWS 和匿名关联值发送给 MeetMi Worker，用于验证订阅、退款、撤销、恢复和签发短期访问令牌。
- JWT 不包含 Apple ID、邮箱、完整交易 JWS 或 OpenRouter key。
- 服务端以不透明 subject 保存权益、额度和无正文 usage 账本。
- 首发只有一个月订阅，包含会按订阅周期重置的 Managed AI 额度。
- 首发不出售 Credit 加购。若未来通过 consumable IAP 购买 Credit，该余额将与月度额度分账，不会仅因月份重置而过期。
- 额度耗尽、权益失效或后端不可用时，新的 AI 请求停止，本地转写、翻译、历史和导出继续。

## 6. Credit 计量

当前技术基线按 `input token + 2 × output token` 计算计费 token，并换算为 Credit。服务端按活动类型保存不含正文的用量：会议监听、用户提问、深入研究、参谋讨论和会议纪要。

App 可显示 Credit、周期重置、活动拆分和按当前设置估算的可用会议时长；估算不是固定承诺。Local 产品不适用 Credit。

## 7. 本地日志与缓存

Debug 详细日志默认关闭。用户开启后，日志可能包含会议内容、提示词和诊断信息，但认证 Header、Apple 交易凭据、JWT、License、API Key 和 Cookie 会被排除或脱敏。

用户可以清除日志和可重建文档缓存。生产 Worker 关闭请求级正文 observability，不使用 Tail、Logpush、Sentry 或其他服务记录会议正文。

## 8. 用户控制与删除

用户可以拒绝或撤回 Managed AI 同意，关闭或撤回联网检索同意，使用 Apple 的订阅管理与恢复购买，删除会议归档、缓存和 Debug 日志，以及删除自己工作区中的文件。

删除 App 不一定删除用户选择工作区中的文件；这些文件由用户在 Finder / 文件 App 中管理。服务端权益或用量记录删除与本地/工作区文件删除是不同流程，上线后通过 Support 页面申请。

## 9. 第三方、跨境与安全

Apple、OpenRouter、当前 policy 中的模型上游，以及（在用户单独同意联网检索后）搜索服务商 Exa，可能在用户所在国家/地区之外处理相关数据，并受各自政策约束。正式发布前会链接最终 OpenRouter 与 provider 条款、保留/训练说明和适用 DPA。无法确认的 provider 不会进入首发 allowlist。

AI 推理链路上的上游 provider 受 ZDR 与 `data_collection: deny` 约束；**联网检索不在这条链路上，也不享有同一保证**，详见第 4 节。

MeetMi 使用最小字段白名单、ZDR allowlist、`store=false`、价格上限、短期 JWT、独立 Keychain、App Sandbox、加密传输和日志禁令降低风险，但任何互联网传输都不能保证绝对安全。

OpenRouter 隐私信息：[https://openrouter.ai/privacy](https://openrouter.ai/privacy)

Exa 隐私信息：[https://exa.ai/privacy-policy](https://exa.ai/privacy-policy)

## 10. 录音与用户责任

会议可能包含其他人的个人信息、商业秘密或受管制数据。用户负责依据适用法律、合同、组织政策和会议约定，完成录音、转写、向 AI 发送内容所需的告知、许可和授权。

系统麦克风/屏幕录制权限、MeetMi 的录音须知和 Managed AI 同意均不等于其他参会者的同意。

## 11. 儿童、追踪和数据出售

MeetMi 不以儿童为目标，不进行跨 App Tracking，不出售个人信息，也不使用会议内容投放广告。

## 12. 地区限制

中国大陆的敏感个人信息跨境、PIPL 和 App 备案需要独立评估；在该评估闭环前，Managed 首发不包含中国大陆。其他地区也会在提交商店记录前根据录音、隐私、消费者和跨境规则复核。

## 13. 变更与联系

政策更新会标明版本和生效日期。影响云端 AI 接收方、数据范围、购买或保留政策的实质变化，还会在 App 内要求重新同意或更新说明。

- 隐私联系：随 Apple Developer Program 经营主体一并发布
- 支持：[支持页面](../support/)
- 阶段 9 后的公开 Privacy URL：`https://kinlu.github.io/meetmi/zh/privacy/`
