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
