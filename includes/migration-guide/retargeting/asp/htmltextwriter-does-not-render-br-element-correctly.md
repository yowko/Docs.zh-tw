---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234394"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="d24f7-101">HtmlTextWriter 無法正確轉譯 `<br/>` 項目</span><span class="sxs-lookup"><span data-stu-id="d24f7-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d24f7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d24f7-102">Details</span></span>|<span data-ttu-id="d24f7-103">從 .NET Framework 4.6 開始，使用 <code>&lt;BR /&gt;</code> 項目呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 將會正確地只插入一個 <code>&lt;BR /&gt;</code> (而不是兩個)</span><span class="sxs-lookup"><span data-stu-id="d24f7-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="d24f7-104">建議</span><span class="sxs-lookup"><span data-stu-id="d24f7-104">Suggestion</span></span>|<span data-ttu-id="d24f7-105">如果應用程式需要額外的 <code>&lt;BR /&gt;</code> 標籤，則應該再次呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="d24f7-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="d24f7-106">請注意，這項行為變更只會影響以 .NET Framework 4.6 或更新版本為目標的應用程式，因此另一個做法是以舊版 .NET Framework 為目標，以取得舊版行為。</span><span class="sxs-lookup"><span data-stu-id="d24f7-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="d24f7-107">範圍</span><span class="sxs-lookup"><span data-stu-id="d24f7-107">Scope</span></span>|<span data-ttu-id="d24f7-108">Edge</span><span class="sxs-lookup"><span data-stu-id="d24f7-108">Edge</span></span>|
|<span data-ttu-id="d24f7-109">版本</span><span class="sxs-lookup"><span data-stu-id="d24f7-109">Version</span></span>|<span data-ttu-id="d24f7-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d24f7-110">4.6</span></span>|
|<span data-ttu-id="d24f7-111">類型</span><span class="sxs-lookup"><span data-stu-id="d24f7-111">Type</span></span>|<span data-ttu-id="d24f7-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d24f7-112">Retargeting</span></span>|
|<span data-ttu-id="d24f7-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d24f7-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
