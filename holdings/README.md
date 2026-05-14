# holdings/

楽天証券からエクスポートした保有株CSVを保管するフォルダ。

## ファイル命名規則

```
holdings_YYYY-MM-DD.csv
```

例：`holdings_2026-05-14.csv`

## CSVの移動方法

楽天証券からダウンロードしたCSVは、Windowsの `Downloads` フォルダに保存される。
以下のどちらかの方法でこのフォルダに移動する。

### 方法①：ターミナルで移動（推奨）

楽天証券のCSVはShift-JIS形式のため、UTF-8に変換して保存する：

```bash
iconv -f SHIFT-JIS -t UTF-8 "/mnt/c/Users/hyou1/Downloads/ダウンロードしたファイル名.csv" \
   > /home/hyou/PPL/stock_corp/holdings/holdings_YYYY-MM-DD.csv
```

例：
```bash
iconv -f SHIFT-JIS -t UTF-8 "/mnt/c/Users/hyou1/Downloads/assetbalance(all)_20260514_160333.csv" \
   > /home/hyou/PPL/stock_corp/holdings/holdings_2026-05-14.csv
```

### 方法②：エクスプローラーからドラッグ＆ドロップ

Windowsエクスプローラーのアドレスバーに以下を入力してフォルダを開き、CSVをドラッグ＆ドロップ：

```
\\wsl$\Ubuntu\home\hyou\PPL\stock_corp\holdings
```

ファイルを置いたら `holdings_YYYY-MM-DD.csv` にリネームする。

## Claude Codeとの連携

株の話題が出たとき、Claude Codeがこのフォルダの最新CSVを自動で読み込んで保有状況を把握する。
