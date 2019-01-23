---
title: HOW TO：管理 Windows Form 中的 ToolStrip 溢位
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
ms.openlocfilehash: 5f26217c92aef1d568349aefb87dd5a882a0cf28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541153"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="5904b-102">HOW TO：管理 Windows Form 中的 ToolStrip 溢位</span><span class="sxs-lookup"><span data-stu-id="5904b-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="5904b-103">當上的所有項目<xref:System.Windows.Forms.ToolStrip>控制項無法放入配置的空間，您可以在啟用溢位功能<xref:System.Windows.Forms.ToolStrip>，並判斷特定的溢位行為<xref:System.Windows.Forms.ToolStripItem>s。</span><span class="sxs-lookup"><span data-stu-id="5904b-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="5904b-104">當您將加入<xref:System.Windows.Forms.ToolStripItem>需要更多的空間比分配給<xref:System.Windows.Forms.ToolStrip>指定表單的目前大小，<xref:System.Windows.Forms.ToolStripOverflowButton>會自動出現在<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="5904b-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="5904b-105"><xref:System.Windows.Forms.ToolStripOverflowButton>隨即出現，並啟用溢位的項目會變成下拉式溢位功能表。</span><span class="sxs-lookup"><span data-stu-id="5904b-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="5904b-106">這可讓您自訂並排定優先順序如何您<xref:System.Windows.Forms.ToolStrip>正確調整中的項目，以不同的表單大小。</span><span class="sxs-lookup"><span data-stu-id="5904b-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="5904b-107">您也可以變更項目的外觀，當他們使用屬於溢位<xref:System.Windows.Forms.ToolStripItem.Placement%2A>並<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="5904b-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="5904b-108">如果您放大表單，在設計階段或執行的階段，更<xref:System.Windows.Forms.ToolStripItem>s 可以顯示在主要<xref:System.Windows.Forms.ToolStrip>而<xref:System.Windows.Forms.ToolStripOverflowButton>直到您在表單的大小縮小，甚至可能會消失。</span><span class="sxs-lookup"><span data-stu-id="5904b-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="5904b-109">若要啟用溢位在 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="5904b-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="5904b-110">請確認<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>屬性未設定為`false`如<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="5904b-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="5904b-111">預設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="5904b-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="5904b-112">當<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>是`True`（預設值），<xref:System.Windows.Forms.ToolStripItem>傳送至下拉式溢位功能表時的內容<xref:System.Windows.Forms.ToolStripItem>超過的水平寬度<xref:System.Windows.Forms.ToolStrip>或高度的垂直<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="5904b-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="5904b-113">若要指定特定的 prvku ToolStripItem 溢位行為</span><span class="sxs-lookup"><span data-stu-id="5904b-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="5904b-114">設定<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性<xref:System.Windows.Forms.ToolStripItem>所要的值。</span><span class="sxs-lookup"><span data-stu-id="5904b-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="5904b-115">您可以徹底`Always`， `Never`，和`AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="5904b-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="5904b-116">Defaultis `AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="5904b-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5904b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5904b-117">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="5904b-118">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="5904b-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="5904b-119">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="5904b-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [<span data-ttu-id="5904b-120">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="5904b-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
