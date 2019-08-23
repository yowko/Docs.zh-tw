---
title: 作法：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964408"
---
# <a name="how-to-create-a-path-gradient"></a><span data-ttu-id="23edb-102">作法：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="23edb-102">How to: Create a Path Gradient</span></span>
<span data-ttu-id="23edb-103"><xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂以逐漸變更色彩填滿圖形的方式。</span><span class="sxs-lookup"><span data-stu-id="23edb-103">The <xref:System.Drawing.Drawing2D.PathGradientBrush> class allows you to customize the way you fill a shape with gradually changing colors.</span></span> <span data-ttu-id="23edb-104">例如, 您可以為路徑的中心指定一個色彩, 並為路徑的界限指定另一個色彩。</span><span class="sxs-lookup"><span data-stu-id="23edb-104">For example, you can specify one color for the center of a path and another color for the boundary of a path.</span></span> <span data-ttu-id="23edb-105">您也可以針對路徑界限中的每個點指定不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="23edb-105">You can also specify separate colors for each of several points along the boundary of a path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23edb-106">在 gdi + 中, 路徑是一系列由<xref:System.Drawing.Drawing2D.GraphicsPath>物件維護的線條和曲線。</span><span class="sxs-lookup"><span data-stu-id="23edb-106">In GDI+, a path is a sequence of lines and curves maintained by a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="23edb-107">如需 GDI + 路徑的詳細資訊, 請參閱[GDI + 中的圖形路徑](graphics-paths-in-gdi.md)和[構造和繪製路徑](constructing-and-drawing-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="23edb-107">For more information about GDI+ paths, see [Graphics Paths in GDI+](graphics-paths-in-gdi.md) and [Constructing and Drawing Paths](constructing-and-drawing-paths.md).</span></span>  

<span data-ttu-id="23edb-108">本文中的範例是從控制項的<xref:System.Windows.Forms.Control.Paint>事件處理常式呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="23edb-108">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a><span data-ttu-id="23edb-109">若要以路徑漸層填滿橢圓形</span><span class="sxs-lookup"><span data-stu-id="23edb-109">To fill an ellipse with a path gradient</span></span>  
  
- <span data-ttu-id="23edb-110">下列範例會以路徑漸層筆刷填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="23edb-110">The following example fills an ellipse with a path gradient brush.</span></span> <span data-ttu-id="23edb-111">中間色彩設定為藍色, 且邊界色彩設定為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="23edb-111">The center color is set to blue and the boundary color is set to aqua.</span></span> <span data-ttu-id="23edb-112">下圖顯示已填滿的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="23edb-112">The following illustration shows the filled ellipse.</span></span>  
  
     ![漸層路徑會填滿橢圓形。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     <span data-ttu-id="23edb-114">根據預設, 路徑漸層筆刷不會延伸至路徑的界限之外。</span><span class="sxs-lookup"><span data-stu-id="23edb-114">By default, a path gradient brush does not extend outside the boundary of the path.</span></span> <span data-ttu-id="23edb-115">如果您使用路徑漸層筆刷來填滿超出路徑界限的圖形, 則不會填滿路徑外的螢幕區域。</span><span class="sxs-lookup"><span data-stu-id="23edb-115">If you use the path gradient brush to fill a figure that extends beyond the boundary of the path, the area of the screen outside the path will not be filled.</span></span>  
  
     <span data-ttu-id="23edb-116">下圖顯示當您將下列程式碼中<xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType>的呼叫變更為`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`時, 會發生什麼情況:</span><span class="sxs-lookup"><span data-stu-id="23edb-116">The following illustration shows what happens if you change the <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> call in the following code to `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:</span></span>  
  
     ![漸層路徑延伸超出路徑界限。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     <span data-ttu-id="23edb-118">上述程式碼範例的設計目的是要與 Windows Forms 搭配使用, 而且<xref:System.Windows.Forms.PaintEventArgs>它需要 e, 這是的<xref:System.Windows.Forms.PaintEventHandler>參數。</span><span class="sxs-lookup"><span data-stu-id="23edb-118">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> e, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
### <a name="to-specify-points-on-the-boundary"></a><span data-ttu-id="23edb-119">若要指定界限上的點</span><span class="sxs-lookup"><span data-stu-id="23edb-119">To specify points on the boundary</span></span>  
  
- <span data-ttu-id="23edb-120">下列範例會從星形形路徑中, 建立路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="23edb-120">The following example constructs a path gradient brush from a star-shaped path.</span></span> <span data-ttu-id="23edb-121">程式碼會設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性, 將星號的距心色彩設定為紅色。</span><span class="sxs-lookup"><span data-stu-id="23edb-121">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> property, which sets the color at the centroid of the star to red.</span></span> <span data-ttu-id="23edb-122">然後, 程式碼會<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>設定屬性, 以指定`points`陣列中個別點`colors`的各種色彩 (儲存在陣列中)。</span><span class="sxs-lookup"><span data-stu-id="23edb-122">Then the code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> property to specify various colors (stored in the `colors` array) at the individual points in the `points` array.</span></span> <span data-ttu-id="23edb-123">最後的程式碼語句會以路徑漸層筆刷填滿星形形路徑。</span><span class="sxs-lookup"><span data-stu-id="23edb-123">The final code statement fills the star-shaped path with the path gradient brush.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- <span data-ttu-id="23edb-124">下列範例會在程式碼中繪製路徑<xref:System.Drawing.Drawing2D.GraphicsPath>漸層, 而不使用物件。</span><span class="sxs-lookup"><span data-stu-id="23edb-124">The following example draws a path gradient without a <xref:System.Drawing.Drawing2D.GraphicsPath> object in the code.</span></span> <span data-ttu-id="23edb-125">範例中<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>的特定函數會接收點陣列, 但不<xref:System.Drawing.Drawing2D.GraphicsPath>需要物件。</span><span class="sxs-lookup"><span data-stu-id="23edb-125">The particular <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructor in the example receives an array of points but does not require a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="23edb-126">另請注意<xref:System.Drawing.Drawing2D.PathGradientBrush> , 是用來填滿矩形, 而不是路徑。</span><span class="sxs-lookup"><span data-stu-id="23edb-126">Also, note that the <xref:System.Drawing.Drawing2D.PathGradientBrush> is used to fill a rectangle, not a path.</span></span> <span data-ttu-id="23edb-127">矩形大於用來定義筆刷的封閉路徑, 因此筆刷不會繪製某些矩形。</span><span class="sxs-lookup"><span data-stu-id="23edb-127">The rectangle is larger than the closed path used to define the brush, so some of the rectangle is not painted by the brush.</span></span> <span data-ttu-id="23edb-128">下圖顯示以路徑漸層筆刷繪製的矩形 (虛線) 和矩形部分:</span><span class="sxs-lookup"><span data-stu-id="23edb-128">The following illustration shows the rectangle (dotted line) and the portion of the rectangle painted by the path gradient brush:</span></span> 
  
     ![由路徑漸層筆刷繪製的漸層部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a><span data-ttu-id="23edb-130">自訂路徑漸層</span><span class="sxs-lookup"><span data-stu-id="23edb-130">To customize a path gradient</span></span>  
  
- <span data-ttu-id="23edb-131">自訂路徑漸層筆刷的其中一個方法是<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="23edb-131">One way to customize a path gradient brush is to set its <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> property.</span></span> <span data-ttu-id="23edb-132">焦點縮放會指定位於主要路徑內部的內部路徑。</span><span class="sxs-lookup"><span data-stu-id="23edb-132">The focus scales specify an inner path that lies inside the main path.</span></span> <span data-ttu-id="23edb-133">中央色彩會顯示在內部路徑的任何位置, 而不是僅在中心點。</span><span class="sxs-lookup"><span data-stu-id="23edb-133">The center color is displayed everywhere inside that inner path rather than only at the center point.</span></span>  
  
     <span data-ttu-id="23edb-134">下列範例會建立以橢圓形路徑為基礎的路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="23edb-134">The following example creates a path gradient brush based on an elliptical path.</span></span> <span data-ttu-id="23edb-135">程式碼會將邊界色彩設定為藍色, 並將中間色彩設定為淺綠色, 然後使用路徑漸層筆刷來填滿橢圓形路徑。</span><span class="sxs-lookup"><span data-stu-id="23edb-135">The code sets the boundary color to blue, sets the center color to aqua, and then uses the path gradient brush to fill the elliptical path.</span></span>  
  
     <span data-ttu-id="23edb-136">接下來, 程式碼會設定路徑漸層筆刷的焦點縮放。</span><span class="sxs-lookup"><span data-stu-id="23edb-136">Next, the code sets the focus scales of the path gradient brush.</span></span> <span data-ttu-id="23edb-137">X 焦點尺規設定為 0.3, 而 y 焦點尺規設定為0.8。</span><span class="sxs-lookup"><span data-stu-id="23edb-137">The x focus scale is set to 0.3, and the y focus scale is set to 0.8.</span></span> <span data-ttu-id="23edb-138">程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics>物件的方法, 讓後續的呼叫填滿位於第一個橢圓形右邊的橢圓形。<xref:System.Drawing.Graphics.FillPath%2A></span><span class="sxs-lookup"><span data-stu-id="23edb-138">The code calls the <xref:System.Drawing.Graphics.TranslateTransform%2A> method of a <xref:System.Drawing.Graphics> object so that the subsequent call to <xref:System.Drawing.Graphics.FillPath%2A> fills an ellipse that sits to the right of the first ellipse.</span></span>  
  
     <span data-ttu-id="23edb-139">若要查看焦點刻度的效果, 請想像一個小橢圓形, 其中心與主要橢圓形共用。</span><span class="sxs-lookup"><span data-stu-id="23edb-139">To see the effect of the focus scales, imagine a small ellipse that shares its center with the main ellipse.</span></span> <span data-ttu-id="23edb-140">小型 (內部) 橢圓形是以0.3 和垂直因數 (0.8) 水準縮放的主要橢圓形 (大約是其中心)。</span><span class="sxs-lookup"><span data-stu-id="23edb-140">The small (inner) ellipse is the main ellipse scaled (about its center) horizontally by a factor of 0.3 and vertically by a factor of 0.8.</span></span> <span data-ttu-id="23edb-141">當您從外部橢圓形的界限移至內部橢圓形的界限時, 色彩會從藍色逐漸變更為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="23edb-141">As you move from the boundary of the outer ellipse to the boundary of the inner ellipse, the color changes gradually from blue to aqua.</span></span> <span data-ttu-id="23edb-142">當您從內部橢圓形的界限移到共用中心時, 色彩會保持為淺綠色。</span><span class="sxs-lookup"><span data-stu-id="23edb-142">As you move from the boundary of the inner ellipse to the shared center, the color remains aqua.</span></span>  
  
     <span data-ttu-id="23edb-143">下圖顯示下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="23edb-143">The following illustration shows the output of the following code.</span></span> <span data-ttu-id="23edb-144">左邊的橢圓形只有在中心點才是淺綠色。</span><span class="sxs-lookup"><span data-stu-id="23edb-144">The ellipse on the left is aqua only at the center point.</span></span> <span data-ttu-id="23edb-145">右邊的橢圓形在內部路徑內部的任何位置都是綠色。</span><span class="sxs-lookup"><span data-stu-id="23edb-145">The ellipse on the right is aqua everywhere inside the inner path.</span></span>  
  
 ![焦點縮放的漸層效果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a><span data-ttu-id="23edb-147">使用插補自訂</span><span class="sxs-lookup"><span data-stu-id="23edb-147">To customize with interpolation</span></span>  
  
- <span data-ttu-id="23edb-148">自訂路徑漸層筆刷的另一種方式, 是指定插補色彩的陣列和插補位置的陣列。</span><span class="sxs-lookup"><span data-stu-id="23edb-148">Another way to customize a path gradient brush is to specify an array of interpolation colors and an array of interpolation positions.</span></span>  
  
     <span data-ttu-id="23edb-149">下列範例會根據三角形建立路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="23edb-149">The following example creates a path gradient brush based on a triangle.</span></span> <span data-ttu-id="23edb-150">程式碼會設定<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷的屬性, 以指定插補色彩的陣列 (深綠色、綠色、藍色) 和插補位置的陣列 (0、0.25、1)。</span><span class="sxs-lookup"><span data-stu-id="23edb-150">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> property of the path gradient brush to specify an array of interpolation colors (dark green, aqua, blue) and an array of interpolation positions (0, 0.25, 1).</span></span> <span data-ttu-id="23edb-151">當您從三角形的邊界移至中心點時, 色彩會從深綠色逐漸變更為淺青, 然後從青色變成藍色。</span><span class="sxs-lookup"><span data-stu-id="23edb-151">As you move from the boundary of the triangle to the center point, the color changes gradually from dark green to aqua and then from aqua to blue.</span></span> <span data-ttu-id="23edb-152">從深綠色到青色的變更會以 25% 的距離, 從深綠色到藍色。</span><span class="sxs-lookup"><span data-stu-id="23edb-152">The change from dark green to aqua happens in 25 percent of the distance from dark green to blue.</span></span>  
  
     <span data-ttu-id="23edb-153">下圖顯示填滿自訂路徑漸層筆刷的三角形。</span><span class="sxs-lookup"><span data-stu-id="23edb-153">The following illustration shows the triangle filled with the custom path gradient brush.</span></span>  
  
     ![填滿自訂路徑漸層筆刷的三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a><span data-ttu-id="23edb-155">若要設定中心點</span><span class="sxs-lookup"><span data-stu-id="23edb-155">To set the center point</span></span>  
  
- <span data-ttu-id="23edb-156">根據預設, 路徑漸層筆刷的中心點會位於用來建立筆刷之路徑的距心。</span><span class="sxs-lookup"><span data-stu-id="23edb-156">By default, the center point of a path gradient brush is at the centroid of the path used to construct the brush.</span></span> <span data-ttu-id="23edb-157">您可以藉由設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> <xref:System.Drawing.Drawing2D.PathGradientBrush>類別的屬性, 來變更中心點的位置。</span><span class="sxs-lookup"><span data-stu-id="23edb-157">You can change the location of the center point by setting the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property of the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
     <span data-ttu-id="23edb-158">下列範例會根據橢圓形建立路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="23edb-158">The following example creates a path gradient brush based on an ellipse.</span></span> <span data-ttu-id="23edb-159">橢圓形的中心位於 (70, 35), 但路徑漸層筆刷的中心點設定為 (120, 40)。</span><span class="sxs-lookup"><span data-stu-id="23edb-159">The center of the ellipse is at (70, 35), but the center point of the path gradient brush is set to (120, 40).</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     <span data-ttu-id="23edb-160">下圖顯示已填滿的橢圓形和路徑漸層筆刷的中心點:</span><span class="sxs-lookup"><span data-stu-id="23edb-160">The following illustration shows the filled ellipse and the center point of the path gradient brush:</span></span>  
  
     ![具有實心橢圓形和中心點的漸層路徑。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- <span data-ttu-id="23edb-162">您可以將路徑漸層筆刷的中心點設定為用來建立筆刷之路徑以外的位置。</span><span class="sxs-lookup"><span data-stu-id="23edb-162">You can set the center point of a path gradient brush to a location outside the path that was used to construct the brush.</span></span> <span data-ttu-id="23edb-163">下列範例會取代呼叫來設定上述程式<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>代碼中的屬性。</span><span class="sxs-lookup"><span data-stu-id="23edb-163">The following example replaces the call to set the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property in the preceding code.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     <span data-ttu-id="23edb-164">下圖顯示此變更的輸出:</span><span class="sxs-lookup"><span data-stu-id="23edb-164">The following illustration shows the output with this change:</span></span>  
  
     ![中間點位於路徑外的漸層路徑。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     <span data-ttu-id="23edb-166">在上圖中, 橢圓形最右邊的點不是純藍色 (雖然非常接近)。</span><span class="sxs-lookup"><span data-stu-id="23edb-166">In the preceding illustration, the points at the far right of the ellipse are not pure blue (although they are very close).</span></span> <span data-ttu-id="23edb-167">漸層中的色彩會位於填滿的點 (145, 35), 其中的色彩會是純藍色 (0, 0, 255)。</span><span class="sxs-lookup"><span data-stu-id="23edb-167">The colors in the gradient are positioned as if the fill reached the point (145, 35) where the color would be pure blue (0, 0, 255).</span></span> <span data-ttu-id="23edb-168">但填滿永遠不會到達 (145, 35), 因為路徑漸層筆刷只會在其路徑內繪製。</span><span class="sxs-lookup"><span data-stu-id="23edb-168">But the fill never reaches (145, 35) because a path gradient brush paints only inside its path.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23edb-169">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="23edb-169">Compiling the Code</span></span>  
 <span data-ttu-id="23edb-170">先前的範例是針對與 Windows Forms 搭配使用所設計, 而且<xref:System.Windows.Forms.PaintEventArgs>它們需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="23edb-170">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23edb-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23edb-171">See also</span></span>

- [<span data-ttu-id="23edb-172">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="23edb-172">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
