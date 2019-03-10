---
title: HOW TO：將控制項和表單邊緣對齊在設計階段
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b81cb839664499d69710d81b7b0c8a479966d569
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724943"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="c464b-102">HOW TO：將控制項和表單邊緣對齊在設計階段</span><span class="sxs-lookup"><span data-stu-id="c464b-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="c464b-103">您可以讓控制項對齊表單邊緣藉由設定<xref:System.Windows.Forms.Control.Dock%2A>。</span><span class="sxs-lookup"><span data-stu-id="c464b-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="c464b-104">這個屬性會指定您的控制項在表單中的位置。</span><span class="sxs-lookup"><span data-stu-id="c464b-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="c464b-105">可將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為下列值：</span><span class="sxs-lookup"><span data-stu-id="c464b-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="c464b-106">設定</span><span class="sxs-lookup"><span data-stu-id="c464b-106">Setting</span></span>|<span data-ttu-id="c464b-107">對控制項的影響</span><span class="sxs-lookup"><span data-stu-id="c464b-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="c464b-108">停駐在表單下方。</span><span class="sxs-lookup"><span data-stu-id="c464b-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="c464b-109">填滿表單中剩下的空間。</span><span class="sxs-lookup"><span data-stu-id="c464b-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="c464b-110">停駐在表單左方。</span><span class="sxs-lookup"><span data-stu-id="c464b-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="c464b-111">未停駐在任何地方，且會出現在所指定的位置及其<xref:System.Windows.Forms.Control.Location%2A>。</span><span class="sxs-lookup"><span data-stu-id="c464b-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="c464b-112">停駐在表單右方。</span><span class="sxs-lookup"><span data-stu-id="c464b-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="c464b-113">停駐在表單上方。</span><span class="sxs-lookup"><span data-stu-id="c464b-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="c464b-114">也可以在程式碼中設定這些值。</span><span class="sxs-lookup"><span data-stu-id="c464b-114">These values can also be set in code.</span></span> <span data-ttu-id="c464b-115">如需詳細資訊，請參閱[如何：將控制項和表單邊緣對齊](how-to-align-a-control-to-the-edges-of-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c464b-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c464b-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="c464b-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c464b-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="c464b-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c464b-118">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="c464b-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="c464b-119">若要在設計階段設定控制項的 Dock 屬性</span><span class="sxs-lookup"><span data-stu-id="c464b-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="c464b-120">在 Windows Form 設計工具中，選取您的控制項。</span><span class="sxs-lookup"><span data-stu-id="c464b-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="c464b-121">在 [**屬性**視窗中，按一下下拉式清單方塊的下的一步]<xref:System.Windows.Forms.Control.Dock%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c464b-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="c464b-122">代表六個可能的圖形化介面<xref:System.Windows.Forms.Control.Dock%2A>設定隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c464b-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="c464b-123">選擇適當的設定。</span><span class="sxs-lookup"><span data-stu-id="c464b-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="c464b-124">您的控制項現在會設定所指定的方式停駐。</span><span class="sxs-lookup"><span data-stu-id="c464b-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c464b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c464b-125">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c464b-126">如何：將控制項和表單邊緣對齊</span><span class="sxs-lookup"><span data-stu-id="c464b-126">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="c464b-127">逐步解說：使用對齊線的 Windows Form 上排列控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="c464b-128">如何：在 Windows Forms 上控制項的錨定</span><span class="sxs-lookup"><span data-stu-id="c464b-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="c464b-129">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="c464b-130">如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="c464b-131">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="c464b-132">逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="c464b-133">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c464b-133">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
