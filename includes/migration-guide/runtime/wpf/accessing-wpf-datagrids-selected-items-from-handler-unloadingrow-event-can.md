---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803472"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="5d314-101">從 DataGrid 的 UnloadingRow 事件處理常式存取 WPF DataGrid 的選取項目可能會導致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="5d314-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5d314-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d314-102">Details</span></span>|<span data-ttu-id="5d314-103">由於 .NET Framework 4.5 中的 Bug)，涉及移除資料列之 <xref:System.Windows.Controls.DataGrid> 事件的事件處理常式，可能會在它們存取 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 屬性時導致擲回 <xref:System.NullReferenceException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="5d314-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="5d314-104">建議</span><span class="sxs-lookup"><span data-stu-id="5d314-104">Suggestion</span></span>|<span data-ttu-id="5d314-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="5d314-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="5d314-106">範圍</span><span class="sxs-lookup"><span data-stu-id="5d314-106">Scope</span></span>|<span data-ttu-id="5d314-107">次要</span><span class="sxs-lookup"><span data-stu-id="5d314-107">Minor</span></span>|
|<span data-ttu-id="5d314-108">版本</span><span class="sxs-lookup"><span data-stu-id="5d314-108">Version</span></span>|<span data-ttu-id="5d314-109">4.5</span><span class="sxs-lookup"><span data-stu-id="5d314-109">4.5</span></span>|
|<span data-ttu-id="5d314-110">類型</span><span class="sxs-lookup"><span data-stu-id="5d314-110">Type</span></span>|<span data-ttu-id="5d314-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="5d314-111">Runtime</span></span>|
|<span data-ttu-id="5d314-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5d314-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
