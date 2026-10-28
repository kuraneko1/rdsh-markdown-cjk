# rdsh-markdown-cjk

> [日本語の README はこちら](README.md)


CJK prose directly after a URL keeps its link instead of being swallowed into it
(`https://example.com（memo）`, `**https://example.com**です`).

```sh
dsh plugin --profile web add github:kuraneko1/rdsh-markdown-cjk
```

Restart DSH. Disable with `RDSH_MARKDOWN_CJK=0` or `config: { enabled: false }`.

## How it works

The renderer ships prebuilt in `@deepseek-ai/dsh-web-frontend`, so the plugin
patches its vendor chunk **at serve time** and serves it from
`/markdown-cjk/v1/`. A new DSH build or a new patch version is a new URL, so
nothing goes stale; a chunk whose shape no longer matches is served untouched
(stock rendering, one log line).


## Related project

[dsh-mobile-maxxing](https://github.com/kuraneko1/dsh-mobile-maxxing) provides independent mobile UX, notification, Markdown table, and Japanese locale components. The CJK link fix remains separate so the integrated package does not change desktop Markdown rendering.
