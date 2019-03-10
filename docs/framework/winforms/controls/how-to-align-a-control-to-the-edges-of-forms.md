---
title: HOW TO：將控制項和表單邊緣對齊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 33a3b2e996bdab280eb7a4cd8ad7c59ccb1a1bd2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713887"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="c4ab6-102">HOW TO：將控制項和表單邊緣對齊</span><span class="sxs-lookup"><span data-stu-id="c4ab6-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="c4ab6-103">您可設定 <xref:System.Windows.Forms.Control.Dock%2A> 屬性讓控制項對齊表單邊緣。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="c4ab6-104">這個屬性會指定您的控制項在表單中的位置。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="c4ab6-105">可將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為下列值：</span><span class="sxs-lookup"><span data-stu-id="c4ab6-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="c4ab6-106">設定</span><span class="sxs-lookup"><span data-stu-id="c4ab6-106">Setting</span></span>|<span data-ttu-id="c4ab6-107">對控制項的影響</span><span class="sxs-lookup"><span data-stu-id="c4ab6-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="c4ab6-108">停駐在表單下方。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="c4ab6-109">填滿表單中剩下的空間。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="c4ab6-110">停駐在表單左方。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="c4ab6-111">不會停駐在任何地方，且會出現在 <xref:System.Windows.Forms.Control.Location%2A> 屬性所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="c4ab6-112">停駐在表單右方。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="c4ab6-113">停駐在表單上方。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="c4ab6-114">Visual Studio 中有針對此功能提供的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="c4ab6-115">在執行階段設定控制項的 Dock 屬性</span><span class="sxs-lookup"><span data-stu-id="c4ab6-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="c4ab6-116">在程式碼中，將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="c4ab6-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4ab6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4ab6-117">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c4ab6-118">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c4ab6-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="c4ab6-119">如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="c4ab6-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="c4ab6-120">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="c4ab6-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="c4ab6-121">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="c4ab6-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
