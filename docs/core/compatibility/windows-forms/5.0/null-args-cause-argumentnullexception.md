---
title: 重大變更： WinForms 方法現在會擲回 System.argumentnullexception
description: 瞭解 .NET 5.0 中的重大變更，其中某些 Windows Forms 方法現在會擲回 null 引數的 System.argumentnullexception。
ms.date: 09/18/2020
ms.openlocfilehash: 77280827d44b0e58533339a09357d518a0bfe508
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760748"
---
# <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="97180-103">WinForms 方法現在會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="97180-103">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="97180-104">某些 Windows Forms 方法現在會擲回 <xref:System.ArgumentNullException> null 引數，其中先前會擲回 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="97180-104">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

## <a name="change-description"></a><span data-ttu-id="97180-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="97180-105">Change description</span></span>

<span data-ttu-id="97180-106">先前，如果傳遞的引數為 null，則某些 Windows Forms 方法會擲回 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="97180-106">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="97180-107">從 .NET 5.0 開始，這些方法現在會擲回 <xref:System.ArgumentNullException> null 引數的。</span><span class="sxs-lookup"><span data-stu-id="97180-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="97180-108">擲回會 <xref:System.ArgumentNullException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="97180-108">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="97180-109">它也可清楚地傳達引數為 null，以及哪個引數，藉此改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="97180-109">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="97180-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="97180-110">Version introduced</span></span>

<span data-ttu-id="97180-111">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="97180-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="97180-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="97180-112">Recommended action</span></span>

<span data-ttu-id="97180-113">如果您呼叫任何方法，而您的程式碼目前會 <xref:System.NullReferenceException> 攔截的是 null 引數，請改為攔截 <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="97180-113">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="97180-114">此外，請考慮更新程式碼，以防止將 null 引數傳遞至列出的方法。</span><span class="sxs-lookup"><span data-stu-id="97180-114">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="97180-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="97180-115">Affected APIs</span></span>

<span data-ttu-id="97180-116">下表列出受影響的方法和參數：</span><span class="sxs-lookup"><span data-stu-id="97180-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="97180-117">方法</span><span class="sxs-lookup"><span data-stu-id="97180-117">Method</span></span> | <span data-ttu-id="97180-118">參數名稱</span><span class="sxs-lookup"><span data-stu-id="97180-118">Parameter name</span></span> | <span data-ttu-id="97180-119">已新增版本</span><span class="sxs-lookup"><span data-stu-id="97180-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="97180-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="97180-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="97180-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="97180-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="97180-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="97180-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="97180-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="97180-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="97180-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="97180-128">Preview 2</span><span class="sxs-lookup"><span data-stu-id="97180-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="97180-129">Preview 2</span><span class="sxs-lookup"><span data-stu-id="97180-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="97180-130">Preview 5</span><span class="sxs-lookup"><span data-stu-id="97180-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="97180-131">Preview 5</span><span class="sxs-lookup"><span data-stu-id="97180-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="97180-132">Preview 5</span><span class="sxs-lookup"><span data-stu-id="97180-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="97180-133">Preview 5</span><span class="sxs-lookup"><span data-stu-id="97180-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="97180-134">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="97180-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="97180-135">`owner`, `value`</span></span> | <span data-ttu-id="97180-136">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="97180-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="97180-137">`owner`, `value`</span></span> | <span data-ttu-id="97180-138">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="97180-139">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="97180-140">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="97180-141">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="97180-142">Preview 6</span><span class="sxs-lookup"><span data-stu-id="97180-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="97180-143">Preview 7</span><span class="sxs-lookup"><span data-stu-id="97180-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="97180-144">`key` 是 `null` 或空白</span><span class="sxs-lookup"><span data-stu-id="97180-144">`key` is `null` or empty</span></span> | <span data-ttu-id="97180-145">Preview 8</span><span class="sxs-lookup"><span data-stu-id="97180-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="97180-146">`key` 是 `null` 或空白</span><span class="sxs-lookup"><span data-stu-id="97180-146">`key` is `null` or empty</span></span> | <span data-ttu-id="97180-147">RC1</span><span class="sxs-lookup"><span data-stu-id="97180-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="97180-148">RC1</span><span class="sxs-lookup"><span data-stu-id="97180-148">RC1</span></span> |

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
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

### Category

Windows Forms

-->
