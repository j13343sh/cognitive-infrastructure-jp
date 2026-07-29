# ケーススタディ：Artifact更新における状態分離

## 背景

Google Docs上のCanonical文書を改訂する実務では、内容追記、書式整形、見出し修復、読戻し、PDF出力、画像検査など、複数の処理が連続して行われた。

実行報告では、PDF出力に成功した一方で、書き出した全ページの画像検査は未実施であることが明示された。

この報告は、「ファイルが生成されたこと」と「生成物の品質が確認されたこと」を同一視しなかった。

---

## 確認された状態

一つのArtifact更新は、次の状態へ分解できた。

* 内容追記済み
* 文書全体の書式整形済み
* 見出し階層・Navigation修復済み
* 最終読戻し済み
* HTML上のスタイル確認済み
* PDF出力成功
* PDF全ページ画像検査は未実施

これらはすべて「更新完了」という一語でまとめることも可能である。

しかし、実際には各状態が意味する確認範囲は異なる。

```text
Artifact Updated
≠
Structure Verified
≠
Export Succeeded
≠
Render Fully Inspected
```

---

## Observation

同一Artifactに対して、Event、State、Verification Scopeが分離して記録された。

| 区分 | 例 |
| --- | --- |
| Event | PDF出力処理を実行した |
| Result State | PDFファイルが生成された |
| Verification | 出力成功を確認した |
| Unverified Scope | 全ページの画像品質は未検査 |

「PDF出力成功」という確認済み状態を保持しながら、「PDF品質確認完了」への昇格を停止している。

この停止は、Unknownをすべてへ拡大するものではない。

確認済み範囲と未確認範囲を局所化している。

---

## 認知基盤論への示唆

情報は、内容だけでなく、その情報がどの工程・確認範囲・時点を表しているかという状態情報を伴う。

「完了」という表現が複数工程を圧縮しすぎると、Future Generationは次の区別を失う可能性がある。

* 実行されたこと
* 成果物が生成されたこと
* 構造が確認されたこと
* 表示品質が確認されたこと
* 全対象が確認されたこと

したがって、Artifactに関する情報を継承可能にするには、状態名だけでなく、Verification Scopeと未確認範囲を保持する必要がある。

---

## Failure Preventionとしての状態分離

状態を分離しない場合、次の誤昇格が起こり得る。

```text
Export Succeeded
↓ 誤昇格
Visual Quality Confirmed
↓ 誤昇格
Artifact Complete
```

状態分離は、作業を細かく報告すること自体を目的としない。

Future Generationが、どこから検証を再開すべきか判断できるNavigationを残すことに意味がある。

---

## Exit Declarationとの構造的類似

同時期のHandover Protocolでは、継承工程終了、Exit Declaration、Role Exitも別の状態として扱われた。

これはArtifact品質確認とは対象が異なる。

しかし、両者には次の共通構造がある。

```text
Event発生
≠
状態成立
≠
成立確認
≠
次状態への遷移
```

現時点では、これを認知一般の法則とは扱わない。

異なる運用対象で同型の状態分離が観測された、という関連Observationとして保持する。

---

## Unknown

* 状態をどこまで細分化すれば実用上十分か
* 詳細化による記録コストと、誤昇格防止効果の均衡
* 異なるArtifact形式でも同じ状態分解が必要か
* Exit Declarationとの類似が共通原理によるものか、Protocol設計上の偶然か

---

## Conclusion

Canonical文書の更新実務では、内容更新、構造確認、PDF出力、全ページ画像検査が別の状態として扱われた。

本事例は、

**「処理を実行したこと、成果物が生成されたこと、その品質が確認されたこと、工程全体が完了したことは同一ではない」**

というObservationを記録するものである。

確認済み範囲と未確認範囲を分離することは、単なる慎重表現ではなく、Future Generationが検証を再開する位置を保持する情報構造として機能する。

