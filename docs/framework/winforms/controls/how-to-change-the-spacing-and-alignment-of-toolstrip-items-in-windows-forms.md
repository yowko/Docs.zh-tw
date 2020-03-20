---
title: 如何：更改工具條專案的間距和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182235"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="a3ef3-102">如何：變更 Windows Form 中 ToolStrip 項目的間距和對齊方式</span><span class="sxs-lookup"><span data-stu-id="a3ef3-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="a3ef3-103">控制項<xref:System.Windows.Forms.ToolStrip>完全支援佈局功能，如大小調整、控制項相對於彼此的<xref:System.Windows.Forms.ToolStripItem>間距、控制項的<xref:System.Windows.Forms.ToolStrip>排列以及控制項相對於 的<xref:System.Windows.Forms.ToolStrip>間距。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="a3ef3-104">由於<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性的預設值為`true`，控制項會自動調整大小，除非您將<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="a3ef3-105">手動調整工具條專案的大小</span><span class="sxs-lookup"><span data-stu-id="a3ef3-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="a3ef3-106">將<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>屬性設置為`false`關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="a3ef3-107">以<xref:System.Windows.Forms.ToolStripItem.Size%2A>所需方式設置關聯的<xref:System.Windows.Forms.ToolStripItem>屬性。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="a3ef3-108">設置工具條專案的間距</span><span class="sxs-lookup"><span data-stu-id="a3ef3-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="a3ef3-109">將所需值（以圖元為單位）插入到關聯<xref:System.Windows.Forms.ToolStripItem.Margin%2A>控制項的屬性中。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="a3ef3-110"><xref:System.Windows.Forms.ToolStripItem.Margin%2A>屬性的值按此順序指定項和相鄰項之間的間距：左、上、右和下。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="a3ef3-111">將工具條專案與工具條的右側對齊</span><span class="sxs-lookup"><span data-stu-id="a3ef3-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="a3ef3-112">將<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性設置為<xref:System.Windows.Forms.ToolStripItemAlignment.Right>關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="a3ef3-113">預設情況下，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>設置為<xref:System.Windows.Forms.ToolStripItemAlignment.Left>，將控制項與 的<xref:System.Windows.Forms.ToolStrip>左側對齊。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="a3ef3-114">在工具條上排列工具條專案</span><span class="sxs-lookup"><span data-stu-id="a3ef3-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="a3ef3-115">將<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性設置為所需的值<xref:System.Windows.Forms.ToolStripLayoutStyle>。</span><span class="sxs-lookup"><span data-stu-id="a3ef3-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3ef3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3ef3-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="a3ef3-117">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a3ef3-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="a3ef3-118">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="a3ef3-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="a3ef3-119">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="a3ef3-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
