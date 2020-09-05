---
ms.openlocfilehash: 31ada197db36be192317e32a37a353d375d9cc65
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497042"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="f0d05-101">在 VirtualizingStackPanel 中捲動 WPF TreeView 或群組 ListBox 可能會造成停止回應</span><span class="sxs-lookup"><span data-stu-id="f0d05-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="f0d05-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0d05-102">Details</span></span>

<span data-ttu-id="f0d05-103">在 .NET Framework v4.5 中，如果檢視區有邊界 (例如在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 中的項目之間或在 ItemsPresenter 項目上)，在虛擬化堆疊面板中捲動 WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 可能會造成停止回應。</span><span class="sxs-lookup"><span data-stu-id="f0d05-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="f0d05-104">此外，在某些情況下，即使沒有邊界，檢視中不同大小的項目也可能會造成不穩定的情況。</span><span class="sxs-lookup"><span data-stu-id="f0d05-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0d05-105">建議</span><span class="sxs-lookup"><span data-stu-id="f0d05-105">Suggestion</span></span>

<span data-ttu-id="f0d05-106">您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="f0d05-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="f0d05-107">或者，如果所有包含的項目大小都相同，您也可以從虛擬化堆疊面板內的檢視集合 (例如 <xref:System.Windows.Controls.TreeView?displayProperty=fullName>) 移除邊界。</span><span class="sxs-lookup"><span data-stu-id="f0d05-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="f0d05-108">名稱</span><span class="sxs-lookup"><span data-stu-id="f0d05-108">Name</span></span>    | <span data-ttu-id="f0d05-109">值</span><span class="sxs-lookup"><span data-stu-id="f0d05-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0d05-110">範圍</span><span class="sxs-lookup"><span data-stu-id="f0d05-110">Scope</span></span>   |<span data-ttu-id="f0d05-111">主要</span><span class="sxs-lookup"><span data-stu-id="f0d05-111">Major</span></span>|
|<span data-ttu-id="f0d05-112">版本</span><span class="sxs-lookup"><span data-stu-id="f0d05-112">Version</span></span>|<span data-ttu-id="f0d05-113">4.5</span><span class="sxs-lookup"><span data-stu-id="f0d05-113">4.5</span></span>|
|<span data-ttu-id="f0d05-114">類型</span><span class="sxs-lookup"><span data-stu-id="f0d05-114">Type</span></span>|<span data-ttu-id="f0d05-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="f0d05-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f0d05-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f0d05-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)`

-->
