---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621108"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="ed34c-101">變更 TextBlock 控制項之父代的 IsEnabled 屬性會影響任何子控制項</span><span class="sxs-lookup"><span data-stu-id="ed34c-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="ed34c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ed34c-102">Details</span></span>

<span data-ttu-id="ed34c-103">從 .NET Framework 4.6.2 開始，變更 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項之父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性，會影響 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項的任何子控制項 (例如超連結和按鈕)。在 .NET Framework 4.6.1 和舊版中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 內的控制項不一定會反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="ed34c-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed34c-104">建議</span><span class="sxs-lookup"><span data-stu-id="ed34c-104">Suggestion</span></span>

<span data-ttu-id="ed34c-105">無。</span><span class="sxs-lookup"><span data-stu-id="ed34c-105">None.</span></span> <span data-ttu-id="ed34c-106">這項變更符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項內的之控制項的預期行為。</span><span class="sxs-lookup"><span data-stu-id="ed34c-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="ed34c-107">名稱</span><span class="sxs-lookup"><span data-stu-id="ed34c-107">Name</span></span>    | <span data-ttu-id="ed34c-108">值</span><span class="sxs-lookup"><span data-stu-id="ed34c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed34c-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="ed34c-109">Scope</span></span>   |<span data-ttu-id="ed34c-110">Minor</span><span class="sxs-lookup"><span data-stu-id="ed34c-110">Minor</span></span>|
|<span data-ttu-id="ed34c-111">版本</span><span class="sxs-lookup"><span data-stu-id="ed34c-111">Version</span></span>|<span data-ttu-id="ed34c-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ed34c-112">4.6.2</span></span>|
|<span data-ttu-id="ed34c-113">類型</span><span class="sxs-lookup"><span data-stu-id="ed34c-113">Type</span></span>|<span data-ttu-id="ed34c-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="ed34c-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed34c-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ed34c-115">Affected APIs</span></span>

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
