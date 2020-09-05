---
ms.openlocfilehash: 1487e32ffca7b4bbebb5edac7efc8961ac05723b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497202"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="3eab1-101">從 DataGrid 的 UnloadingRow 事件處理常式存取 WPF DataGrid 的選取項目可能會導致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="3eab1-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="3eab1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3eab1-102">Details</span></span>

<span data-ttu-id="3eab1-103">由於 .NET Framework 4.5 中的 Bug)，涉及移除資料列之 <xref:System.Windows.Controls.DataGrid> 事件的事件處理常式，可能會在它們存取 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 屬性時導致擲回 <xref:System.NullReferenceException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3eab1-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3eab1-104">建議</span><span class="sxs-lookup"><span data-stu-id="3eab1-104">Suggestion</span></span>

<span data-ttu-id="3eab1-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="3eab1-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="3eab1-106">名稱</span><span class="sxs-lookup"><span data-stu-id="3eab1-106">Name</span></span>    | <span data-ttu-id="3eab1-107">值</span><span class="sxs-lookup"><span data-stu-id="3eab1-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3eab1-108">範圍</span><span class="sxs-lookup"><span data-stu-id="3eab1-108">Scope</span></span>   |<span data-ttu-id="3eab1-109">Minor</span><span class="sxs-lookup"><span data-stu-id="3eab1-109">Minor</span></span>|
|<span data-ttu-id="3eab1-110">版本</span><span class="sxs-lookup"><span data-stu-id="3eab1-110">Version</span></span>|<span data-ttu-id="3eab1-111">4.5</span><span class="sxs-lookup"><span data-stu-id="3eab1-111">4.5</span></span>|
|<span data-ttu-id="3eab1-112">類型</span><span class="sxs-lookup"><span data-stu-id="3eab1-112">Type</span></span>|<span data-ttu-id="3eab1-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="3eab1-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3eab1-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3eab1-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.Controls.DataGrid.UnloadingRow`
- `E:System.Windows.Controls.DataGrid.UnloadingRowDetails`

-->
