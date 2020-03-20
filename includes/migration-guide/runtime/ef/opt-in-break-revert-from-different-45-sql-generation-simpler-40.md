---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803193"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>選擇中斷以從不同的 4.5 SQL 產生還原為更簡單的 4.0 SQL 產生

|   |   |
|---|---|
|詳細資料|產生 JOIN 陳述式並包含限制作業呼叫 (不先使用 OrderBy) 的查詢，現在能產生更簡單的 SQL。 升級至 .NET Framework 4.5 之後，這些查詢會產生比舊版更複雜的 SQL。|
|建議|此功能預設為停用。 如果 Entity Framework 產生額外的 JOIN 陳述式而造成效能降低，您可以啟用這項功能，方法是在應用程式組態檔 (app.config) 的 <code>&lt;appSettings&gt;</code> 區段中新增下列項目：<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|影響範圍|透明|
|版本|4.5.2|
|類型|執行階段|
