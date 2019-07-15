---
ms.openlocfilehash: a7a8bd1a9823a621f3a63c6877da9454489b48fd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858551"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>AllowCustomPaging 設為 true 的 GridView 可能在離開檢視的最後一頁時引發 PageIndexChanging 事件

|   |   |
|---|---|
|詳細資料|.NET Framework 4.5 中的 Bug) 導致有時不會針對已啟用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=name> 引發 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name>。|
|建議|此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。 應用程式可以對叫用這些條件 (<xref:System.Web.UI.WebControls.GridView?displayProperty=name> 位在最後一個頁面上且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> 不同於 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>) 的 <code>Page_Load</code> 執行明確的 BindGrid，來解決這個問題。 或者，可以修改應用程式以允許分頁 (而不是自訂分頁)，因為該情況不會顯示此問題。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

