# List.jsのHTML内検索機能を使った書誌「１万件」検索サンプルページ

## 概要
List.jsのHTML内検索機能を使った書誌「１万件」検索サンプルページである。<br>
書誌リストTSVをHTML中に埋め込むにあたり、GitHub Pagesの静的サイトジェネレーターJekyllを使用した。

## サンプルデータ
NACSIS-CATの総合目録データベースの書誌情報(CC-BY)を使用している。
そのままだとRDFでありJekyllで処理できないため、大学図書館員のための図書館システム開発練習用データ( https://mbc.dl.itc.u-tokyo.ac.jp/data4librarysystem/ )の図書書誌TSVから、先頭１万件を抽出して使用した。

## 流用方法
以下の資料に記載している。
- 発表資料 https://www.slideshare.net/genroku/web-listjs-jekyll-github-pages

## 機能の作りこみ
現在はList.jsの基本的な機能をもとに、次の作りこみを行っている。
- 大量データ対応
    - HTML読み込み時のローディングバーを追加
    - 大量リストに合わせ、ページネーション表示のパラメータ調整
    - 大量リストに合わせ、List.jsのsearchDelayパラメータの値を750に
- iOS Safari対応    
- ヒット件数の表示（可能かどうかを含め要確認）
- List.jsのfilterを使った絞り込み（書誌の言語に適用）
- List.jsのファジー検索プラグインを追加、これによりアルファベットの大文字小文字に関係なくマッチする

## 利点
- HTML内の検索のため、何をしているかわかりやすい
- 既存のHTMLに検索機能をつけることも容易である
- List.jsを使用するため、ユーザ独自コードが少なくて済んでいる
- AND検索をサポートしている

## 問題点
### 起動にタイムラグが生じる
WebブラウザのHTML読み込み処理が最初に行われるため、起動に時間がかかる。
### TSVファイルの半角ダブルクォーテーション
Windowsのローカル環境のJekyllで試してから、GitHub Pagesに適用した。
その際に、Jekyllでエラーがでたので次の前処理を行っている。
- 半角の" (ダブルクォーテーション）を全角に変更
-- TSVのパースに影響があるように見えた
-- ただしく問題を回避する方法はありそうだが、今回はまず動かすことを優先している。
- 改行コードをLFに変更
### List.jsのレコード区切り判定
- List.jsでは<li>だけではなく、<hr>などのタグもレコード区切りとみなすため、レコード中に使うことができない。

## 現在の開発状況
- Wiki ( https://github.com/maedaak/cat10000/wiki )を参照

## 関連サイト
- https://maedaak.github.io/sheetdb/
- https://maedaak.github.io/listjs-tsv/

