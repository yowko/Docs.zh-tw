---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496659"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="20b7c-101">從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 會卸除焦點</span><span class="sxs-lookup"><span data-stu-id="20b7c-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="20b7c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="20b7c-102">Details</span></span>

<span data-ttu-id="20b7c-103">從其中一個 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的 <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> 事件處理常式呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit> 會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 失去焦點。</span><span class="sxs-lookup"><span data-stu-id="20b7c-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20b7c-104">建議</span><span class="sxs-lookup"><span data-stu-id="20b7c-104">Suggestion</span></span>

<span data-ttu-id="20b7c-105">此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。</span><span class="sxs-lookup"><span data-stu-id="20b7c-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="20b7c-106">或者，您也可以在呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> 之後明確重新選取 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>，來避免此 Bug。</span><span class="sxs-lookup"><span data-stu-id="20b7c-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="20b7c-107">名稱</span><span class="sxs-lookup"><span data-stu-id="20b7c-107">Name</span></span>    | <span data-ttu-id="20b7c-108">值</span><span class="sxs-lookup"><span data-stu-id="20b7c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20b7c-109">範圍</span><span class="sxs-lookup"><span data-stu-id="20b7c-109">Scope</span></span>   |<span data-ttu-id="20b7c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="20b7c-110">Edge</span></span>|
|<span data-ttu-id="20b7c-111">版本</span><span class="sxs-lookup"><span data-stu-id="20b7c-111">Version</span></span>|<span data-ttu-id="20b7c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="20b7c-112">4.5</span></span>|
|<span data-ttu-id="20b7c-113">類型</span><span class="sxs-lookup"><span data-stu-id="20b7c-113">Type</span></span>|<span data-ttu-id="20b7c-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="20b7c-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="20b7c-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="20b7c-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
