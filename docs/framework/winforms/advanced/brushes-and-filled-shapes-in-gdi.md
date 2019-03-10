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
ms.openlocfilehash: fc6d6857e912ba14fca382eb49373655004534d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720939"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="e5b4b-102">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="e5b4b-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="e5b4b-103">封閉的形狀，例如矩形或橢圓形，是由外框和內部所組成。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="e5b4b-104">使用畫筆繪製外框，並使用筆刷填滿內部。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="e5b4b-105">提供來填滿的封閉的形狀內部的筆刷的數個類別： <xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，和<xref:System.Drawing.Drawing2D.PathGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-105">provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="e5b4b-106">所有這些類別繼承自<xref:System.Drawing.Brush>類別。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="e5b4b-107">下圖顯示使用實心筆刷填滿的矩形和橢圓形填滿影線筆刷。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="e5b4b-108">![填滿形狀](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="e5b4b-109">實心筆刷</span><span class="sxs-lookup"><span data-stu-id="e5b4b-109">Solid Brushes</span></span>  
 <span data-ttu-id="e5b4b-110">若要填滿一個封閉的形狀 中，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Brush>。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="e5b4b-111">執行個體<xref:System.Drawing.Graphics>類別提供方法，例如<xref:System.Drawing.Graphics.FillRectangle%2A>並<xref:System.Drawing.Graphics.FillEllipse%2A>，和<xref:System.Drawing.Brush>儲存的填滿，例如色彩和模式的屬性。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="e5b4b-112"><xref:System.Drawing.Brush>做為其中一個引數傳遞至填滿方法。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="e5b4b-113">下列程式碼範例示範如何使用紅色純色填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="e5b4b-114">在上述範例中，筆刷是型別的<xref:System.Drawing.SolidBrush>，該項則繼承自<xref:System.Drawing.Brush>。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="e5b4b-115">筆刷</span><span class="sxs-lookup"><span data-stu-id="e5b4b-115">Hatch Brushes</span></span>  
 <span data-ttu-id="e5b4b-116">當您規劃筆刷填滿圖形時，請指定前景色彩、 背景色彩和影線樣式。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="e5b4b-117">前景色彩是影線色彩。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="e5b4b-118">提供超過 50 的影線樣式;下圖所示的三個樣式如下<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>， <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>，和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-118">provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="e5b4b-119">![填滿形狀](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="e5b4b-120">紋理筆刷</span><span class="sxs-lookup"><span data-stu-id="e5b4b-120">Texture Brushes</span></span>  
 <span data-ttu-id="e5b4b-121">使用紋理筆刷可以填滿形狀，以儲存在點陣圖中的模式。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="e5b4b-122">例如，假設下列圖片會儲存在名為的磁碟檔案`MyTexture.bmp`。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="e5b4b-123">![填滿形狀](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="e5b4b-124">下列程式碼範例示範如何藉由重複圖片儲存在填滿橢圓形`MyTexture.bmp`。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="e5b4b-125">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="e5b4b-126">![填滿形狀](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="e5b4b-127">漸層筆刷</span><span class="sxs-lookup"><span data-stu-id="e5b4b-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="e5b4b-128">提供的漸層筆刷的兩種類型： 線性和路徑。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-128">provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="e5b4b-129">若要變更逐漸，當您移動形狀之間水平、 垂直或對角線方式的色彩填滿圖形，您可以使用線性漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="e5b4b-130">下列程式碼範例示範如何使用變更從藍綠色當您從省略符號的左邊緣移至 右邊緣的水平漸層筆刷填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="e5b4b-131">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="e5b4b-132">![填滿形狀](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="e5b4b-133">若要變更色彩，當您從邊緣，圖案的中心移動，可以設定路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="e5b4b-134">![填滿形狀](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="e5b4b-135">路徑漸層筆刷會很有彈性。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="e5b4b-136">漸層筆刷，用來填滿每個頂點的三個不同色彩逐漸從紅色中心下列圖變更中的三角形。</span><span class="sxs-lookup"><span data-stu-id="e5b4b-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="e5b4b-137">![填滿形狀](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="e5b4b-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b4b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5b4b-138">See also</span></span>
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="e5b4b-139">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="e5b4b-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="e5b4b-140">如何：Windows Form 上繪製實心的矩形</span><span class="sxs-lookup"><span data-stu-id="e5b4b-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="e5b4b-141">如何：Windows Form 上繪製實心的橢圓形</span><span class="sxs-lookup"><span data-stu-id="e5b4b-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
