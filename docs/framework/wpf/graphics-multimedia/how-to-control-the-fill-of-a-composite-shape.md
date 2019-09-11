---
title: 作法：控制複合圖形的填色
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855907"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a><span data-ttu-id="8153d-102">作法：控制複合圖形的填色</span><span class="sxs-lookup"><span data-stu-id="8153d-102">How to: Control the Fill of a Composite Shape</span></span>

<span data-ttu-id="8153d-103"><xref:System.Windows.Media.GeometryGroup>或的屬性會指定「規則」 ，讓複合圖形用來判斷指定的點是否為幾何的一部分。<xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.GeometryGroup.FillRule%2A></span><span class="sxs-lookup"><span data-stu-id="8153d-103">The <xref:System.Windows.Media.GeometryGroup.FillRule%2A> property of a <xref:System.Windows.Media.GeometryGroup> or a <xref:System.Windows.Media.PathGeometry>, specifies a "rule" which the composite shape uses to determine whether a given point is part of the geometry.</span></span> <span data-ttu-id="8153d-104">有兩個可能的<xref:System.Windows.Media.FillRule>值： <xref:System.Windows.Media.FillRule.EvenOdd>和。 <xref:System.Windows.Media.FillRule.Nonzero></span><span class="sxs-lookup"><span data-stu-id="8153d-104">There are two possible values for <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> and <xref:System.Windows.Media.FillRule.Nonzero>.</span></span> <span data-ttu-id="8153d-105">以下各節將說明如何使用這兩個規則。</span><span class="sxs-lookup"><span data-stu-id="8153d-105">The following sections will describe how to use these two rules.</span></span>

<span data-ttu-id="8153d-106">**EvenOdd**此規則會以任何方向繪製從該點到無限大的光線，並計算給定形狀中光線相交的路徑線段數目，藉此判斷某個點是否在填滿區域中。</span><span class="sxs-lookup"><span data-stu-id="8153d-106">**EvenOdd:** This rule determines whether a point is in the fill region by drawing a ray from that point to infinity in any direction and counting the number of path segments within the given shape that the ray crosses.</span></span> <span data-ttu-id="8153d-107">如果這個數字是奇數，該點即是在區域內；如為偶數，該點即在區域外。</span><span class="sxs-lookup"><span data-stu-id="8153d-107">If this number is odd, the point is inside; if even, the point is outside.</span></span>

<span data-ttu-id="8153d-108">例如，下列 XAML 會建立由一系列的同心圓（目標）組成的複合圖形， <xref:System.Windows.Media.GeometryGroup.FillRule%2A>其設定為。 <xref:System.Windows.Media.FillRule.EvenOdd></span><span class="sxs-lookup"><span data-stu-id="8153d-108">For example, the XAML below creates a composite shape made up of a series of concentric rings (target) with a <xref:System.Windows.Media.GeometryGroup.FillRule%2A> set to <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

<span data-ttu-id="8153d-109">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="8153d-109">The following illustration shows the shape created in the previous example.</span></span>

![由具有交替色彩的數列同心環組成的圓形。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

<span data-ttu-id="8153d-111">在上圖中，請注意中央和第三個環形不會填滿。</span><span class="sxs-lookup"><span data-stu-id="8153d-111">In the previous illustration, notice that the center and third ring are not filled.</span></span> <span data-ttu-id="8153d-112">這是因為從這兩個環形中的任何點所繪製的光線，會通過偶數數目的線段。</span><span class="sxs-lookup"><span data-stu-id="8153d-112">This is because a ray drawn from any point within either of those two rings passes through an even number of segments.</span></span> <span data-ttu-id="8153d-113">請參閱下圖：</span><span class="sxs-lookup"><span data-stu-id="8153d-113">See the following illustration:</span></span>

![圖表，顯示在圓形中繪製的 EvenOdd 光線。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

<span data-ttu-id="8153d-115">**零下**此規則會以任何方向繪製從該點到無限大的光線，然後檢查圖形線段與光線相交的位置，藉以決定該點是否在路徑填滿區域中。</span><span class="sxs-lookup"><span data-stu-id="8153d-115">**NonZero:** This rule determines whether a point is in the fill region of the path by drawing a ray from that point to infinity in any direction and then examining the places where a segment of the shape crosses the ray.</span></span> <span data-ttu-id="8153d-116">從零開始計算，路徑線段每次從左到右與光線交會就加一，每次從右到左與光線交會就減一。</span><span class="sxs-lookup"><span data-stu-id="8153d-116">Starting with a count of zero, add one each time a Segment crosses the ray from left to right and subtract one each time a path segment crosses the ray from right to left.</span></span> <span data-ttu-id="8153d-117">計算交會後，如果結果為零，則點即在路徑外。</span><span class="sxs-lookup"><span data-stu-id="8153d-117">After counting the crossings, if the result is zero then the point is outside the path.</span></span> <span data-ttu-id="8153d-118">否則就在路徑內。</span><span class="sxs-lookup"><span data-stu-id="8153d-118">Otherwise, it is inside.</span></span>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

<span data-ttu-id="8153d-119">使用上述範例時，的值<xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.GeometryGroup.FillRule%2A>會提供下圖的結果：</span><span class="sxs-lookup"><span data-stu-id="8153d-119">Using the previous example, a value of <xref:System.Windows.Media.FillRule.Nonzero> for <xref:System.Windows.Media.GeometryGroup.FillRule%2A> gives the following illustration as a result:</span></span>

![由一連串同心環形組成的圓形，全都以相同的色彩填滿。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

<span data-ttu-id="8153d-121">如您所見，所有環形都會填滿。</span><span class="sxs-lookup"><span data-stu-id="8153d-121">As you can see, all the rings are filled.</span></span> <span data-ttu-id="8153d-122">這是因為所有的線段都是相同的方向，因此從任何點所繪製的光線會與一或多個線段交會，而相交的總和不等於零。</span><span class="sxs-lookup"><span data-stu-id="8153d-122">This is because all the segments are running in the same direction and so a ray drawn from any point will cross one or more segments and the sum of the crossings will not equal zero.</span></span> <span data-ttu-id="8153d-123">例如，在下圖中，紅色箭號代表線段繪製的方向，而白色箭號代表從最內層環形的某個點執行的任意光線。</span><span class="sxs-lookup"><span data-stu-id="8153d-123">For example, in the following illustration, the red arrows represent the direction the segments are drawn and the white arrow represents an arbitrary ray running from a point in the innermost ring.</span></span> <span data-ttu-id="8153d-124">起始值為零，針對光線交會的每個線段，值會增加 1，因為線段由左至右與光線交會。</span><span class="sxs-lookup"><span data-stu-id="8153d-124">Starting with a value of zero, for each segment that the ray crosses, a value of one is added because the segment crosses the ray from left to right.</span></span>

![顯示 FillRule 屬性值等於非零的圖表。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

<span data-ttu-id="8153d-126">為了更清楚地示範「 <xref:System.Windows.Media.FillRule.Nonzero>規則」的行為，需要以不同的方向執行區段。</span><span class="sxs-lookup"><span data-stu-id="8153d-126">To better demonstrate the behavior of <xref:System.Windows.Media.FillRule.Nonzero> rule a more complex shape with segments running in different directions is required.</span></span> <span data-ttu-id="8153d-127">下列 XAML 程式碼會建立與上一個範例類似的圖形，不同之處在于它<xref:System.Windows.Media.PathGeometry>是使用建立<xref:System.Windows.Media.EllipseGeometry>的，而後者會建立四個同心圓，而不是完全封閉的同心圓。</span><span class="sxs-lookup"><span data-stu-id="8153d-127">The XAML code below creates a similar shape as the previous example except that it is created with a <xref:System.Windows.Media.PathGeometry> rather then a <xref:System.Windows.Media.EllipseGeometry> which creates four concentric arcs rather then fully closed concentric circles.</span></span>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

<span data-ttu-id="8153d-128">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="8153d-128">The following illustration shows the shape created in the previous example.</span></span>

![由數列同心圓組成的圓形，其中包含未填滿第三個弧線的交替色彩。](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

<span data-ttu-id="8153d-130">請注意，由中心開始的第三個弧形不會填滿。</span><span class="sxs-lookup"><span data-stu-id="8153d-130">Notice that the third arc from the center is not filled.</span></span> <span data-ttu-id="8153d-131">下圖顯示為何這種情況。</span><span class="sxs-lookup"><span data-stu-id="8153d-131">The following illustration shows why this is.</span></span> <span data-ttu-id="8153d-132">在圖中，紅色箭頭代表繪製線段的方向。</span><span class="sxs-lookup"><span data-stu-id="8153d-132">In the illustration, the red arrows represent the direction the segments are drawn.</span></span> <span data-ttu-id="8153d-133">兩個白色箭頭代表兩個從「未填滿」區域中的點射出的任意光線。</span><span class="sxs-lookup"><span data-stu-id="8153d-133">The two white arrows represent two arbitrary rays that move out from a point in the "non-filled" region.</span></span> <span data-ttu-id="8153d-134">從圖中可以看出，交會線段的指定光線，在其路徑中之值的總和為零。</span><span class="sxs-lookup"><span data-stu-id="8153d-134">As can be seen from the illustration, the sum of the values from a given ray crossing the segments in its path is zero.</span></span> <span data-ttu-id="8153d-135">如上面所定義，總和為零表示該點不屬於幾何的一部分 (並非填滿的一部分)，而「非」零的總和 (包含負值) 則屬於幾何的一部分。</span><span class="sxs-lookup"><span data-stu-id="8153d-135">As defined above, a sum of zero means that the point is not part of the geometry (not part of the fill) while a sum that is *not* zero, including a negative value, is part of the geometry.</span></span>

![顯示任意光線交叉線段的圖表。](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> <span data-ttu-id="8153d-137">基於的目的<xref:System.Windows.Media.FillRule>，所有圖形都會被視為已關閉。</span><span class="sxs-lookup"><span data-stu-id="8153d-137">For the purposes of <xref:System.Windows.Media.FillRule>, all shapes are considered closed.</span></span> <span data-ttu-id="8153d-138">如果線段中有間隙，請繪製虛構線段將它封閉。</span><span class="sxs-lookup"><span data-stu-id="8153d-138">If there is a gap in a segment, draw an imaginary line to close it.</span></span> <span data-ttu-id="8153d-139">在上面的範例中，環形中有小型的間隙。</span><span class="sxs-lookup"><span data-stu-id="8153d-139">In the example above, there are small gaps in the rings.</span></span> <span data-ttu-id="8153d-140">有鑑於此，我們可能會預期通過間隙射出的光線，會提供與另一個方向的光線不同的結果。</span><span class="sxs-lookup"><span data-stu-id="8153d-140">Given this, one might expect a ray that runs through the gap to give a different result then a ray running in another direction.</span></span> <span data-ttu-id="8153d-141">以下是其中一個間距的放大圖，以及關閉它的「虛數區段」（針對套用所<xref:System.Windows.Media.FillRule>繪製的區段）。</span><span class="sxs-lookup"><span data-stu-id="8153d-141">Below is an enlarged illustration of one of these gaps and the "imaginary segment" (segment that is drawn for purposes of applying the <xref:System.Windows.Media.FillRule>) that closes it.</span></span>

![此圖顯示永遠關閉的 FillRule 區段。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a><span data-ttu-id="8153d-143">範例</span><span class="sxs-lookup"><span data-stu-id="8153d-143">Example</span></span>

## <a name="see-also"></a><span data-ttu-id="8153d-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8153d-144">See also</span></span>

- [<span data-ttu-id="8153d-145">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="8153d-145">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="8153d-146">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="8153d-146">Geometry Overview</span></span>](geometry-overview.md)
