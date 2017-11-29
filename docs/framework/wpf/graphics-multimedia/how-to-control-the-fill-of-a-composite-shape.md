---
title: "操作說明：控制複合圖案的填色"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5730b930a4f863ad01fcb6153d9bfd8f700fdb92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a><span data-ttu-id="ee68f-102">操作說明：控制複合圖案的填色</span><span class="sxs-lookup"><span data-stu-id="ee68f-102">How to: Control the Fill of a Composite Shape</span></span>
<span data-ttu-id="ee68f-103"><xref:System.Windows.Media.GeometryGroup.FillRule%2A>屬性<xref:System.Windows.Media.GeometryGroup>或<xref:System.Windows.Media.PathGeometry>，指定 「 規則 」 複合圖形會用來判斷指定的點是否幾何的一部分。</span><span class="sxs-lookup"><span data-stu-id="ee68f-103">The <xref:System.Windows.Media.GeometryGroup.FillRule%2A> property of a <xref:System.Windows.Media.GeometryGroup> or a <xref:System.Windows.Media.PathGeometry>, specifies a "rule" which the composite shape uses to determine whether a given point is part of the geometry.</span></span> <span data-ttu-id="ee68f-104">有兩個可能的值為<xref:System.Windows.Media.FillRule>:<xref:System.Windows.Media.FillRule.EvenOdd>和<xref:System.Windows.Media.FillRule.Nonzero>。</span><span class="sxs-lookup"><span data-stu-id="ee68f-104">There are two possible values for <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> and <xref:System.Windows.Media.FillRule.Nonzero>.</span></span> <span data-ttu-id="ee68f-105">以下各節將說明如何使用這兩個規則。</span><span class="sxs-lookup"><span data-stu-id="ee68f-105">The following sections will describe how to use these two rules.</span></span>  
  
 <span data-ttu-id="ee68f-106">**EvenOdd：**這個規則會從某個點朝任意方向繪製無限遠的光線，並且計算給定圖案中與光線相交的路徑線段數目，以判斷該點是否在填滿區域中。</span><span class="sxs-lookup"><span data-stu-id="ee68f-106">**EvenOdd:** This rule determines whether a point is in the fill region by drawing a ray from that point to infinity in any direction and counting the number of path segments within the given shape that the ray crosses.</span></span> <span data-ttu-id="ee68f-107">如果這個數字是奇數，該點即是在區域內；如為偶數，該點即在區域外。</span><span class="sxs-lookup"><span data-stu-id="ee68f-107">If this number is odd, the point is inside; if even, the point is outside.</span></span>  
  
 <span data-ttu-id="ee68f-108">例如，以下的 XAML 會建立一系列的同心圓環形 （目標） 所組成的複合圖形<xref:System.Windows.Media.GeometryGroup.FillRule%2A>設<xref:System.Windows.Media.FillRule.EvenOdd>。</span><span class="sxs-lookup"><span data-stu-id="ee68f-108">For example, the XAML below creates a composite shape made up of a series of concentric rings (target) with a <xref:System.Windows.Media.GeometryGroup.FillRule%2A> set to <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 <span data-ttu-id="ee68f-109">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="ee68f-109">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="ee68f-110">![螢幕擷取畫面：EvenOdd 的 FillRule 屬性](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")</span><span class="sxs-lookup"><span data-stu-id="ee68f-110">![Screenshot: FillRule Property of EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")</span></span>  
  
 <span data-ttu-id="ee68f-111">在上圖中，請注意中間和第 3 個環形不會填滿。</span><span class="sxs-lookup"><span data-stu-id="ee68f-111">In the illustration above, notice that the center and 3rd ring are not filled.</span></span> <span data-ttu-id="ee68f-112">這是因為從這兩個環形中的任何點所繪製的光線，會通過偶數數目的線段。</span><span class="sxs-lookup"><span data-stu-id="ee68f-112">This is because a ray drawn from any point within either of those two rings passes through an even number of segments.</span></span> <span data-ttu-id="ee68f-113">請參閱下圖︰</span><span class="sxs-lookup"><span data-stu-id="ee68f-113">See illustration below:</span></span>  
  
 <span data-ttu-id="ee68f-114">![圖表：FillRule 屬性值為 EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")</span><span class="sxs-lookup"><span data-stu-id="ee68f-114">![Diagram: FillRule property value of EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")</span></span>  
  
 <span data-ttu-id="ee68f-115">**NonZero：**這個規則會從某個點朝任意方向繪製無限遠的光線，然後檢查圖案線段與光線相交的位置，以判斷該點是否在路徑填滿區域內。</span><span class="sxs-lookup"><span data-stu-id="ee68f-115">**NonZero:** This rule determines whether a point is in the fill region of the path by drawing a ray from that point to infinity in any direction and then examining the places where a segment of the shape crosses the ray.</span></span> <span data-ttu-id="ee68f-116">從零開始計算，路徑線段每次從左到右與光線交會就加一，每次從右到左與光線交會就減一。</span><span class="sxs-lookup"><span data-stu-id="ee68f-116">Starting with a count of zero, add one each time a Segment crosses the ray from left to right and subtract one each time a path segment crosses the ray from right to left.</span></span> <span data-ttu-id="ee68f-117">計算交會後，如果結果為零，則點即在路徑外。</span><span class="sxs-lookup"><span data-stu-id="ee68f-117">After counting the crossings, if the result is zero then the point is outside the path.</span></span> <span data-ttu-id="ee68f-118">否則就在路徑內。</span><span class="sxs-lookup"><span data-stu-id="ee68f-118">Otherwise, it is inside.</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 <span data-ttu-id="ee68f-119">使用上述的值範例<xref:System.Windows.Media.FillRule.Nonzero>如<xref:System.Windows.Media.GeometryGroup.FillRule%2A>結果提供下圖：</span><span class="sxs-lookup"><span data-stu-id="ee68f-119">Using the example above, a value of <xref:System.Windows.Media.FillRule.Nonzero> for <xref:System.Windows.Media.GeometryGroup.FillRule%2A> gives the following illustration as a result:</span></span>  
  
 <span data-ttu-id="ee68f-120">![螢幕擷取畫面：FillRule 屬性值為 NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")</span><span class="sxs-lookup"><span data-stu-id="ee68f-120">![Screenshot: FillRule value of NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")</span></span>  
  
 <span data-ttu-id="ee68f-121">如您所見，所有環形都會填滿。</span><span class="sxs-lookup"><span data-stu-id="ee68f-121">As you can see, all the rings are filled.</span></span> <span data-ttu-id="ee68f-122">這是因為所有的線段都是相同的方向，因此從任何點所繪製的光線會與一或多個線段交會，而相交的總和不等於零。</span><span class="sxs-lookup"><span data-stu-id="ee68f-122">This is because all the segments are running in the same direction and so a ray drawn from any point will cross one or more segments and the sum of the crossings will not equal zero.</span></span> <span data-ttu-id="ee68f-123">例如，在下圖中，紅色箭頭代表繪製線段的方向，而白色箭頭代表從最內側環形中的點射出的任意光線。</span><span class="sxs-lookup"><span data-stu-id="ee68f-123">For example, in the illustration below, the red arrows represent the direction the segments are drawn and the white arrow represents an arbitrary ray running from a point in the innermost ring.</span></span> <span data-ttu-id="ee68f-124">起始值為零，針對光線交會的每個線段，值會增加 1，因為線段由左至右與光線交會。</span><span class="sxs-lookup"><span data-stu-id="ee68f-124">Starting with a value of zero, for each segment that the ray crosses, a value of one is added because the segment crosses the ray from left to right.</span></span>  
  
 <span data-ttu-id="ee68f-125">![圖表：FillRule 屬性值等於 NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")</span><span class="sxs-lookup"><span data-stu-id="ee68f-125">![Diagram: FillRule property value equal to NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")</span></span>  
  
 <span data-ttu-id="ee68f-126">若要詳細說明的行為<xref:System.Windows.Media.FillRule.Nonzero>規則複雜的圖形，以執行不同方向的區段是必要。</span><span class="sxs-lookup"><span data-stu-id="ee68f-126">To better demonstrate the behavior of <xref:System.Windows.Media.FillRule.Nonzero> rule a more complex shape with segments running in different directions is required.</span></span> <span data-ttu-id="ee68f-127">下列 XAML 程式碼會建立與前一個範例形狀相似之處在於它會透過<xref:System.Windows.Media.PathGeometry>而非<xref:System.Windows.Media.EllipseGeometry>可建立四個同心圓弧形而不是完全關閉同心圓。</span><span class="sxs-lookup"><span data-stu-id="ee68f-127">The XAML code below creates a similar shape as the previous example except that it is created with a <xref:System.Windows.Media.PathGeometry> rather then a <xref:System.Windows.Media.EllipseGeometry> which creates four concentric arcs rather then fully closed concentric circles.</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 <span data-ttu-id="ee68f-128">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="ee68f-128">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="ee68f-129">![螢幕擷取畫面：FillRule 屬性值為 NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")</span><span class="sxs-lookup"><span data-stu-id="ee68f-129">![Screenshot: FillRule property value of NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")</span></span>  
  
 <span data-ttu-id="ee68f-130">請注意，由中心開始的第三個弧形不會填滿。</span><span class="sxs-lookup"><span data-stu-id="ee68f-130">Notice that the third arc from the center is not filled.</span></span> <span data-ttu-id="ee68f-131">下圖說明其原因。</span><span class="sxs-lookup"><span data-stu-id="ee68f-131">The illustration below shows why this is.</span></span> <span data-ttu-id="ee68f-132">在圖中，紅色箭頭代表繪製線段的方向。</span><span class="sxs-lookup"><span data-stu-id="ee68f-132">In the illustration, the red arrows represent the direction the segments are drawn.</span></span> <span data-ttu-id="ee68f-133">兩個白色箭頭代表兩個從「未填滿」區域中的點射出的任意光線。</span><span class="sxs-lookup"><span data-stu-id="ee68f-133">The two white arrows represent two arbitrary rays that move out from a point in the "non-filled" region.</span></span> <span data-ttu-id="ee68f-134">從圖中可以看出，交會線段的指定光線，在其路徑中之值的總和為零。</span><span class="sxs-lookup"><span data-stu-id="ee68f-134">As can be seen from the illustration, the sum of the values from a given ray crossing the segments in its path is zero.</span></span> <span data-ttu-id="ee68f-135">如上面所定義，總和為零表示該點不屬於幾何的一部分 (並非填滿的一部分)，而「非」零的總和 (包含負值) 則屬於幾何的一部分。</span><span class="sxs-lookup"><span data-stu-id="ee68f-135">As defined above, a sum of zero means that the point is not part of the geometry (not part of the fill) while a sum that is *not* zero, including a negative value, is part of the geometry.</span></span>  
  
 <span data-ttu-id="ee68f-136">![圖表：FillRule 屬性值為 NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")</span><span class="sxs-lookup"><span data-stu-id="ee68f-136">![Diagram: FillRule property value of NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")</span></span>  
  
 <span data-ttu-id="ee68f-137">**注意：**目的<xref:System.Windows.Media.FillRule>，所有圖形都視為封閉式。</span><span class="sxs-lookup"><span data-stu-id="ee68f-137">**Note:** For the purposes of <xref:System.Windows.Media.FillRule>, all shapes are considered closed.</span></span> <span data-ttu-id="ee68f-138">如果線段中有間隙，請繪製虛構線段將它封閉。</span><span class="sxs-lookup"><span data-stu-id="ee68f-138">If there is a gap in a segment, draw an imaginary line to close it.</span></span> <span data-ttu-id="ee68f-139">在上面的範例中，環形中有小型的間隙。</span><span class="sxs-lookup"><span data-stu-id="ee68f-139">In the example above, there are small gaps in the rings.</span></span> <span data-ttu-id="ee68f-140">有鑑於此，我們可能會預期通過間隙射出的光線，會提供與另一個方向的光線不同的結果。</span><span class="sxs-lookup"><span data-stu-id="ee68f-140">Given this, one might expect a ray that runs through the gap to give a different result then a ray running in another direction.</span></span> <span data-ttu-id="ee68f-141">以下是放大的圖中的其中一個這些間距和 「 虛數區段 」 (繪製基於套用的區段<xref:System.Windows.Media.FillRule>)，就會關閉它。</span><span class="sxs-lookup"><span data-stu-id="ee68f-141">Below is an enlarged illustration of one of these gaps and the "imaginary segment" (segment that is drawn for purposes of applying the <xref:System.Windows.Media.FillRule>) that closes it.</span></span>  
  
 <span data-ttu-id="ee68f-142">![]圖表：對於 FillRule，線段一定都會封閉(../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")</span><span class="sxs-lookup"><span data-stu-id="ee68f-142">![Diagram: For FillRule, segments are always closed](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee68f-143">範例</span><span class="sxs-lookup"><span data-stu-id="ee68f-143">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee68f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee68f-144">See Also</span></span>  
 [<span data-ttu-id="ee68f-145">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="ee68f-145">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="ee68f-146">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="ee68f-146">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
