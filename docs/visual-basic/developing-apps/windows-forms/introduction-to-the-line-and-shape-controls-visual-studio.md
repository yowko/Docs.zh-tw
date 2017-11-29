---
title: "Line 和 Shape 控制項簡介 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e691d57c6de640c83556937eeddedf89e79b6846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a><span data-ttu-id="fea2d-102">Line 和 Shape 控制項簡介 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="fea2d-102">Introduction to the Line and Shape Controls (Visual Studio)</span></span>
<span data-ttu-id="fea2d-103">Visual Basic Power Pack 線條和圖案控制項是一組可讓您在表單和容器上繪製線條和形狀的三個圖形化控制項。</span><span class="sxs-lookup"><span data-stu-id="fea2d-103">The Visual Basic Power Packs Line and Shape controls are a set of three graphical controls that enable you to draw lines and shapes on forms and containers.</span></span> <span data-ttu-id="fea2d-104"><xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項用來繪製水平、 垂直和對角線線條。</span><span class="sxs-lookup"><span data-stu-id="fea2d-104">The <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control is used to draw horizontal, vertical, and diagonal lines.</span></span> <span data-ttu-id="fea2d-105"><xref:Microsoft.VisualBasic.PowerPacks.OvalShape>控制項用來繪製圓形和橢圓形，而<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項用來繪製的矩形和正方形。</span><span class="sxs-lookup"><span data-stu-id="fea2d-105">The <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control is used to draw circles and ovals, and the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control is used to draw rectangles and squares.</span></span>  
  
## <a name="line-and-shape-controls"></a><span data-ttu-id="fea2d-106">Line 和 Shape 控制項</span><span class="sxs-lookup"><span data-stu-id="fea2d-106">Line and Shape Controls</span></span>  
 <span data-ttu-id="fea2d-107">Line 和 Shape 控制項封裝的圖形方法中所包含的許多<xref:System.Drawing>命名空間。</span><span class="sxs-lookup"><span data-stu-id="fea2d-107">Line and Shape controls encapsulate many of the graphics methods that are contained in the <xref:System.Drawing> namespace.</span></span> <span data-ttu-id="fea2d-108">這可讓您在單一步驟中繪製線條與圖形，而不需要建立圖形物件，畫筆和筆刷。</span><span class="sxs-lookup"><span data-stu-id="fea2d-108">This enables you to draw lines and shapes in a single step without having to create graphics objects, pens, and brushes.</span></span> <span data-ttu-id="fea2d-109">複雜圖形技術，例如漸層填滿可藉由直接設定某些屬性。</span><span class="sxs-lookup"><span data-stu-id="fea2d-109">Complex graphics techniques such as gradient fills can be accomplished by just setting some properties.</span></span>  
  
 <span data-ttu-id="fea2d-110">此外，也可以使用圖形方法來繪製線條和形狀，雖然有使用線條和圖案控制項的數個優點：</span><span class="sxs-lookup"><span data-stu-id="fea2d-110">Although it is also possible to draw lines and shapes by using graphics methods, there are several advantages to using the Line and Shape controls:</span></span>  
  
-   <span data-ttu-id="fea2d-111">可以呼叫圖形方法只能在執行階段。</span><span class="sxs-lookup"><span data-stu-id="fea2d-111">Graphics methods can be called only at run time.</span></span> <span data-ttu-id="fea2d-112">在設計階段時，可以加入線條和圖案控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="fea2d-112">Line and Shape controls can be added to a form at design time.</span></span> <span data-ttu-id="fea2d-113">這可讓您若要查看其外觀及位置一樣大。它們也可以加入在執行階段。</span><span class="sxs-lookup"><span data-stu-id="fea2d-113">This enables you to see what they look like and to position them exactly; they can also be added at run time.</span></span>  
  
-   <span data-ttu-id="fea2d-114">Line 和 Shape 控制項可在執行階段選取，提供的事件，例如<xref:Microsoft.VisualBasic.PowerPacks.Shape.Click>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>。</span><span class="sxs-lookup"><span data-stu-id="fea2d-114">Line and Shape controls are selectable at run time, providing events such as <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> and <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>.</span></span> <span data-ttu-id="fea2d-115">圖形方法的輸出不能選取，並不提供事件。</span><span class="sxs-lookup"><span data-stu-id="fea2d-115">The outputs of graphics methods are not selectable and do not provide events.</span></span>  
  
-   <span data-ttu-id="fea2d-116">Line 和 Shape 控制項提供<xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A>可讓您控制他們的疊置順序，在設計階段和執行階段方法。</span><span class="sxs-lookup"><span data-stu-id="fea2d-116">Line and Shape controls provide <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> and <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> methods that enable you to control their z-order at design time and at run time.</span></span> <span data-ttu-id="fea2d-117">可以控制圖形方法疊置順序，只是藉由變更其在執行階段的執行順序。</span><span class="sxs-lookup"><span data-stu-id="fea2d-117">The z-order of graphics methods can be controlled only by changing their order of execution at run time.</span></span>  
  
-   <span data-ttu-id="fea2d-118">線條和圖案控制項是無視窗控制項。它們有沒有任何視窗控制代碼，因此使用較少的系統資源。</span><span class="sxs-lookup"><span data-stu-id="fea2d-118">Line and Shape controls are windowless controls; they have no window handles and therefore use less system resources.</span></span>  
  
### <a name="object-model"></a><span data-ttu-id="fea2d-119">物件模型</span><span class="sxs-lookup"><span data-stu-id="fea2d-119">Object Model</span></span>  
 <span data-ttu-id="fea2d-120">Line 和 Shape 控制項衍生自基底<xref:Microsoft.VisualBasic.PowerPacks.Shape>類別來定義其共用的屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="fea2d-120">Line and Shape controls derive from a base <xref:Microsoft.VisualBasic.PowerPacks.Shape> class that defines their shared properties, methods, and events.</span></span>  
  
 <span data-ttu-id="fea2d-121">下圖顯示 Line 和 Shape 物件階層架構。</span><span class="sxs-lookup"><span data-stu-id="fea2d-121">The following illustration shows the Line and Shape object hierarchy.</span></span>  
  
 <span data-ttu-id="fea2d-122">![Line 和 Shape 物件階層架構圖表](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")</span><span class="sxs-lookup"><span data-stu-id="fea2d-122">![A diagram of the Line and Shape object hierarchy](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")</span></span>  
<span data-ttu-id="fea2d-123">Line 和 Shape 物件階層架構</span><span class="sxs-lookup"><span data-stu-id="fea2d-123">Line and Shape object hierarchy</span></span>  
  
 <span data-ttu-id="fea2d-124">在衍生<xref:Microsoft.VisualBasic.PowerPacks.LineShape>類別包含屬性、 方法和事件都是唯一的各行。</span><span class="sxs-lookup"><span data-stu-id="fea2d-124">The derived <xref:Microsoft.VisualBasic.PowerPacks.LineShape> class contains properties, methods, and events that are unique to lines.</span></span> <span data-ttu-id="fea2d-125">在衍生<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>類別是基底類別<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; 它包含屬性、 方法和事件通用於所有形狀。</span><span class="sxs-lookup"><span data-stu-id="fea2d-125">The derived <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> class is the base class for <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; it contains properties, methods, and events common to all shapes.</span></span> <span data-ttu-id="fea2d-126">您也可以衍生自<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>自行建立`Shape`控制項。</span><span class="sxs-lookup"><span data-stu-id="fea2d-126">You can also derive from <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> to create your own `Shape` controls.</span></span>  
  
 <span data-ttu-id="fea2d-127"><xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>類別可以用來繪製圓形、 橢圓形、 矩形和具有圓角矩形。</span><span class="sxs-lookup"><span data-stu-id="fea2d-127">The <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> classes can be used to draw circles, ovals, rectangles, and rectangles with rounded corners.</span></span>  
  
 <span data-ttu-id="fea2d-128">當加入線條或圖形控制項在表單或容器，隱藏<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>建立物件。</span><span class="sxs-lookup"><span data-stu-id="fea2d-128">When a Line or Shape control is added to a form or container, an invisible <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> object is created.</span></span> <span data-ttu-id="fea2d-129"><xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>做為每個容器控制項中的圖形畫布; 每一個<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>都有對應<xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>，可讓您逐一查看 Line 和 Shape 控制項。</span><span class="sxs-lookup"><span data-stu-id="fea2d-129">The <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> acts as a canvas for the shapes within each container control; each <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> has a corresponding <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> that enables you to iterate through the Line and Shape controls.</span></span> <span data-ttu-id="fea2d-130">您可以移動圖形從一個容器到另一個使用剪下和貼上或透過拖放。</span><span class="sxs-lookup"><span data-stu-id="fea2d-130">You can move shapes from one container to another by using cut and paste or by dragging and dropping.</span></span> <span data-ttu-id="fea2d-131">從容器中，移除最後一個圖形時<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>也會移除。</span><span class="sxs-lookup"><span data-stu-id="fea2d-131">When the last shape is removed from a container, the <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> is removed also.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fea2d-132">並非所有的容器控制項支援線條和圖案控制項。</span><span class="sxs-lookup"><span data-stu-id="fea2d-132">Not all container controls support the Line and Shape controls.</span></span> <span data-ttu-id="fea2d-133">您無法將裝載線條或圖形控制項上<xref:System.Windows.Forms.TableLayoutPanel>或<xref:System.Windows.Forms.FlowLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="fea2d-133">You cannot host a Line or Shape control on a <xref:System.Windows.Forms.TableLayoutPanel> or a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea2d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fea2d-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [<span data-ttu-id="fea2d-135">操作說明：使用 LineShape 控制項繪製線條</span><span class="sxs-lookup"><span data-stu-id="fea2d-135">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="fea2d-136">操作說明：使用 OvalShape 和 RectangleShape 控制項繪製圖案</span><span class="sxs-lookup"><span data-stu-id="fea2d-136">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="fea2d-137">操作說明：在圖案間啟用定位停駐點</span><span class="sxs-lookup"><span data-stu-id="fea2d-137">How to: Enable Tabbing Between Shapes</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
