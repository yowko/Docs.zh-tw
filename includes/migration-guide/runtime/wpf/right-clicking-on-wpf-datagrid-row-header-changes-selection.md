---
ms.openlocfilehash: e1faee846627b22b88eb888d6241d47d8ea6ea06
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497859"
---
### <a name="right-clicking-on-a-wpf-datagrid-row-header-changes-the-datagrid-selection"></a><span data-ttu-id="dd133-101">以滑鼠右鍵按一下 WPF DataGrid 資料列標頭會變更 DataGrid 選取項目</span><span class="sxs-lookup"><span data-stu-id="dd133-101">Right clicking on a WPF DataGrid row header changes the DataGrid selection</span></span>

#### <a name="details"></a><span data-ttu-id="dd133-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd133-102">Details</span></span>

<span data-ttu-id="dd133-103">選取多個資料列時，若以滑鼠右鍵按一下選取的 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 資料列標頭，會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的選取項目變更為只有該資料列。</span><span class="sxs-lookup"><span data-stu-id="dd133-103">Right-clicking a selected <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> row header while multiple rows are selected results in the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s selection changing to only that row.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dd133-104">建議</span><span class="sxs-lookup"><span data-stu-id="dd133-104">Suggestion</span></span>

<span data-ttu-id="dd133-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="dd133-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="dd133-106">名稱</span><span class="sxs-lookup"><span data-stu-id="dd133-106">Name</span></span>    | <span data-ttu-id="dd133-107">值</span><span class="sxs-lookup"><span data-stu-id="dd133-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dd133-108">範圍</span><span class="sxs-lookup"><span data-stu-id="dd133-108">Scope</span></span>   |<span data-ttu-id="dd133-109">Edge</span><span class="sxs-lookup"><span data-stu-id="dd133-109">Edge</span></span>|
|<span data-ttu-id="dd133-110">版本</span><span class="sxs-lookup"><span data-stu-id="dd133-110">Version</span></span>|<span data-ttu-id="dd133-111">4.5</span><span class="sxs-lookup"><span data-stu-id="dd133-111">4.5</span></span>|
|<span data-ttu-id="dd133-112">類型</span><span class="sxs-lookup"><span data-stu-id="dd133-112">Type</span></span>|<span data-ttu-id="dd133-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="dd133-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="dd133-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dd133-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.#ctor`

-->
