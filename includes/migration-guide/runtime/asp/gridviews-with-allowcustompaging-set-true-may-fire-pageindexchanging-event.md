---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496674"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="43cb8-101">AllowCustomPaging 設為 true 的 GridView 可能在離開檢視的最後一頁時引發 PageIndexChanging 事件</span><span class="sxs-lookup"><span data-stu-id="43cb8-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="43cb8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="43cb8-102">Details</span></span>

<span data-ttu-id="43cb8-103">.NET Framework 4.5 中的 Bug) 導致有時不會針對已啟用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 引發 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="43cb8-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="43cb8-104">建議</span><span class="sxs-lookup"><span data-stu-id="43cb8-104">Suggestion</span></span>

<span data-ttu-id="43cb8-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="43cb8-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="43cb8-106">應用程式可以對叫用這些條件 (<xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 位在最後一個頁面上且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> 不同於 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>) 的 <code>Page_Load</code> 執行明確的 BindGrid，來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="43cb8-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="43cb8-107">或者，可以修改應用程式以允許分頁 (而不是自訂分頁)，因為該情況不會顯示此問題。</span><span class="sxs-lookup"><span data-stu-id="43cb8-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="43cb8-108">名稱</span><span class="sxs-lookup"><span data-stu-id="43cb8-108">Name</span></span>    | <span data-ttu-id="43cb8-109">值</span><span class="sxs-lookup"><span data-stu-id="43cb8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="43cb8-110">範圍</span><span class="sxs-lookup"><span data-stu-id="43cb8-110">Scope</span></span>   |<span data-ttu-id="43cb8-111">Minor</span><span class="sxs-lookup"><span data-stu-id="43cb8-111">Minor</span></span>|
|<span data-ttu-id="43cb8-112">版本</span><span class="sxs-lookup"><span data-stu-id="43cb8-112">Version</span></span>|<span data-ttu-id="43cb8-113">4.5</span><span class="sxs-lookup"><span data-stu-id="43cb8-113">4.5</span></span>|
|<span data-ttu-id="43cb8-114">類型</span><span class="sxs-lookup"><span data-stu-id="43cb8-114">Type</span></span>|<span data-ttu-id="43cb8-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="43cb8-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="43cb8-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="43cb8-116">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
