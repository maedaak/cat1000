# list.jsとjekyllによる書誌「１万件」検索サンプルページ

## 概要
GitHub PagesでList.jsとJekyllを使うにあたり、書誌1万件の検索が可能なサンプルページを作成した。

## 使用データ
NACSIS-CATの総合目録データベースのCC-BY書誌情報を使用。
そのままだとRDFでありJekyllで処理できないため、大学図書館員のための図書館システム開発練習用データ( https://mbc.dl.itc.u-tokyo.ac.jp/data4librarysystem/ )の図書書誌TSVから、先頭１万件を抽出して使っている。

## TSVファイルをjekyllで処理するにあたり気づいたこと
Windowsのローカル環境のJekyllで試してから、GitHub Pagesに適用した。
その際に、Jekyllでエラーがでたので次の前処理を行っている。
- 半角の" (ダブルクォーテーション）を全角に変更
-- TSVのパースに影響があるように見えた
-- ただしく問題を回避する方法はありそうだが、今回はまず動かすことを優先している。
- 改行コードをLFに変更

## 作りこみ
現在はList.jsの基本的な機能をもとに、次の作りこみを行っている。
- ローディングのバーを追加
- ヒット件数の表示（可能かどうかを含め要確認）
- iOS Safari対応
- 大量リストに合わせ、ページネーション表示のパラメータ調整
- 大量リストに合わせ、searchDelay の値を750に
- ファジー検索プラグインを追加、これによりアルファベットの大文字小文字に関係なくマッチするようになった
- filterを使った絞り込み（言語に適用）

## 開発について
- Wiki ( https://github.com/maedaak/cat10000/wiki )を参照

## 参考
### code4lib japan 2021ライトニングトーク
- 発表資料 https://www.slideshare.net/genroku/web-listjs-jekyll-github-pages
- GitHub Pagesで作ったサンプルページ https://maedaak.github.io/listjs_jikyll-test
