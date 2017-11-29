---
title: "GDI+ 中的多邊形"
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
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 740a454873976e407843c417a7b09e5a5218398d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="d3330-102">GDI+ 中的多邊形</span><span class="sxs-lookup"><span data-stu-id="d3330-102">Polygons in GDI+</span></span>
<span data-ttu-id="d3330-103">多邊形是具有三個或多個直線邊封閉的圖形。</span><span class="sxs-lookup"><span data-stu-id="d3330-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="d3330-104">例如，三角形是具有三個邊的多邊形、 矩形是具有四個邊的多邊形和五邊形是具有五個邊的多邊形。</span><span class="sxs-lookup"><span data-stu-id="d3330-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="d3330-105">下圖顯示幾個多邊形。</span><span class="sxs-lookup"><span data-stu-id="d3330-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="d3330-106">![多邊形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="d3330-106">![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="d3330-107">繪製多邊形</span><span class="sxs-lookup"><span data-stu-id="d3330-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="d3330-108">若要繪製多邊形，您需要<xref:System.Drawing.Graphics>物件<xref:System.Drawing.Pen>物件和陣列<xref:System.Drawing.Point>(或<xref:System.Drawing.PointF>) 物件。</span><span class="sxs-lookup"><span data-stu-id="d3330-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="d3330-109"><xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawPolygon%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d3330-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="d3330-110"><xref:System.Drawing.Pen>物件會儲存屬性，例如寬度和色彩，用來呈現多邊形，且陣列的行<xref:System.Drawing.Point>物件會儲存要以直線連接的點。</span><span class="sxs-lookup"><span data-stu-id="d3330-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="d3330-111"><xref:System.Drawing.Pen>物件和陣列<xref:System.Drawing.Point>物件會傳遞做為引數<xref:System.Drawing.Graphics.DrawPolygon%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d3330-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="d3330-112">下列範例會繪製三邊的多邊形。</span><span class="sxs-lookup"><span data-stu-id="d3330-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="d3330-113">請注意，只有三個點`myPointArray`: （0，0） （50，30） 和 （30、 60）。</span><span class="sxs-lookup"><span data-stu-id="d3330-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="d3330-114"><xref:System.Drawing.Graphics.DrawPolygon%2A>方法就會自動關閉多邊形繪製的線 （30、 60） 回起點 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="d3330-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="d3330-115">下圖顯示多邊形。</span><span class="sxs-lookup"><span data-stu-id="d3330-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="d3330-116">![多邊形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="d3330-116">![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3330-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3330-117">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="d3330-118">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="d3330-118">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="d3330-119">操作說明：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="d3330-119">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
