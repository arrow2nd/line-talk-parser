# line-talk-parser

日本語環境の LINE（スマホ・PC）で出力したトーク履歴ファイルをパースするやつ

## 使い方

### パースする

```ts
import {
  parse,
  TalkData,
} from "https://github.com/arrow2nd/line-talk-parser/raw/main/mod.ts";

const text = Deno.readTextFileSync("talk_histroy.txt");
const histories: TalkData[] = parse(text);

console.log(histories);
```

### JSON にする

```ts
import { toJson } from "https://github.com/arrow2nd/line-talk-parser/raw/main/mod.ts";

const text = Deno.readTextFileSync("talk_histroy.txt");
const json = toJson(text);

Deno.writeTextFileSync("histroy.json", json);
```

## 検証環境

- Windows / Mac 版 LINE v7.2.0
- Android 版 LINE v11.17.1

## 仕様

- LINE のシステムメッセージや URL、LINE 依存の絵文字を含むメッセージは除外されます
- 時刻は全て 24 時間表記です
