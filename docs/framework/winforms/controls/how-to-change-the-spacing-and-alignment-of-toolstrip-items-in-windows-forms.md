---
title: HOW TO：變更 Windows Forms 中 ToolStrip 項目的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: bed943466348447e30947c170e27027f324342c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323170"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="9e533-102">HOW TO：變更 Windows Forms 中 ToolStrip 項目的間距和對齊方式</span><span class="sxs-lookup"><span data-stu-id="9e533-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="9e533-103"><xref:System.Windows.Forms.ToolStrip>完全支援控制項的版面配置功能，例如調整大小、 間距<xref:System.Windows.Forms.ToolStripItem>彼此相對，控制項的排列方式的控制項<xref:System.Windows.Forms.ToolStrip>，以及相對於控制項的間距<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="9e533-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="9e533-104">因為預設值<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性是`true`，除非您設定控制項的自動大小<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="9e533-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="9e533-105">若要手動調整大小 prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="9e533-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="9e533-106">設定<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設`false`關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="9e533-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="9e533-107">設定<xref:System.Windows.Forms.ToolStripItem.Size%2A>屬性是您所要關聯<xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="9e533-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="9e533-108">若要設定的間距 prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="9e533-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="9e533-109">插入所需的值，單位為像素<xref:System.Windows.Forms.ToolStripItem.Margin%2A>關聯控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="9e533-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="9e533-110">值<xref:System.Windows.Forms.ToolStripItem.Margin%2A>屬性指定的項目和相鄰項目之間的間距，順序如下：左側、 頂端、 右側，與下方。</span><span class="sxs-lookup"><span data-stu-id="9e533-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="9e533-111">若要靠右對齊的 ToolStrip prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="9e533-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="9e533-112">設定<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性設<xref:System.Windows.Forms.ToolStripItemAlignment.Right>關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="9e533-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="9e533-113">根據預設，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>設定為<xref:System.Windows.Forms.ToolStripItemAlignment.Left>，以配合控制項的左邊<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="9e533-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="9e533-114">若要排列 ToolStrip 項目，在 ToolStrip 上</span><span class="sxs-lookup"><span data-stu-id="9e533-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="9e533-115">設定<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性設為值的<xref:System.Windows.Forms.ToolStripLayoutStyle>您想要的。</span><span class="sxs-lookup"><span data-stu-id="9e533-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9e533-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e533-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="9e533-117">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="9e533-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="9e533-118">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="9e533-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="9e533-119">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="9e533-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
