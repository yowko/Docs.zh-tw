---
ms.openlocfilehash: 6d804dd335cb18d5febc2ca5f794af92963bece1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620107"
---
### <a name="right-clicking-on-a-wpf-datagrid-row-header-changes-the-datagrid-selection"></a><span data-ttu-id="832f0-101">以滑鼠右鍵按一下 WPF DataGrid 資料列標頭會變更 DataGrid 選取項目</span><span class="sxs-lookup"><span data-stu-id="832f0-101">Right clicking on a WPF DataGrid row header changes the DataGrid selection</span></span>

#### <a name="details"></a><span data-ttu-id="832f0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="832f0-102">Details</span></span>

<span data-ttu-id="832f0-103">選取多個資料列時，若以滑鼠右鍵按一下選取的 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 資料列標頭，會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的選取項目變更為只有該資料列。</span><span class="sxs-lookup"><span data-stu-id="832f0-103">Right-clicking a selected <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> row header while multiple rows are selected results in the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s selection changing to only that row.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="832f0-104">建議</span><span class="sxs-lookup"><span data-stu-id="832f0-104">Suggestion</span></span>

<span data-ttu-id="832f0-105">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="832f0-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="832f0-106">名稱</span><span class="sxs-lookup"><span data-stu-id="832f0-106">Name</span></span>    | <span data-ttu-id="832f0-107">值</span><span class="sxs-lookup"><span data-stu-id="832f0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="832f0-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="832f0-108">Scope</span></span>   |<span data-ttu-id="832f0-109">Edge</span><span class="sxs-lookup"><span data-stu-id="832f0-109">Edge</span></span>|
|<span data-ttu-id="832f0-110">版本</span><span class="sxs-lookup"><span data-stu-id="832f0-110">Version</span></span>|<span data-ttu-id="832f0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="832f0-111">4.5</span></span>|
|<span data-ttu-id="832f0-112">類型</span><span class="sxs-lookup"><span data-stu-id="832f0-112">Type</span></span>|<span data-ttu-id="832f0-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="832f0-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="832f0-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="832f0-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.%23ctor></li></ul>|
