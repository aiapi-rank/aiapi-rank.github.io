# AI API 价格对比 · 中转站公开价格快照

AI API 价格对比站整理 Folkbench 公开快照里各家中转站已公布的 API价格：同一模型按币种和计价单位分组列出中转站价格，并附官方参考价，方便比较 Claude、GPT、Gemini 等模型的 AI API 价格。每家中转站另有一页价格汇总（`/stations/{slug}/prices/`），列出该站当日全部公开价格行，适合先比较中转站价格、再决定选哪家中转站的读者。未公布的价格不估算，也不做汇率换算。

发布地址：https://aiapi-rank.github.io/

AI API 公开价格快照与厂商站点列表，数据来自 Folkbench。 数据来自 [folkbench-data](https://github.com/Folkbench/folkbench-data) 的已归档公开快照，由 [Folkbench](https://folkbench.com/?utm_source=aiapi-rank&utm_medium=pages&utm_campaign=subsite&utm_content=repo-readme) 维护。

排序沿用主站规则，包含合作档位与运营加分；部分数据为展示样本。

[打开站点](https://aiapi-rank.github.io/) · [方法说明](https://folkbench.com/methodology?utm_source=aiapi-rank&utm_medium=pages&utm_campaign=subsite&utm_content=repo-methodology)

同一模型、同一币种和单位的价格表按输入价排列，输入相同再看输出价。官方参考价不作汇率换算；价格顺序不是主站综合排名。

## 徽章

```markdown
![公开快照](https://aiapi-rank.github.io/badge.svg)
```

## 运维

- 每日 21:00（北京时间）读取公开归档发布；失败不覆盖当前版本。
- 固定已审核的 FOLKBENCH_TOOLING_SHA，定时启用变量为 PUBLIC_DISTRIBUTION_ENABLED=true；手动 workflow_dispatch 可在定时关闭时运行。
- 访问来源使用 utm_source=aiapi-rank、utm_medium=pages、utm_campaign=subsite。
- 验证变量 BING_SITE_VERIFICATION、BAIDU_SITE_VERIFICATION 为空时不输出标签；取得验证码后填入变量并重新发布。
- sitemap：https://aiapi-rank.github.io/sitemap.xml 。本仓库不自动注册或登录搜索平台。
- 不在仓库中写入每日快照；构建只读公共工具和数据，无额外 token。
- 手动 data_ref 可指定数据仓库提交。不存在的 ref 会在真实 checkout 阶段失败，部署步骤不执行。
- 提交和推送使用正常 Git hooks；FOLKBENCH_DISTRIBUTION_TOOL_ROOT 指向已审核的公共工具工作区。

## 兜底发布与 IndexNow

- 原定时任务保持不变，另有两个入口：数据仓库归档成功后的 `repository_dispatch`（`public-snapshot-archived`）通知，以及北京时间 23:35 的备用定时。自动触发时，如果线上 `publish-state.json` 已经是最新快照，就直接结束，不重复发布。
- 自动发布失败时，本仓库会开一个「公开快照站点自动发布失败」issue，之后发布成功会自动关闭。
- 配置仓库变量 `INDEXNOW_KEY` 后，发布产物输出 `/{key}.txt`；部署成功后，把 sitemap 中 lastmod 等于本次归档日期的 URL 推送到 IndexNow。推送失败只记日志，不影响发布结果。

## 其它公开快照视图

- [AI 中转站排行](https://folkbench.github.io/relay-rank/)：按模型的每日公开快照与历史名次
- [中转站检测周报](https://folkbench.github.io/integrity-weekly/)：模型身份探针的每周汇总
- [AI 中转站对比](https://ai-relay-bench.github.io/)：同一模型在各中转站的并排对比
- [AI 中转站大全](https://ai-zhongzhuan.github.io/)：站点目录、公开资料与新手指南
- [模型检测快照](https://ai-model-check.github.io/)：每日模型身份探针汇总
