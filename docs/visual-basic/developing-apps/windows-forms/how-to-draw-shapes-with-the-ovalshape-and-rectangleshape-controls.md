---
title: "如何：使用 OvalShape 和 RectangleShape 控制項繪製圖案 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="40117-102">如何：使用 OvalShape 和 RectangleShape 控制項繪製圖案 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="40117-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="40117-103">您可以在設計階段和執行階段使用 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 控制項，在表單或容器上繪製圓形或橢圓形。</span><span class="sxs-lookup"><span data-stu-id="40117-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="40117-104">您可以使用 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項在表單或容器上繪製正方形、矩形或是有圓角的矩形。</span><span class="sxs-lookup"><span data-stu-id="40117-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="40117-105">您也可以在設計階段和執行階段使用此控制項來繪製圖形。</span><span class="sxs-lookup"><span data-stu-id="40117-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="40117-106">您可以藉由變更框線的寬度、色彩和樣式，來自訂圖形的外觀。</span><span class="sxs-lookup"><span data-stu-id="40117-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="40117-107">圖形的背景預設是透明的；您可以自訂背景以顯示單色、圖樣、漸層填滿 (從一種色彩轉換到另一種色彩) 或影像。</span><span class="sxs-lookup"><span data-stu-id="40117-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="40117-108">在設計階段繪製簡單圖形</span><span class="sxs-lookup"><span data-stu-id="40117-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="40117-109">拖曳<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>或<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項從**Visual Basic PowerPacks**  索引標籤 (若要安裝，請參閱[Visual Basic Power Packs 控制項](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) 中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-110">拖曳調整大小，並移動控點以調整圖形的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="40117-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="40117-111">您可以調整大小，並將圖形藉由變更`Size`和`Position`中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="40117-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="40117-112">若要建立具有圓角的矩形，請選取`CornerRadius`屬性**屬性**視窗並將它設為大於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="40117-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="40117-113">在**屬性** 視窗中，選擇性地設定其他屬性，來變更圖形的外觀。</span><span class="sxs-lookup"><span data-stu-id="40117-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="40117-114">在執行階段繪製簡單圖形</span><span class="sxs-lookup"><span data-stu-id="40117-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="40117-115">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="40117-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="40117-116">在**加入參考**對話方塊中，選取**Microsoft.VisualBasic.PowerPacks.VS**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="40117-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="40117-117">在**程式碼編輯器**，新增`Imports`或`using`陳述式之模組的頂端：</span><span class="sxs-lookup"><span data-stu-id="40117-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="40117-118">在 `Event` 程序中加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="40117-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="40117-119">自訂圖形</span><span class="sxs-lookup"><span data-stu-id="40117-119">Customizing Shapes</span></span>  
 <span data-ttu-id="40117-120">使用預設設定時，<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 和 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項會顯示為一個像素寬的實心黑色框線以及透明背景。</span><span class="sxs-lookup"><span data-stu-id="40117-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="40117-121">藉由設定屬性，可以變更框線的寬度、樣式和色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="40117-122">其他屬性可讓您將圖形的背景變更為單色、圖樣、漸層填滿或影像。</span><span class="sxs-lookup"><span data-stu-id="40117-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="40117-123">變更圖形的背景之前，您應該知道數個屬性互動的方式。</span><span class="sxs-lookup"><span data-stu-id="40117-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="40117-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> 屬性設定沒有任何作用，除非 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>。</span><span class="sxs-lookup"><span data-stu-id="40117-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="40117-125">如果 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>，<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> 會覆寫 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>。</span><span class="sxs-lookup"><span data-stu-id="40117-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="40117-126">如果 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性設定為圖樣值 (如 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> 或 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>)，圖樣將顯示在 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> 中。</span><span class="sxs-lookup"><span data-stu-id="40117-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="40117-127">背景將會顯示在 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> 中，條件是 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>。</span><span class="sxs-lookup"><span data-stu-id="40117-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="40117-128">若要顯示漸層填滿，<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性必須設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>，且 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> 屬性必須設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None> 以外的值。</span><span class="sxs-lookup"><span data-stu-id="40117-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="40117-129">將 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> 屬性設定為影像會覆寫所有其他的背景設定。</span><span class="sxs-lookup"><span data-stu-id="40117-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="40117-130">繪製有自訂框線的圓形</span><span class="sxs-lookup"><span data-stu-id="40117-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="40117-131">拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-132">在**屬性**視窗，請在`Size`屬性，將`Height`和`Width`為相等的值。</span><span class="sxs-lookup"><span data-stu-id="40117-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="40117-133">將 `BorderColor` 屬性設定為所要的色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="40117-134">將 `BorderStyle` 屬性設定為 `Solid` 以外的任何值。</span><span class="sxs-lookup"><span data-stu-id="40117-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="40117-135">將 `BorderWidth` 設定為您想要的大小 (以像素為單位)。</span><span class="sxs-lookup"><span data-stu-id="40117-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="40117-136">繪製有實心填滿的圓形</span><span class="sxs-lookup"><span data-stu-id="40117-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="40117-137">拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-138">在**屬性**視窗，請在`Size`屬性，將`Height`和`Width`為相等的值。</span><span class="sxs-lookup"><span data-stu-id="40117-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="40117-139">將 `BackColor` 屬性設定為所要的色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="40117-140">將 `BackStyle` 屬性設定為 `Opaque`。</span><span class="sxs-lookup"><span data-stu-id="40117-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="40117-141">繪製有圖樣填滿的圓形</span><span class="sxs-lookup"><span data-stu-id="40117-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="40117-142">拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-143">在**屬性**視窗，請在`Size`屬性，將`Height`和`Width`為相等的值。</span><span class="sxs-lookup"><span data-stu-id="40117-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="40117-144">將 `BackColor` 屬性設定為您想要的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="40117-145">將 `BackStyle` 屬性設定為 `Opaque`。</span><span class="sxs-lookup"><span data-stu-id="40117-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="40117-146">將 `FillColor` 屬性設定為您想要的圖樣色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="40117-147">將 `FillStyle` 屬性設定為 `Transparent` 或 `Solid` 以外的任何值。</span><span class="sxs-lookup"><span data-stu-id="40117-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="40117-148">繪製有漸層填滿的圓形</span><span class="sxs-lookup"><span data-stu-id="40117-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="40117-149">拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-150">在**屬性**視窗，請在`Size`屬性，將`Height`和`Width`為相等的值。</span><span class="sxs-lookup"><span data-stu-id="40117-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="40117-151">將 `FillColor` 屬性設定為您想要的開始色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="40117-152">將 `FillGradientColor` 屬性設定為您想要的結束色彩。</span><span class="sxs-lookup"><span data-stu-id="40117-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="40117-153">將 `FillGradientStyle` 屬性設定為 `None` 以外的任何值。</span><span class="sxs-lookup"><span data-stu-id="40117-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="40117-154">繪製填滿影像的圓形</span><span class="sxs-lookup"><span data-stu-id="40117-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="40117-155">拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="40117-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="40117-156">在**屬性**視窗，請在`Size`屬性，將`Height`和`Width`為相等的值。</span><span class="sxs-lookup"><span data-stu-id="40117-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="40117-157">選取`BackgroundImage`屬性，然後按一下**省略**按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="40117-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="40117-158">在**選取資源**對話方塊中，選取要顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="40117-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="40117-159">如果未不列出任何影像資源，請按一下**匯入**瀏覽至影像的位置。</span><span class="sxs-lookup"><span data-stu-id="40117-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="40117-160">按一下**確定**以插入影像。</span><span class="sxs-lookup"><span data-stu-id="40117-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40117-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40117-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="40117-162">Line 和 Shape 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="40117-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="40117-163">操作說明：使用 LineShape 控制項繪製線條</span><span class="sxs-lookup"><span data-stu-id="40117-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
