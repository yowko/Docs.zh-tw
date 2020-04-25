---
ms.openlocfilehash: 7a6b0b15de4295506ff03b8566c06010b918566c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158385"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="b0549-101">WinForms 方法現在會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="b0549-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="b0549-102">有些 Windows Forms 方法現在會<xref:System.ArgumentNullException>針對 null 引數擲回，而先前會<xref:System.NullReferenceException>在其擲回。</span><span class="sxs-lookup"><span data-stu-id="b0549-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b0549-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="b0549-103">Change description</span></span>

<span data-ttu-id="b0549-104">先前， <xref:System.NullReferenceException>如果傳遞的引數為 null，某些 Windows Forms 方法會擲回。</span><span class="sxs-lookup"><span data-stu-id="b0549-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="b0549-105">從 .NET 5.0 開始，這些方法現在會改<xref:System.ArgumentNullException>為擲回 null 引數的。</span><span class="sxs-lookup"><span data-stu-id="b0549-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="b0549-106">擲回<xref:System.ArgumentNullException>會符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="b0549-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="b0549-107">它也會藉由清楚地傳達引數為 null 和哪一個引數，來改善偵錯工具體驗。</span><span class="sxs-lookup"><span data-stu-id="b0549-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0549-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b0549-108">Version introduced</span></span>

<span data-ttu-id="b0549-109">.NET 5.0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="b0549-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="b0549-110">.NET 5.0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="b0549-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0549-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b0549-111">Recommended action</span></span>

<span data-ttu-id="b0549-112">如果您呼叫其中任何一種方法，而且您的程式<xref:System.NullReferenceException>代碼目前會攔截 null 自<xref:System.ArgumentNullException>變數的，請改為捕捉。</span><span class="sxs-lookup"><span data-stu-id="b0549-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="b0549-113">此外，請考慮更新程式碼，以避免將 null 引數傳遞給列出的方法。</span><span class="sxs-lookup"><span data-stu-id="b0549-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="b0549-114">類別</span><span class="sxs-lookup"><span data-stu-id="b0549-114">Category</span></span>

<span data-ttu-id="b0549-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0549-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0549-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b0549-116">Affected APIs</span></span>

<span data-ttu-id="b0549-117">從 .NET 5.0 Preview 1 開始：</span><span class="sxs-lookup"><span data-stu-id="b0549-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="b0549-118">從 .NET 5.0 Preview 2 開始：</span><span class="sxs-lookup"><span data-stu-id="b0549-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="b0549-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>（僅適用<xref:System.IO.Stream>于參數）</span><span class="sxs-lookup"><span data-stu-id="b0549-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
