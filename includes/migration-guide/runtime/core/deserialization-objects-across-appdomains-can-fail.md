---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619959"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>還原序列化跨應用程式網域的物件會失敗

#### <a name="details"></a>詳細資料

在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。

#### <a name="suggestion"></a>建議

請參閱[緩和：在應用程式定義域之間還原序列化物件](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5.1|
|類型|執行階段|
