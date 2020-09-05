---
ms.openlocfilehash: a84d72813a46d6bb39f4710b35d2c9dc859e30ef
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496973"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="2f3cf-101">Page.LoadComplete 事件不再導致 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結</span><span class="sxs-lookup"><span data-stu-id="2f3cf-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="2f3cf-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2f3cf-102">Details</span></span>

<span data-ttu-id="2f3cf-103"><xref:System.Web.UI.Page.LoadComplete> 事件不再使 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控制項叫用資料繫結，讓變更建立/更新/刪除參數。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="2f3cf-104">這項變更可以消除來回存取資料庫的額外作業，防止重設控制項的值，並且產生與其他資料控制項 (例如 <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>) 一致的行為。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="2f3cf-105">在像是應用程式倚賴於 <xref:System.Web.UI.Page.LoadComplete> 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2f3cf-106">建議</span><span class="sxs-lookup"><span data-stu-id="2f3cf-106">Suggestion</span></span>

<span data-ttu-id="2f3cf-107">如果需要資料繫結，請在回傳初期的事件中手動叫用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="2f3cf-108">名稱</span><span class="sxs-lookup"><span data-stu-id="2f3cf-108">Name</span></span>    | <span data-ttu-id="2f3cf-109">值</span><span class="sxs-lookup"><span data-stu-id="2f3cf-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2f3cf-110">範圍</span><span class="sxs-lookup"><span data-stu-id="2f3cf-110">Scope</span></span>   |<span data-ttu-id="2f3cf-111">Edge</span><span class="sxs-lookup"><span data-stu-id="2f3cf-111">Edge</span></span>|
|<span data-ttu-id="2f3cf-112">版本</span><span class="sxs-lookup"><span data-stu-id="2f3cf-112">Version</span></span>|<span data-ttu-id="2f3cf-113">4.5</span><span class="sxs-lookup"><span data-stu-id="2f3cf-113">4.5</span></span>|
|<span data-ttu-id="2f3cf-114">類型</span><span class="sxs-lookup"><span data-stu-id="2f3cf-114">Type</span></span>|<span data-ttu-id="2f3cf-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="2f3cf-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2f3cf-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2f3cf-116">Affected APIs</span></span>

<span data-ttu-id="2f3cf-117">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
