# 后端 QA 入口

本目录包含公开病例登记、软件测试矩阵、覆盖范围和记录模板。当前结果应以实际运行的提交与环境为准，不沿用旧内部开发分支的结论。

## 当前入口

- [公开病例登记](../../data/public_cases/registry.json)：来源、许可、改编、预期行为和限制。
- [运行夹具](../../data/public_cases/cases.json)：scripts.demo 与评测读取的轻量数据。校验脚本强制它与登记表逐条一致。
- [测试矩阵](test-matrix.md)：当前后端范围、证据和未验证项。
- [覆盖表](coverage.md)：十项核心保护的当前判断。
- [缺陷记录](defects.md)、[缺陷模板](defect-template.md) 和 [证据模板](evidence-template.md)。

## 可重复校验

在仓库根目录运行 python3.12 scripts/validate_task_d.py，再运行 python3.12 -m pytest -q tests/test_task_d_retry.py。

第一个命令只读仓库内的 JSON 与 Markdown，不联网、不读密钥。它检查公开病例双份表示是否同步、病例引用的用例是否存在、旧结论是否误入当前矩阵，以及 P1 边界是否保持可见。

测试通过只证明对应提交和环境里的软件行为。Mock、测试替身、公开病例和合成 WAV/PNG 都不能证明真实患者效果、临床安全或生产可用性。
