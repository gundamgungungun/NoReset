# 模型服务与本地配置

本仓库不包含可用 API 密钥、服务账号、调用额度或使用者资料。复制根目录 `.env.example` 为本机 `.env`，只在本机填写自己的服务配置；`.env` 不应提交到 GitHub。环境变量与配置项以 `.env.example` 和当前实现为准。

## 默认文字服务

```dotenv
MODEL_PROVIDER=deepseek
DEEPSEEK_BASE_URL=https://api.deepseek.com/v1
DEEPSEEK_MODEL=deepseek-chat
DEEPSEEK_API_KEY=your_api_key
MODEL_TIMEOUT_SECONDS=60
MODEL_MAX_TOKENS=4096
```

文字整理采用非流式 JSON 响应，结果经过来源、完整原话与安全校验后才被接受。AI 请求失败时保留已保存的原话，不生成成功结果。模型权限、可用性与费用由所选服务决定，本仓库不附赠服务。

## 语音与照片识字

```dotenv
MEDIA_RECOGNITION_PROVIDER=aihubmix
AIHUBMIX_API_KEY=your_api_key
MEDIA_RECOGNITION_TIMEOUT_SECONDS=60
```

默认语音转写与照片识字共用此服务配置。支持范围与错误响应以当前 `backend/recognition.py` 和 [API 文档](API.md) 为准。转写与识字是待核对文字；不会将识别成功等同于人工核对或医学解读。

使用者明确选择的文字、录音或照片会发送到配置的供应商。演示应使用仓库里的合成素材；真实健康资料不应作为公开 Issue、测试附件或仓库内容上传。

## 其他兼容文字服务

实现支持 OpenAI Chat Completions 兼容的非流式 JSON 接口，可按实际服务修改：

```dotenv
MODEL_PROVIDER=openai_compatible
LLM_BASE_URL=https://api.example.com/v1
LLM_API_KEY=your_api_key
LLM_MODEL=your_model_id
LLM_JSON_MODE=false
LLM_EXTRA_BODY_JSON={}
```

示例地址与密钥是占位符，不能直接调用。地址、模型 ID 和密钥必须属于同一服务。通用接口没有默认供应商；不跟随 HTTP 重定向，不接受地址中的用户名、密码或查询参数。本机测试地址可使用 HTTP，外部服务使用 HTTPS。

ModelScope 兼容配置使用 `MODEL_PROVIDER=modelscope`、`MODELSCOPE_BASE_URL`、`MODELSCOPE_MODEL` 与 `MODELSCOPE_ACCESS_TOKEN`。模型 ID 和账号权限应以使用者实际可用的服务为准；不保留此前开发账号的配置或联调记录。

## 启动与检查

```bash
python -m scripts.start_app --check-config
python -m scripts.start_dev
```

配置检查不会调用外部模型，也不能证明所配服务当前可用。未填写密钥时仍可打开本机页面，使用加密资料库、保存文字、回看记录和本地备份；AI 对话、整理和识别功能需要有效服务配置。

普通产品接口不会把 Mock 输出当作真实 AI 结果。离线软件回归见 [验证方法](VALIDATION.md)，不要将 Mock 结果称为真实供应商或临床验证。

## 可选云备份

本机下载与恢复 `.bingli` 备份不需要云服务。只有启用云端密文备份时才配置 `.env.example` 中的 TOS 字段；密钥、桶名、临时授权和个人备份文件均不进入公开仓库。
