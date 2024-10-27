# LlamaIndex Workflows を使った Dynamic Few-shot prompting のサンプル（Docker版）

## About

以下で公開されている、LlamaIndex Workflows を使った Dynamic Few-shot prompting のサンプルを、Dockerで動かせるように修正したものです。

https://github.com/rsrohan99/dynamic-few-shot-llamaindex-workflow

元のレポジトリに以下の変更を加えています。

- Frontend/Backend、それぞれのDockerコンテナを作成、docker composeで起動できるようにしています
- サンプルのデータベースの内容を日本語に変更しました

## Usage

dockernizeブランチをクローンします。

```
$ git clone -b dockernize https://github.com/kun432/dynamic-few-shot-llamaindex-workflow
$ cd dynamic-few-shot-llamaindex-workflow
```

docker-compose.yamlを修正します。

```
  backend:
    (snip)
    environment:
      - PHOENIX_API_KEY=XXXXXXXXXX   # LlamaTraceのAPIキー
      - OPENAI_API_KEY=XXXXXXXXXX    # OpenAIのAPIキー
```

docker composeを起動します。

```
$ docker compose up
```

ブラウザで http://localhost:5173 にアクセスします。なお、デフォルトではbackendは http://localhost:8000 になります。

チャットが開きますので、以下を参考にチャットを試してみてください。

- backend/dataset.json: Dynamic Few-shot prompting のデータ。この内容を参考にクエリしてみてください。
- backend/sample_database.json: サンプルの注文データベース。この内容にある注文情報ヲ参考にクエリしてみてください。

---

**以下は元のREADMEの内容です**


Watch the tutorial on YouTube 👇

[![Dynamic Few-shot prompting using LlamaIndex Workflows](https://img.youtube.com/vi/Nseuty3LsxY/maxresdefault.jpg)](https://www.youtube.com/watch?v=Nseuty3LsxY)


Dynamic Few-shot prompting is an intuitive alternative to finetuning LLMs where:

- we can get consistent output for many use-cases
- rapid iteration
- takes effect right away
- easy to implement

In Dynamic Few-shot prompting, instead of putting a static list of examples in the prompt, we dynamically pull the best examples from our database based on the user query.
