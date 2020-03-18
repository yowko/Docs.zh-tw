---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567354"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="cbc02-101">如果顯示工具提示，則不引發儲存格格式事件</span><span class="sxs-lookup"><span data-stu-id="cbc02-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="cbc02-102">現在<xref:System.Windows.Forms.DataGridView>，當滑鼠懸停並通過鍵盤選擇時，將顯示儲存格的文本和錯誤工具提示。</span><span class="sxs-lookup"><span data-stu-id="cbc02-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="cbc02-103">如果顯示工具提示，則不會引發<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>該事件。</span><span class="sxs-lookup"><span data-stu-id="cbc02-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cbc02-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="cbc02-104">Change description</span></span>

<span data-ttu-id="cbc02-105">在 .NET Core 3.1<xref:System.Windows.Forms.DataGridView>之前，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>將屬性設置為`true`顯示儲存格文本的工具提示，當儲存格被滑鼠懸停時，錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbc02-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="cbc02-106">當通過鍵盤選擇儲存格時（例如，通過使用 Tab 鍵、快速鍵或箭頭導航），不會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="cbc02-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="cbc02-107">如果使用者編輯了儲存格，然後，當<xref:System.Windows.Forms.DataGridView>仍處於編輯模式時，將滑鼠懸停在沒有<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>屬性集的儲存格上，則會引發一個<xref:System.Windows.Forms.DataGridView.CellFormatting>事件來設置儲存格的文本格式，以便顯示在儲存格中。</span><span class="sxs-lookup"><span data-stu-id="cbc02-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="cbc02-108">為了滿足協助工具標準，從 .NET Core 3.1<xref:System.Windows.Forms.DataGridView>開始，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>該屬性設置為`true`顯示儲存格文本的工具提示，不僅在儲存格懸停時，而且通過鍵盤選擇時的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbc02-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="cbc02-109">由於此更改，當在 編輯<xref:System.Windows.Forms.DataGridView.CellFormatting>模式下將沒有<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>屬性集的儲存格懸停時，<xref:System.Windows.Forms.DataGridView>*不會*引發事件。</span><span class="sxs-lookup"><span data-stu-id="cbc02-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="cbc02-110">不會引發該事件，因為懸停儲存格的內容顯示為工具提示，而不是顯示在儲存格中。</span><span class="sxs-lookup"><span data-stu-id="cbc02-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cbc02-111">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="cbc02-111">Version introduced</span></span>

<span data-ttu-id="cbc02-112">3.1</span><span class="sxs-lookup"><span data-stu-id="cbc02-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cbc02-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="cbc02-113">Recommended action</span></span>

<span data-ttu-id="cbc02-114">重構任何依賴于<xref:System.Windows.Forms.DataGridView.CellFormatting>事件的代碼，<xref:System.Windows.Forms.DataGridView>而處於編輯模式。</span><span class="sxs-lookup"><span data-stu-id="cbc02-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="cbc02-115">類別</span><span class="sxs-lookup"><span data-stu-id="cbc02-115">Category</span></span>

<span data-ttu-id="cbc02-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbc02-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cbc02-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="cbc02-117">Affected APIs</span></span>

<span data-ttu-id="cbc02-118">無法通過 API 分析檢測。</span><span class="sxs-lookup"><span data-stu-id="cbc02-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
