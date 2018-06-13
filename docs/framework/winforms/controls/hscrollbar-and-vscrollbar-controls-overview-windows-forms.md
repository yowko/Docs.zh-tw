---
title: HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
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
ms.openlocfilehash: 572ba9f16d1c78e1825d0c9db7530c6c78175d27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538462"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="9dbd1-102">HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9dbd1-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="9dbd1-103">Windows Form<xref:System.Windows.Forms.ScrollBar>控制項可用來捲動的水平或垂直應用程式或控制項內提供輕鬆瀏覽一長串的項目或大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="9dbd1-104">捲軸是通用的項目，Windows 介面，所以<xref:System.Windows.Forms.ScrollBar>控制項則通常會搭配控制項不是衍生自<xref:System.Windows.Forms.ScrollableControl>類別。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="9dbd1-105">同樣地，許多開發人員選擇加入<xref:System.Windows.Forms.ScrollBar>控制製作自己的使用者控制項時。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="9dbd1-106"><xref:System.Windows.Forms.HScrollBar> （水平） 和<xref:System.Windows.Forms.VScrollBar>（垂直） 的控制項是其他控制項從獨立運作，並且有它們自己的事件、 屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="9dbd1-107"><xref:System.Windows.Forms.ScrollBar> 控制項不會附加至文字方塊、 清單方塊、 下拉式方塊或 MDI 表單的內建的捲軸相同 (<xref:System.Windows.Forms.TextBox>控制項有<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，即可顯示或隱藏附加到控制項的捲軸)。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="9dbd1-108"><xref:System.Windows.Forms.ScrollBar>會控制使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件監視 （有時稱為 「 捲動方塊 」） 的捲動方塊的移動捲軸上。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="9dbd1-109">使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件提供正在拖曳捲軸值的存取。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="9dbd1-110">值屬性</span><span class="sxs-lookup"><span data-stu-id="9dbd1-110">Value Property</span></span>  
 <span data-ttu-id="9dbd1-111"><xref:System.Windows.Forms.ScrollBar.Value%2A> （即，根據預設，0） 的屬性是`integer`捲軸的捲動方塊的位置對應的值。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="9dbd1-112">最小值捲動方塊位置時，它會移動到最左邊的位置 （適用於水平捲軸） 或 （適用於垂直捲軸） 上方的位置。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="9dbd1-113">捲動方塊時的最大值、 捲軸方塊移至最右側或底部的位置。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="9dbd1-114">同樣地，中間範圍的最底部之間的值將放在前置邊緣的中間捲軸的捲動方塊。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="9dbd1-115">除了使用滑鼠點按動作來變更捲軸值，使用者也可以拖曳捲動方塊的軸上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="9dbd1-116">產生的值取決於捲動方塊的位置，但它一定會在各種<xref:System.Windows.Forms.ScrollBar.Minimum%2A>至<xref:System.Windows.Forms.ScrollBar.Maximum%2A>使用者所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="9dbd1-117">LargeChange 和 SmallChange 屬性</span><span class="sxs-lookup"><span data-stu-id="9dbd1-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="9dbd1-118">當使用者按下 PAGE UP 或 PAGE DOWN 鍵，或在捲軸追蹤任一邊的捲軸 方塊中，按一下<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更的設定值根據<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="9dbd1-119">當使用者按下一個箭號的索引鍵或按下捲軸按鈕中，其中<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更的設定值根據<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9dbd1-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbd1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dbd1-120">See Also</span></span>  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [<span data-ttu-id="9dbd1-121">Windows form 的新增項目，適用於.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="9dbd1-121">Additions to Windows Forms for the .NET Framework 2.0</span></span>](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [<span data-ttu-id="9dbd1-122">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="9dbd1-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
