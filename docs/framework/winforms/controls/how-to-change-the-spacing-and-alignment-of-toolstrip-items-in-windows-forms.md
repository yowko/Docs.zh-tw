---
title: 如何：變更 ToolStrip 專案的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746558"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="624cf-102">如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式</span><span class="sxs-lookup"><span data-stu-id="624cf-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="624cf-103"><xref:System.Windows.Forms.ToolStrip> 控制項完全支援調整大小、每個 <xref:System.Windows.Forms.ToolStripItem> 控制項的間距、<xref:System.Windows.Forms.ToolStrip>上的控制項相片順序，以及相對於 <xref:System.Windows.Forms.ToolStrip>的控制項間距等版面配置功能。</span><span class="sxs-lookup"><span data-stu-id="624cf-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="624cf-104">由於 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性的預設值是 `true`，因此除非您將 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性設定為 `false`，否則控制項會自動調整大小。</span><span class="sxs-lookup"><span data-stu-id="624cf-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="624cf-105">手動調整 ToolStripItem 大小</span><span class="sxs-lookup"><span data-stu-id="624cf-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="624cf-106">將相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> 屬性設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="624cf-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="624cf-107">以您想要的方式，將 <xref:System.Windows.Forms.ToolStripItem.Size%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="624cf-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="624cf-108">設定 ToolStripItem 的間距</span><span class="sxs-lookup"><span data-stu-id="624cf-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="624cf-109">將想要的值（以圖元為單位）插入相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="624cf-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="624cf-110">[<xref:System.Windows.Forms.ToolStripItem.Margin%2A>] 屬性的值會以下列順序指定專案與相鄰專案之間的間距： [左]、[上]、[右] 和 [下]。</span><span class="sxs-lookup"><span data-stu-id="624cf-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="624cf-111">將 ToolStripItem 對齊 ToolStrip 的右側</span><span class="sxs-lookup"><span data-stu-id="624cf-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="624cf-112">將相關聯控制項的 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性設定為 [<xref:System.Windows.Forms.ToolStripItemAlignment.Right>]。</span><span class="sxs-lookup"><span data-stu-id="624cf-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="624cf-113">根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 設定為 [<xref:System.Windows.Forms.ToolStripItemAlignment.Left>]，這會將控制項對齊 <xref:System.Windows.Forms.ToolStrip>的左邊。</span><span class="sxs-lookup"><span data-stu-id="624cf-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="624cf-114">排列 ToolStrip 上的 ToolStrip 專案</span><span class="sxs-lookup"><span data-stu-id="624cf-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="624cf-115">將 [<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>] 屬性設為您想要 <xref:System.Windows.Forms.ToolStripLayoutStyle> 的值。</span><span class="sxs-lookup"><span data-stu-id="624cf-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="624cf-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="624cf-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="624cf-117">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="624cf-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="624cf-118">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="624cf-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="624cf-119">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="624cf-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
