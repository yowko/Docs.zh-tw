---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497429"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序

#### <a name="details"></a>詳細資料

<code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。

#### <a name="suggestion"></a>建議

這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。 依賴損毀資料的應用程式可能會失敗。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |透明|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
