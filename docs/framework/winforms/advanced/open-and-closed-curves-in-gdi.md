---
title: GDI+ 中的開放型和封閉型曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 33a8954296a7e63637ad5e210fb30fba1a3fdd53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165109"
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="425b7-102">GDI+ 中的開放型和封閉型曲線</span><span class="sxs-lookup"><span data-stu-id="425b7-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="425b7-103">下圖顯示兩個曲線： 開啟和其中一個已關閉。</span><span class="sxs-lookup"><span data-stu-id="425b7-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="425b7-104">![開啟 & 封閉型曲線](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="425b7-104">![Open & Closed curves](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="425b7-105">曲線的 managed 的介面</span><span class="sxs-lookup"><span data-stu-id="425b7-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="425b7-106">封閉型曲線有內部，因此可以填滿筆刷。</span><span class="sxs-lookup"><span data-stu-id="425b7-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="425b7-107"><xref:System.Drawing.Graphics>類別內[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供下列方法來填滿封閉的形狀和曲線： <xref:System.Drawing.Graphics.FillRectangle%2A>， <xref:System.Drawing.Graphics.FillEllipse%2A>， <xref:System.Drawing.Graphics.FillPie%2A>， <xref:System.Drawing.Graphics.FillPolygon%2A>， <xref:System.Drawing.Graphics.FillClosedCurve%2A>， <xref:System.Drawing.Graphics.FillPath%2A>，和<xref:System.Drawing.Graphics.FillRegion%2A>。</span><span class="sxs-lookup"><span data-stu-id="425b7-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="425b7-108">每當您呼叫其中一個方法，您必須傳遞其中一個特定的筆刷類型 (<xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，或<xref:System.Drawing.Drawing2D.PathGradientBrush>) 做為引數。</span><span class="sxs-lookup"><span data-stu-id="425b7-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="425b7-109"><xref:System.Drawing.Graphics.FillPie%2A>方法是附隨於<xref:System.Drawing.Graphics.DrawArc%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="425b7-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="425b7-110">就如同<xref:System.Drawing.Graphics.DrawArc%2A>方法會繪製外框的橢圓形，部分<xref:System.Drawing.Graphics.FillPie%2A>方法會填滿橢圓形內部的一部分。</span><span class="sxs-lookup"><span data-stu-id="425b7-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="425b7-111">下列範例會繪製弧形，並填滿橢圓形內部的相對應的部分：</span><span class="sxs-lookup"><span data-stu-id="425b7-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="425b7-112">下圖顯示弧線和填滿的圓形。</span><span class="sxs-lookup"><span data-stu-id="425b7-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="425b7-113">![開啟 & 封閉型曲線](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="425b7-113">![Open & Closed curves](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="425b7-114"><xref:System.Drawing.Graphics.FillClosedCurve%2A>方法是附隨於<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="425b7-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="425b7-115">這兩種方法會藉由連接的起始點的結束點，自動關閉曲線。</span><span class="sxs-lookup"><span data-stu-id="425b7-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="425b7-116">下列範例會繪製曲線通過 （0，0），（60，20），以及 （40、 50）。</span><span class="sxs-lookup"><span data-stu-id="425b7-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="425b7-117">然後曲線會自動關閉連接 （40、 50） 開始的點 （0，0），並使用純色填滿內部。</span><span class="sxs-lookup"><span data-stu-id="425b7-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="425b7-118"><xref:System.Drawing.Graphics.FillPath%2A>方法會填滿之路徑的個別部分的內部互相。</span><span class="sxs-lookup"><span data-stu-id="425b7-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="425b7-119">如果一段路徑不會形成封閉的曲線或圖形，<xref:System.Drawing.Graphics.FillPath%2A>方法會自動關閉該路徑的部分填滿它之前。</span><span class="sxs-lookup"><span data-stu-id="425b7-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="425b7-120">下列範例會繪製，並填滿弧線、 基線曲線、 字串和圓形圖組成的路徑：</span><span class="sxs-lookup"><span data-stu-id="425b7-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="425b7-121">下圖顯示包含或不含純色填滿的路徑。</span><span class="sxs-lookup"><span data-stu-id="425b7-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="425b7-122">請注意，在字串中的文字是所述，但未填入，藉由<xref:System.Drawing.Graphics.DrawPath%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="425b7-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="425b7-123">它是<xref:System.Drawing.Graphics.FillPath%2A>繪製字串中字元的內部互相的方法。</span><span class="sxs-lookup"><span data-stu-id="425b7-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="425b7-124">![路徑中的字串](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="425b7-124">![String in a path](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425b7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="425b7-125">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="425b7-126">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="425b7-126">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="425b7-127">HOW TO：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="425b7-127">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="425b7-128">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="425b7-128">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
