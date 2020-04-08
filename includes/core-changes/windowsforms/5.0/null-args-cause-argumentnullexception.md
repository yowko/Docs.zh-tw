---
ms.openlocfilehash: 63959c240b2fe16e086b97881a5a1792035bb3f8
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888102"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="e3eae-101">WinForms API 現在引發參數無效</span><span class="sxs-lookup"><span data-stu-id="e3eae-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="e3eae-102">一個 Windows 的<xref:System.ArgumentNullException>相檔方法為 null 參數<xref:System.NullReferenceException>引發一個參數, 它會引發一個 。</span><span class="sxs-lookup"><span data-stu-id="e3eae-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e3eae-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e3eae-103">Change description</span></span>

<span data-ttu-id="e3eae-104">以前,某些 Windows 窗<xref:System.NullReferenceException>體方法 引發 if 傳遞了 null 的參數。</span><span class="sxs-lookup"><span data-stu-id="e3eae-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="e3eae-105">從 .NET 5.0 開始,<xref:System.ArgumentNullException>這些方法現在將改為為 null 參數。</span><span class="sxs-lookup"><span data-stu-id="e3eae-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="e3eae-106">引發<xref:System.ArgumentNullException>符合 .NET 運行時的行為。</span><span class="sxs-lookup"><span data-stu-id="e3eae-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e3eae-107">它還通過清楚地傳達參數為空以及參數為空來改善調試體驗。</span><span class="sxs-lookup"><span data-stu-id="e3eae-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e3eae-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="e3eae-108">Version introduced</span></span>

<span data-ttu-id="e3eae-109">.NET 5.0 預覽 1\*</span><span class="sxs-lookup"><span data-stu-id="e3eae-109">.NET 5.0 Preview 1\</span></span>
<span data-ttu-id="e3eae-110">.NET 5.0 預覽 2</span><span class="sxs-lookup"><span data-stu-id="e3eae-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e3eae-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e3eae-111">Recommended action</span></span>

<span data-ttu-id="e3eae-112">如果呼叫這些方法中的任何一個,並且代碼目前捕捉<xref:System.NullReferenceException>for null 參數,請<xref:System.ArgumentNullException>改為 捕捉 。</span><span class="sxs-lookup"><span data-stu-id="e3eae-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="e3eae-113">此外,請考慮更新代碼以防止將空參數傳遞給列出的方法。</span><span class="sxs-lookup"><span data-stu-id="e3eae-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="e3eae-114">類別</span><span class="sxs-lookup"><span data-stu-id="e3eae-114">Category</span></span>

<span data-ttu-id="e3eae-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3eae-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3eae-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e3eae-116">Affected APIs</span></span>

<span data-ttu-id="e3eae-117">從 .NET 5.0 預覽 1 開始:</span><span class="sxs-lookup"><span data-stu-id="e3eae-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="e3eae-118">從 .NET 5.0 預覽 2 開始:</span><span class="sxs-lookup"><span data-stu-id="e3eae-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="e3eae-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>( 僅<xref:System.IO.Stream>適用於參數 )</span><span class="sxs-lookup"><span data-stu-id="e3eae-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

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
