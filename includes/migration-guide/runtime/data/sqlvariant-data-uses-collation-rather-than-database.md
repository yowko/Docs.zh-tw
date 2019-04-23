---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235147"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序

|   |   |
|---|---|
|詳細資料|<code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。|
|建議|這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。 依賴損毀資料的應用程式可能會失敗。|
|範圍|透明|
|版本|4.5|
|類型|執行階段|
