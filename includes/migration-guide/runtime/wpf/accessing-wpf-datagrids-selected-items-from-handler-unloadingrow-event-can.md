---
ms.openlocfilehash: 4b87fb0161059eb9df919a64a9966c00177caf89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858622"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="4d9ab-101">從 DataGrid 的 UnloadingRow 事件處理常式存取 WPF DataGrid 的選取項目可能會導致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="4d9ab-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4d9ab-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4d9ab-102">Details</span></span>|<span data-ttu-id="4d9ab-103">由於 .NET Framework 4.5 中的 Bug)，涉及移除資料列之 <xref:System.Windows.Controls.DataGrid> 事件的事件處理常式，可能會在它們存取 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 屬性時導致擲回 <xref:System.NullReferenceException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="4d9ab-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="4d9ab-104">建議</span><span class="sxs-lookup"><span data-stu-id="4d9ab-104">Suggestion</span></span>|<span data-ttu-id="4d9ab-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="4d9ab-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="4d9ab-106">範圍</span><span class="sxs-lookup"><span data-stu-id="4d9ab-106">Scope</span></span>|<span data-ttu-id="4d9ab-107">次要</span><span class="sxs-lookup"><span data-stu-id="4d9ab-107">Minor</span></span>|
|<span data-ttu-id="4d9ab-108">版本</span><span class="sxs-lookup"><span data-stu-id="4d9ab-108">Version</span></span>|<span data-ttu-id="4d9ab-109">4.5</span><span class="sxs-lookup"><span data-stu-id="4d9ab-109">4.5</span></span>|
|<span data-ttu-id="4d9ab-110">類型</span><span class="sxs-lookup"><span data-stu-id="4d9ab-110">Type</span></span>|<span data-ttu-id="4d9ab-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="4d9ab-111">Runtime</span></span>|
|<span data-ttu-id="4d9ab-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4d9ab-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

