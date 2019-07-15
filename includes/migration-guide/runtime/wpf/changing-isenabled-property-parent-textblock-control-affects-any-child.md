---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857492"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="555a7-101">變更 TextBlock 控制項之父代的 IsEnabled 屬性會影響任何子控制項</span><span class="sxs-lookup"><span data-stu-id="555a7-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

|   |   |
|---|---|
|<span data-ttu-id="555a7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="555a7-102">Details</span></span>|<span data-ttu-id="555a7-103">從 .NET Framework 4.6.2 開始，變更 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項之父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 屬性，會影響 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項的任何子控制項 (例如超連結和按鈕)。在 .NET Framework 4.6.1 和舊版中，<xref:System.Windows.Controls.TextBlock?displayProperty=name> 內的控制項不一定會反映 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="555a7-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=name> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=name> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=name> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=name> parent.</span></span>|
|<span data-ttu-id="555a7-104">建議</span><span class="sxs-lookup"><span data-stu-id="555a7-104">Suggestion</span></span>|<span data-ttu-id="555a7-105">無。</span><span class="sxs-lookup"><span data-stu-id="555a7-105">None.</span></span> <span data-ttu-id="555a7-106">這項變更符合 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控制項內的之控制項的預期行為。</span><span class="sxs-lookup"><span data-stu-id="555a7-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=name> control.</span></span>|
|<span data-ttu-id="555a7-107">範圍</span><span class="sxs-lookup"><span data-stu-id="555a7-107">Scope</span></span>|<span data-ttu-id="555a7-108">次要</span><span class="sxs-lookup"><span data-stu-id="555a7-108">Minor</span></span>|
|<span data-ttu-id="555a7-109">版本</span><span class="sxs-lookup"><span data-stu-id="555a7-109">Version</span></span>|<span data-ttu-id="555a7-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="555a7-110">4.6.2</span></span>|
|<span data-ttu-id="555a7-111">類型</span><span class="sxs-lookup"><span data-stu-id="555a7-111">Type</span></span>|<span data-ttu-id="555a7-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="555a7-112">Runtime</span></span>|
|<span data-ttu-id="555a7-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="555a7-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

