---
title: GDI+ 中的筆刷和填滿的形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912236"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="0e546-102">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="0e546-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="0e546-103">「封閉」圖形 (例如矩形或橢圓形) 包含外框和內部。</span><span class="sxs-lookup"><span data-stu-id="0e546-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="0e546-104">外框會以畫筆繪製, 而內部則會填滿筆刷。</span><span class="sxs-lookup"><span data-stu-id="0e546-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> <span data-ttu-id="0e546-105">Gdi + 提供數筆刷類別來填滿封閉圖形的<xref:System.Drawing.SolidBrush>內部<xref:System.Drawing.Drawing2D.HatchBrush>: <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、、 <xref:System.Drawing.Drawing2D.PathGradientBrush>和。</span><span class="sxs-lookup"><span data-stu-id="0e546-105">GDI+ provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="0e546-106">所有這些類別都是<xref:System.Drawing.Brush>繼承自類別。</span><span class="sxs-lookup"><span data-stu-id="0e546-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="0e546-107">下圖顯示填滿實心筆刷的矩形, 以及填滿影線筆刷的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="0e546-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="0e546-108">![填滿的圖案](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="0e546-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="0e546-109">實心筆刷</span><span class="sxs-lookup"><span data-stu-id="0e546-109">Solid Brushes</span></span>  
 <span data-ttu-id="0e546-110">若要填滿封閉圖形, 您需要<xref:System.Drawing.Graphics>類別的實例<xref:System.Drawing.Brush>和。</span><span class="sxs-lookup"><span data-stu-id="0e546-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="0e546-111"><xref:System.Drawing.Graphics>類別的實例會提供方法 ( <xref:System.Drawing.Graphics.FillRectangle%2A>例如和<xref:System.Drawing.Graphics.FillEllipse%2A>), 並<xref:System.Drawing.Brush>儲存填滿的屬性 (例如色彩和模式)。</span><span class="sxs-lookup"><span data-stu-id="0e546-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="0e546-112"><xref:System.Drawing.Brush>會當做其中一個引數傳遞至 fill 方法。</span><span class="sxs-lookup"><span data-stu-id="0e546-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="0e546-113">下列程式碼範例示範如何以純色紅色填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="0e546-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> <span data-ttu-id="0e546-114">在上述範例中, 筆刷的類型<xref:System.Drawing.SolidBrush>為, 其繼承自。 <xref:System.Drawing.Brush></span><span class="sxs-lookup"><span data-stu-id="0e546-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="0e546-115">影線筆刷</span><span class="sxs-lookup"><span data-stu-id="0e546-115">Hatch Brushes</span></span>  
 <span data-ttu-id="0e546-116">當您填滿具有影線筆刷的圖形時, 您可以指定前景色彩、背景色彩和影線樣式。</span><span class="sxs-lookup"><span data-stu-id="0e546-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="0e546-117">前景色彩是影線的色彩。</span><span class="sxs-lookup"><span data-stu-id="0e546-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 <span data-ttu-id="0e546-118">GDI + 提供超過50的影線樣式;下圖所示的三種樣式為<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>、 <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。</span><span class="sxs-lookup"><span data-stu-id="0e546-118">GDI+ provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="0e546-119">![填滿的圖案](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="0e546-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="0e546-120">材質筆刷</span><span class="sxs-lookup"><span data-stu-id="0e546-120">Texture Brushes</span></span>  
 <span data-ttu-id="0e546-121">使用材質筆刷時, 您可以使用儲存在點陣圖中的模式來填滿圖形。</span><span class="sxs-lookup"><span data-stu-id="0e546-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="0e546-122">例如, 假設下圖儲存在名為`MyTexture.bmp`的磁片檔案中。</span><span class="sxs-lookup"><span data-stu-id="0e546-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="0e546-123">![填滿的圖形](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="0e546-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="0e546-124">下列程式碼範例示範如何透過重複儲存在中`MyTexture.bmp`的圖片來填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="0e546-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="0e546-125">下圖顯示已填滿的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="0e546-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="0e546-126">![填滿的圖形](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="0e546-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="0e546-127">漸層筆刷</span><span class="sxs-lookup"><span data-stu-id="0e546-127">Gradient Brushes</span></span>  
 <span data-ttu-id="0e546-128">GDI + 提供兩種漸層筆刷: 線性和路徑。</span><span class="sxs-lookup"><span data-stu-id="0e546-128">GDI+ provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="0e546-129">您可以使用線性漸層筆刷, 將色彩變更為水準、垂直或對角線地在圖形上移動時, 逐漸變化。</span><span class="sxs-lookup"><span data-stu-id="0e546-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="0e546-130">下列程式碼範例示範如何使用水準漸層筆刷來填滿橢圓形, 這會在您從橢圓形的左邊緣移至右邊緣時, 從藍色變更為綠色。</span><span class="sxs-lookup"><span data-stu-id="0e546-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="0e546-131">下圖顯示已填滿的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="0e546-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="0e546-132">![填滿的圖形](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="0e546-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="0e546-133">您可以設定路徑漸層筆刷, 以便在您從圖形的中央往邊緣移動時變更色彩。</span><span class="sxs-lookup"><span data-stu-id="0e546-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="0e546-134">![填滿的圖形](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="0e546-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="0e546-135">路徑漸層筆刷相當有彈性。</span><span class="sxs-lookup"><span data-stu-id="0e546-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="0e546-136">在下圖中用來填滿三角形的漸層筆刷, 會從中央的紅色逐漸變更為頂點上的三種不同色彩。</span><span class="sxs-lookup"><span data-stu-id="0e546-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="0e546-137">![填滿的圖形](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="0e546-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e546-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e546-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="0e546-139">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="0e546-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="0e546-140">如何：在 Windows Form 上繪製實心矩形</span><span class="sxs-lookup"><span data-stu-id="0e546-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="0e546-141">如何：在 Windows Form 上繪製實心橢圓形</span><span class="sxs-lookup"><span data-stu-id="0e546-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
