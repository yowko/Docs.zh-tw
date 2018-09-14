---
title: 路徑標記語法
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: d681cd15fa3daa3698edc5e0ad3d3c2669c1dfdf
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519861"
---
# <a name="path-markup-syntax"></a><span data-ttu-id="cfae5-102">路徑標記語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-102">Path Markup Syntax</span></span>
<span data-ttu-id="cfae5-103">路徑中會討論[圖案和基本繪圖中 WPF 概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)並[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)，不過，本主題詳細說明您可以指定路徑中使用功能強大且複雜的迷你語言幾何更簡潔地使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cfae5-103">Paths are discussed in [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) and the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), however, this topic describes in detail the powerful and complex mini-language you can use to specify path geometries more compactly using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a><span data-ttu-id="cfae5-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="cfae5-104">Prerequisites</span></span>  
 <span data-ttu-id="cfae5-105">若要了解本主題，您應該熟悉基本功能的<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="cfae5-105">To understand this topic, you should be familiar with the basic features of <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="cfae5-106">如需詳細資訊，請參閱 <<c0> [ 幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-106">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a><span data-ttu-id="cfae5-107">StreamGeometry 和 PathFigureCollection 迷你語言</span><span class="sxs-lookup"><span data-stu-id="cfae5-107">StreamGeometry and PathFigureCollection Mini-Languages</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="cfae5-108"> 提供提供描述幾何路徑的迷你語言的兩個類別：<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.PathFigureCollection>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-108"> provides two classes that provide mini-languages for describing geometric paths: <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.PathFigureCollection>.</span></span>  
  
-   <span data-ttu-id="cfae5-109">您使用<xref:System.Windows.Media.StreamGeometry>設定類型的屬性時的迷你語言<xref:System.Windows.Media.Geometry>，這類<xref:System.Windows.UIElement.Clip%2A>屬性<xref:System.Windows.UIElement>或<xref:System.Windows.Shapes.Path.Data%2A>屬性<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="cfae5-109">You use the <xref:System.Windows.Media.StreamGeometry> mini-language when setting a property of type <xref:System.Windows.Media.Geometry>, such as the <xref:System.Windows.UIElement.Clip%2A> property of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Shapes.Path.Data%2A> property of a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="cfae5-110">下列範例會使用屬性語法來建立<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-110">The following example uses attribute syntax to create a <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   <span data-ttu-id="cfae5-111">您使用<xref:System.Windows.Media.PathFigureCollection>設定時的迷你語言<xref:System.Windows.Media.PathGeometry.Figures%2A>屬性<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-111">You use the <xref:System.Windows.Media.PathFigureCollection> mini-language when setting the <xref:System.Windows.Media.PathGeometry.Figures%2A> property of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="cfae5-112">下列範例會使用屬性語法來建立<xref:System.Windows.Media.PathFigureCollection>針對<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-112">The following example uses a attribute syntax to create a <xref:System.Windows.Media.PathFigureCollection> for a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 <span data-ttu-id="cfae5-113">在上述範例中，您可以發現這兩個迷你語言非常相似。</span><span class="sxs-lookup"><span data-stu-id="cfae5-113">As you can see from the preceding examples, the two mini-languages are very similar.</span></span> <span data-ttu-id="cfae5-114">就一定能夠使用<xref:System.Windows.Media.PathGeometry>在任何情況下，您可以使用<xref:System.Windows.Media.StreamGeometry>; 因此您應該使用哪一個？</span><span class="sxs-lookup"><span data-stu-id="cfae5-114">It's always possible to use a <xref:System.Windows.Media.PathGeometry> in any situation where you could use a <xref:System.Windows.Media.StreamGeometry>; so which one should you use?</span></span> <span data-ttu-id="cfae5-115">使用 <xref:System.Windows.Media.StreamGeometry>當您不需要修改的路徑建立之後, 使用<xref:System.Windows.Media.PathGeometry>如果您需要修改的路徑。</span><span class="sxs-lookup"><span data-stu-id="cfae5-115">Use a <xref:System.Windows.Media.StreamGeometry> when you don't need to modify the path after creating it; use a <xref:System.Windows.Media.PathGeometry> if you do need to modify the path.</span></span>  
  
 <span data-ttu-id="cfae5-116">如需有關之間的差異<xref:System.Windows.Media.PathGeometry>並<xref:System.Windows.Media.StreamGeometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-116">For more information about the differences between <xref:System.Windows.Media.PathGeometry> and <xref:System.Windows.Media.StreamGeometry> objects, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
### <a name="a-note-about-white-space"></a><span data-ttu-id="cfae5-117">關於空白字元</span><span class="sxs-lookup"><span data-stu-id="cfae5-117">A Note about White Space</span></span>  
 <span data-ttu-id="cfae5-118">為了簡潔起見，會在後續的語法區段中會顯示單一空格，但是在顯示單一空格的位置也接受多個空格。</span><span class="sxs-lookup"><span data-stu-id="cfae5-118">For brevity, a single space is shown in the syntax sections that follow, but multiple spaces are also acceptable wherever a single space is shown.</span></span>  
  
 <span data-ttu-id="cfae5-119">兩個數字不一定要分隔的逗號或空格，但是這只能在明確產生的字串。</span><span class="sxs-lookup"><span data-stu-id="cfae5-119">Two numbers don’t actually have to be separated by a comma or white space, but this can only be done when the resulting string is unambiguous.</span></span> <span data-ttu-id="cfae5-120">比方說，`2..3`是實際的兩個數字:"2"。</span><span class="sxs-lookup"><span data-stu-id="cfae5-120">For instance, `2..3` is actually two numbers: "2."</span></span> <span data-ttu-id="cfae5-121">和 ".3"。</span><span class="sxs-lookup"><span data-stu-id="cfae5-121">And ".3".</span></span> <span data-ttu-id="cfae5-122">同樣地，`2-3`是"2"和"-3"。</span><span class="sxs-lookup"><span data-stu-id="cfae5-122">Similarly, `2-3` is "2" and "-3".</span></span> <span data-ttu-id="cfae5-123">命令之前或之後也一樣不需要空格。</span><span class="sxs-lookup"><span data-stu-id="cfae5-123">Spaces are not required before or after commands, either.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="cfae5-124">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-124">Syntax</span></span>  
 <span data-ttu-id="cfae5-125">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.StreamGeometry>所組成的選擇性<xref:System.Windows.Media.FillRule>值與一個或多個圖描述。</span><span class="sxs-lookup"><span data-stu-id="cfae5-125">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.StreamGeometry> is composed of an optional <xref:System.Windows.Media.FillRule> value and one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="cfae5-126">StreamGeometry XAML 屬性使用方式</span><span class="sxs-lookup"><span data-stu-id="cfae5-126">StreamGeometry XAML Attribute Usage</span></span>|  
|-----------------------------------------|  
|<span data-ttu-id="cfae5-127">`<` *物件\*\*屬性* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] \* `" ... />`</span><span class="sxs-lookup"><span data-stu-id="cfae5-127">`<` *object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]\* `" ... />`</span></span>|  
  
 <span data-ttu-id="cfae5-128">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.PathFigureCollection>是一或多個圖表描述所組成。</span><span class="sxs-lookup"><span data-stu-id="cfae5-128">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.PathFigureCollection> is composed of one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="cfae5-129">PathFigureCollection XAML 屬性使用方式</span><span class="sxs-lookup"><span data-stu-id="cfae5-129">PathFigureCollection XAML Attribute Usage</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="cfae5-130">`<` *物件\*\*屬性* `="` `figureDescription`[ `figureDescription`] \* `" ... />`</span><span class="sxs-lookup"><span data-stu-id="cfae5-130">`<` *object* *property* `="` `figureDescription`[ `figureDescription`]\* `" ... />`</span></span>|  
  
|<span data-ttu-id="cfae5-131">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-131">Term</span></span>|<span data-ttu-id="cfae5-132">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-132">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-133">*fillRule*</span><span class="sxs-lookup"><span data-stu-id="cfae5-133">*fillRule*</span></span>|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-134">指定是否<xref:System.Windows.Media.StreamGeometry>會使用<xref:System.Windows.Media.FillRule.EvenOdd>或是<xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-134">Specifies whether the <xref:System.Windows.Media.StreamGeometry> uses the <xref:System.Windows.Media.FillRule.EvenOdd> or <xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span></span><br /><br /> <span data-ttu-id="cfae5-135">-   `F0` 指定<xref:System.Windows.Media.FillRule.EvenOdd>填滿規則。</span><span class="sxs-lookup"><span data-stu-id="cfae5-135">-   `F0` specifies the <xref:System.Windows.Media.FillRule.EvenOdd> fill rule.</span></span><br /><span data-ttu-id="cfae5-136">-   `F1` 指定<xref:System.Windows.Media.FillRule.Nonzero>填滿規則。</span><span class="sxs-lookup"><span data-stu-id="cfae5-136">-   `F1` specifies the <xref:System.Windows.Media.FillRule.Nonzero> fill rule.</span></span><br /><br /> <span data-ttu-id="cfae5-137">如果您省略這個命令時，子路徑會使用預設行為，也就是<xref:System.Windows.Media.FillRule.EvenOdd>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-137">If you omit this command, the subpath uses the default behavior, which is <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span> <span data-ttu-id="cfae5-138">如果您指定此命令，您必須先放置它。</span><span class="sxs-lookup"><span data-stu-id="cfae5-138">If you specify this command, you must place it first.</span></span>|  
|<span data-ttu-id="cfae5-139">*figureDescription*</span><span class="sxs-lookup"><span data-stu-id="cfae5-139">*figureDescription*</span></span>|<span data-ttu-id="cfae5-140">由移動命令、繪製命令以及選擇性的關閉命令所組成的圖表。</span><span class="sxs-lookup"><span data-stu-id="cfae5-140">A figure composed of a move command, draw commands, and an optional close command.</span></span><br /><br /> <span data-ttu-id="cfae5-141">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span><span class="sxs-lookup"><span data-stu-id="cfae5-141">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span></span>|  
|<span data-ttu-id="cfae5-142">*moveCommand*</span><span class="sxs-lookup"><span data-stu-id="cfae5-142">*moveCommand*</span></span>|<span data-ttu-id="cfae5-143">指定圖表起點的移動命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-143">A move command that specifies the start point of the figure.</span></span> <span data-ttu-id="cfae5-144">請參閱[移動命令](#themovecommand)一節。</span><span class="sxs-lookup"><span data-stu-id="cfae5-144">See the [Move Command](#themovecommand) section.</span></span>|  
|<span data-ttu-id="cfae5-145">*drawCommands*</span><span class="sxs-lookup"><span data-stu-id="cfae5-145">*drawCommands*</span></span>|<span data-ttu-id="cfae5-146">說明圖表內容的一或多個繪製命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-146">One or more drawing commands that describe the figure's contents.</span></span> <span data-ttu-id="cfae5-147">請參閱[繪製命令](#drawcommands)一節。</span><span class="sxs-lookup"><span data-stu-id="cfae5-147">See the [Draw Commands](#drawcommands) section.</span></span>|  
|<span data-ttu-id="cfae5-148">*closeCommand*</span><span class="sxs-lookup"><span data-stu-id="cfae5-148">*closeCommand*</span></span>|<span data-ttu-id="cfae5-149">關閉圖表的選擇性關閉命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-149">An optional close command that closes figure.</span></span> <span data-ttu-id="cfae5-150">請參閱[關閉命令](#closecommand)一節。</span><span class="sxs-lookup"><span data-stu-id="cfae5-150">See the [Close Command](#closecommand) section.</span></span>|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a><span data-ttu-id="cfae5-151">移動命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-151">Move Command</span></span>  
 <span data-ttu-id="cfae5-152">指定新圖表的起點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-152">Specifies the start point of a new figure.</span></span>  
  
|<span data-ttu-id="cfae5-153">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-153">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-154">`M` *startPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-154">`M` *startPoint*</span></span><br /><br /> <span data-ttu-id="cfae5-155">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-155">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-156">`m` *startPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-156">`m` *startPoint*</span></span>|  
  
|<span data-ttu-id="cfae5-157">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-157">Term</span></span>|<span data-ttu-id="cfae5-158">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-158">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-159">*startPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-159">*startPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-160">新圖表的起點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-160">The start point of a new figure.</span></span>|  
  
 <span data-ttu-id="cfae5-161">以大寫`M`指出`startPoint`為絕對值; 小寫`m`表示`startPoint`是位移至前一個點，或 (0，0) 如果不存在。</span><span class="sxs-lookup"><span data-stu-id="cfae5-161">An uppercase `M` indicates that `startPoint` is an absolute value; a lowercase `m` indicates that `startPoint` is an offset to the previous point, or (0,0) if none exists.</span></span> <span data-ttu-id="cfae5-162">如果您在移動命令之後列出多個點，則會如您指定線條命令一般，在這些點之間繪製線條。</span><span class="sxs-lookup"><span data-stu-id="cfae5-162">If you list multiple points after the move command, a line is drawn to those points though you specified the line command.</span></span>  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a><span data-ttu-id="cfae5-163">繪製命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-163">Draw Commands</span></span>  
 <span data-ttu-id="cfae5-164">繪製命令可以由數個圖形命令組成。</span><span class="sxs-lookup"><span data-stu-id="cfae5-164">A draw command can consist of several shape commands.</span></span> <span data-ttu-id="cfae5-165">有下列圖形命令可使用：線條、水平線、垂直線、三次方貝茲曲線、二次方貝茲曲線、平滑三次方貝茲曲線、平滑二次方貝茲曲線，以及橢圓形弧線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-165">The following shape commands are available: line, horizontal line, vertical line, cubic Bezier curve, quadratic Bezier curve, smooth cubic Bezier curve, smooth quadratic Bezier curve, and elliptical arc.</span></span>  
  
 <span data-ttu-id="cfae5-166">透過使用大寫或小寫字母來輸入每個命令：大寫字母表示絕對值，而小寫字母表示相對值：該區段的控制點相對於先前範例的結束點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-166">You enter each command by using either an uppercase or a lowercase letter: uppercase letters denote absolute values and lowercase letters denote relative values: the control points for that segment are relative to the end point of the preceding example.</span></span> <span data-ttu-id="cfae5-167">依序輸入相同類型的多個命令時，您就可以省略重複的命令輸入;例如，`L 100,200 300,400`相當於`L 100,200 L 300,400`。</span><span class="sxs-lookup"><span data-stu-id="cfae5-167">When sequentially entering more than one command of the same type, you can omit the duplicate command entry; for example, `L 100,200 300,400` is equivalent to `L 100,200 L 300,400`.</span></span> <span data-ttu-id="cfae5-168">下表描述**移動**並**繪製**命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-168">The following table describes the **move** and **draw** commands.</span></span>  
  
### <a name="line-command"></a><span data-ttu-id="cfae5-169">線條命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-169">Line Command</span></span>  
 <span data-ttu-id="cfae5-170">在目前的點和指定的點之間建立直線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-170">Creates a straight line between the current point and the specified end point.</span></span> <span data-ttu-id="cfae5-171">`l 20 30` 並`L 20,30`都是有效的範例**列**命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-171">`l 20 30` and `L 20,30` are examples of valid **line** commands.</span></span>  
  
|<span data-ttu-id="cfae5-172">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-172">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-173">`L` *endPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-173">`L` *endPoint*</span></span><br /><br /> <span data-ttu-id="cfae5-174">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-174">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-175">`l` *endPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-175">`l` *endPoint*</span></span>|  
  
|<span data-ttu-id="cfae5-176">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-176">Term</span></span>|<span data-ttu-id="cfae5-177">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-177">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-178">*endPoint*</span><span class="sxs-lookup"><span data-stu-id="cfae5-178">*endPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-179">行的結束點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-179">The end point of the line.</span></span>|  

<span data-ttu-id="cfae5-180">以大寫`L`指出`endPoint`為絕對值; 小寫`l`表示`endPoint`是位移至前一個點，或 (0，0) 如果不存在。</span><span class="sxs-lookup"><span data-stu-id="cfae5-180">An uppercase `L` indicates that `endPoint` is an absolute value; a lowercase `l` indicates that `endPoint` is an offset to the previous point, or (0,0) if none exists.</span></span>

### <a name="horizontal-line-command"></a><span data-ttu-id="cfae5-181">水平線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-181">Horizontal Line Command</span></span>  
 <span data-ttu-id="cfae5-182">在目前的點和指定的 X 座標之間建立水平線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-182">Creates a horizontal line between the current point and the specified x-coordinate.</span></span> <span data-ttu-id="cfae5-183">`H 90` 為有效水平線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="cfae5-183">`H 90` is an example of a valid horizontal line command.</span></span>

  
|<span data-ttu-id="cfae5-184">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-184">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-185">`H`  *x*</span><span class="sxs-lookup"><span data-stu-id="cfae5-185">`H`  *x*</span></span><br /><br /> <span data-ttu-id="cfae5-186">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-186">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-187">`h`  *x*</span><span class="sxs-lookup"><span data-stu-id="cfae5-187">`h`  *x*</span></span>|  
  
|<span data-ttu-id="cfae5-188">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-188">Term</span></span>|<span data-ttu-id="cfae5-189">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-189">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-190">*x*</span><span class="sxs-lookup"><span data-stu-id="cfae5-190">*x*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-191">線條結束點的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="cfae5-191">The x-coordinate of the end point of the line.</span></span>|  
  
<span data-ttu-id="cfae5-192">以大寫`H`指出`x`為絕對值; 小寫`h`表示`x`是位移至前一個點，或 (0，0) 如果不存在。</span><span class="sxs-lookup"><span data-stu-id="cfae5-192">An uppercase `H` indicates that `x` is an absolute value; a lowercase `h` indicates that `x` is an offset to the previous point, or (0,0) if none exists.</span></span>
  
### <a name="vertical-line-command"></a><span data-ttu-id="cfae5-193">垂直線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-193">Vertical Line Command</span></span>  
 <span data-ttu-id="cfae5-194">在目前的點和指定的 Y 座標之間建立垂直線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-194">Creates a vertical line between the current point and the specified y-coordinate.</span></span> <span data-ttu-id="cfae5-195">`v 90` 為有效垂直線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="cfae5-195">`v 90` is an example of a valid vertical line command.</span></span>

  
|<span data-ttu-id="cfae5-196">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-196">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-197">`V`  *y*</span><span class="sxs-lookup"><span data-stu-id="cfae5-197">`V`  *y*</span></span><br /><br /> <span data-ttu-id="cfae5-198">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-198">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-199">`v`  *y*</span><span class="sxs-lookup"><span data-stu-id="cfae5-199">`v`  *y*</span></span>|  
  
|<span data-ttu-id="cfae5-200">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-200">Term</span></span>|<span data-ttu-id="cfae5-201">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-201">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-202">*y*</span><span class="sxs-lookup"><span data-stu-id="cfae5-202">*y*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-203">線條結束點的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="cfae5-203">The y-coordinate of the end point of the line.</span></span>|  

<span data-ttu-id="cfae5-204">以大寫`V`指出`y`為絕對值; 小寫`v`表示`y`是位移至前一個點，或 (0，0) 如果不存在。</span><span class="sxs-lookup"><span data-stu-id="cfae5-204">An uppercase `V` indicates that `y` is an absolute value; a lowercase `v` indicates that `y` is an offset to the previous point, or (0,0) if none exists.</span></span>  
    
### <a name="cubic-bezier-curve-command"></a><span data-ttu-id="cfae5-205">三次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-205">Cubic Bezier Curve Command</span></span>  
 <span data-ttu-id="cfae5-206">建立三次方貝茲曲線目前點和指定的結束點之間使用兩個指定的控制點 (`controlPoint`1 和`controlPoint`2)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-206">Creates a cubic Bezier curve between the current point and the specified end point by using the two specified control points (`controlPoint`1 and `controlPoint`2).</span></span> <span data-ttu-id="cfae5-207">`C 100,200 200,400 300,200` 為有效曲線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="cfae5-207">`C 100,200 200,400 300,200` is an example of a valid curve command.</span></span>  
  
|<span data-ttu-id="cfae5-208">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-208">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-209">`C` `controlPoint`1`controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-209">`C` `controlPoint`1`controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="cfae5-210">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-210">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-211">`c` `controlPoint`1`controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-211">`c` `controlPoint`1`controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="cfae5-212">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-212">Term</span></span>|<span data-ttu-id="cfae5-213">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-213">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-214">`controlPoint`1</span><span class="sxs-lookup"><span data-stu-id="cfae5-214">`controlPoint`1</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-215">曲線的第一個控制點，它能決定曲線的起始正切函數。</span><span class="sxs-lookup"><span data-stu-id="cfae5-215">The first control point of the curve, which determines the starting tangent of the curve.</span></span>|  
|<span data-ttu-id="cfae5-216">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="cfae5-216">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-217">曲線的第二個控制點，它能決定曲線的結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="cfae5-217">The second control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-218">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-218">The point to which the curve is drawn.</span></span>|  
  
### <a name="quadratic-bezier-curve-command"></a><span data-ttu-id="cfae5-219">二次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-219">Quadratic Bezier Curve Command</span></span>  
 <span data-ttu-id="cfae5-220">建立二次方的貝茲曲線，目前的點和指定的結束點之間使用指定的控制點 (`controlPoint`)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-220">Creates a quadratic Bezier curve between the current point and the specified end point by using the specified control point (`controlPoint`).</span></span> <span data-ttu-id="cfae5-221">`q 100,200 300,200` 為有效二次方貝茲曲線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="cfae5-221">`q 100,200 300,200` is an example of a valid quadratic Bezier curve command.</span></span>  
  
|<span data-ttu-id="cfae5-222">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-222">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-223">`Q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-223">`Q` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="cfae5-224">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-224">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-225">`q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-225">`q` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="cfae5-226">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-226">Term</span></span>|<span data-ttu-id="cfae5-227">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-227">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-228">曲線的控制點，它能決定曲線的起始正切函數和結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="cfae5-228">The control point of the curve, which determines the starting and ending tangents of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-229">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-229">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-cubic-bezier-curve-command"></a><span data-ttu-id="cfae5-230">平滑三次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-230">Smooth cubic Bezier curve Command</span></span>  
 <span data-ttu-id="cfae5-231">在目前的點和指定的結束點之間建立三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-231">Creates a cubic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="cfae5-232">第一個控制點會假設為 (相對於目前的點) 上一個命令之第二個控制點的反映。</span><span class="sxs-lookup"><span data-stu-id="cfae5-232">The first control point is assumed to be the reflection of the second control point of the previous command relative to the current point.</span></span> <span data-ttu-id="cfae5-233">如果沒有上一個命令，或者上一個命令不是三次方貝茲曲線命令或平滑三次方貝茲曲線命令，則會假設第一個控制點和目前的點一致。</span><span class="sxs-lookup"><span data-stu-id="cfae5-233">If there is no previous command or if the previous command was not a cubic Bezier curve command or a smooth cubic Bezier curve command, assume the first control point is coincident with the current point.</span></span> <span data-ttu-id="cfae5-234">第二個控制點，曲線結尾的控制點所指定`controlPoint`2。</span><span class="sxs-lookup"><span data-stu-id="cfae5-234">The second control point, the control point for the end of the curve, is specified by `controlPoint`2.</span></span> <span data-ttu-id="cfae5-235">比方說，`S 100,200 200,300`是有效平滑三次方貝茲曲線命令。</span><span class="sxs-lookup"><span data-stu-id="cfae5-235">For example, `S 100,200 200,300` is a valid smooth cubic Bezier curve command.</span></span>  
  
|<span data-ttu-id="cfae5-236">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-236">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-237">`S` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-237">`S` `controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="cfae5-238">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-238">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-239">`s` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-239">`s` `controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="cfae5-240">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-240">Term</span></span>|<span data-ttu-id="cfae5-241">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-241">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cfae5-242">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="cfae5-242">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-243">曲線的控制點，它能決定曲線的結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="cfae5-243">The control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-244">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-244">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a><span data-ttu-id="cfae5-245">平滑二次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-245">Smooth quadratic Bezier curve Command</span></span>  
 <span data-ttu-id="cfae5-246">在目前的點和指定的結束點之間建立二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-246">Creates a quadratic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="cfae5-247">控制點會假設為 (相對於目前的點) 上一個命令之控制點的反映。</span><span class="sxs-lookup"><span data-stu-id="cfae5-247">The control point is assumed to be the reflection of the control point of the previous command relative to the current point.</span></span> <span data-ttu-id="cfae5-248">如果沒有上一個命令，或者上一個命令不是二次方貝茲曲線命令或平滑二次方貝茲曲線命令，則控制點和目前的點一致。</span><span class="sxs-lookup"><span data-stu-id="cfae5-248">If there is no previous command or if the previous command was not a quadratic Bezier curve command or a smooth quadratic Bezier curve command, the control point is coincident with the current point.</span></span>  
  
|<span data-ttu-id="cfae5-249">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-249">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-250">`T` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-250">`T` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="cfae5-251">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-251">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-252">`t` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-252">`t` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="cfae5-253">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-253">Term</span></span>|<span data-ttu-id="cfae5-254">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-254">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-255">曲線的控制點，它能決定曲線的起始正切函數。</span><span class="sxs-lookup"><span data-stu-id="cfae5-255">The control point of the curve, which determines the starting and tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-256">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-256">The point to which the curve is drawn.</span></span>|  
  
### <a name="elliptical-arc-command"></a><span data-ttu-id="cfae5-257">橢圓形弧線命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-257">Elliptical Arc Command</span></span>  
 <span data-ttu-id="cfae5-258">在目前的點和指定的結束點之間建立橢圓形弧線。</span><span class="sxs-lookup"><span data-stu-id="cfae5-258">Creates an elliptical arc between the current point and the specified end point.</span></span>  
  
|<span data-ttu-id="cfae5-259">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-259">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-260">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-260">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span><br /><br /> <span data-ttu-id="cfae5-261">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-261">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-262">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="cfae5-262">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span>|  
  
|<span data-ttu-id="cfae5-263">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-263">Term</span></span>|<span data-ttu-id="cfae5-264">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-264">Description</span></span>|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-265">弧線的半徑 X 和 Y。</span><span class="sxs-lookup"><span data-stu-id="cfae5-265">The x- and y-radius of the arc.</span></span>|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-266">橢圓形的旋轉 (以角度為單位)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-266">The rotation of the ellipse, in degrees.</span></span>|  
|`isLargeArcFlag`|<span data-ttu-id="cfae5-267">如果弧線的角度應該為 180 度或大於 180 度，則設定為 1；否則，請設定為 0。</span><span class="sxs-lookup"><span data-stu-id="cfae5-267">Set to 1 if the angle of the arc should be 180 degrees or greater; otherwise, set to 0.</span></span>|  
|`sweepDirectionFlag`|<span data-ttu-id="cfae5-268">如果弧線是以正值角度的方向繪製，則設定為 1；否則，請設定為 0。</span><span class="sxs-lookup"><span data-stu-id="cfae5-268">Set to 1 if the arc is drawn in a positive-angle direction; otherwise, set to 0.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-269">弧線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="cfae5-269">The point to which the arc is drawn.</span></span>|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a><span data-ttu-id="cfae5-270">關閉命令</span><span class="sxs-lookup"><span data-stu-id="cfae5-270">The Close Command</span></span>  
 <span data-ttu-id="cfae5-271">結束目前的圖表，並建立連接目前的點和圖表起點的線條。</span><span class="sxs-lookup"><span data-stu-id="cfae5-271">Ends the current figure and creates a line that connects the current point to the starting point of the figure.</span></span> <span data-ttu-id="cfae5-272">此命令會在圖表的最後一個區段和第一個區段之間建立線條聯結 (邊角)。</span><span class="sxs-lookup"><span data-stu-id="cfae5-272">This command creates a line-join (corner) between the last segment and the first segment of the figure.</span></span>  
  
|<span data-ttu-id="cfae5-273">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-273">Syntax</span></span>|  
|------------|  
|`Z`<br /><br /> <span data-ttu-id="cfae5-274">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-274">- or -</span></span><br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a><span data-ttu-id="cfae5-275">點語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-275">Point Syntax</span></span>  
 <span data-ttu-id="cfae5-276">描述點 x 和 y 座標位置 (0，0) 是左上的角。</span><span class="sxs-lookup"><span data-stu-id="cfae5-276">Describes the x- and y-coordinates of a point where (0,0) is the top left corner.</span></span>
  
|<span data-ttu-id="cfae5-277">語法</span><span class="sxs-lookup"><span data-stu-id="cfae5-277">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="cfae5-278">`x` `,` `y`</span><span class="sxs-lookup"><span data-stu-id="cfae5-278">`x` `,` `y`</span></span><br /><br /> <span data-ttu-id="cfae5-279">-或-</span><span class="sxs-lookup"><span data-stu-id="cfae5-279">- or -</span></span><br /><br /> <span data-ttu-id="cfae5-280">`x` `y`</span><span class="sxs-lookup"><span data-stu-id="cfae5-280">`x` `y`</span></span>|  
  
|<span data-ttu-id="cfae5-281">詞彙</span><span class="sxs-lookup"><span data-stu-id="cfae5-281">Term</span></span>|<span data-ttu-id="cfae5-282">描述</span><span class="sxs-lookup"><span data-stu-id="cfae5-282">Description</span></span>|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-283">點的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="cfae5-283">The x-coordinate of the point.</span></span>|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="cfae5-284">點的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="cfae5-284">The y-coordinate of the point.</span></span>|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a><span data-ttu-id="cfae5-285">特殊值</span><span class="sxs-lookup"><span data-stu-id="cfae5-285">Special Values</span></span>  
 <span data-ttu-id="cfae5-286">除了標準數值，您也可以使用下列特殊值。</span><span class="sxs-lookup"><span data-stu-id="cfae5-286">Instead of a standard numerical value, you can also use the following special values.</span></span> <span data-ttu-id="cfae5-287">這些值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="cfae5-287">These values are case-sensitive.</span></span>  
  
 <span data-ttu-id="cfae5-288">Infinity</span><span class="sxs-lookup"><span data-stu-id="cfae5-288">Infinity</span></span>  
 <span data-ttu-id="cfae5-289">代表<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-289">Represents <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cfae5-290">-Infinity</span><span class="sxs-lookup"><span data-stu-id="cfae5-290">-Infinity</span></span>  
 <span data-ttu-id="cfae5-291">代表<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-291">Represents <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cfae5-292">NaN</span><span class="sxs-lookup"><span data-stu-id="cfae5-292">NaN</span></span>  
 <span data-ttu-id="cfae5-293">代表<xref:System.Double.NaN?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cfae5-293">Represents <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cfae5-294">您也可以使用科學記號標記法。</span><span class="sxs-lookup"><span data-stu-id="cfae5-294">You may also use scientific notation.</span></span> <span data-ttu-id="cfae5-295">比方說，`+1.e17`是有效的值。</span><span class="sxs-lookup"><span data-stu-id="cfae5-295">For example, `+1.e17` is a valid value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfae5-296">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfae5-296">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [<span data-ttu-id="cfae5-297">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="cfae5-297">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="cfae5-298">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="cfae5-298">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="cfae5-299">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="cfae5-299">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
