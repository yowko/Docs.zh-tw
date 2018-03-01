---
title: "SplitContainer 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d2e538241cca8288158628df777895fae9aa756
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="splitcontainer-control-overview-windows-forms"></a><span data-ttu-id="48027-102">SplitContainer 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="48027-102">SplitContainer Control Overview (Windows Forms)</span></span>
<span data-ttu-id="48027-103">Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。</span><span class="sxs-lookup"><span data-stu-id="48027-103">The Windows Forms <xref:System.Windows.Forms.SplitContainer> control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="48027-104">將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。</span><span class="sxs-lookup"><span data-stu-id="48027-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48027-105">在**工具箱**，<xref:System.Windows.Forms.SplitContainer>控制項取代<xref:System.Windows.Forms.Splitter>控制了在舊版的[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48027-105">In the **Toolbox**, <xref:System.Windows.Forms.SplitContainer> control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="48027-106"><xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。</span><span class="sxs-lookup"><span data-stu-id="48027-106">The <xref:System.Windows.Forms.SplitContainer> control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="48027-107"><xref:System.Windows.Forms.Splitter>類別仍然包含在[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]相容性與現有的應用程式，但強烈建議您將<xref:System.Windows.Forms.SplitContainer>新專案的控制項。</span><span class="sxs-lookup"><span data-stu-id="48027-107">The <xref:System.Windows.Forms.Splitter> class is still included in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for compatibility with existing applications, but we strongly encourage you to use the <xref:System.Windows.Forms.SplitContainer> control for new projects.</span></span>  
  
 <span data-ttu-id="48027-108">與<xref:System.Windows.Forms.SplitContainer>控制項，您可以建立複雜的使用者介面; 通常，一個面板中的選擇會決定其他面板中所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="48027-108">With the <xref:System.Windows.Forms.SplitContainer> control, you can create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="48027-109">這種排列方式可有效地顯示及瀏覽資訊。</span><span class="sxs-lookup"><span data-stu-id="48027-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="48027-110">擁有兩個面板可讓您彙總資訊區域中，並提升列或 「 分隔器 」 可讓輕鬆調整面板的大小的使用者。</span><span class="sxs-lookup"><span data-stu-id="48027-110">Having two panels lets you aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
 <span data-ttu-id="48027-111">多個<xref:System.Windows.Forms.SplitContainer>控制項也可以巢狀，第二個<xref:System.Windows.Forms.SplitContainer>控制項的水平導向建立上方和下方的面板。</span><span class="sxs-lookup"><span data-stu-id="48027-111">More than one <xref:System.Windows.Forms.SplitContainer> control can also be nested, with the second <xref:System.Windows.Forms.SplitContainer> control oriented horizontally, to create top and bottom panels.</span></span>  
  
 <span data-ttu-id="48027-112">請注意，<xref:System.Windows.Forms.SplitContainer>鍵盤存取預設控制項; 使用者可以按下方向鍵，如果移動分隔器<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="48027-112">Be aware that the <xref:System.Windows.Forms.SplitContainer> control is keyboard-accessible by default; users can press the ARROW keys to move the splitter if the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property is set to `false`.</span></span>  
  
 <span data-ttu-id="48027-113"><xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.SplitContainer>控制項會決定分隔器，而不是控制項本身的方向。</span><span class="sxs-lookup"><span data-stu-id="48027-113">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span> <span data-ttu-id="48027-114">因此，當這個屬性設定為<xref:System.Windows.Forms.Orientation.Vertical>，分隔器執行由上往下，建立左、 右面板。</span><span class="sxs-lookup"><span data-stu-id="48027-114">Hence, when this property is set to <xref:System.Windows.Forms.Orientation.Vertical>, the splitter runs from top to bottom, creating left and right panels.</span></span>  
  
 <span data-ttu-id="48027-115">此外，請注意，值<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性的值而有所不同<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48027-115">Additionally, be aware that the value of the <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> property varies depending on the value of the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property.</span></span> <span data-ttu-id="48027-116">如需詳細資訊，請參閱<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48027-116">For more information, see <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> property.</span></span>  
  
 <span data-ttu-id="48027-117">您也可以限制的大小和移動<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="48027-117">You can also restrict the size and movement of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="48027-118"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>屬性會決定哪個面板會維持相同大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小，而<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性會決定分隔器是否可移動的鍵盤或滑鼠。</span><span class="sxs-lookup"><span data-stu-id="48027-118">The <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> property determines which panel will remain the same size after the <xref:System.Windows.Forms.SplitContainer> control is resized, and the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property determines if the splitter is movable by the keyboard or mouse.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48027-119">即使<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`true`，分隔器可能仍然以程式設計的方式，例如使用移動<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48027-119">Even if the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property is set to `true`, the splitter may still be moved programmatically; for example, by using the <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property.</span></span>  
  
 <span data-ttu-id="48027-120">最後，每個面板<xref:System.Windows.Forms.SplitContainer>控制項具有屬性，以決定其個別的大小。</span><span class="sxs-lookup"><span data-stu-id="48027-120">Finally, each panel of the <xref:System.Windows.Forms.SplitContainer> control has properties to determine its individual size.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="48027-121">常用屬性、方法和事件</span><span class="sxs-lookup"><span data-stu-id="48027-121">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="48027-122">名稱</span><span class="sxs-lookup"><span data-stu-id="48027-122">Name</span></span>|<span data-ttu-id="48027-123">描述</span><span class="sxs-lookup"><span data-stu-id="48027-123">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="48027-124"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-124"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> property</span></span>|<span data-ttu-id="48027-125">決定哪個面板維持相同大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小。</span><span class="sxs-lookup"><span data-stu-id="48027-125">Determines which panel will remain the same size after the <xref:System.Windows.Forms.SplitContainer> control is resized.</span></span>|  
|<span data-ttu-id="48027-126"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-126"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="48027-127">決定分隔器是否可移動的鍵盤或滑鼠。</span><span class="sxs-lookup"><span data-stu-id="48027-127">Determines if the splitter can be moved with the keyboard or mouse.</span></span>|  
|<span data-ttu-id="48027-128"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-128"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> property</span></span>|<span data-ttu-id="48027-129">決定分隔器是否垂直或水平排列。</span><span class="sxs-lookup"><span data-stu-id="48027-129">Determines if the splitter is arranged vertically or horizontally.</span></span>|  
|<span data-ttu-id="48027-130"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-130"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="48027-131">決定從左方或上方的邊緣可移動的分隔列以像素為單位的距離。</span><span class="sxs-lookup"><span data-stu-id="48027-131">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="48027-132"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-132"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="48027-133">決定最小距離，單位為像素，使用者可以移動分隔器。</span><span class="sxs-lookup"><span data-stu-id="48027-133">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
|<span data-ttu-id="48027-134"><xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="48027-134"><xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> property</span></span>|<span data-ttu-id="48027-135">決定的厚度，以像素的分隔器。</span><span class="sxs-lookup"><span data-stu-id="48027-135">Determines the thickness, in pixels, of the splitter.</span></span>|  
|<span data-ttu-id="48027-136"><xref:System.Windows.Forms.SplitContainer.SplitterMoving>事件</span><span class="sxs-lookup"><span data-stu-id="48027-136"><xref:System.Windows.Forms.SplitContainer.SplitterMoving> event</span></span>|<span data-ttu-id="48027-137">發生於分隔器移動。</span><span class="sxs-lookup"><span data-stu-id="48027-137">Occurs when the splitter is moving.</span></span>|  
|<span data-ttu-id="48027-138"><xref:System.Windows.Forms.SplitContainer.SplitterMoved>事件</span><span class="sxs-lookup"><span data-stu-id="48027-138"><xref:System.Windows.Forms.SplitContainer.SplitterMoved> event</span></span>|<span data-ttu-id="48027-139">發生於分隔器移動。</span><span class="sxs-lookup"><span data-stu-id="48027-139">Occurs when the splitter has moved.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48027-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="48027-140">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="48027-141">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="48027-141">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [<span data-ttu-id="48027-142">SplitContainer 控制項範例</span><span class="sxs-lookup"><span data-stu-id="48027-142">SplitContainer Control Sample</span></span>](http://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
