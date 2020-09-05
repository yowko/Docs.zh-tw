---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497778"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>還原序列化跨應用程式網域的物件會失敗

#### <a name="details"></a>詳細資料

在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。

#### <a name="suggestion"></a>建議

請參閱[緩和：在應用程式定義域之間還原序列化物件](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5.1|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
