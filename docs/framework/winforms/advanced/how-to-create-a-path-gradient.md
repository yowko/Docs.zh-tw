---
title: "如何：建立路徑漸層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a70e55d0f5b6197dc7c77b9e95f2279b814737
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-path-gradient"></a><span data-ttu-id="ce5b5-102">如何：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="ce5b5-102">How to: Create a Path Gradient</span></span>
<span data-ttu-id="ce5b5-103"><xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂您漸層色彩填滿圖形的方式。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-103">The <xref:System.Drawing.Drawing2D.PathGradientBrush> class allows you to customize the way you fill a shape with gradually changing colors.</span></span> <span data-ttu-id="ce5b5-104">比方說，您可以指定一個色彩為路徑的中央和路徑的界限的另一種色彩。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-104">For example, you can specify one color for the center of a path and another color for the boundary of a path.</span></span> <span data-ttu-id="ce5b5-105">您也可以指定不同的色彩，每個界限的幾個點的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-105">You can also specify separate colors for each of several points along the boundary of a path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce5b5-106">在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，路徑是一串的直線和曲線所維護<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-106">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a path is a sequence of lines and curves maintained by a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="ce5b5-107">如需有關[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]路徑，請參閱[GDI + 中的圖形路徑](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)和[Constructing 和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-107">For more information about [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] paths, see [Graphics Paths in GDI+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) and [Constructing and Drawing Paths](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).</span></span>  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a><span data-ttu-id="ce5b5-108">若要使用的路徑漸層填滿橢圓形</span><span class="sxs-lookup"><span data-stu-id="ce5b5-108">To fill an ellipse with a path gradient</span></span>  
  
-   <span data-ttu-id="ce5b5-109">下列範例會填滿橢圓形路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-109">The following example fills an ellipse with a path gradient brush.</span></span> <span data-ttu-id="ce5b5-110">中心色彩設定為藍色並界限色彩設定為青色。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-110">The center color is set to blue and the boundary color is set to aqua.</span></span> <span data-ttu-id="ce5b5-111">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-111">The following illustration shows the filled ellipse.</span></span>  
  
     <span data-ttu-id="ce5b5-112">![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-112">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")</span></span>  
  
     <span data-ttu-id="ce5b5-113">根據預設，路徑漸層筆刷不會延伸超出路徑的界限。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-113">By default, a path gradient brush does not extend outside the boundary of the path.</span></span> <span data-ttu-id="ce5b5-114">如果您使用路徑漸層筆刷填滿超出路徑的邊界的圖形，在路徑外螢幕區域不會被填入。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-114">If you use the path gradient brush to fill a figure that extends beyond the boundary of the path, the area of the screen outside the path will not be filled.</span></span>  
  
     <span data-ttu-id="ce5b5-115">下圖顯示如果您變更，會發生什麼事<xref:System.Drawing.Graphics.FillEllipse%2A>在下列程式碼中呼叫`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-115">The following illustration shows what happens if you change the <xref:System.Drawing.Graphics.FillEllipse%2A> call in the following code to `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.</span></span>  
  
     <span data-ttu-id="ce5b5-116">![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-116">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     <span data-ttu-id="ce5b5-117">上述程式碼範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs>e 是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-117">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> e, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
### <a name="to-specify-points-on-the-boundary"></a><span data-ttu-id="ce5b5-118">若要指定點的界限</span><span class="sxs-lookup"><span data-stu-id="ce5b5-118">To specify points on the boundary</span></span>  
  
-   <span data-ttu-id="ce5b5-119">下列範例會建構路徑漸層筆刷從星形的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-119">The following example constructs a path gradient brush from a star-shaped path.</span></span> <span data-ttu-id="ce5b5-120">程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性，設定在為紅色星號的距心的色彩。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-120">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> property, which sets the color at the centroid of the star to red.</span></span> <span data-ttu-id="ce5b5-121">然後程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>屬性來指定不同的色彩 (儲存在`colors`陣列) 中的個別點`points`陣列。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-121">Then the code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> property to specify various colors (stored in the `colors` array) at the individual points in the `points` array.</span></span> <span data-ttu-id="ce5b5-122">最後的程式碼陳述式會填滿星形路徑與路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-122">The final code statement fills the star-shaped path with the path gradient brush.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   <span data-ttu-id="ce5b5-123">下列範例會繪製路徑漸層，而不<xref:System.Drawing.Drawing2D.GraphicsPath>程式碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-123">The following example draws a path gradient without a <xref:System.Drawing.Drawing2D.GraphicsPath> object in the code.</span></span> <span data-ttu-id="ce5b5-124">特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>接收的點陣列建構函式在範例中，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-124">The particular <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructor in the example receives an array of points but does not require a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="ce5b5-125">另請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用來填滿的矩形，不是路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-125">Also, note that the <xref:System.Drawing.Drawing2D.PathGradientBrush> is used to fill a rectangle, not a path.</span></span> <span data-ttu-id="ce5b5-126">矩形會大於已關閉用來定義筆刷，因此部分矩形將不會繪製筆刷的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-126">The rectangle is larger than the closed path used to define the brush, so some of the rectangle is not painted by the brush.</span></span> <span data-ttu-id="ce5b5-127">下圖顯示的矩形 （虛線） 和部分路徑漸層筆刷繪製的矩形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-127">The following illustration shows the rectangle (dotted line) and the portion of the rectangle painted by the path gradient brush.</span></span>  
  
     <span data-ttu-id="ce5b5-128">![漸層停駐](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-128">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a><span data-ttu-id="ce5b5-129">若要自訂路徑漸層</span><span class="sxs-lookup"><span data-stu-id="ce5b5-129">To customize a path gradient</span></span>  
  
-   <span data-ttu-id="ce5b5-130">若要自訂路徑漸層筆刷的一種方式為設定其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-130">One way to customize a path gradient brush is to set its <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> property.</span></span> <span data-ttu-id="ce5b5-131">焦點比例指定主要路徑內的內部路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-131">The focus scales specify an inner path that lies inside the main path.</span></span> <span data-ttu-id="ce5b5-132">中心色彩全部都會顯示內部路徑，而不是只在中心點。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-132">The center color is displayed everywhere inside that inner path rather than only at the center point.</span></span>  
  
     <span data-ttu-id="ce5b5-133">下列範例會建立路徑漸層筆刷根據橢圓形的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-133">The following example creates a path gradient brush based on an elliptical path.</span></span> <span data-ttu-id="ce5b5-134">程式碼界限色彩設定為藍色，中心色彩設定為青色，，然後再使用路徑漸層筆刷填滿橢圓形的路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-134">The code sets the boundary color to blue, sets the center color to aqua, and then uses the path gradient brush to fill the elliptical path.</span></span>  
  
     <span data-ttu-id="ce5b5-135">接下來，此程式碼會設定路徑的漸層筆刷的焦點比例。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-135">Next, the code sets the focus scales of the path gradient brush.</span></span> <span data-ttu-id="ce5b5-136">X 焦點小數位數設定為 0.3，和 y 焦點小數位數設定為 0.8。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-136">The x focus scale is set to 0.3, and the y focus scale is set to 0.8.</span></span> <span data-ttu-id="ce5b5-137">程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A>方法<xref:System.Drawing.Graphics>物件以便後續呼叫<xref:System.Drawing.Graphics.FillPath%2A>會填滿橢圓形位於右邊的第一個橢圓形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-137">The code calls the <xref:System.Drawing.Graphics.TranslateTransform%2A> method of a <xref:System.Drawing.Graphics> object so that the subsequent call to <xref:System.Drawing.Graphics.FillPath%2A> fills an ellipse that sits to the right of the first ellipse.</span></span>  
  
     <span data-ttu-id="ce5b5-138">若要查看焦點比例的效果，假設共用同一個中心與主要橢圓形的小型橢圓形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-138">To see the effect of the focus scales, imagine a small ellipse that shares its center with the main ellipse.</span></span> <span data-ttu-id="ce5b5-139">小 （內部） 橢圓形是主要的省略符號 （關於其中心） 水平調整，因數為 0.3 平和垂直方式，因數為 0.8。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-139">The small (inner) ellipse is the main ellipse scaled (about its center) horizontally by a factor of 0.3 and vertically by a factor of 0.8.</span></span> <span data-ttu-id="ce5b5-140">當您移動從外部橢圓形的邊界內部的橢圓形的邊界時，色彩逐漸從變成藍色青色。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-140">As you move from the boundary of the outer ellipse to the boundary of the inner ellipse, the color changes gradually from blue to aqua.</span></span> <span data-ttu-id="ce5b5-141">當您從內部橢圓形的邊界移到共用的中心，色彩會保持為青色。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-141">As you move from the boundary of the inner ellipse to the shared center, the color remains aqua.</span></span>  
  
     <span data-ttu-id="ce5b5-142">下圖顯示下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-142">The following illustration shows the output of the following code.</span></span> <span data-ttu-id="ce5b5-143">在左側橢圓形是青色的中心點。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-143">The ellipse on the left is aqua only at the center point.</span></span> <span data-ttu-id="ce5b5-144">在右邊的省略符號是青色 everywhere 內的內部路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-144">The ellipse on the right is aqua everywhere inside the inner path.</span></span>  
  
 <span data-ttu-id="ce5b5-145">![漸層停駐](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-145">![Gradient](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a><span data-ttu-id="ce5b5-146">若要自訂使用插補</span><span class="sxs-lookup"><span data-stu-id="ce5b5-146">To customize with interpolation</span></span>  
  
-   <span data-ttu-id="ce5b5-147">若要自訂路徑漸層筆刷的另一種方式是指定插補色彩的陣列和陣列的插補的位置。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-147">Another way to customize a path gradient brush is to specify an array of interpolation colors and an array of interpolation positions.</span></span>  
  
     <span data-ttu-id="ce5b5-148">下列範例會建立路徑漸層筆刷根據三角形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-148">The following example creates a path gradient brush based on a triangle.</span></span> <span data-ttu-id="ce5b5-149">程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷深綠色、 青色 （藍） 的插補色彩的陣列和陣列的插補位置 （0，0.25，1） 指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-149">The code sets the <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> property of the path gradient brush to specify an array of interpolation colors (dark green, aqua, blue) and an array of interpolation positions (0, 0.25, 1).</span></span> <span data-ttu-id="ce5b5-150">當您移動的三角形界限從中心點，色彩會逐漸從深綠色青色，然後從青色為藍色。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-150">As you move from the boundary of the triangle to the center point, the color changes gradually from dark green to aqua and then from aqua to blue.</span></span> <span data-ttu-id="ce5b5-151">深綠色青色的變更會發生在 25%的距離為藍色深綠色。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-151">The change from dark green to aqua happens in 25 percent of the distance from dark green to blue.</span></span>  
  
     <span data-ttu-id="ce5b5-152">下圖顯示自訂路徑漸層筆刷填滿的三角形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-152">The following illustration shows the triangle filled with the custom path gradient brush.</span></span>  
  
     <span data-ttu-id="ce5b5-153">![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-153">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a><span data-ttu-id="ce5b5-154">若要設定的中心點</span><span class="sxs-lookup"><span data-stu-id="ce5b5-154">To set the center point</span></span>  
  
-   <span data-ttu-id="ce5b5-155">根據預設，路徑漸層筆刷的中心點位於用來建構筆刷的路徑的距心。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-155">By default, the center point of a path gradient brush is at the centroid of the path used to construct the brush.</span></span> <span data-ttu-id="ce5b5-156">您可以藉由設定變更的中心點的位置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-156">You can change the location of the center point by setting the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property of the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
     <span data-ttu-id="ce5b5-157">下列範例會建立路徑漸層筆刷根據橢圓形。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-157">The following example creates a path gradient brush based on an ellipse.</span></span> <span data-ttu-id="ce5b5-158">橢圓形的中心位於 70 (35），但路徑漸層筆刷的中心點設定為 120 (40）。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-158">The center of the ellipse is at (70, 35), but the center point of the path gradient brush is set to (120, 40).</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     <span data-ttu-id="ce5b5-159">下圖顯示實心的橢圓形和路徑的漸層筆刷的中心點。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-159">The following illustration shows the filled ellipse and the center point of the path gradient brush.</span></span>  
  
     <span data-ttu-id="ce5b5-160">![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-160">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")</span></span>  
  
-   <span data-ttu-id="ce5b5-161">您可以設定用來建構筆刷的路徑以外的位置路徑的漸層筆刷的中心點。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-161">You can set the center point of a path gradient brush to a location outside the path that was used to construct the brush.</span></span> <span data-ttu-id="ce5b5-162">下列範例會取代設定的呼叫<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>上述程式碼中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-162">The following example replaces the call to set the <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> property in the preceding code.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     <span data-ttu-id="ce5b5-163">下圖顯示這項變更的輸出。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-163">The following illustration shows the output with this change.</span></span>  
  
     <span data-ttu-id="ce5b5-164">![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")</span><span class="sxs-lookup"><span data-stu-id="ce5b5-164">![Gradient Path](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")</span></span>  
  
     <span data-ttu-id="ce5b5-165">在上圖中，最右邊的省略符號的點不是純藍色 （雖然它們是非常接近）。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-165">In the preceding illustration, the points at the far right of the ellipse are not pure blue (although they are very close).</span></span> <span data-ttu-id="ce5b5-166">中所使用漸層的色彩都位於如同填滿到達其中色彩會 （0，0，255） 的純藍色點 （145，35）。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-166">The colors in the gradient are positioned as if the fill reached the point (145, 35) where the color would be pure blue (0, 0, 255).</span></span> <span data-ttu-id="ce5b5-167">但永遠不會到達填滿 （145，35） 因為路徑的漸層筆刷繪製只在其路徑。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-167">But the fill never reaches (145, 35) because a path gradient brush paints only inside its path.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce5b5-168">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ce5b5-168">Compiling the Code</span></span>  
 <span data-ttu-id="ce5b5-169">前面的範例專為搭配 Windows Form 使用，而且會要求<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce5b5-169">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5b5-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce5b5-170">See Also</span></span>  
 [<span data-ttu-id="ce5b5-171">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="ce5b5-171">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
