# 验证方法

从仓库根目录使用 Python 3.12 执行离线软件检查：

```bash
python -m pytest -q
python -m backend.evaluate_mock
python -m scripts.demo --out runtime/demo-result.json
python -m scripts.validate_task_d
```

这些命令使用临时数据库、Mock 或明确标注的合成/公开病例改编材料，不证明真实供应商当前可用、临床效果或生产可用性。运行生成的结果保存在被忽略的 `runtime/` 下，不应提交个人数据。

公开病例的来源、作者和许可保留在 [病例说明](../data/public_cases/README.md) 和 [登记表](../data/public_cases/registry.json)；合成素材的来源见 [合成自测素材](../data/synthetic/selftest/README.md)。不能将公开病例或合成素材称为本项目的真实用户测试。

浏览器演示使用新的浏览器配置和虚构资料。真实录音权限、录制格式、识别、人工原件核对、断网恢复与备份恢复需分别检查，不能由 HTTP 或 Mock 测试代替。使用真实供应商的检查可能产生费用，应在使用者自己的本机配置中明确启用。

公开源码不包含旧开发账号、内部合并/交接记录或历史在线请求凭据。验证结论应绑定实际执行的提交、环境、命令和覆盖范围，不沿用历史分支的通过数。
