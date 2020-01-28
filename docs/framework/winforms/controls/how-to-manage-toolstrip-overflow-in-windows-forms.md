---
title: 如何：管理 ToolStrip 溢位
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736141"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="f95f5-102">如何：管理 Windows Form 中的 ToolStrip 溢位</span><span class="sxs-lookup"><span data-stu-id="f95f5-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="f95f5-103">當 <xref:System.Windows.Forms.ToolStrip> 控制項上的所有專案都無法納入配置的空間時，您可以在 <xref:System.Windows.Forms.ToolStrip> 上啟用溢位功能，並判斷特定 <xref:System.Windows.Forms.ToolStripItem>的溢位行為。</span><span class="sxs-lookup"><span data-stu-id="f95f5-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="f95f5-104">當您加入的 <xref:System.Windows.Forms.ToolStripItem>需要比配置給 <xref:System.Windows.Forms.ToolStrip> 的空間，並指定表單的目前大小，<xref:System.Windows.Forms.ToolStripOverflowButton> 會自動出現在 <xref:System.Windows.Forms.ToolStrip>上。</span><span class="sxs-lookup"><span data-stu-id="f95f5-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f95f5-105">此時會出現 <xref:System.Windows.Forms.ToolStripOverflowButton>，而且已啟用溢位的專案會移至下拉式 溢位 功能表中。</span><span class="sxs-lookup"><span data-stu-id="f95f5-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="f95f5-106">這可讓您自訂 <xref:System.Windows.Forms.ToolStrip> 專案適當調整成不同表單大小的方式，並設定其優先順序。</span><span class="sxs-lookup"><span data-stu-id="f95f5-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="f95f5-107">您也可以使用 [<xref:System.Windows.Forms.ToolStripItem.Placement%2A>] 和 [<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> 屬性] 和 [<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>] 事件，在專案落入溢位時變更其外觀。</span><span class="sxs-lookup"><span data-stu-id="f95f5-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="f95f5-108">如果您在設計階段或執行時間放大表單，主要 <xref:System.Windows.Forms.ToolStrip> 上可以顯示更多 <xref:System.Windows.Forms.ToolStripItem>，而 <xref:System.Windows.Forms.ToolStripOverflowButton> 甚至可能會消失，直到您減少表單的大小。</span><span class="sxs-lookup"><span data-stu-id="f95f5-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="f95f5-109">啟用 ToolStrip 控制項的溢位</span><span class="sxs-lookup"><span data-stu-id="f95f5-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="f95f5-110">確定 <xref:System.Windows.Forms.ToolStrip>的 [<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>] 屬性未設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="f95f5-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f95f5-111">預設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="f95f5-111">The default is `True`.</span></span>

     <span data-ttu-id="f95f5-112">當 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` （預設值）時，當 <xref:System.Windows.Forms.ToolStripItem> 的內容超過水準 <xref:System.Windows.Forms.ToolStrip> 的寬度或垂直 <xref:System.Windows.Forms.ToolStrip>的高度時，<xref:System.Windows.Forms.ToolStripItem> 就會傳送至下拉式溢位功能表。</span><span class="sxs-lookup"><span data-stu-id="f95f5-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="f95f5-113">若要指定特定 ToolStripItem 的溢位行為</span><span class="sxs-lookup"><span data-stu-id="f95f5-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="f95f5-114">將 <xref:System.Windows.Forms.ToolStripItem> 的 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="f95f5-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="f95f5-115">可能的情況包括 `Always`、`Never`和 `AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="f95f5-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="f95f5-116">預設為 `AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="f95f5-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="f95f5-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f95f5-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="f95f5-118">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f95f5-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="f95f5-119">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="f95f5-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="f95f5-120">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="f95f5-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
