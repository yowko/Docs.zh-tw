---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857492"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="bff29-101">變更 TextBlock 控制項之父代的 IsEnabled 屬性會影響任何子控制項</span><span class="sxs-lookup"><span data-stu-id="bff29-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bff29-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bff29-102">Details</span></span>|<span data-ttu-id="bff29-103">從 .NET Framework 4.6.2 開始，變更 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項之父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 屬性，會影響 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項的任何子控制項 (例如超連結和按鈕)。在 .NET Framework 4.6.1 和舊版中，<xref:System.Windows.Controls.TextBlock?displayProperty=name> 內的控制項不一定會反映 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="bff29-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=name> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=name> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=name> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=name> parent.</span></span>|
|<span data-ttu-id="bff29-104">建議</span><span class="sxs-lookup"><span data-stu-id="bff29-104">Suggestion</span></span>|<span data-ttu-id="bff29-105">無。</span><span class="sxs-lookup"><span data-stu-id="bff29-105">None.</span></span> <span data-ttu-id="bff29-106">這項變更符合 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項內的之控制項的預期行為。</span><span class="sxs-lookup"><span data-stu-id="bff29-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=name> control.</span></span>|
|<span data-ttu-id="bff29-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="bff29-107">Scope</span></span>|<span data-ttu-id="bff29-108">Minor</span><span class="sxs-lookup"><span data-stu-id="bff29-108">Minor</span></span>|
|<span data-ttu-id="bff29-109">版本</span><span class="sxs-lookup"><span data-stu-id="bff29-109">Version</span></span>|<span data-ttu-id="bff29-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="bff29-110">4.6.2</span></span>|
|<span data-ttu-id="bff29-111">類型</span><span class="sxs-lookup"><span data-stu-id="bff29-111">Type</span></span>|<span data-ttu-id="bff29-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="bff29-112">Runtime</span></span>|
|<span data-ttu-id="bff29-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bff29-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
