---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721060"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="6b0b7-101">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="6b0b7-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="6b0b7-102">A <xref:System.Windows.Forms.DataGridView> 現在會在滑鼠停留時顯示儲存格的文字和錯誤工具提示，並透過鍵盤選取。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="6b0b7-103">如果顯示工具提示，則 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b0b7-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="6b0b7-104">Change description</span></span>

<span data-ttu-id="6b0b7-105">在 .NET Core 3.1 之前， <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 已將屬性設定為的會在 `true` 滑鼠游標停留時，顯示儲存格文字和錯誤的工具提示。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="6b0b7-106">透過鍵盤選取資料格時，不會顯示工具提示（例如，使用 Tab 鍵、快速鍵或箭號導覽）。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="6b0b7-107">如果使用者編輯了資料格，而當 <xref:System.Windows.Forms.DataGridView> 仍然處於編輯模式時，將滑鼠停留在未設定屬性的資料格上，就會 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView.CellFormatting> 引發事件來格式化儲存格的文字，以便顯示在資料格中。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="6b0b7-108">為了符合協助工具標準，從 .NET Core 3.1 開始，將 <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性設定為的會 `true` 顯示資料格文字的工具提示，而不只是在資料格已暫留時，也會在透過鍵盤選取時出現的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="6b0b7-109">由於這項變更的結果， <xref:System.Windows.Forms.DataGridView.CellFormatting> 當*not* <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView> 處於編輯模式時，不會引發未設定屬性的資料格時，就不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="6b0b7-110">事件不會引發，因為暫留的資料格內容會顯示為工具提示，而不會顯示在資料格中。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b0b7-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6b0b7-111">Version introduced</span></span>

<span data-ttu-id="6b0b7-112">3.1</span><span class="sxs-lookup"><span data-stu-id="6b0b7-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b0b7-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6b0b7-113">Recommended action</span></span>

<span data-ttu-id="6b0b7-114"><xref:System.Windows.Forms.DataGridView.CellFormatting>當處於編輯模式時，重構相依于事件的任何程式碼 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="6b0b7-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="6b0b7-115">類別</span><span class="sxs-lookup"><span data-stu-id="6b0b7-115">Category</span></span>

<span data-ttu-id="6b0b7-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b0b7-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b0b7-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6b0b7-117">Affected APIs</span></span>

<span data-ttu-id="6b0b7-118">無</span><span class="sxs-lookup"><span data-stu-id="6b0b7-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
