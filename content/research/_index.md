---
title: "Research"
description: "自然言語処理とMeta-Attentionの研究"
layout: "article"
math: true # KaTeXを有効化
---

## 大学院での研究

### 研究テーマ

Value State Gated Meta Attention の開発

### 研究の全容

[先行研究(voita 2019)](https://arxiv.org/pdf/1905.09418)により、従来のTransformerアーキテクチャに内在するAttention Networkは8割から9割が削減可能であることが実験的に示されました。この結果により、よりロバストで効率的なAttention計算メカニズムの登場が求められています。私の研究の目的は、Transformer内部のAttention Networkにおいて動的重みづけを再度行うValue State Gated Meta Attention(VMA)を新たに提案し、性能の検証を行うことです。

### Attention Networkの課題

トークン入力列に対し一般的なAttention Networkは以下式でAttentionの計算を行い、出力yを得ます。
$$ y = Softmax(\frac{xW_q(xW_k)^T}{\sqrt d_k})xW_v $$
[先行研究](https://arxiv.org/pdf/1905.09418)において上式で計算されるAttention Networkを内在するTransformerは、WMT翻訳タスクにおいて79%のAttention Headの削減により約0.5%, 92%のAttention Headの削減により約10.5%の性能低下にとどまることが報告されました。これにより、現状のAttention Networkの計算では多くのAttention Headが削減可能なことが示され、計算効率性の面で非常に大きな課題を有していることが明らかになりました。

### VMAの提案

前述した課題に対し、私が提案するValue State Gated Attention (VMA) ではAttention Network内部に関係を一般化し、更に再度重みづけを付加する以下式で表されるアーキテクチャを用いることで、課題に潜在化している本質的な問題であるAttention Networkがトークン間の特徴を深く把握できないという問題を解決します。VMAアーキテクチャでは通常Attentionの出力yを以て以下式で出力zを得ます。

<div>
$$ y = Softmax(\frac{(kernel(y)W_{QP})(kernel(y)W_{KP})^T}{\sqrt d_k})y $$
</div>
