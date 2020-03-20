---
title: 如何：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182638"
---
# <a name="how-to-create-a-path-gradient"></a><span data-ttu-id="84c4c-102">如何：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="84c4c-102">How to: Create a Path Gradient</span></span>
<span data-ttu-id="84c4c-103">該<xref:System.Drawing.Drawing2D.PathGradientBrush>類允許您自訂使用逐漸更改的顏色填充形狀的方式。</span><span class="sxs-lookup"><span data-stu-id="84c4c-103">The <xref:System.Drawing.Drawing2D.PathGradientBrush> class allows you to customize the way you fill a shape with gradually changing colors.</span></span> <span data-ttu-id="84c4c-104">例如，可以為路徑的中心指定一種顏色，為路徑的邊界指定另一種顏色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-104">For example, you can specify one color for the center of a path and another color for the boundary of a path.</span></span> <span data-ttu-id="84c4c-105">您還可以為路徑邊界上的多個點指定單獨的顏色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-105">You can also specify separate colors for each of several points along the boundary of a path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84c4c-106">在 GDI+中，路徑是由<xref:System.Drawing.Drawing2D.GraphicsPath>物件維護的線和曲線序列。</span><span class="sxs-lookup"><span data-stu-id="84c4c-106">In GDI+, a path is a sequence of lines and curves maintained by a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="84c4c-107">有關 GDI+ 路徑的詳細資訊，請參閱[GDI+ 中的圖形路徑](graphics-paths-in-gdi.md)以及[構造和繪圖路徑](constructing-and-drawing-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="84c4c-107">For more information about GDI+ paths, see [Graphics Paths in GDI+](graphics-paths-in-gdi.md) and [Constructing and Drawing Paths](constructing-and-drawing-paths.md).</span></span>  

<span data-ttu-id="84c4c-108">本文中的示例是從控制項<xref:System.Windows.Forms.Control.Paint>的事件處理常式調用的方法。</span><span class="sxs-lookup"><span data-stu-id="84c4c-108">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a><span data-ttu-id="84c4c-109">用路徑漸變填充橢圓</span><span class="sxs-lookup"><span data-stu-id="84c4c-109">To fill an ellipse with a path gradient</span></span>  
  
- <span data-ttu-id="84c4c-110">下面的示例使用路徑漸層筆刷填充橢圓。</span><span class="sxs-lookup"><span data-stu-id="84c4c-110">The following example fills an ellipse with a path gradient brush.</span></span> <span data-ttu-id="84c4c-111">中心顏色設置為藍色，邊界顏色設置為水色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-111">The center color is set to blue and the boundary color is set to aqua.</span></span> <span data-ttu-id="84c4c-112">下圖顯示了填充的橢圓。</span><span class="sxs-lookup"><span data-stu-id="84c4c-112">The following illustration shows the filled ellipse.</span></span>  
  
     ![漸變路徑填充橢圓。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     <span data-ttu-id="84c4c-114">預設情況下，路徑漸層筆刷不會擴展到路徑的邊界之外。</span><span class="sxs-lookup"><span data-stu-id="84c4c-114">By default, a path gradient brush does not extend outside the boundary of the path.</span></span> <span data-ttu-id="84c4c-115">如果使用路徑漸層筆刷填充超出路徑邊界的圖形，則不會填充路徑外部的螢幕區域。</span><span class="sxs-lookup"><span data-stu-id="84c4c-115">If you use the path gradient brush to fill a figure that extends beyond the boundary of the path, the area of the screen outside the path will not be filled.</span></span>  
  
     <span data-ttu-id="84c4c-116">下圖顯示了如果將以下代碼中的<xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType>調用更改為`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`：</span><span class="sxs-lookup"><span data-stu-id="84c4c-116">The following illustration shows what happens if you change the <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> call in the following code to `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:</span></span>  
  
     ![漸變路徑超出路徑的邊界。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     <span data-ttu-id="84c4c-118">前面的代碼示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>e，這是 的<xref:System.Windows.Forms.PaintEventHandler>參數。</span><span class="sxs-lookup"><span data-stu-id="84c4c-118">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> e, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
### <a name="to-specify-points-on-the-boundary"></a><span data-ttu-id="84c4c-119">指定邊界上的點</span><span class="sxs-lookup"><span data-stu-id="84c4c-119">To specify points on the boundary</span></span>  
  
- <span data-ttu-id="84c4c-120">下面的示例從星形路徑構造路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="84c4c-120">The following example constructs a path gradient brush from a star-shaped path.</span></span> <span data-ttu-id="84c4c-121">代碼設置屬性<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>，該屬性將星形的質心處的顏色設置為紅色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-121">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> property, which sets the color at the centroid of the star to red.</span></span> <span data-ttu-id="84c4c-122">然後，代碼設置屬性<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>以在`points`陣列中的單個點指定各種顏色`colors`（存儲在陣列中）。</span><span class="sxs-lookup"><span data-stu-id="84c4c-122">Then the code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> property to specify various colors (stored in the `colors` array) at the individual points in the `points` array.</span></span> <span data-ttu-id="84c4c-123">最後的代碼語句使用路徑漸層筆刷填充星形路徑。</span><span class="sxs-lookup"><span data-stu-id="84c4c-123">The final code statement fills the star-shaped path with the path gradient brush.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- <span data-ttu-id="84c4c-124">下面的示例繪製一個路徑漸變，沒有<xref:System.Drawing.Drawing2D.GraphicsPath>代碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="84c4c-124">The following example draws a path gradient without a <xref:System.Drawing.Drawing2D.GraphicsPath> object in the code.</span></span> <span data-ttu-id="84c4c-125">示例中的特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>建構函式接收點陣列，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="84c4c-125">The particular <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructor in the example receives an array of points but does not require a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="84c4c-126">此外，請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用於填充矩形，而不是路徑。</span><span class="sxs-lookup"><span data-stu-id="84c4c-126">Also, note that the <xref:System.Drawing.Drawing2D.PathGradientBrush> is used to fill a rectangle, not a path.</span></span> <span data-ttu-id="84c4c-127">矩形大於用於定義畫筆的封閉路徑，因此某些矩形不是由畫筆繪製的。</span><span class="sxs-lookup"><span data-stu-id="84c4c-127">The rectangle is larger than the closed path used to define the brush, so some of the rectangle is not painted by the brush.</span></span> <span data-ttu-id="84c4c-128">下圖顯示了矩形（虛線）和由路徑漸層筆刷繪製的矩形部分：</span><span class="sxs-lookup"><span data-stu-id="84c4c-128">The following illustration shows the rectangle (dotted line) and the portion of the rectangle painted by the path gradient brush:</span></span>
  
     ![由路徑漸層筆刷繪製的漸變部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a><span data-ttu-id="84c4c-130">自訂路徑漸變</span><span class="sxs-lookup"><span data-stu-id="84c4c-130">To customize a path gradient</span></span>  
  
- <span data-ttu-id="84c4c-131">自訂路徑漸層筆刷的一種方法是設置其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="84c4c-131">One way to customize a path gradient brush is to set its <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> property.</span></span> <span data-ttu-id="84c4c-132">焦點比例指定位於主路徑內的內路徑。</span><span class="sxs-lookup"><span data-stu-id="84c4c-132">The focus scales specify an inner path that lies inside the main path.</span></span> <span data-ttu-id="84c4c-133">中心顏色顯示在該內部路徑的任何地方，而不僅僅是中心點。</span><span class="sxs-lookup"><span data-stu-id="84c4c-133">The center color is displayed everywhere inside that inner path rather than only at the center point.</span></span>  
  
     <span data-ttu-id="84c4c-134">下面的示例基於橢圓路徑創建路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="84c4c-134">The following example creates a path gradient brush based on an elliptical path.</span></span> <span data-ttu-id="84c4c-135">代碼將邊界顏色設置為藍色，將中心顏色設置為水族，然後使用路徑漸層筆刷填充橢圓路徑。</span><span class="sxs-lookup"><span data-stu-id="84c4c-135">The code sets the boundary color to blue, sets the center color to aqua, and then uses the path gradient brush to fill the elliptical path.</span></span>  
  
     <span data-ttu-id="84c4c-136">接下來，代碼設置路徑漸層筆刷的焦點比例。</span><span class="sxs-lookup"><span data-stu-id="84c4c-136">Next, the code sets the focus scales of the path gradient brush.</span></span> <span data-ttu-id="84c4c-137">x 焦點比例設置為 0.3，y 焦點比例設置為 0.8。</span><span class="sxs-lookup"><span data-stu-id="84c4c-137">The x focus scale is set to 0.3, and the y focus scale is set to 0.8.</span></span> <span data-ttu-id="84c4c-138">代碼調用<xref:System.Drawing.Graphics.TranslateTransform%2A><xref:System.Drawing.Graphics>物件的方法，以便後續調用以<xref:System.Drawing.Graphics.FillPath%2A>填充位於第一個橢圓右側的橢圓。</span><span class="sxs-lookup"><span data-stu-id="84c4c-138">The code calls the <xref:System.Drawing.Graphics.TranslateTransform%2A> method of a <xref:System.Drawing.Graphics> object so that the subsequent call to <xref:System.Drawing.Graphics.FillPath%2A> fills an ellipse that sits to the right of the first ellipse.</span></span>  
  
     <span data-ttu-id="84c4c-139">要查看焦點縮放的效果，想像一個與主橢圓共用中心的小橢圓。</span><span class="sxs-lookup"><span data-stu-id="84c4c-139">To see the effect of the focus scales, imagine a small ellipse that shares its center with the main ellipse.</span></span> <span data-ttu-id="84c4c-140">小橢圓是水準縮放（大約其中心）的主橢圓，由 0.3 倍和垂直 0.8 倍數垂直縮放。</span><span class="sxs-lookup"><span data-stu-id="84c4c-140">The small (inner) ellipse is the main ellipse scaled (about its center) horizontally by a factor of 0.3 and vertically by a factor of 0.8.</span></span> <span data-ttu-id="84c4c-141">當您從外部橢圓的邊界移動到內部橢圓的邊界時，顏色會逐漸從藍色變為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-141">As you move from the boundary of the outer ellipse to the boundary of the inner ellipse, the color changes gradually from blue to aqua.</span></span> <span data-ttu-id="84c4c-142">當您從內部橢圓的邊界移動到共用中心時，顏色將保持淺色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-142">As you move from the boundary of the inner ellipse to the shared center, the color remains aqua.</span></span>  
  
     <span data-ttu-id="84c4c-143">下圖顯示下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="84c4c-143">The following illustration shows the output of the following code.</span></span> <span data-ttu-id="84c4c-144">左側的橢圓僅在中心點處是水族。</span><span class="sxs-lookup"><span data-stu-id="84c4c-144">The ellipse on the left is aqua only at the center point.</span></span> <span data-ttu-id="84c4c-145">右邊的橢圓在內路內隨處可見。</span><span class="sxs-lookup"><span data-stu-id="84c4c-145">The ellipse on the right is aqua everywhere inside the inner path.</span></span>  
  
 ![焦點尺度的漸變效果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a><span data-ttu-id="84c4c-147">使用插值進行自訂</span><span class="sxs-lookup"><span data-stu-id="84c4c-147">To customize with interpolation</span></span>  
  
- <span data-ttu-id="84c4c-148">自訂路徑漸層筆刷的另一種方法是指定插值顏色陣列和插值位置陣列。</span><span class="sxs-lookup"><span data-stu-id="84c4c-148">Another way to customize a path gradient brush is to specify an array of interpolation colors and an array of interpolation positions.</span></span>  
  
     <span data-ttu-id="84c4c-149">下面的示例基於三角形創建路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="84c4c-149">The following example creates a path gradient brush based on a triangle.</span></span> <span data-ttu-id="84c4c-150">代碼設置路徑漸變<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>畫筆的屬性以指定插值顏色陣列（深綠色、水彩、藍色）和插值位置陣列（0、0.25、1）。</span><span class="sxs-lookup"><span data-stu-id="84c4c-150">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> property of the path gradient brush to specify an array of interpolation colors (dark green, aqua, blue) and an array of interpolation positions (0, 0.25, 1).</span></span> <span data-ttu-id="84c4c-151">當您從三角形的邊界移動到中心點時，顏色逐漸從深綠色變為淺綠色，然後從淺綠色變為藍色。</span><span class="sxs-lookup"><span data-stu-id="84c4c-151">As you move from the boundary of the triangle to the center point, the color changes gradually from dark green to aqua and then from aqua to blue.</span></span> <span data-ttu-id="84c4c-152">從深綠色到淺綠色的變化發生在從深綠色到藍色25%的距離。</span><span class="sxs-lookup"><span data-stu-id="84c4c-152">The change from dark green to aqua happens in 25 percent of the distance from dark green to blue.</span></span>  
  
     <span data-ttu-id="84c4c-153">下圖顯示了使用自訂路徑漸層筆刷填充的三角形。</span><span class="sxs-lookup"><span data-stu-id="84c4c-153">The following illustration shows the triangle filled with the custom path gradient brush.</span></span>  
  
     ![用自訂路徑漸層筆刷填充的三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a><span data-ttu-id="84c4c-155">設置中心點</span><span class="sxs-lookup"><span data-stu-id="84c4c-155">To set the center point</span></span>  
  
- <span data-ttu-id="84c4c-156">預設情況下，路徑漸層筆刷的中心點位於用於構造畫筆的路徑的質心。</span><span class="sxs-lookup"><span data-stu-id="84c4c-156">By default, the center point of a path gradient brush is at the centroid of the path used to construct the brush.</span></span> <span data-ttu-id="84c4c-157">您可以通過設置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A><xref:System.Drawing.Drawing2D.PathGradientBrush>類的屬性來更改中心點的位置。</span><span class="sxs-lookup"><span data-stu-id="84c4c-157">You can change the location of the center point by setting the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property of the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
     <span data-ttu-id="84c4c-158">下面的示例基於橢圓創建路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="84c4c-158">The following example creates a path gradient brush based on an ellipse.</span></span> <span data-ttu-id="84c4c-159">橢圓的中心位於 （70， 35），但路徑漸層筆刷的中心點設置為 （120， 40）。</span><span class="sxs-lookup"><span data-stu-id="84c4c-159">The center of the ellipse is at (70, 35), but the center point of the path gradient brush is set to (120, 40).</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     <span data-ttu-id="84c4c-160">下圖顯示了填充橢圓和路徑漸層筆刷的中心點：</span><span class="sxs-lookup"><span data-stu-id="84c4c-160">The following illustration shows the filled ellipse and the center point of the path gradient brush:</span></span>  
  
     ![具有填充橢圓和中心點的漸變路徑。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- <span data-ttu-id="84c4c-162">您可以將路徑漸層筆刷的中心點設置為用於構造畫筆的路徑外部的位置。</span><span class="sxs-lookup"><span data-stu-id="84c4c-162">You can set the center point of a path gradient brush to a location outside the path that was used to construct the brush.</span></span> <span data-ttu-id="84c4c-163">下面的示例替換調用以在前面的代碼中設置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="84c4c-163">The following example replaces the call to set the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property in the preceding code.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     <span data-ttu-id="84c4c-164">下圖顯示了此更改的輸出：</span><span class="sxs-lookup"><span data-stu-id="84c4c-164">The following illustration shows the output with this change:</span></span>  
  
     ![路徑外部中心點的漸變路徑。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     <span data-ttu-id="84c4c-166">在前面的圖中，橢圓最右邊的點不是純藍色（儘管它們非常接近）。</span><span class="sxs-lookup"><span data-stu-id="84c4c-166">In the preceding illustration, the points at the far right of the ellipse are not pure blue (although they are very close).</span></span> <span data-ttu-id="84c4c-167">漸變中的顏色定位如下填充到達該點 （145， 35），其中顏色為純藍色 （0，0，255）。</span><span class="sxs-lookup"><span data-stu-id="84c4c-167">The colors in the gradient are positioned as if the fill reached the point (145, 35) where the color would be pure blue (0, 0, 255).</span></span> <span data-ttu-id="84c4c-168">但填充永遠不會達到 （145， 35），因為路徑漸層筆刷只在其路徑內繪製。</span><span class="sxs-lookup"><span data-stu-id="84c4c-168">But the fill never reaches (145, 35) because a path gradient brush paints only inside its path.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84c4c-169">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="84c4c-169">Compiling the Code</span></span>  
 <span data-ttu-id="84c4c-170">前面的示例設計用於 Windows 表單，它們需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。</span><span class="sxs-lookup"><span data-stu-id="84c4c-170">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c4c-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84c4c-171">See also</span></span>

- [<span data-ttu-id="84c4c-172">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="84c4c-172">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
