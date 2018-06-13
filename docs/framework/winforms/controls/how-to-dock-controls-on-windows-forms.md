---
title: 如何：將控制項停駐在 Windows Form 上
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532312"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="a8f51-102">如何：將控制項停駐在 Windows Form 上</span><span class="sxs-lookup"><span data-stu-id="a8f51-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="a8f51-103">您可以停駐控制項至表單的邊緣，或讓它們填滿控制項的容器 （表單或容器控制項）。</span><span class="sxs-lookup"><span data-stu-id="a8f51-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="a8f51-104">例如，Windows 檔案總管停駐於其<xref:System.Windows.Forms.TreeView>控制項視窗的左邊及其<xref:System.Windows.Forms.ListView>視窗右邊的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8f51-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="a8f51-105">使用<xref:System.Windows.Forms.Control.Dock%2A>所有可見的 Windows Form 控制項定義的固定模式屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f51-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8f51-106">反轉 z 軸順序停駐控制項。</span><span class="sxs-lookup"><span data-stu-id="a8f51-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="a8f51-107"><xref:System.Windows.Forms.Control.Dock%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f51-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="a8f51-108">如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a8f51-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="a8f51-109">若要停駐控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="a8f51-110">選取您想要停駐的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8f51-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="a8f51-111">在 [屬性] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Dock%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f51-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="a8f51-112">編輯器會隨即出現，顯示一系列代表的邊緣和表單的中央的方塊。</span><span class="sxs-lookup"><span data-stu-id="a8f51-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="a8f51-113">按一下代表您要停駐控制項的表單的邊緣的按鈕。</span><span class="sxs-lookup"><span data-stu-id="a8f51-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="a8f51-114">若要填滿控制項的表單或容器控制項的內容，請按一下中央方塊。</span><span class="sxs-lookup"><span data-stu-id="a8f51-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="a8f51-115">按一下 **（無）** 停用停駐。</span><span class="sxs-lookup"><span data-stu-id="a8f51-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="a8f51-116">控制項是自動調整大小以填滿停駐邊緣的邊界。</span><span class="sxs-lookup"><span data-stu-id="a8f51-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8f51-117">繼承的控制項必須是`Protected`能夠停駐。</span><span class="sxs-lookup"><span data-stu-id="a8f51-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="a8f51-118">若要變更控制項的存取層級，設定其**修飾詞**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f51-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f51-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f51-119">See Also</span></span>  
 [<span data-ttu-id="a8f51-120">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a8f51-121">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a8f51-122">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="a8f51-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="a8f51-123">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="a8f51-124">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="a8f51-125">操作說明：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="a8f51-126">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="a8f51-127">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="a8f51-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="a8f51-128">操作說明：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a8f51-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
