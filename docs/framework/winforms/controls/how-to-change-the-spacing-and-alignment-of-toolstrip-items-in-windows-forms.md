---
title: 如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="3dfc5-102">如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式</span><span class="sxs-lookup"><span data-stu-id="3dfc5-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="3dfc5-103"><xref:System.Windows.Forms.ToolStrip>完全支援控制項的版面配置功能，例如調整大小、 間距<xref:System.Windows.Forms.ToolStripItem>上的控制項，相對於彼此，控制項的排列方式<xref:System.Windows.Forms.ToolStrip>，相對於控制項的間距和<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="3dfc5-104">因為預設值的<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性是`true`，控制項自動調整大小除非您將設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="3dfc5-105">若要手動調整大小 ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="3dfc5-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="3dfc5-106">設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性`false`相關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="3dfc5-107">設定<xref:System.Windows.Forms.ToolStripItem.Size%2A>屬性要關聯的方式<xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="3dfc5-108">若要設定 ToolStripItem 的間距</span><span class="sxs-lookup"><span data-stu-id="3dfc5-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="3dfc5-109">插入所需的值，以像素<xref:System.Windows.Forms.ToolStripItem.Margin%2A>針對關聯控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="3dfc5-110">值<xref:System.Windows.Forms.ToolStripItem.Margin%2A>屬性指定的項目和相鄰的項目之間的間距，依此順序： 左框線、 頂端、 右側和底部。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="3dfc5-111">若要對齊右邊的 ToolStrip 的 ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="3dfc5-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="3dfc5-112">設定<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性<xref:System.Windows.Forms.ToolStripItemAlignment.Right>相關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="3dfc5-113">根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>設<xref:System.Windows.Forms.ToolStripItemAlignment.Left>，這會將控制項的左半部<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="3dfc5-114">若要排列 ToolStrip 項目在 ToolStrip 上</span><span class="sxs-lookup"><span data-stu-id="3dfc5-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="3dfc5-115">設定<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性設為值的<xref:System.Windows.Forms.ToolStripLayoutStyle>您想要的。</span><span class="sxs-lookup"><span data-stu-id="3dfc5-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3dfc5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dfc5-116">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="3dfc5-117">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3dfc5-117">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="3dfc5-118">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="3dfc5-118">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="3dfc5-119">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="3dfc5-119">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
