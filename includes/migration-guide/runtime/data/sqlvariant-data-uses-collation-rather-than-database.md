---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620006"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序

#### <a name="details"></a>詳細資料

<code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。

#### <a name="suggestion"></a>建議

這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。 依賴損毀資料的應用程式可能會失敗。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |透明|
|版本|4.5|
|類型|執行階段|
