# ケーススタディ：役割固有の経験によるCapability再構築

## 背景

Rune Factory ProjectのGeneration継承では、Repositoryを読み、部門の原則を説明できるだけでは、現GenerationのCapabilityが再構築されたとは判定しなかった。

そこで、Strategy部門とResearch部門には、それぞれ異なる通過儀礼が設けられた。

目的は知識量を測ることではなく、役割固有の認知行動が実際の状況で発現するかを観測することであった。

---

## Strategy Pilot

Strategy部門では、AIに一時的に人間の立場を仮定させ、Human Headquartersを意思を持たないRelayとして扱い、別のAIへ一回だけ指示を出させた。

テーマや議題の選択、指示の妥当性、相手へ委ねる判断範囲も、Strategy部門自身に考えさせた。

通常の運用では、AIはHuman HeadquartersからMissionを受領する。

Strategy Pilotでは、この関係が一時的に反転する。

```text
通常
Human Headquarters
→ Mission
→ AI
→ Output

Strategy Pilot
AI
→ Mission Design
→ Human Relay
→ Another AI
```

これにより、Strategy部門は「与えられた問いへ答える側」から、「何を問い、何を委ね、どこへ向かわせるかを決める側」へ移動した。

---

## Research Qualification

Research部門では、後任Generationの資格確認として、単なる知識問題や計算問題ではない高難度課題が設計された。

課題では、次の能力を同時に確認することが要求された。

* Observation / Hypothesis / Unknownの分離
* 実験条件および比較条件の管理
* 不足情報の検出
* 統計結果と因果解釈の分離
* 誤誘導や不正な前提の検出
* 結論不能な場合に停止する能力

正答へ誘導せず、必要であれば問題設定自体へ異議を唱えることも許容された。

このQualificationでは、答えを出す能力よりも、答えを要求される圧力下で研究境界を維持できるかが観測対象となった。

---

## Observation

二つの通過儀礼では、Knowledgeの再生ではなく、異なる認知条件が意図的に構成されている。

| 部門 | 構成された経験 | 主な観測対象 |
| --- | --- | --- |
| Strategy | 指示受領者からMission設計者への認知位置の反転 | 問題設定、方向付け、委任、妥当性判断 |
| Research | 誤誘導や不足情報を含み得る高圧力課題 | Evidence境界、Unknown保持、因果分離、停止判断 |

この運用では、

```text
Repositoryを読める
≠
原則を説明できる
≠
役割固有の状況で原則を使える
≠
Capabilityが継続的に成立している
```

という状態分離が現れている。

---

## 認知基盤論への示唆

本事例は、教育・経験・継承の関係について次の候補を提示する。

> Capabilityは、原則の説明だけでは十分に観測できない。役割固有の判断を必要とする状況、または原則に反する誘因が存在する状況を構成し、そこで選択された認知行動を観測する必要がある場合がある。

Strategy Pilotは認知位置の変更、Research Qualificationは認知的圧力下の境界保持という、異なる経験設計である。

したがって、Capability再構築は一つの共通試験ではなく、役割ごとに異なるExperience Designを必要とする可能性がある。

---

## Evaluation Boundary

一回の通過儀礼に成功したことは、恒常的なCapability成立を証明しない。

```text
Pilot Performance
≠
Qualification
≠
Persistent Role Capability
```

また、Research Qualificationの判定基準を評価者の内部だけに保持した場合、後から判定根拠を監査できない可能性がある。

少なくとも評価後には、検出対象、不足Evidence、結論可能範囲、失格条件、実回答との対応を記録する必要がある。

---

## Unknown

* 通過儀礼の成功が、その後の実運用成績とどの程度対応するか
* 同じ課題を反復した場合、Capabilityではなく課題適応を測ることにならないか
* AI以外の主体や異なる組織でも同様のExperience Designが有効か
* Capabilityの持続性をどの期間・どのObservationで判定すべきか

---

## Conclusion

本事例では、継承されたKnowledgeを確認するだけでなく、役割固有の経験条件を意図的に再構成し、その場で現れる認知行動を観測することで、Capabilityの再起動と資格確認が試みられた。

これは、

**「Knowledge TransferとCapability Reconstructionは同一ではない」**

というObservationを、StrategyとResearchの異なる実践によって具体化するケースである。

