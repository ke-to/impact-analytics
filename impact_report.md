# キャンペーンの効果測定レポート

## 基本情報
今回のレポートに含まれるデータは以下。

- 取得期間： `r min(causal_impact_web_access$time)`から`r max(causal_impact_web_access$time)`
- ユーザー数合計： `r sum(causal_impact_web_access_raw$users)`
- 国数： `r n_distinct(causal_impact_web_access_raw$country)`

## キャンペーン内容
日本を対象にあるキャンペーンを実施した。
詳細についてはサンプルなので省略する。

## 効果
もしキャンペーンを実施しなかった場合と比較すると、ユーザー数は`r sum(causal_impact_web_access_2_copy_1$上昇率)*100`%`r if (sum(causal_impact_web_access_2_copy_1$上昇率) > 0){return("上昇")}else{return("下降")}`した。

```{exploratory}
/causal_impact_web_access_2/viz/1
```

__キャンペーンを実施しなかった場合の算出について__
キャンペーンを実施していない かつ 日本の傾向と似ている以下の国からMCMCの手法を使って算出している。

```{exploratory}
/causal_impact_web_access_1/viz/1
```


### サイト全体の効果
他のキャンペーンの効果を含めたサイト全体のユーザー数の推移。
全体的にも上昇している。
```{exploratory}
/causal_impact_web_access/viz/3
```

### ノイズを取り除いた結果
このキャンペーンは`r max(causal_impact_web_access$time)`時点でユーザー約`r sum(causal_impact_web_access_2_copy_1$獲得数)`人の獲得に貢献した。
信頼区間は00-00でこの範囲より外にある確率は5%以下である。
```{exploratory}
/causal_impact_web_access/viz/4
```


## 不明点
- 信頼区間はどの指標の合計（平均）なのか
- sum関数の結果がおかしなことになっている（現状表示されている表記がなんなのかわからないので検索することもできず、、）
