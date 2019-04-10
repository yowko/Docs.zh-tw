---
title: HOW TO：固定 Windows Forms 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 61ccad615eec81eb1aa77e6a99d48ef29ecb5be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231522"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="b7e66-102">HOW TO：固定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="b7e66-103">您可以將控制項停駐在表單的邊緣，或讓它們填滿控制項的容器 （表單或容器控制項）。</span><span class="sxs-lookup"><span data-stu-id="b7e66-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="b7e66-104">比方說，Windows 檔案總管停駐於其<xref:System.Windows.Forms.TreeView>視窗的左側的控制項及其<xref:System.Windows.Forms.ListView>視窗右邊的控制項。</span><span class="sxs-lookup"><span data-stu-id="b7e66-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="b7e66-105">使用<xref:System.Windows.Forms.Control.Dock%2A>所有可見定義固定模式的 Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7e66-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7e66-106">控制項停駐在反向的疊置順序。</span><span class="sxs-lookup"><span data-stu-id="b7e66-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="b7e66-107"><xref:System.Windows.Forms.Control.Dock%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b7e66-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="b7e66-108">如需詳細資訊，請參閱 < [AutoSize 屬性概觀](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e66-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="b7e66-109">若要停駐控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="b7e66-110">選取您想要停駐的控制項。</span><span class="sxs-lookup"><span data-stu-id="b7e66-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="b7e66-111">在 [屬性] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Dock%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b7e66-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="b7e66-112">編輯器隨即出現，顯示一系列代表的邊緣和表單的中央的方塊。</span><span class="sxs-lookup"><span data-stu-id="b7e66-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="b7e66-113">按一下按鈕，表示您想要的控制項停駐在表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="b7e66-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="b7e66-114">若要填滿控制項的表單或容器控制項的內容，請按一下 [中心] 方塊。</span><span class="sxs-lookup"><span data-stu-id="b7e66-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="b7e66-115">按一下  **（無）** 停用停駐。</span><span class="sxs-lookup"><span data-stu-id="b7e66-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="b7e66-116">控制會自動調整大小以填滿停駐的邊緣的邊界。</span><span class="sxs-lookup"><span data-stu-id="b7e66-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7e66-117">繼承的控制項必須`Protected`能夠停駐。</span><span class="sxs-lookup"><span data-stu-id="b7e66-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="b7e66-118">若要變更控制項的存取層級，設定其**修飾詞**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7e66-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e66-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e66-119">See also</span></span>

- [<span data-ttu-id="b7e66-120">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="b7e66-121">排列 Windows Form 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="b7e66-122">標記個別 Windows Form 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="b7e66-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b7e66-123">在 Windows Form 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b7e66-124">依功能區分 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="b7e66-125">HOW TO：錨定和停駐 FlowLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="b7e66-126">HOW TO：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="b7e66-127">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="b7e66-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="b7e66-128">HOW TO：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b7e66-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
