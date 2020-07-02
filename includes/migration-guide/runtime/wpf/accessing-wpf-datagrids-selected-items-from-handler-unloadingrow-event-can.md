---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620088"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="7c68e-101">從 DataGrid 的 UnloadingRow 事件處理常式存取 WPF DataGrid 的選取項目可能會導致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="7c68e-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="7c68e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7c68e-102">Details</span></span>

<span data-ttu-id="7c68e-103">由於 .NET Framework 4.5 中的 Bug)，涉及移除資料列之 <xref:System.Windows.Controls.DataGrid> 事件的事件處理常式，可能會在它們存取 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 屬性時導致擲回 <xref:System.NullReferenceException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="7c68e-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c68e-104">建議</span><span class="sxs-lookup"><span data-stu-id="7c68e-104">Suggestion</span></span>

<span data-ttu-id="7c68e-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="7c68e-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="7c68e-106">名稱</span><span class="sxs-lookup"><span data-stu-id="7c68e-106">Name</span></span>    | <span data-ttu-id="7c68e-107">值</span><span class="sxs-lookup"><span data-stu-id="7c68e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c68e-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="7c68e-108">Scope</span></span>   |<span data-ttu-id="7c68e-109">Minor</span><span class="sxs-lookup"><span data-stu-id="7c68e-109">Minor</span></span>|
|<span data-ttu-id="7c68e-110">版本</span><span class="sxs-lookup"><span data-stu-id="7c68e-110">Version</span></span>|<span data-ttu-id="7c68e-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7c68e-111">4.5</span></span>|
|<span data-ttu-id="7c68e-112">類型</span><span class="sxs-lookup"><span data-stu-id="7c68e-112">Type</span></span>|<span data-ttu-id="7c68e-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="7c68e-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7c68e-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7c68e-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
