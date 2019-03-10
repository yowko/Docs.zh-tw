---
title: HOW TO：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 6fbe8a78131cb64e28326133a7cc0fbdcbffd46b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720393"
---
# <a name="how-to-create-a-path-gradient"></a><span data-ttu-id="11369-102">HOW TO：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="11369-102">How to: Create a Path Gradient</span></span>
<span data-ttu-id="11369-103"><xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂您逐漸變更色彩填滿圖形的方式。</span><span class="sxs-lookup"><span data-stu-id="11369-103">The <xref:System.Drawing.Drawing2D.PathGradientBrush> class allows you to customize the way you fill a shape with gradually changing colors.</span></span> <span data-ttu-id="11369-104">例如，您可以指定路徑的中心的一種色彩和路徑的界限的另一種色彩。</span><span class="sxs-lookup"><span data-stu-id="11369-104">For example, you can specify one color for the center of a path and another color for the boundary of a path.</span></span> <span data-ttu-id="11369-105">您也可以指定不同的色彩，每個界限的數個點的路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-105">You can also specify separate colors for each of several points along the boundary of a path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11369-106">在  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，路徑是一系列的線條和曲線維護<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="11369-106">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a path is a sequence of lines and curves maintained by a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="11369-107">如需詳細資訊[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]路徑，請參閱[GDI + 中的圖形路徑](graphics-paths-in-gdi.md)並[Constructing 和繪製路徑](constructing-and-drawing-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="11369-107">For more information about [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] paths, see [Graphics Paths in GDI+](graphics-paths-in-gdi.md) and [Constructing and Drawing Paths](constructing-and-drawing-paths.md).</span></span>  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a><span data-ttu-id="11369-108">若要使用的路徑漸層填滿橢圓形</span><span class="sxs-lookup"><span data-stu-id="11369-108">To fill an ellipse with a path gradient</span></span>  
  
-   <span data-ttu-id="11369-109">下列範例會填滿橢圓形使用路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="11369-109">The following example fills an ellipse with a path gradient brush.</span></span> <span data-ttu-id="11369-110">之中心色彩設定為藍色，邊界色彩設定為青色。</span><span class="sxs-lookup"><span data-stu-id="11369-110">The center color is set to blue and the boundary color is set to aqua.</span></span> <span data-ttu-id="11369-111">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="11369-111">The following illustration shows the filled ellipse.</span></span>  
  
     <span data-ttu-id="11369-112">![路徑漸層停駐](./media/pathgradient1.png "pathgradient1")</span><span class="sxs-lookup"><span data-stu-id="11369-112">![Gradient Path](./media/pathgradient1.png "pathgradient1")</span></span>  
  
     <span data-ttu-id="11369-113">根據預設，路徑漸層筆刷不會延伸超出路徑的界限。</span><span class="sxs-lookup"><span data-stu-id="11369-113">By default, a path gradient brush does not extend outside the boundary of the path.</span></span> <span data-ttu-id="11369-114">如果您使用路徑漸層筆刷填滿圖形超出路徑的界限時，在路徑外螢幕區域不會被填入。</span><span class="sxs-lookup"><span data-stu-id="11369-114">If you use the path gradient brush to fill a figure that extends beyond the boundary of the path, the area of the screen outside the path will not be filled.</span></span>  
  
     <span data-ttu-id="11369-115">下圖顯示如果您變更，會發生什麼事<xref:System.Drawing.Graphics.FillEllipse%2A>在下列程式碼中呼叫`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`。</span><span class="sxs-lookup"><span data-stu-id="11369-115">The following illustration shows what happens if you change the <xref:System.Drawing.Graphics.FillEllipse%2A> call in the following code to `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.</span></span>  
  
     <span data-ttu-id="11369-116">![路徑漸層停駐](./media/pathgradient2.png "pathgradient2")</span><span class="sxs-lookup"><span data-stu-id="11369-116">![Gradient Path](./media/pathgradient2.png "pathgradient2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     <span data-ttu-id="11369-117">上述程式碼範例專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>e，也就是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="11369-117">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> e, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
### <a name="to-specify-points-on-the-boundary"></a><span data-ttu-id="11369-118">若要指定點的界限</span><span class="sxs-lookup"><span data-stu-id="11369-118">To specify points on the boundary</span></span>  
  
-   <span data-ttu-id="11369-119">下列範例會建構路徑漸層筆刷從星形的路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-119">The following example constructs a path gradient brush from a star-shaped path.</span></span> <span data-ttu-id="11369-120">程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性，設定在為紅色星號的距心的色彩。</span><span class="sxs-lookup"><span data-stu-id="11369-120">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> property, which sets the color at the centroid of the star to red.</span></span> <span data-ttu-id="11369-121">然後程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>屬性來指定各種色彩 (儲存在`colors`陣列) 在個別的點`points`陣列。</span><span class="sxs-lookup"><span data-stu-id="11369-121">Then the code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> property to specify various colors (stored in the `colors` array) at the individual points in the `points` array.</span></span> <span data-ttu-id="11369-122">最後的程式碼陳述式會填滿星形路徑與路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="11369-122">The final code statement fills the star-shaped path with the path gradient brush.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   <span data-ttu-id="11369-123">下列範例會繪製路徑漸層，而不需要<xref:System.Drawing.Drawing2D.GraphicsPath>程式碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="11369-123">The following example draws a path gradient without a <xref:System.Drawing.Drawing2D.GraphicsPath> object in the code.</span></span> <span data-ttu-id="11369-124">特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>建構函式，在範例中會收到一個點的陣列，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="11369-124">The particular <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructor in the example receives an array of points but does not require a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="11369-125">另請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用來填滿矩形，而不是路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-125">Also, note that the <xref:System.Drawing.Drawing2D.PathGradientBrush> is used to fill a rectangle, not a path.</span></span> <span data-ttu-id="11369-126">矩形大於封閉的路徑，用來定義筆刷，因此部分矩形將不會繪製筆刷。</span><span class="sxs-lookup"><span data-stu-id="11369-126">The rectangle is larger than the closed path used to define the brush, so some of the rectangle is not painted by the brush.</span></span> <span data-ttu-id="11369-127">下圖顯示矩形 （虛線） 和路徑的漸層筆刷繪製之矩形的部分。</span><span class="sxs-lookup"><span data-stu-id="11369-127">The following illustration shows the rectangle (dotted line) and the portion of the rectangle painted by the path gradient brush.</span></span>  
  
     <span data-ttu-id="11369-128">![漸層停駐](./media/gradient4.png "gradient4")</span><span class="sxs-lookup"><span data-stu-id="11369-128">![Gradient](./media/gradient4.png "gradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a><span data-ttu-id="11369-129">若要自訂路徑漸層</span><span class="sxs-lookup"><span data-stu-id="11369-129">To customize a path gradient</span></span>  
  
-   <span data-ttu-id="11369-130">自訂路徑漸層筆刷的一種方法是設定其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="11369-130">One way to customize a path gradient brush is to set its <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> property.</span></span> <span data-ttu-id="11369-131">焦點標尺指定內部路徑位於內的主要路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-131">The focus scales specify an inner path that lies inside the main path.</span></span> <span data-ttu-id="11369-132">內部路徑中，而不是只在 center 點時，會到處都顯示在中心色彩。</span><span class="sxs-lookup"><span data-stu-id="11369-132">The center color is displayed everywhere inside that inner path rather than only at the center point.</span></span>  
  
     <span data-ttu-id="11369-133">下列範例會建立路徑的漸層筆刷，根據橢圓形的路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-133">The following example creates a path gradient brush based on an elliptical path.</span></span> <span data-ttu-id="11369-134">程式碼界限色彩設定為藍色，中心色彩設定為青色、，然後再使用路徑漸層筆刷填滿橢圓形的路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-134">The code sets the boundary color to blue, sets the center color to aqua, and then uses the path gradient brush to fill the elliptical path.</span></span>  
  
     <span data-ttu-id="11369-135">接下來，程式碼會設定路徑漸層筆刷的焦點比例。</span><span class="sxs-lookup"><span data-stu-id="11369-135">Next, the code sets the focus scales of the path gradient brush.</span></span> <span data-ttu-id="11369-136">X 焦點小數位數設定為 0.3，而 y 焦點比例設為 0.8。</span><span class="sxs-lookup"><span data-stu-id="11369-136">The x focus scale is set to 0.3, and the y focus scale is set to 0.8.</span></span> <span data-ttu-id="11369-137">程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A>方法<xref:System.Drawing.Graphics>物件，讓後續呼叫<xref:System.Drawing.Graphics.FillPath%2A>會填滿橢圓形位在右邊的第一個橢圓形。</span><span class="sxs-lookup"><span data-stu-id="11369-137">The code calls the <xref:System.Drawing.Graphics.TranslateTransform%2A> method of a <xref:System.Drawing.Graphics> object so that the subsequent call to <xref:System.Drawing.Graphics.FillPath%2A> fills an ellipse that sits to the right of the first ellipse.</span></span>  
  
     <span data-ttu-id="11369-138">若要查看焦點標尺的效果，想像一下與主要的橢圓形共用其中心點小橢圓形。</span><span class="sxs-lookup"><span data-stu-id="11369-138">To see the effect of the focus scales, imagine a small ellipse that shares its center with the main ellipse.</span></span> <span data-ttu-id="11369-139">小 （內部） 的橢圓形是主要的省略符號 （繞著中心中） 水平調整，以 0.3 的因數和垂直 0.8 倍。</span><span class="sxs-lookup"><span data-stu-id="11369-139">The small (inner) ellipse is the main ellipse scaled (about its center) horizontally by a factor of 0.3 and vertically by a factor of 0.8.</span></span> <span data-ttu-id="11369-140">當您移動從外部的橢圓形的界限內部的橢圓形的界限時，色彩會逐漸從藍色為青色。</span><span class="sxs-lookup"><span data-stu-id="11369-140">As you move from the boundary of the outer ellipse to the boundary of the inner ellipse, the color changes gradually from blue to aqua.</span></span> <span data-ttu-id="11369-141">當您從內部的橢圓形的界限移到共用的中心，色彩會保持為青色。</span><span class="sxs-lookup"><span data-stu-id="11369-141">As you move from the boundary of the inner ellipse to the shared center, the color remains aqua.</span></span>  
  
     <span data-ttu-id="11369-142">下圖顯示下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="11369-142">The following illustration shows the output of the following code.</span></span> <span data-ttu-id="11369-143">在左側的省略符號是 aqua 只在 center 點。</span><span class="sxs-lookup"><span data-stu-id="11369-143">The ellipse on the left is aqua only at the center point.</span></span> <span data-ttu-id="11369-144">在右邊的省略符號是 aqua everywhere 內的內部路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-144">The ellipse on the right is aqua everywhere inside the inner path.</span></span>  
  
 <span data-ttu-id="11369-145">![Gradient](./media/focusscales1nogamma.png "focusscales1NoGamma")</span><span class="sxs-lookup"><span data-stu-id="11369-145">![Gradient](./media/focusscales1nogamma.png "focusscales1NoGamma")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a><span data-ttu-id="11369-146">若要自訂內插補點</span><span class="sxs-lookup"><span data-stu-id="11369-146">To customize with interpolation</span></span>  
  
-   <span data-ttu-id="11369-147">若要自訂路徑漸層筆刷的另一種方式是指定插補色彩的陣列和陣列的內插補點位置。</span><span class="sxs-lookup"><span data-stu-id="11369-147">Another way to customize a path gradient brush is to specify an array of interpolation colors and an array of interpolation positions.</span></span>  
  
     <span data-ttu-id="11369-148">下列範例會建立路徑漸層筆刷的三角形為基礎。</span><span class="sxs-lookup"><span data-stu-id="11369-148">The following example creates a path gradient brush based on a triangle.</span></span> <span data-ttu-id="11369-149">程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷指定深綠色、 青色 （藍） 的插補色彩的陣列和陣列的內插補點位置 （0，0.25，1） 的屬性。</span><span class="sxs-lookup"><span data-stu-id="11369-149">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> property of the path gradient brush to specify an array of interpolation colors (dark green, aqua, blue) and an array of interpolation positions (0, 0.25, 1).</span></span> <span data-ttu-id="11369-150">當您移動三角形的界限從中心點時，色彩會逐漸從深綠色為青綠色，然後從青色藍色。</span><span class="sxs-lookup"><span data-stu-id="11369-150">As you move from the boundary of the triangle to the center point, the color changes gradually from dark green to aqua and then from aqua to blue.</span></span> <span data-ttu-id="11369-151">深綠色 aqua 的變更會在 25%的深綠色和藍色之間的距離。</span><span class="sxs-lookup"><span data-stu-id="11369-151">The change from dark green to aqua happens in 25 percent of the distance from dark green to blue.</span></span>  
  
     <span data-ttu-id="11369-152">下圖顯示填入 自訂路徑漸層筆刷的三角形。</span><span class="sxs-lookup"><span data-stu-id="11369-152">The following illustration shows the triangle filled with the custom path gradient brush.</span></span>  
  
     <span data-ttu-id="11369-153">![路徑漸層停駐](./media/pathgradient4.png "pathgradient4")</span><span class="sxs-lookup"><span data-stu-id="11369-153">![Gradient Path](./media/pathgradient4.png "pathgradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a><span data-ttu-id="11369-154">若要設定的中心點</span><span class="sxs-lookup"><span data-stu-id="11369-154">To set the center point</span></span>  
  
-   <span data-ttu-id="11369-155">根據預設，路徑漸層筆刷的中心點位於用來建構筆刷的路徑的距心。</span><span class="sxs-lookup"><span data-stu-id="11369-155">By default, the center point of a path gradient brush is at the centroid of the path used to construct the brush.</span></span> <span data-ttu-id="11369-156">您可以藉由設定變更的中心點的位置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="11369-156">You can change the location of the center point by setting the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property of the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
     <span data-ttu-id="11369-157">下列範例會建立路徑的漸層筆刷，根據一個橢圓形。</span><span class="sxs-lookup"><span data-stu-id="11369-157">The following example creates a path gradient brush based on an ellipse.</span></span> <span data-ttu-id="11369-158">橢圓形的中心是 70 (35），但會設定路徑漸層筆刷的中心點為 （120，40）。</span><span class="sxs-lookup"><span data-stu-id="11369-158">The center of the ellipse is at (70, 35), but the center point of the path gradient brush is set to (120, 40).</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     <span data-ttu-id="11369-159">下圖顯示實心的橢圓形和路徑的漸層筆刷的中心點。</span><span class="sxs-lookup"><span data-stu-id="11369-159">The following illustration shows the filled ellipse and the center point of the path gradient brush.</span></span>  
  
     <span data-ttu-id="11369-160">![路徑漸層停駐](./media/pathgradient5.png "pathgradient5")</span><span class="sxs-lookup"><span data-stu-id="11369-160">![Gradient Path](./media/pathgradient5.png "pathgradient5")</span></span>  
  
-   <span data-ttu-id="11369-161">您可以設定路徑漸層筆刷的中心點，用來建構筆刷在路徑外的位置。</span><span class="sxs-lookup"><span data-stu-id="11369-161">You can set the center point of a path gradient brush to a location outside the path that was used to construct the brush.</span></span> <span data-ttu-id="11369-162">下列範例會將呼叫以設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>前面的程式碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="11369-162">The following example replaces the call to set the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property in the preceding code.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     <span data-ttu-id="11369-163">下圖顯示這項變更的輸出。</span><span class="sxs-lookup"><span data-stu-id="11369-163">The following illustration shows the output with this change.</span></span>  
  
     <span data-ttu-id="11369-164">![路徑漸層停駐](./media/pathgradient6.png "pathgradient6")</span><span class="sxs-lookup"><span data-stu-id="11369-164">![Gradient Path](./media/pathgradient6.png "pathgradient6")</span></span>  
  
     <span data-ttu-id="11369-165">在上圖中，最右邊的省略符號的點不是單純的藍色 （不過非常接近）。</span><span class="sxs-lookup"><span data-stu-id="11369-165">In the preceding illustration, the points at the far right of the ellipse are not pure blue (although they are very close).</span></span> <span data-ttu-id="11369-166">在漸層色彩位於如同填滿達到 （145，35） 點，色彩會是純藍色 （0，0，255）。</span><span class="sxs-lookup"><span data-stu-id="11369-166">The colors in the gradient are positioned as if the fill reached the point (145, 35) where the color would be pure blue (0, 0, 255).</span></span> <span data-ttu-id="11369-167">但永遠不會達到填滿 （145，35） 因為路徑漸層筆刷繪製只在其路徑。</span><span class="sxs-lookup"><span data-stu-id="11369-167">But the fill never reaches (145, 35) because a path gradient brush paints only inside its path.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11369-168">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="11369-168">Compiling the Code</span></span>  
 <span data-ttu-id="11369-169">上述範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="11369-169">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11369-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11369-170">See also</span></span>
- [<span data-ttu-id="11369-171">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="11369-171">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
