---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619922"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging 設為 true 的 GridView 可能在離開檢視的最後一頁時引發 PageIndexChanging 事件

#### <a name="details"></a>詳細資料

.NET Framework 4.5 中的 Bug) 導致有時不會針對已啟用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 引發 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。 應用程式可以對叫用這些條件 (<xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 位在最後一個頁面上且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> 不同於 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>) 的 <code>Page_Load</code> 執行明確的 BindGrid，來解決這個問題。 或者，可以修改應用程式以允許分頁 (而不是自訂分頁)，因為該情況不會顯示此問題。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
