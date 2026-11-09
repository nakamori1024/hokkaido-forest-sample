# hokkaido-forest-sample

北海道の「森林計画関係資料オープンデータ」のうち「林小班区画及び森林資源データ」を、[Portolan](https://github.com/portolan-sdi/portolan-spec) 仕様（v0.2.0）に沿って整備するためのデータ仕様書です。

Portolan は、STAC 1.1.0 の静的カタログ、GeoParquet、PMTiles を組み合わせて地理空間データを配る仕様です。この仕様書では、北海道が Shapefile と Excel で配っているデータを、どの列・型・処理で GeoParquet・Parquet・PMTiles と STAC のメタデータにするかを定めています。

> **北海道の公式データではありません。** 北海道が公開しているデータを、個人が Portolan の形式に変換して再配布する非公式コピー（mirror）の仕様です。

## 対象データ

北海道「森林計画関係資料オープンデータ」の「林小班区画及び森林資源データ」の 2 年分をサンプルとして扱います。

| 年 | カタログの名前 | 元のページ |
|---|---|---|
| 令和5年末現在 | `y2023` | <https://www.pref.hokkaido.lg.jp/sr/srk/218703.html> |
| 令和6年末現在 | `y2024` | <https://www.pref.hokkaido.lg.jp/sr/srk/252373.html> |

各年のカタログには、次の 5 つの collection があります。

| collection | 中身 | 形式 |
|---|---|---|
| `subcompartments` | 小班の区画（1 行 1 小班） | GeoParquet、PMTiles |
| `compartments` | 林班の区画（1 行 1 林班） | GeoParquet、PMTiles |
| `stand_layers` | 調査簿（1 行 小班 × 層） | Parquet |
| `codes` | 森林簿コードと名称 | Parquet |
| `municipalities` | 振興局・市町村 | Parquet |

## データの範囲と取扱の注意

- **範囲**：一般民有林（民有林のうち道有林を除いたもの）だけです。国有林と道有林は含みません。道有林のデータは、北海道の道有林課のサイトで公開されています
- **取扱の注意**：元のページの「資料の取扱の注意」によると、このデータは実測ではなく、地域森林計画樹立のため間接調査法により作成したものです。所有権等の諸権利、所有界、面積、木竹の評価等を証明するものではなく、現況と異なる場合があります

## 出典

この情報は北海道のオープンデータ（森林計画関係資料オープンデータ）を改変して利用しています。CC-BY4.0 Hokkaido

- 元のページ：<https://www.pref.hokkaido.lg.jp/sr/srk/A004/B003/>
- 改変の内容：[docs/spec.md の「10. 元データに加えた変更」](docs/spec.md#10-元データに加えた変更)

## ファイル

| ファイル | 内容 |
|---|---|
| [docs/spec.md](docs/spec.md) | データ仕様。カタログの構成、各 collection の列と型、形状の処理、STAC のメタデータ、PMTiles とスタイル、元データに加えた変更、年による違い |
| [docs/design-rationale.md](docs/design-rationale.md) | 設計の理由。spec.md の各決定について、理由と検討したほかの案を、spec.md と同じ章立てでまとめたもの |

## カタログ（データ）の置き場所

カタログは次の場所に置いています。ルートの `catalog.json` から、2 年分の各 collection をたどれます。

- <https://pub-68d4a01dd22641ef9e2ac3ef54da0b61.r2.dev/catalog.json>

## ライセンス

| 対象 | ライセンス |
|---|---|
| この仕様書の文章（`README.md`、`docs/`） | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ja)（著作権者：nakamori1024） |
| カタログのデータ | 元データの [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ja) を継承します（[北海道オープンデータ利用規約](https://www.pref.hokkaido.lg.jp/kz/dxs/opendata/hokkaido_od_kiyaku.html)） |
