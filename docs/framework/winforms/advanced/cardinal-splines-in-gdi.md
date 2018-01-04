---
title: "GDI+ 中的基本曲線"
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
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b7653e05fff241f05836624ff02273fb8c24ef6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cardinal-splines-in-gdi"></a><span data-ttu-id="88b19-102">GDI+ 中的基本曲線</span><span class="sxs-lookup"><span data-stu-id="88b19-102">Cardinal Splines in GDI+</span></span>
<span data-ttu-id="88b19-103">基本曲線是一連串個別聯結成更大的曲線的曲線。</span><span class="sxs-lookup"><span data-stu-id="88b19-103">A cardinal spline is a sequence of individual curves joined to form a larger curve.</span></span> <span data-ttu-id="88b19-104">曲線的點和張力參數陣列所指定。</span><span class="sxs-lookup"><span data-stu-id="88b19-104">The spline is specified by an array of points and a tension parameter.</span></span> <span data-ttu-id="88b19-105">基本曲線平滑通過陣列; 中的每個點有沒有尖角和曲線的 tightness 沒有突然變更。</span><span class="sxs-lookup"><span data-stu-id="88b19-105">A cardinal spline passes smoothly through each point in the array; there are no sharp corners and no abrupt changes in the tightness of the curve.</span></span> <span data-ttu-id="88b19-106">下圖顯示一組點和通過集中的每個點的基本曲線。</span><span class="sxs-lookup"><span data-stu-id="88b19-106">The following illustration shows a set of points and a cardinal spline that passes through each point in the set.</span></span>  
  
 <span data-ttu-id="88b19-107">![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")</span><span class="sxs-lookup"><span data-stu-id="88b19-107">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")</span></span>  
  
## <a name="physical-and-mathematical-splines"></a><span data-ttu-id="88b19-108">實體和數學曲線</span><span class="sxs-lookup"><span data-stu-id="88b19-108">Physical and Mathematical Splines</span></span>  
 <span data-ttu-id="88b19-109">實體的曲線是指薄木材或其他彈性的資料。</span><span class="sxs-lookup"><span data-stu-id="88b19-109">A physical spline is a thin piece of wood or other flexible material.</span></span> <span data-ttu-id="88b19-110">之前的數學曲線，設計工具會用來繪製曲線實體曲線。</span><span class="sxs-lookup"><span data-stu-id="88b19-110">Before the advent of mathematical splines, designers used physical splines to draw curves.</span></span> <span data-ttu-id="88b19-111">設計工具會對於紙張的曲線，而且錨定它指定的點集合。</span><span class="sxs-lookup"><span data-stu-id="88b19-111">A designer would place the spline on a piece of paper and anchor it to a given set of points.</span></span> <span data-ttu-id="88b19-112">在設計工具無法再建立曲線沿著曲線繪製與畫筆或鉛筆。</span><span class="sxs-lookup"><span data-stu-id="88b19-112">The designer could then create a curve by drawing along the spline with a pen or pencil.</span></span> <span data-ttu-id="88b19-113">指定的點集合可能會產生不同的曲線，視實體曲線的內容。</span><span class="sxs-lookup"><span data-stu-id="88b19-113">A given set of points could yield a variety of curves, depending on the properties of the physical spline.</span></span> <span data-ttu-id="88b19-114">例如，和彎曲的曲線會產生不同曲線比具有彈性的曲線。</span><span class="sxs-lookup"><span data-stu-id="88b19-114">For example, a spline with a high resistance to bending would produce a different curve than an extremely flexible spline.</span></span>  
  
 <span data-ttu-id="88b19-115">讓所產生的數學曲線的曲線如下一次作業所產生的實體曲線的曲線數學曲線公式為基礎的彈性的木棍屬性。</span><span class="sxs-lookup"><span data-stu-id="88b19-115">The formulas for mathematical splines are based on the properties of flexible rods, so the curves produced by mathematical splines are similar to the curves that were once produced by physical splines.</span></span> <span data-ttu-id="88b19-116">就如同實體不同張力的曲線會產生不同的曲線，透過指定的點集合，數學曲線的張力參數不同的值將會產生不同曲線透過指定的點集合。</span><span class="sxs-lookup"><span data-stu-id="88b19-116">Just as physical splines of different tension will produce different curves through a given set of points, mathematical splines with different values for the tension parameter will produce different curves through a given set of points.</span></span> <span data-ttu-id="88b19-117">下圖顯示四個通過相同的一組點的基本曲線。</span><span class="sxs-lookup"><span data-stu-id="88b19-117">The following illustration shows four cardinal splines passing through the same set of points.</span></span> <span data-ttu-id="88b19-118">則會顯示每個曲線的張力。</span><span class="sxs-lookup"><span data-stu-id="88b19-118">The tension is shown for each spline.</span></span> <span data-ttu-id="88b19-119">張力 0 會對應至無限實體的張力，強迫曲線採取點之間最短的方式 （直線）。</span><span class="sxs-lookup"><span data-stu-id="88b19-119">A tension of 0 corresponds to infinite physical tension, forcing the curve to take the shortest way (straight lines) between points.</span></span> <span data-ttu-id="88b19-120">張力 1 對應至任何實體的張力，允許曲線至少總彎曲的路徑。</span><span class="sxs-lookup"><span data-stu-id="88b19-120">A tension of 1 corresponds to no physical tension, allowing the spline to take the path of least total bend.</span></span> <span data-ttu-id="88b19-121">張力值大於 1，曲線行為就像壓縮 spring，推送至需要較長的路徑。</span><span class="sxs-lookup"><span data-stu-id="88b19-121">With tension values greater than 1, the curve behaves like a compressed spring, pushed to take a longer path.</span></span>  
  
 <span data-ttu-id="88b19-122">![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")</span><span class="sxs-lookup"><span data-stu-id="88b19-122">![Cardinal Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")</span></span>  
  
 <span data-ttu-id="88b19-123">在上圖中的四個曲線共用相同的切線在起始點。</span><span class="sxs-lookup"><span data-stu-id="88b19-123">The four splines in the preceding illustration share the same tangent line at the starting point.</span></span> <span data-ttu-id="88b19-124">將正切函數是從起始點繪製到下一個點沿著曲線的線條。</span><span class="sxs-lookup"><span data-stu-id="88b19-124">The tangent is the line drawn from the starting point to the next point along the curve.</span></span> <span data-ttu-id="88b19-125">同樣地，共用的正切函數結束點是曲線上繪製的結束點從先前的點的線條。</span><span class="sxs-lookup"><span data-stu-id="88b19-125">Likewise, the shared tangent at the ending point is the line drawn from the ending point to the previous point on the curve.</span></span>  
  
 <span data-ttu-id="88b19-126">若要繪製基本曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別， <xref:System.Drawing.Pen>，以及陣列<xref:System.Drawing.Point>物件的執行個體<xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.DrawCurve%2A>方法，這個方法會繪製曲線，和<xref:System.Drawing.Pen>儲存曲線，例如線條寬度和色彩的屬性。</span><span class="sxs-lookup"><span data-stu-id="88b19-126">To draw a cardinal spline, you need an instance of the <xref:System.Drawing.Graphics> class, a <xref:System.Drawing.Pen>, and an array of <xref:System.Drawing.Point> objects The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawCurve%2A> method, which draws the spline, and the <xref:System.Drawing.Pen> stores attributes of the spline, such as line width and color.</span></span> <span data-ttu-id="88b19-127">陣列<xref:System.Drawing.Point>物件將會通過曲線的點。</span><span class="sxs-lookup"><span data-stu-id="88b19-127">The array of <xref:System.Drawing.Point> objects stores the points that the curve will pass through.</span></span> <span data-ttu-id="88b19-128">下列程式碼範例顯示如何畫通過中點的基本曲線`myPointArray`。</span><span class="sxs-lookup"><span data-stu-id="88b19-128">The following code example shows how to draw a cardinal spline that passes through the points in `myPointArray`.</span></span> <span data-ttu-id="88b19-129">第三個參數是張力。</span><span class="sxs-lookup"><span data-stu-id="88b19-129">The third parameter is the tension.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="88b19-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="88b19-130">See Also</span></span>  
 [<span data-ttu-id="88b19-131">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="88b19-131">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="88b19-132">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="88b19-132">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
