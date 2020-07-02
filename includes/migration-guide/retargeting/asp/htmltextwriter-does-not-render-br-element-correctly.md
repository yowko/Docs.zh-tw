---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615618"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="62999-101">HtmlTextWriter 無法正確轉譯 `<br/>` 項目</span><span class="sxs-lookup"><span data-stu-id="62999-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="62999-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62999-102">Details</span></span>

<span data-ttu-id="62999-103">從 .NET Framework 4.6 開始，使用 `<BR />` 項目呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 將會正確地只插入一個 `<BR />` (而不是兩個)</span><span class="sxs-lookup"><span data-stu-id="62999-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62999-104">建議</span><span class="sxs-lookup"><span data-stu-id="62999-104">Suggestion</span></span>

<span data-ttu-id="62999-105">如果應用程式需要額外的 `<BR />` 標籤，則應該再次呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="62999-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="62999-106">請注意，這項行為變更只會影響以 .NET Framework 4.6 或更新版本為目標的應用程式，因此另一個做法是以舊版 .NET Framework 為目標，以取得舊版行為。</span><span class="sxs-lookup"><span data-stu-id="62999-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="62999-107">名稱</span><span class="sxs-lookup"><span data-stu-id="62999-107">Name</span></span>    | <span data-ttu-id="62999-108">值</span><span class="sxs-lookup"><span data-stu-id="62999-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62999-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="62999-109">Scope</span></span>   | <span data-ttu-id="62999-110">Edge</span><span class="sxs-lookup"><span data-stu-id="62999-110">Edge</span></span>        |
| <span data-ttu-id="62999-111">版本</span><span class="sxs-lookup"><span data-stu-id="62999-111">Version</span></span> | <span data-ttu-id="62999-112">4.6</span><span class="sxs-lookup"><span data-stu-id="62999-112">4.6</span></span>         |
| <span data-ttu-id="62999-113">類型</span><span class="sxs-lookup"><span data-stu-id="62999-113">Type</span></span>    | <span data-ttu-id="62999-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="62999-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="62999-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="62999-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
