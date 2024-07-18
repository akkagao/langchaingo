v0.1.12-mv.1

llms/openai/internal/openaiclient/chat.go

删除createChat方法 343 行
```golang
// if payload.StreamOptions == nil {
// 	payload.StreamOptions = &StreamOptions{IncludeUsage: true}
// }
```
原因：

调用azure openai 报错：

Unrecognized request argument supplied: stream_options

---
v0.1.12-mv.2

llms/bedrock/internal/bedrockclient/provider_meta.go

添加

parseLlamaStreamingCompletionResponse 方法

streamingLlamaCompletionResponseChunk 结构体

createMetaCompletion 方法 第70行新增
``` golang
if options.StreamingFunc != nil {
		modelInput := &bedrockruntime.InvokeModelWithResponseStreamInput{
			ModelId:     aws.String(modelID),
			Accept:      aws.String("*/*"),
			ContentType: aws.String("application/json"),
			Body:        body,
		}
		return parseLlamaStreamingCompletionResponse(ctx, client, modelInput, options)
	}
```

原因：

调用bedrock llama3 模型无法流式返回数据

---



v0.1.12-mv.3

langchaingo/llms/bedrock/models_list.go

添加
ModelAnthropicClaudeV35Sonnet = "anthropic.claude-3-5-sonnet-20240620-v1:0"
原因：

增加 claude 3.5 模型配置
