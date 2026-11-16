# AI API 公开价格快照

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
