---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619929"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="d5b7f-101">Page.LoadComplete 事件不再導致 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結</span><span class="sxs-lookup"><span data-stu-id="d5b7f-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="d5b7f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5b7f-102">Details</span></span>

<span data-ttu-id="d5b7f-103"><xref:System.Web.UI.Page.LoadComplete> 事件不再使 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控制項叫用資料繫結，讓變更建立/更新/刪除參數。</span><span class="sxs-lookup"><span data-stu-id="d5b7f-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="d5b7f-104">這項變更可以消除來回存取資料庫的額外作業，防止重設控制項的值，並且產生與其他資料控制項 (例如 <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>) 一致的行為。</span><span class="sxs-lookup"><span data-stu-id="d5b7f-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="d5b7f-105">在像是應用程式倚賴於 <xref:System.Web.UI.Page.LoadComplete> 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。</span><span class="sxs-lookup"><span data-stu-id="d5b7f-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d5b7f-106">建議</span><span class="sxs-lookup"><span data-stu-id="d5b7f-106">Suggestion</span></span>

<span data-ttu-id="d5b7f-107">如果需要資料繫結，請在回傳初期的事件中手動叫用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="d5b7f-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="d5b7f-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d5b7f-108">Name</span></span>    | <span data-ttu-id="d5b7f-109">值</span><span class="sxs-lookup"><span data-stu-id="d5b7f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d5b7f-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d5b7f-110">Scope</span></span>   |<span data-ttu-id="d5b7f-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d5b7f-111">Edge</span></span>|
|<span data-ttu-id="d5b7f-112">版本</span><span class="sxs-lookup"><span data-stu-id="d5b7f-112">Version</span></span>|<span data-ttu-id="d5b7f-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d5b7f-113">4.5</span></span>|
|<span data-ttu-id="d5b7f-114">類型</span><span class="sxs-lookup"><span data-stu-id="d5b7f-114">Type</span></span>|<span data-ttu-id="d5b7f-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d5b7f-115">Runtime</span></span>|
