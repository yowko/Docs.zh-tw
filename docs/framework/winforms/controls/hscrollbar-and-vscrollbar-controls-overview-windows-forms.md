---
title: HScrollBar 和 VScrollBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728168"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="12454-102">HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="12454-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="12454-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> 控制項是用來透過在應用程式或控制項內水準或垂直捲動，輕鬆地流覽長清單的專案或大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="12454-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="12454-104">捲軸是 Windows 介面的通用元素，因此，<xref:System.Windows.Forms.ScrollBar> 控制項通常會與不是衍生自 <xref:System.Windows.Forms.ScrollableControl> 類別的控制項一起使用。</span><span class="sxs-lookup"><span data-stu-id="12454-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="12454-105">同樣地，許多開發人員在撰寫自己的使用者控制項時，也會選擇納入 <xref:System.Windows.Forms.ScrollBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="12454-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="12454-106"><xref:System.Windows.Forms.HScrollBar> （水準）和 <xref:System.Windows.Forms.VScrollBar> （垂直）控制項與其他控制項獨立運作，而且有自己的一組事件、屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="12454-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="12454-107"><xref:System.Windows.Forms.ScrollBar> 控制項與附加至文字方塊、清單方塊、下拉式方塊或 MDI 表單的內建捲軸不同（<xref:System.Windows.Forms.TextBox> 控制項具有 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性，可顯示或隱藏附加至控制項的捲軸）。</span><span class="sxs-lookup"><span data-stu-id="12454-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="12454-108"><xref:System.Windows.Forms.ScrollBar> 控制項使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件來監視捲動方塊的移動（有時也稱為捲軸）。</span><span class="sxs-lookup"><span data-stu-id="12454-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="12454-109">使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件會在拖曳時提供捲軸值的存取權。</span><span class="sxs-lookup"><span data-stu-id="12454-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="12454-110">值屬性</span><span class="sxs-lookup"><span data-stu-id="12454-110">Value Property</span></span>  
 <span data-ttu-id="12454-111">[<xref:System.Windows.Forms.ScrollBar.Value%2A>] 屬性（預設為0）是對應到捲軸之捲動方塊位置的 `integer` 值。</span><span class="sxs-lookup"><span data-stu-id="12454-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="12454-112">當捲動方塊位置是最小值時，它會移至最左邊的位置（適用于水準捲軸）或頂端位置（適用于垂直捲動條）。</span><span class="sxs-lookup"><span data-stu-id="12454-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="12454-113">當捲動方塊為最大值時，捲動方塊會移到最右邊或底部的位置。</span><span class="sxs-lookup"><span data-stu-id="12454-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="12454-114">同樣地，範圍底端和頂端之間的值，會將捲動方塊的前置邊緣放在捲軸的中間。</span><span class="sxs-lookup"><span data-stu-id="12454-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="12454-115">除了使用滑鼠點按來變更捲軸值之外，使用者也可以將捲動方塊拖曳至橫條的任何點。</span><span class="sxs-lookup"><span data-stu-id="12454-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="12454-116">產生的值會根據捲動方塊的位置而定，但一定會在 <xref:System.Windows.Forms.ScrollBar.Minimum%2A> 的範圍內，以 <xref:System.Windows.Forms.ScrollBar.Maximum%2A> 使用者所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="12454-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="12454-117">LargeChange 和 SmallChange 屬性</span><span class="sxs-lookup"><span data-stu-id="12454-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="12454-118">當使用者按 PAGE UP 或 PAGE DOWN 鍵，或按一下捲動方塊任一側的捲軸播放軌時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> 屬性中設定的值而變更。</span><span class="sxs-lookup"><span data-stu-id="12454-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="12454-119">當使用者按下其中一個方向鍵或按一下其中一個捲軸按鈕時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> 屬性中設定的值而變更。</span><span class="sxs-lookup"><span data-stu-id="12454-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12454-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12454-120">See also</span></span>

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [<span data-ttu-id="12454-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="12454-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
