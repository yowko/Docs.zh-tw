---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379250"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a><span data-ttu-id="92a57-101">在 VirtualizingStackPanel 中捲動 WPF TreeView 或群組 ListBox 可能會導致應用程式停止回應</span><span class="sxs-lookup"><span data-stu-id="92a57-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can result in an unresponsive application</span></span>

|   |   |
|---|---|
|<span data-ttu-id="92a57-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="92a57-102">Details</span></span>|<span data-ttu-id="92a57-103">使用 .NET Framework v4.5 時，如果檢視區有邊界 (例如在 <xref:System.Windows.Controls.TreeView?displayProperty=name> 中的項目之間或在 ItemsPresenter 項目上)，在虛擬化堆疊面板中捲動 WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> 可能會造成應用程式停止回應。</span><span class="sxs-lookup"><span data-stu-id="92a57-103">In .NET Framework 4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> in a virtualized stack panel can cause an application to become unresponsive if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=name>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="92a57-104">此外，在某些情況下，即使沒有邊界，檢視中不同大小的項目也可能會造成不穩定的情況。</span><span class="sxs-lookup"><span data-stu-id="92a57-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>|
|<span data-ttu-id="92a57-105">建議</span><span class="sxs-lookup"><span data-stu-id="92a57-105">Suggestion</span></span>|<span data-ttu-id="92a57-106">您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="92a57-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="92a57-107">或者，如果所有包含的項目大小都相同，您也可以從虛擬化堆疊面板內的檢視集合 (例如 <xref:System.Windows.Controls.TreeView?displayProperty=name>) 移除邊界。</span><span class="sxs-lookup"><span data-stu-id="92a57-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=name>s) within virtualized stack panels if all contained items are the same size.</span></span>|
|<span data-ttu-id="92a57-108">範圍</span><span class="sxs-lookup"><span data-stu-id="92a57-108">Scope</span></span>|<span data-ttu-id="92a57-109">主要</span><span class="sxs-lookup"><span data-stu-id="92a57-109">Major</span></span>|
|<span data-ttu-id="92a57-110">版本</span><span class="sxs-lookup"><span data-stu-id="92a57-110">Version</span></span>|<span data-ttu-id="92a57-111">4.5</span><span class="sxs-lookup"><span data-stu-id="92a57-111">4.5</span></span>|
|<span data-ttu-id="92a57-112">類型</span><span class="sxs-lookup"><span data-stu-id="92a57-112">Type</span></span>|<span data-ttu-id="92a57-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="92a57-113">Runtime</span></span>|
|<span data-ttu-id="92a57-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="92a57-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
