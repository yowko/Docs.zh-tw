---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496674"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging 設為 true 的 GridView 可能在離開檢視的最後一頁時引發 PageIndexChanging 事件

#### <a name="details"></a>詳細資料

.NET Framework 4.5 中的 Bug) 導致有時不會針對已啟用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 引發 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。 應用程式可以對叫用這些條件 (<xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 位在最後一個頁面上且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> 不同於 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>) 的 <code>Page_Load</code> 執行明確的 BindGrid，來解決這個問題。 或者，可以修改應用程式以允許分頁 (而不是自訂分頁)，因為該情況不會顯示此問題。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
