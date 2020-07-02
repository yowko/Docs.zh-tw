---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620018"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>選擇中斷以從不同的 4.5 SQL 產生還原為更簡單的 4.0 SQL 產生

#### <a name="details"></a>詳細資料

產生 JOIN 陳述式並包含限制作業呼叫 (不先使用 OrderBy) 的查詢，現在能產生更簡單的 SQL。 升級至 .NET Framework 4.5 之後，這些查詢會產生比舊版更複雜的 SQL。

#### <a name="suggestion"></a>建議

此功能預設為停用。 如果 Entity Framework 產生額外的 JOIN 陳述式而造成效能降低，您可以啟用這項功能，方法是在應用程式組態檔 (app.config) 的 <code>&lt;appSettings&gt;</code> 區段中新增下列項目：<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |透明|
|版本|4.5.2|
|類型|執行階段|
