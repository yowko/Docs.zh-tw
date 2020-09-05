---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496420"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="cfd82-101">變更 TextBlock 控制項之父代的 IsEnabled 屬性會影響任何子控制項</span><span class="sxs-lookup"><span data-stu-id="cfd82-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="cfd82-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cfd82-102">Details</span></span>

<span data-ttu-id="cfd82-103">從 .NET Framework 4.6.2 開始，變更 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項之父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性，會影響 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項的任何子控制項 (例如超連結和按鈕)。在 .NET Framework 4.6.1 和舊版中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 內的控制項不一定會反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="cfd82-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cfd82-104">建議</span><span class="sxs-lookup"><span data-stu-id="cfd82-104">Suggestion</span></span>

<span data-ttu-id="cfd82-105">無。</span><span class="sxs-lookup"><span data-stu-id="cfd82-105">None.</span></span> <span data-ttu-id="cfd82-106">這項變更符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項內的之控制項的預期行為。</span><span class="sxs-lookup"><span data-stu-id="cfd82-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="cfd82-107">名稱</span><span class="sxs-lookup"><span data-stu-id="cfd82-107">Name</span></span>    | <span data-ttu-id="cfd82-108">值</span><span class="sxs-lookup"><span data-stu-id="cfd82-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cfd82-109">範圍</span><span class="sxs-lookup"><span data-stu-id="cfd82-109">Scope</span></span>   |<span data-ttu-id="cfd82-110">Minor</span><span class="sxs-lookup"><span data-stu-id="cfd82-110">Minor</span></span>|
|<span data-ttu-id="cfd82-111">版本</span><span class="sxs-lookup"><span data-stu-id="cfd82-111">Version</span></span>|<span data-ttu-id="cfd82-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="cfd82-112">4.6.2</span></span>|
|<span data-ttu-id="cfd82-113">類型</span><span class="sxs-lookup"><span data-stu-id="cfd82-113">Type</span></span>|<span data-ttu-id="cfd82-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="cfd82-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cfd82-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="cfd82-115">Affected APIs</span></span>

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
